---
title: Rozdział 8 — zdarzenia śledzenia usługi Azure RTO NetX
description: Ten rozdział zawiera opis zdarzeń usługi Azure RTO NetX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: ce355d86d7db0b7e259ae58e306d990277b77a8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824258"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a><span data-ttu-id="e608e-103">Rozdział 8 — zdarzenia śledzenia usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="e608e-103">Chapter 8 - Azure RTOS NetX trace events</span></span>

<span data-ttu-id="e608e-104">Ten rozdział zawiera opis zdarzeń usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-104">This chapter contains a description of the Azure RTOS NetX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="e608e-105">Lista zdarzeń i ikon</span><span class="sxs-lookup"><span data-stu-id="e608e-105">List of Events and Icons</span></span>

<span data-ttu-id="e608e-106">Poniżej znajduje się lista zdarzeń NetX wyświetlanych przez TraceX.</span><span class="sxs-lookup"><span data-stu-id="e608e-106">The following is a list of NetX events displayed by TraceX.</span></span>

| <span data-ttu-id="e608e-107">Ikona</span><span class="sxs-lookup"><span data-stu-id="e608e-107">Icon</span></span>                                           | <span data-ttu-id="e608e-108">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="e608e-108">Meaning</span></span>                 |
| -------------------------------- | ------------------------------------- |
| ![Ikona odbierania żądania w języku R P](./media/user-guide/netx-events/image1.png)    | <span data-ttu-id="e608e-110">Odbieranie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-110">Internal ARP Request Receive</span></span> |
| ![Wewnętrzna ikona wysyłania żądania R P](./media/user-guide/netx-events/image2.png)    | <span data-ttu-id="e608e-112">Wysyłanie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-112">Internal ARP Request Send</span></span> |
| ![Wewnętrzna ikona odbioru odpowiedzi R P](./media/user-guide/netx-events/image3.png)    | <span data-ttu-id="e608e-114">Odbieranie wewnętrznej odpowiedzi ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-114">Internal ARP Response Receive</span></span> |
| ![Wewnętrzna ikona wysyłania odpowiedzi R P](./media/user-guide/netx-events/image4.png)    | <span data-ttu-id="e608e-116">Wysyłanie odpowiedzi wewnętrznego protokołu ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-116">Internal ARP Response Send</span></span> |
| ![Ikona Odbierz wewnętrznej I C M P](./media/user-guide/netx-events/image5.png)    | <span data-ttu-id="e608e-118">Wewnętrzne odbieranie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-118">Internal ICMP Receive</span></span> |
| ![Ikona wysyłania w wewnętrznej I C M P](./media/user-guide/netx-events/image6.png)    | <span data-ttu-id="e608e-120">Wewnętrzne wysyłanie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-120">Internal ICMP Send</span></span> |
| ![Wewnętrzna NetX I G M P ikona odbioru](./media/user-guide/netx-events/image7.png)    | <span data-ttu-id="e608e-122">NetX IGMP — odbieranie</span><span class="sxs-lookup"><span data-stu-id="e608e-122">Internal NetX IGMP Receive</span></span> |
| ![Ikona odbioru wewnętrznego I P](./media/user-guide/netx-events/image8.png)    | <span data-ttu-id="e608e-124">Wewnętrzny adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-124">Internal IP Receive</span></span> |
| ![Ikona wewnętrznej I P wysłania](./media/user-guide/netx-events/image9.png)    | <span data-ttu-id="e608e-126">Wewnętrzny wysyłanie adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-126">Internal IP Send</span></span> |
| ![Ikona odbierania danych wewnętrznych T C P](./media/user-guide/netx-events/image10.png)    | <span data-ttu-id="e608e-128">Odbieranie danych wewnętrznych protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-128">Internal TCP Data Receive</span></span> |
| ![Ikona wysyłania danych wewnętrznych T C P](./media/user-guide/netx-events/image11.png)    | <span data-ttu-id="e608e-130">Wysyłanie danych wewnętrznych protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-130">Internal TCP Data Send</span></span> |
| ![Ikona odbierania noty wewnętrznej T C P](./media/user-guide/netx-events/image12.png)    | <span data-ttu-id="e608e-132">Odbieranie wewnętrznego FIN TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-132">Internal TCP FIN Receive</span></span> |
| ![Ikona wewnętrznej wysyłki P C I N](./media/user-guide/netx-events/image13.png)    | <span data-ttu-id="e608e-134">Wysyłanie wewnętrznego FIN protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-134">Internal TCP FIN Send</span></span> |
| ![Ikona Odbierz wewnętrznego T C P R S T](./media/user-guide/netx-events/image14.png)    | <span data-ttu-id="e608e-136">Wewnętrzny odbieranie protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-136">Internal TCP RST Receive</span></span> |
| ![Ikona wysyłania do wewnątrz T C P R S T](./media/user-guide/netx-events/image15.png)    | <span data-ttu-id="e608e-138">Wewnętrzny parametr TCP RST</span><span class="sxs-lookup"><span data-stu-id="e608e-138">Internal TCP RST Send</span></span> |
| ![Ikona Odbierz wewnętrznej T C P S Y](./media/user-guide/netx-events/image16.png)    | <span data-ttu-id="e608e-140">Odbieranie wewnętrznego protokołu TCP SYN</span><span class="sxs-lookup"><span data-stu-id="e608e-140">Internal TCP SYN Receive</span></span> |
| ![Ikona wysyłania do wewnątrz T C P S Y](./media/user-guide/netx-events/image17.png)    | <span data-ttu-id="e608e-142">Wysyłanie wewnętrznego protokołu TCP SYN</span><span class="sxs-lookup"><span data-stu-id="e608e-142">Internal TCP SYN Send</span></span> |
| ![Wewnętrzna ikona Odbierz U D P](./media/user-guide/netx-events/image18.png)    | <span data-ttu-id="e608e-144">Odbieranie wewnętrznego protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-144">Internal UDP Receive</span></span> |
| ![Wewnętrzna ikona wysyłania U D P](./media/user-guide/netx-events/image19.png)    | <span data-ttu-id="e608e-146">Wewnętrzne wysyłanie UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-146">Internal UDP Send</span></span> |
| ![Ikona odbierania w języku R P](./media/user-guide/netx-events/image20.png)    | <span data-ttu-id="e608e-148">Wewnętrzny RARP odbierania</span><span class="sxs-lookup"><span data-stu-id="e608e-148">Internal RARP Receive</span></span> |
| ![Wewnętrzna ikona wysyłania r A R P](./media/user-guide/netx-events/image21.png)    | <span data-ttu-id="e608e-150">Wewnętrzne wysyłanie RARP</span><span class="sxs-lookup"><span data-stu-id="e608e-150">Internal RARP Send</span></span> |
| ![Ikona wewnętrznej ponownej próby T C P](./media/user-guide/netx-events/image22.png)    | <span data-ttu-id="e608e-152">Wewnętrzna ponowna próba protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-152">Internal TCP Retry</span></span> |
| ![Ikona wewnętrznej zmiany stanu T C P](./media/user-guide/netx-events/image23.png)    | <span data-ttu-id="e608e-154">Zmiana stanu wewnętrznego protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-154">Internal TCP State Change</span></span> |
| ![Ikona wysyłania pakietów sterowników wewnętrznych we/wy](./media/user-guide/netx-events/image24.png)    | <span data-ttu-id="e608e-156">Wysyłanie pakietów sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-156">Internal I/O Driver Packet Send</span></span> |
| ![ikona](./media/user-guide/netx-events/image25.png)    | <span data-ttu-id="e608e-158">Inicjowanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-158">Internal I/O Driver Initialize</span></span> |
| ![Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image26.png)    | <span data-ttu-id="e608e-160">Włączenie linku wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-160">Internal I/O Driver Link Enable</span></span> |
| ![Ikona wyłączenia łącza sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image27.png)    | <span data-ttu-id="e608e-162">Wyłączenie linku wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-162">Internal I/O Driver Link Disable</span></span> |
| ![Ikona transmisji pakietu sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image28.png)    | <span data-ttu-id="e608e-164">Emisja pakietu sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-164">Internal I/O Driver Packet Broadcast</span></span> |
| ![Ikona wysyłania sterownika protokołu ARP wewnętrznej operacji we/wy](./media/user-guide/netx-events/image29.png)    | <span data-ttu-id="e608e-166">Wysyłanie wewnętrznego sterownika we/wy ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-166">Internal I/O Driver ARP Send</span></span> |
| ![Ikona wysyłania odpowiedzi protokołu ARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image30.png)    | <span data-ttu-id="e608e-168">Wysyłanie odpowiedzi do wewnętrznego sterownika we/wy ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-168">Internal I/O Driver ARP Response Send</span></span> |
| ![Ikona wysyłania RARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image31.png)    | <span data-ttu-id="e608e-170">RARP wysyłania sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-170">Internal I/O Driver RARP Send</span></span> |
| ![Ikona wewnętrznej sprzężenia multiemisji sterownika we/wy](./media/user-guide/netx-events/image32.png)    | <span data-ttu-id="e608e-172">Wewnętrzny sprzężenie multiemisji sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-172">Internal I/O Driver Multicast Join</span></span> |
| ![Ikona opuszczania wewnętrznego multiemisji sterownika we/wy](./media/user-guide/netx-events/image33.png)    | <span data-ttu-id="e608e-174">Wyjście z wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-174">Internal I/O Driver Multicast Leave</span></span> |
| ![Ikona stanu pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image34.png)    | <span data-ttu-id="e608e-176">Stan wewnętrznego pobierania sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-176">Internal I/O Driver Get Status</span></span> |
| ![Ikona szybkość pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image35.png)    | <span data-ttu-id="e608e-178">Szybkość uzyskiwania sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-178">Internal I/O Driver Get Speed</span></span> |
| ![Wewnętrzny sterownik we/wy — ikona typu dupleksu](./media/user-guide/netx-events/image36.png)    | <span data-ttu-id="e608e-180">Wewnętrzny sterownik we/wy — dostęp do typu dupleksowego</span><span class="sxs-lookup"><span data-stu-id="e608e-180">Internal I/O Driver Get Duplex Type</span></span> |
| ![Ikona "Pobierz liczbę błędów" sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image37.png)    | <span data-ttu-id="e608e-182">Wystąpił błąd wewnętrzny sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-182">Internal I/O Driver Get Error Count</span></span> |
| ![Ikona licznika odbierania dla sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image38.png)    | <span data-ttu-id="e608e-184">Wewnętrzny sterownik we/wy — pobieranie liczby RX</span><span class="sxs-lookup"><span data-stu-id="e608e-184">Internal I/O Driver Get RX Count</span></span> |
| ![Ikona licznika wysyłania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image39.png)    | <span data-ttu-id="e608e-186">Wewnętrzny sterownik we/wy — pobieranie liczby transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-186">Internal I/O Driver Get TX Count</span></span> |
| ![Ikona wewnętrznego pobierania sterowników we/wy](./media/user-guide/netx-events/image40.png)    | <span data-ttu-id="e608e-188">Wewnętrzny sterownik we/wy — pobieranie błędów alokacji</span><span class="sxs-lookup"><span data-stu-id="e608e-188">Internal I/O Driver Get Allocation Errors</span></span> |
| ![Ikona anulowania inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image41.png)    | <span data-ttu-id="e608e-190">Wewnętrzny sterownik we/wy — anulowanie inicjalizacji</span><span class="sxs-lookup"><span data-stu-id="e608e-190">Internal I/O Driver Un-initialize</span></span> |
| ![Ikona przetwarzania odroczonego sterownika we/wy](./media/user-guide/netx-events/image42.png)    | <span data-ttu-id="e608e-192">Przetwarzanie Odroczone wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-192">Internal I/O Driver Deferred Processing</span></span> |
| ![Ikona unieważnienia wpisów dynamicznych R P](./media/user-guide/netx-events/image43.png)    | <span data-ttu-id="e608e-194">**Unieważnienie wpisów dynamicznych ARP** (*nx_arp_dynamic_entries_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="e608e-194">**ARP Dynamic Entries Invalidate** (*nx_arp_dynamic_entries_invalidate*)</span></span> |
| ![Ikona dynamicznego zestawu wpisów R P](./media/user-guide/netx-events/image44.png)    | <span data-ttu-id="e608e-196">**Dynamiczny zestaw wpisów ARP** (*nx_arp_dynamic_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="e608e-196">**ARP Dynamic Entry Set** (*nx_arp_dynamic_entry_set*)</span></span> |
| ![Ikona włączenia R P](./media/user-guide/netx-events/image45.png)    | <span data-ttu-id="e608e-198">**Włączanie protokołu ARP** (*nx_arp_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-198">**ARP Enable** (*nx_arp_enable*)</span></span> |
| ![Ikona wysyłania na żądanie w języku R P](./media/user-guide/netx-events/image46.png)    | <span data-ttu-id="e608e-200">**Wysyłanie na żądanie protokołu ARP** (*nx_arp_gratuitous_send*)</span><span class="sxs-lookup"><span data-stu-id="e608e-200">**ARP Gratuitous Send** (*nx_arp_gratuitous_send*)</span></span> |
| ![Ikona wyszukiwania adresu sprzętu R P](./media/user-guide/netx-events/image47.png)    | <span data-ttu-id="e608e-202">**Znajdowanie adresu sprzętowego ARP** (*nx_arp_hardware_address_find*)</span><span class="sxs-lookup"><span data-stu-id="e608e-202">**ARP Hardware Address Find** (*nx_arp_hardware_address_find*)</span></span> |
| ![Ikona pobierania informacji R P](./media/user-guide/netx-events/image48.png)    | <span data-ttu-id="e608e-204">**Pobieranie informacji o ARP** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-204">**ARP Information Get** (*nx_arp_info_get*)</span></span> |
| ![Ikona wyszukiwania adresu IP R P](./media/user-guide/netx-events/image49.png)    | <span data-ttu-id="e608e-206">**Znajdź adres IP ARP** (*nx_arp_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="e608e-206">**ARP IP Address Find** (*nx_arp_ip_address_find*)</span></span> |
| ![Ikona tworzenia wpisu statycznego R P](./media/user-guide/netx-events/image50.png)    | <span data-ttu-id="e608e-208">**Tworzenie wpisu statycznego ARP** (*nx_arp_static_entry_create*)</span><span class="sxs-lookup"><span data-stu-id="e608e-208">**ARP Static Entry Create** (*nx_arp_static_entry_create*)</span></span> |
| ![Ikona usuwania wpisów statycznych R P](./media/user-guide/netx-events/image51.png)    | <span data-ttu-id="e608e-210">**Usuwanie wpisów statycznych ARP** (*nx_arp_static_entries_delete*)</span><span class="sxs-lookup"><span data-stu-id="e608e-210">**ARP Static Entries Delete** (*nx_arp_static_entries_delete*)</span></span> |
| ![Ikona usuwania wpisu statycznego R P](./media/user-guide/netx-events/image52.png)    | <span data-ttu-id="e608e-212">**Usuwanie wpisu statycznego ARP** (*nx_arp_static_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="e608e-212">**ARP Static Entry Delete** (*nx_arp_static_entry_delete*)</span></span> |
| ![Ikona usuwania wpisu pamięci podręcznej Duo](./media/user-guide/netx-events/image53.png)    | <span data-ttu-id="e608e-214">**Usuwanie wpisu pamięci podręcznej Duo** (*nxd_nd_cache_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="e608e-214">**Duo Cache Entry Delete** (*nxd_nd_cache_entry_delete*)</span></span> |
| ![Ikona zestawu wpisów pamięci podręcznej Duo](./media/user-guide/netx-events/image54.png)    | <span data-ttu-id="e608e-216">**Zestaw wpisów pamięci podręcznej Duo** (*nxd_nd_cache_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="e608e-216">**Duo Cache Entry Set** (*nxd_nd_cache_entry_set*)</span></span> |
| ![Ikona unieważniania pamięci podręcznej Duo](./media/user-guide/netx-events/image55.png)    | <span data-ttu-id="e608e-218">**Unieważnienie pamięci podręcznej Duo** (*nxd_nd_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="e608e-218">**Duo Cache Invalidate** (*nxd_nd_cache_invalidate*)</span></span> |
| ![Ikona znajdowania pamięci podręcznej Duo I adresu](./media/user-guide/netx-events/image56.png)    | <span data-ttu-id="e608e-220">**Znajdź adres IP pamięci podręcznej Duo** (*nxd_nd_cache_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="e608e-220">**Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*)</span></span> |
| ![Ikona włączania Duo I C M](./media/user-guide/netx-events/image57.png)    | <span data-ttu-id="e608e-222">**Włącz protokół ICMP** (*nxd_icmp_enable*) w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span></span> |
| ![Duo I C M P I P 6 ikona ping](./media/user-guide/netx-events/image58.png)    | <span data-ttu-id="e608e-224">**Żądanie ping protokołu ICMP IPv6** (*nxd_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="e608e-224">**Duo ICMP IPv6 Ping** (*nxd_icmp_ping*)</span></span> |
| ![Ikona wyszukiwania Duo I P z maksymalnym rozmiarem ładunku](./media/user-guide/netx-events/image59.png)    | <span data-ttu-id="e608e-226">**Maksymalny rozmiar ładunku** w programie Duo — znajdź (*nx_max_payload_size_find*)</span><span class="sxs-lookup"><span data-stu-id="e608e-226">**Duo IP Max Payload Size Find** (*nx_max_payload_size_find*)</span></span> |
| ![Ikona odrzuconego wysyłania pakietów w programie Duo I](./media/user-guide/netx-events/image60.png)    | <span data-ttu-id="e608e-228">**Wysyłanie pakietów Raw IP** (*nxd_ip_raw_packet_send*) w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-228">**Duo IP Raw Packet Send** (*nxd_ip_raw_packet_send*)</span></span> |
| ![Ikona dodawania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image61.png)    | <span data-ttu-id="e608e-230">**Dodatek do domyślnego routera IPv6** w programie Duo (*nxd_ipv6_default_router_add*)</span><span class="sxs-lookup"><span data-stu-id="e608e-230">**Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*)</span></span> |
| ![Ikona usuwania domyślnego routera Duo I v 6](./media/user-guide/netx-events/image62.png)    | <span data-ttu-id="e608e-232">**Domyślne usunięcie routera IPv6** w programie Duo (*nxd_ipv6_default_router_delete)*</span><span class="sxs-lookup"><span data-stu-id="e608e-232">**Duo IPv6 Default Router Delete** (*nxd_ipv6_default_router_delete)*</span></span> |
| ![Ikona włączania Duo I v 6](./media/user-guide/netx-events/image63.png)    | <span data-ttu-id="e608e-234">**Włącz protokół IPv6** w programie Duo (*nxd_ipv6_enable)*</span><span class="sxs-lookup"><span data-stu-id="e608e-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span></span> |
| ![Ikona uzyskiwania adresu globalnego Duo I P v 6](./media/user-guide/netx-events/image64.png)    | <span data-ttu-id="e608e-236">**Pobieranie globalnego adresu IPv6** (*nxd_ipv6_global_address_get*) w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-236">**Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*)</span></span> |
| ![Ikona zestawu adresów globalnych Duo I P v 6](./media/user-guide/netx-events/image65.png)    | <span data-ttu-id="e608e-238">**Globalny zestaw adresów IPv6** (*nxd_ipv6_global_address_set*) w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-238">**Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*)</span></span> |
| ![Duo I P v 6 — ikona inicjowania procesu DAD](./media/user-guide/netx-events/image66.png)    | <span data-ttu-id="e608e-240">**Zainicjowanie procesu DAD przez protokół IPv6** (*nxd_ipv6_initiate_dad_process*)</span><span class="sxs-lookup"><span data-stu-id="e608e-240">**Duo IPv6 Initiate Dad Process** (*nxd_ipv6_initiate_dad_process*)</span></span> |
| ![Ikona uzyskiwania adresu interfejsu Duo I P v 6](./media/user-guide/netx-events/image67.png)    | <span data-ttu-id="e608e-242">**Uzyskaj adres interfejsu IPv6** (*nxd_ipv6_interface_address_get*) w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-242">**Duo IPv6 Interface Address Get** (*nxd_ipv6_interface_address_get*)</span></span> |
| ![Ikona zestawu adresów interfejsu Duo I v 6](./media/user-guide/netx-events/image68.png)    | <span data-ttu-id="e608e-244">**Zestaw adresów interfejsu IPv6** (*nxd_ipv6_interface_address_set*) Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-244">**Duo IPv6 Interface Address Set** (*nxd_ipv6_interface_address_set*)</span></span> |
| ![Ikona uzyskiwania adresu lokalnego linku Duo I P 6](./media/user-guide/netx-events/image69.png)    | <span data-ttu-id="e608e-246">**Pobieranie adresu lokalnego linku do protokołu Duo** (*nxd_ipv6_linklocal_address_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-246">**Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*)</span></span> |
| ![Ikona zestawu adresów lokalnych linku Duo I v 6](./media/user-guide/netx-events/image70.png)    | <span data-ttu-id="e608e-248">**Zestaw adresów IPv6 linku Duo** (*nxd_ipv6_linklocal_address_set*)</span><span class="sxs-lookup"><span data-stu-id="e608e-248">**Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*)</span></span> |
| ![Ikona wysyłania pakietów pierwotnych Duo I v 6](./media/user-guide/netx-events/image71.png)    | <span data-ttu-id="e608e-250">**Wysyłanie pakietów RAW IPv6** (*nxd_ipv6_raw_packet_send)* w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-250">**Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)*</span></span> |
| ![Ikona pobierania informacji o komunikacji równorzędnej z gniazdami w programie Duo T C](./media/user-guide/netx-events/image72.png)    | <span data-ttu-id="e608e-252">**Pobieranie informacji o komunikacji równorzędnej gniazda TCP** (*nxd_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-252">**Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*)</span></span> |
| ![Ikona interfejsu zestawu gniazd w programie Duo T C](./media/user-guide/netx-events/image73.png)    | <span data-ttu-id="e608e-254">**Interfejs zestawu gniazd TCP Duo** (*nxd_tcp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="e608e-254">**Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*)</span></span> |
| ![Ikona wysyłania z gniazdem Duo U D P](./media/user-guide/netx-events/image74.png)    | <span data-ttu-id="e608e-256">(*Nxd_udp_socket_send*) **Duo — wysyłanie gniazda UDP**</span><span class="sxs-lookup"><span data-stu-id="e608e-256">**Duo UDP Socket Send** (*nxd_udp_socket_send*)</span></span> |
| ![Ikona interfejsu zestawu gniazd w programie Duo U D](./media/user-guide/netx-events/image75.png)    | <span data-ttu-id="e608e-258">**Interfejs zestawu gniazd UDP Duo** (*nxd_udp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="e608e-258">**Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*)</span></span> |
| ![Ikona wyodrębnienia źródła w usłudze Duo U D](./media/user-guide/netx-events/image76.png)    | <span data-ttu-id="e608e-260">**Wyodrębnij Źródło UDP Duo** (*nxd_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="e608e-260">**Duo UDP Source Extract** (*nxd_udp_source_extract*)</span></span> |
| ![Ikona włączenia I C M](./media/user-guide/netx-events/image77.png)    | <span data-ttu-id="e608e-262">**Włączanie protokołu ICMP** (*nx_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-262">**ICMP Enable** (*nx_icmp_enable*)</span></span> |
| ![I C M P informacje o ikonie](./media/user-guide/netx-events/image78.png)    | <span data-ttu-id="e608e-264">**Informacje o protokole ICMP** (*nx_icmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-264">**ICMP Information Get** (*nx_icmp_info_get*)</span></span> |
| ![I C M P ikona ping](./media/user-guide/netx-events/image79.png)    | <span data-ttu-id="e608e-266">**Polecenie ping protokołu ICMP** (*nx_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="e608e-266">**ICMP Ping** (*nx_icmp_ping*)</span></span> |
| ![Ikona włączenia I G M](./media/user-guide/netx-events/image80.png)    | <span data-ttu-id="e608e-268">**Włączanie IGMP** (*nx_igmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-268">**IGMP Enable** (*nx_igmp_enable*)</span></span> |
| ![Ikona uzyskiwania informacji o & G M](./media/user-guide/netx-events/image81.png)    | <span data-ttu-id="e608e-270">**Informacje o** protokole IGMP (*nx_igmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-270">**IGMP Information Get** (*nx_igmp_info_get*)</span></span> |
| ![Ikona wyłączenia sprzężenia zwrotnego I G M](./media/user-guide/netx-events/image82.png)    | <span data-ttu-id="e608e-272">**Wyłączenie sprzężenia zwrotnego protokołu IGMP** (*nx_igmp_loopback_disable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-272">**IGMP Loopback Disable** (*nx_igmp_loopback_disable*)</span></span> |
| ![Ikona włączania sprzężenia zwrotnego M P](./media/user-guide/netx-events/image83.png)    | <span data-ttu-id="e608e-274">**Włączanie sprzężenia zwrotnego protokołu IGMP** (*nx_igmp_loopback_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-274">**IGMP Loopback Enable** (*nx_igmp_loopback_enable*)</span></span> |
| ![Ikona sprzężenia multiemisji I G M](./media/user-guide/netx-events/image84.png)    | <span data-ttu-id="e608e-276">**Sprzężenie multiemisyjne IGMP** (*nx_igmp_multicast_join*)</span><span class="sxs-lookup"><span data-stu-id="e608e-276">**IGMP Multicast Join** (*nx_igmp_multicast_join*)</span></span> |
| ![Ikona urlopu multiemisji I G M](./media/user-guide/netx-events/image85.png)    | <span data-ttu-id="e608e-278">**Wyjście z multiemisji IGMP** (*nx_igmp_multicast_leave*)</span><span class="sxs-lookup"><span data-stu-id="e608e-278">**IGMP Multicast Leave** (*nx_igmp_multicast_leave*)</span></span> |
| ![Ikona powiadomienia o zmianie adresu](./media/user-guide/netx-events/image86.png)    | <span data-ttu-id="e608e-280">**Powiadomienie o zmianie adresu IP** (*nx_ip_address_change_notify*)</span><span class="sxs-lookup"><span data-stu-id="e608e-280">**IP Address Change Notify** (*nx_ip_address_change_notify*)</span></span> |
| ![Ikona pobierania adresu](./media/user-guide/netx-events/image87.png)    | <span data-ttu-id="e608e-282">**Pobieranie adresu IP** (*nx_ip_address_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-282">**IP Address Get** (*nx_ip_address_get*)</span></span> |
| ![Ikona zestawu adresów I P](./media/user-guide/netx-events/image88.png)    | <span data-ttu-id="e608e-284">**Zestaw adresów IP** (*nx_ip_address_set*)</span><span class="sxs-lookup"><span data-stu-id="e608e-284">**IP Address Set** (*nx_ip_address_set*)</span></span> |
| ![Ikona tworzenia](./media/user-guide/netx-events/image89.png)    | <span data-ttu-id="e608e-286">**Tworzenie adresu IP** (*nx_ip_create*)</span><span class="sxs-lookup"><span data-stu-id="e608e-286">**IP Create** (*nx_ip_create*)</span></span> |
| ![Ikona usuwania](./media/user-guide/netx-events/image90.png)    | <span data-ttu-id="e608e-288">**Usuwanie adresu IP** (*nx_ip_delete*)</span><span class="sxs-lookup"><span data-stu-id="e608e-288">**IP Delete** (*nx_ip_delete*)</span></span> |
| ![Ikona poleceń I P sterownika](./media/user-guide/netx-events/image91.png)    | <span data-ttu-id="e608e-290">**Polecenie bezpośredniego sterownika IP** (*nx_ip_driver_direct_command*)</span><span class="sxs-lookup"><span data-stu-id="e608e-290">**IP Driver Direct Command** (*nx_ip_driver_direct_command*)</span></span> |
| ![Ikona wyłączonego przesyłania dalej](./media/user-guide/netx-events/image92.png)    | <span data-ttu-id="e608e-292">**Wyłączenie przesyłania dalej IP** (*nx_ip_forwarding_disable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-292">**IP Forwarding Disable** (*nx_ip_forwarding_disable*)</span></span> |
| ![Ikona włączania przesyłania dalej](./media/user-guide/netx-events/image93.png)    | <span data-ttu-id="e608e-294">**Włączanie przekazywania adresów IP** (*nx_ip_forwarding_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-294">**IP Forwarding Enable** (*nx_ip_forwarding_enable*)</span></span> |
| ![Ikona wyłączenia fragmentu](./media/user-guide/netx-events/image94.png)    | <span data-ttu-id="e608e-296">**Wyłączenie fragmentu IP** (*nx_ip_fragment_disable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-296">**IP Fragment Disable** (*nx_ip_fragment_disable*)</span></span> |
| ![Ikona włączenia fragmentu](./media/user-guide/netx-events/image95.png)    | <span data-ttu-id="e608e-298">**Włączanie fragmentu IP** (*nx_ip_fragment_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-298">**IP Fragment Enable** (*nx_ip_fragment_enable*)</span></span>  |
| ![Ikona zestawu adresów bramy I](./media/user-guide/netx-events/image96.png)    | <span data-ttu-id="e608e-300">**Zestaw adresów IP Gateway** (*nx_ip_gateway_address_set*)</span><span class="sxs-lookup"><span data-stu-id="e608e-300">**IP Gateway Address Set** (*nx_ip_gateway_address_set*)</span></span> |
| ![Ikona uzyskiwania informacji](./media/user-guide/netx-events/image97.png)    | <span data-ttu-id="e608e-302">**Pobieranie informacji o adresie IP** (*nx_ip_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-302">**IP Information Get** (*nx_ip_info_get*)</span></span> |
| ![Ikona dołączania interfejsu I P](./media/user-guide/netx-events/image98.png)    | <span data-ttu-id="e608e-304">**Dołączanie interfejsu IP** (*nx_ip_interface_attach*)</span><span class="sxs-lookup"><span data-stu-id="e608e-304">**IP Interface Attach** (*nx_ip_interface_attach*)</span></span> |
| ![Ikona uzyskiwania informacji o interfejsie](./media/user-guide/netx-events/image99.png)    | <span data-ttu-id="e608e-306">**Pobieranie informacji o interfejsie IP** (*nx_ip_interface_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-306">**IP Interface Info Get** (*nx_ip_interface_info_get*)</span></span> |
| ![Ikona wyłączania pakietów pierwotnych](./media/user-guide/netx-events/image100.png)    | <span data-ttu-id="e608e-308">**Wyłączanie pierwotnego pakietu IP** (*nx_ip_raw_packet_disable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-308">**IP Raw Packet Disable** (*nx_ip_raw_packet_disable*)</span></span> |
| ![Ikona włączenia pakietu RAW](./media/user-guide/netx-events/image101.png)    | <span data-ttu-id="e608e-310">**Włącz pierwotny pakiet IP** (*nx_ip_raw_packet_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-310">**IP Raw Packet Enable** (*nx_ip_raw_packet_enable*)</span></span> |
| ![Ikona odbierania pakietów RAW](./media/user-guide/netx-events/image102.png)    | <span data-ttu-id="e608e-312">**Odbieranie pakietów pierwotnych adresów IP** (*nx_ip_raw_packet_receive*)</span><span class="sxs-lookup"><span data-stu-id="e608e-312">**IP Raw Packet Receive** (*nx_ip_raw_packet_receive*)</span></span> |
| ![Ikona wysyłania pakietów RAW](./media/user-guide/netx-events/image103.png)    | <span data-ttu-id="e608e-314">**Wysyłanie pakietów Raw IP** (*nx_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="e608e-314">**IP Raw Packet Send** (*nx_ip_raw_packet_send*)</span></span> |
| ![Ikona dodawania trasy statycznej](./media/user-guide/netx-events/image104.png)    | <span data-ttu-id="e608e-316">**Dodawanie statycznej trasy IP** (*nx_ip_static_route_add*)</span><span class="sxs-lookup"><span data-stu-id="e608e-316">**IP Static Route Add** (*nx_ip_static_route_add*)</span></span> |
| ![Ikona usuwania trasy statycznej](./media/user-guide/netx-events/image105.png)    | <span data-ttu-id="e608e-318">**Usuwanie statycznej trasy IP** (*nx_ip_static_route_delete)*</span><span class="sxs-lookup"><span data-stu-id="e608e-318">**IP Static Route Delete** (*nx_ip_static_route_delete)*</span></span> |
| ![Ikona sprawdzania stanu P](./media/user-guide/netx-events/image106.png)    | <span data-ttu-id="e608e-320">**Sprawdzenie stanu IP** (*nx_ip_status_check*)</span><span class="sxs-lookup"><span data-stu-id="e608e-320">**IP Status Check** (*nx_ip_status_check*)</span></span>|
| ![Ikona włączenia I S E C](./media/user-guide/netx-events/image107.png)    | <span data-ttu-id="e608e-322">**Włączanie protokołu IPSec** (*nx_ipsec_enable)*</span><span class="sxs-lookup"><span data-stu-id="e608e-322">**IPSEC Enable** (*nx_ipsec_enable)*</span></span> |
| ![Ikona alokacji pakietów](./media/user-guide/netx-events/image108.png)    | <span data-ttu-id="e608e-324">**Przydział pakietu** (*nx_packet_allocate*)</span><span class="sxs-lookup"><span data-stu-id="e608e-324">**Packet Allocate** (*nx_packet_allocate*)</span></span> |
| ![Ikona kopiowania pakietów](./media/user-guide/netx-events/image109.png)    | <span data-ttu-id="e608e-326">**Kopiowanie pakietów** (*nx_packet_copy*)</span><span class="sxs-lookup"><span data-stu-id="e608e-326">**Packet Copy** (*nx_packet_copy*)</span></span> |
| ![Ikona dołączania danych pakietu](./media/user-guide/netx-events/image110.png)    | <span data-ttu-id="e608e-328">**Dołączanie danych pakietu** (*nx_packet_data_append*)</span><span class="sxs-lookup"><span data-stu-id="e608e-328">**Packet Data Append** (*nx_packet_data_append*)</span></span> |
| ![Ikona przesunięcia wyodrębniania danych pakietu](./media/user-guide/netx-events/image111.png)    | <span data-ttu-id="e608e-330">**Przesunięcie wyodrębniania danych pakietu** (*nx_packet_data_extract_offset*)</span><span class="sxs-lookup"><span data-stu-id="e608e-330">**Packet Data Extract Offset** (*nx_packet_data_extract_offset*)</span></span> |
| ![Ikona pobierania danych pakietu](./media/user-guide/netx-events/image112.png)    | <span data-ttu-id="e608e-332">**Pobieranie danych pakietu** (*nx_packet_data_retrieve*)</span><span class="sxs-lookup"><span data-stu-id="e608e-332">**Packet Data Retrieve** (*nx_packet_data_retrieve*)</span></span> |
| ![Ikona pobierania długości pakietu](./media/user-guide/netx-events/image113.png)    | <span data-ttu-id="e608e-334">**Pobieranie długości pakietu** (*nx_packet_length_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-334">**Packet Length Get** (*nx_packet_length_get*)</span></span> |
| ![Ikona tworzenia puli pakietów](./media/user-guide/netx-events/image114.png)    | <span data-ttu-id="e608e-336">**Tworzenie puli pakietów** (*nx_packet_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="e608e-336">**Packet Pool Create** (*nx_packet_pool_create*)</span></span> |
| ![Ikona usuwania puli pakietów](./media/user-guide/netx-events/image115.png)    | <span data-ttu-id="e608e-338">**Usuwanie puli pakietów** (*nx_packet_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="e608e-338">**Packet Pool Delete** (*nx_packet_pool_delete*)</span></span> |
| ![Ikona pobierania informacji o puli pakietów](./media/user-guide/netx-events/image116.png)    | <span data-ttu-id="e608e-340">**Pobieranie informacji o puli pakietów** (*nx_packet_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-340">**Packet Pool Information Get** (*nx_packet_pool_info_get*)</span></span> |
| ![Ikona wydania pakietu](./media/user-guide/netx-events/image117.png)    | <span data-ttu-id="e608e-342">**Wydanie pakietów** (*nx_packet_release*)</span><span class="sxs-lookup"><span data-stu-id="e608e-342">**Packet Release** (*nx_packet_release*)</span></span> |
| ![Ikona wydania transmisji pakietu](./media/user-guide/netx-events/image118.png)    | <span data-ttu-id="e608e-344">**Wydanie transmisji pakietów** (*nx_packet_transmit_release*)</span><span class="sxs-lookup"><span data-stu-id="e608e-344">**Packet Transmit Release** (*nx_packet_transmit_release*)</span></span> |
| ![Ikona wyłączenia r P](./media/user-guide/netx-events/image119.png)    | <span data-ttu-id="e608e-346">**RARP Wyłącz** (*nx_rarp_disable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-346">**RARP Disable** (*nx_rarp_disable*)</span></span> |
| ![Ikona włączenia języka r P](./media/user-guide/netx-events/image120.png)    | <span data-ttu-id="e608e-348">**Włącz RARP** (*nx_rarp_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-348">**RARP Enable** (*nx_rarp_enable*)</span></span> |
| ![Ikona uzyskiwania informacji o języku r P](./media/user-guide/netx-events/image121.png)    | <span data-ttu-id="e608e-350">**RARP informacji** (*nx_rarp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-350">**RARP Information Get** (*nx_rarp_info_get*)</span></span> |
| ![Ikona inicjowania systemu](./media/user-guide/netx-events/image122.png)    | <span data-ttu-id="e608e-352">**Inicjowanie systemu** (*nx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="e608e-352">**System Initialize** (*nx_system_initialize*)</span></span> |
| ![Ikona powiązania gniazda klienta T C P](./media/user-guide/netx-events/image123.png)    | <span data-ttu-id="e608e-354">**Powiązanie gniazda klienta TCP** (*nx_tcp_client_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="e608e-354">**TCP Client Socket Bind** (*nx_tcp_client_socket_bind*)</span></span> |
| ![Ikona połączenia z gniazdem klienta T C P](./media/user-guide/netx-events/image124.png)    | <span data-ttu-id="e608e-356">**Połączenie gniazda klienta TCP** (*nx_tcp_client_socket_connect*)</span><span class="sxs-lookup"><span data-stu-id="e608e-356">**TCP Client Socket Connect** (*nx_tcp_client_socket_connect*)</span></span> |
| ![Ikona pobierania portu gniazda klienta T C P](./media/user-guide/netx-events/image125.png)    | <span data-ttu-id="e608e-358">**Pobieranie portu gniazda klienta TCP** (*nx_tcp_client_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-358">**TCP Client Socket Port Get** (*nx_tcp_client_socket_port_get*)</span></span> |
| ![Ikona usuwania powiązania gniazda klienta T C P](./media/user-guide/netx-events/image126.png)    | <span data-ttu-id="e608e-360">**Niepowiązanie gniazda klienta TCP** (*nx_tcp_client_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="e608e-360">**TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*)</span></span> |
| ![Ikona włączenia P C](./media/user-guide/netx-events/image127.png)    | <span data-ttu-id="e608e-362">**Włączanie protokołu TCP** (*nx_tcp_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-362">**TCP Enable** (*nx_tcp_enable*)</span></span> |
| ![Ikona wyszukiwania wolnego portu T C P](./media/user-guide/netx-events/image128.png)    | <span data-ttu-id="e608e-364">**Znajdź port bezpłatny TCP** (*nx_tcp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="e608e-364">**TCP Free Port Find** (*nx_tcp_free_port_find*)</span></span> |
| ![Ikona pobierania informacji T C P](./media/user-guide/netx-events/image129.png)    | <span data-ttu-id="e608e-366">**Pobieranie informacji o protokole TCP** (*nx_tcp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-366">**TCP Information Get** (*nx_tcp_info_get*)</span></span> |
| ![Ikona akceptowania gniazda serwera T C P](./media/user-guide/netx-events/image130.png)    | <span data-ttu-id="e608e-368">**Akceptowanie gniazda serwera TCP** (*nx_tcp_server_socket_accept*)</span><span class="sxs-lookup"><span data-stu-id="e608e-368">**TCP Server Socket Accept** (*nx_tcp_server_socket_accept*)</span></span> |
| ![Ikona nasłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image131.png)    | <span data-ttu-id="e608e-370">**Nasłuchiwanie gniazda serwera TCP** (*nx_tcp_server_socket_listen*)</span><span class="sxs-lookup"><span data-stu-id="e608e-370">**TCP Server Socket Listen** (*nx_tcp_server_socket_listen*)</span></span> |
| ![Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image132.png)    | <span data-ttu-id="e608e-372">**Przesłuchiwanie gniazda serwera TCP** (*nx_tcp_server_socket_relisten*)</span><span class="sxs-lookup"><span data-stu-id="e608e-372">**TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*)</span></span> |
| ![Ikona nieakceptowania gniazda serwera T C P](./media/user-guide/netx-events/image133.png)    | <span data-ttu-id="e608e-374">**Nieakceptowanie gniazda serwera TCP** (*nx_tcp_server_socket_unaccept*)</span><span class="sxs-lookup"><span data-stu-id="e608e-374">**TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*)</span></span> |
| ![Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image134.png)    | <span data-ttu-id="e608e-376">**Odsłuchiwanie gniazda serwera TCP** (*nx_tcp_server_socket_unlisten*)</span><span class="sxs-lookup"><span data-stu-id="e608e-376">**TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*)</span></span> |
| ![Ikona dostępnych bajtów gniazda T C](./media/user-guide/netx-events/image135.png)    | <span data-ttu-id="e608e-378">**Dostępne bajty gniazda TCP** (*nx_tcp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="e608e-378">**TCP Socket Bytes Available** (*nx_tcp_socket_bytes_available*)</span></span> |
| ![Ikona tworzenia gniazda T C P](./media/user-guide/netx-events/image136.png)    | <span data-ttu-id="e608e-380">**Tworzenie gniazda TCP** (*nx_tcp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="e608e-380">**TCP Socket Create** (*nx_tcp_socket_create*)</span></span> |
| ![Ikona usuwania gniazda T C P](./media/user-guide/netx-events/image137.png)    | <span data-ttu-id="e608e-382">**Usuwanie gniazda TCP** (*nx_tcp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="e608e-382">**TCP Socket Delete** (*nx_tcp_socket_delete*)</span></span> |
| ![Ikona rozłączenia gniazda T C P](./media/user-guide/netx-events/image138.png)    | <span data-ttu-id="e608e-384">**Odłączanie gniazda TCP** (*nx_tcp_socket_disconnect*)</span><span class="sxs-lookup"><span data-stu-id="e608e-384">**TCP Socket Disconnect** (*nx_tcp_socket_disconnect*)</span></span> |
| ![Ikona uzyskiwania informacji o gnieździe T C P](./media/user-guide/netx-events/image139.png)    | <span data-ttu-id="e608e-386">**Pobieranie informacji o gnieździe TCP** (*nx_tcp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-386">**TCP Socket Information Get** (*nx_tcp_socket_info_get*)</span></span> |
| ![Ikona pobierania o przełączeniu do gniazda T C P](./media/user-guide/netx-events/image140.png)    | <span data-ttu-id="e608e-388">**Pobieranie z gniazda TCP** (w *nx_tcp_socket_mss_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-388">**TCP Socket MSS Get** (*nx_tcp_socket_mss_get*)</span></span> |
| ![Ikona pobierania elementu równorzędnego w gnieździe T C P Socket](./media/user-guide/netx-events/image141.png)    | <span data-ttu-id="e608e-390">**Pobieranie elementu równorzędnego** (*Nx_tcp_socket_mss_peer_get*) w gnieździe TCP Socket</span><span class="sxs-lookup"><span data-stu-id="e608e-390">**TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*)</span></span> |
| ![Ikona zestawu o wzgnieździe T C P Socket](./media/user-guide/netx-events/image142.png)    | <span data-ttu-id="e608e-392">Zestaw (*nx_tcp_socket_mss_set*) **gniazda TCP**</span><span class="sxs-lookup"><span data-stu-id="e608e-392">**TCP Socket MSS Set** (*nx_tcp_socket_mss_set*)</span></span> |
| ![Ikona pobierania informacji o komunikacji równorzędnej gniazda T C](./media/user-guide/netx-events/image143.png)    | <span data-ttu-id="e608e-394">**Pobieranie informacji o komunikacji równorzędnej gniazda TCP** (*nx_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-394">**TCP Socket Peer Info Get** (*nx_tcp_socket_peer_info_get*)</span></span> |
| ![Ikona odbioru gniazda T C P](./media/user-guide/netx-events/image144.png)    | <span data-ttu-id="e608e-396">**Odbieranie gniazda TCP** (*nx_tcp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="e608e-396">**TCP Socket Receive** (*nx_tcp_socket_receive*)</span></span> |
| ![Ikona powiadomienia o odebraniu gniazda T C P](./media/user-guide/netx-events/image145.png)    | <span data-ttu-id="e608e-398">**Powiadomienie o odebraniu gniazda TCP** (*nx_tcp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="e608e-398">**TCP Socket Receive Notify** (*nx_tcp_socket_receive_notify*)</span></span> |
| ![Ikona wysyłania gniazda T C P](./media/user-guide/netx-events/image146.png)    | <span data-ttu-id="e608e-400">**Wysyłanie gniazda TCP** (*nx_tcp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="e608e-400">**TCP Socket Send** (*nx_tcp_socket_send*)</span></span> |
| ![Ikona oczekiwania stanu gniazda T C P](./media/user-guide/netx-events/image147.png)    | <span data-ttu-id="e608e-402">**Oczekiwanie stanu gniazda TCP** (*nx_tcp_socket_state_wait*)</span><span class="sxs-lookup"><span data-stu-id="e608e-402">**TCP Socket State Wait** (*nx_tcp_socket_state_wait*)</span></span> |
| ![Ikona wysyłania gniazda sieciowego T C P](./media/user-guide/netx-events/image148.png)    | <span data-ttu-id="e608e-404">**Konfigurowanie transmisji gniazda TCP** (*nx_tcp_socket_transmit_configure*)</span><span class="sxs-lookup"><span data-stu-id="e608e-404">**TCP Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*)</span></span> |
| ![Ikona zestawu powiadomień o aktualizacji okna gniazda T C](./media/user-guide/netx-events/image149.png)    | <span data-ttu-id="e608e-406">**Zestaw powiadomień o aktualizacji okna gniazda TCP** (*nx_tcp_socket_window_update_notify_set*)</span><span class="sxs-lookup"><span data-stu-id="e608e-406">**TCP Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)</span></span>  |
| ![Ikona włączenia u D P](./media/user-guide/netx-events/image150.png)    | <span data-ttu-id="e608e-408">**Włączanie protokołu UDP** (*nx_udp_enable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-408">**UDP Enable** (*nx_udp_enable*)</span></span> |
| ![Ikona Znajdź bezpłatny port U D P](./media/user-guide/netx-events/image151.png)    | <span data-ttu-id="e608e-410">**Znajdowanie portów bezpłatnych UDP** (*nx_udp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="e608e-410">**UDP Free Port Find** (*nx_udp_free_port_find*)</span></span> |
| ![Ikona pobierania informacji u D P](./media/user-guide/netx-events/image152.png)    | <span data-ttu-id="e608e-412">**Pobieranie informacji o UDP** (*nx_udp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-412">**UDP Information Get** (*nx_udp_info_get*)</span></span> |
| ![Ikona powiązania z gniazdem u D P](./media/user-guide/netx-events/image153.png)    | <span data-ttu-id="e608e-414">**Powiązanie gniazda UDP** (*nx_udp_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="e608e-414">**UDP Socket Bind** (*nx_udp_socket_bind*)</span></span> |
| ![Ikona U-D P Sockets available](./media/user-guide/netx-events/image154.png)    | <span data-ttu-id="e608e-416">**Dostępne bajty gniazda UDP** (*nx_udp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="e608e-416">**UDP Socket Bytes Available** (*nx_udp_socket_bytes_available*)</span></span> |
| ![Ikona wyłączenia sumy kontrolnej P D w gnieździe](./media/user-guide/netx-events/image155.png)    | <span data-ttu-id="e608e-418">**Wyłącz sumę kontrolną gniazda UDP** (*nx_udp_socket_checksum_disable*)</span><span class="sxs-lookup"><span data-stu-id="e608e-418">**UDP Socket Checksum Disable** (*nx_udp_socket_checksum_disable*)</span></span> |
| ![Ikona włączenia sumy kontrolnej w gnieździe u D P](./media/user-guide/netx-events/image156.png)    | <span data-ttu-id="e608e-420">**Włącz sumę kontrolną gniazda UDP** *(nx_udp_socket_checksum_enable)*</span><span class="sxs-lookup"><span data-stu-id="e608e-420">**UDP Socket Checksum Enable** *(nx_udp_socket_checksum_enable)*</span></span> |
| ![Ikona tworzenia gniazda P D](./media/user-guide/netx-events/image157.png)    | <span data-ttu-id="e608e-422">**Tworzenie gniazda UDP** (*nx_udp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="e608e-422">**UDP Socket Create** (*nx_udp_socket_create*)</span></span> |
| ![Ikona "Usuń" u gniazda P D](./media/user-guide/netx-events/image158.png)    | <span data-ttu-id="e608e-424">**Usuwanie gniazda UDP** (*nx_udp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="e608e-424">**UDP Socket Delete** (*nx_udp_socket_delete*)</span></span> |
| ![Ikona uzyskiwania informacji o gnieździe U D](./media/user-guide/netx-events/image159.png)    | <span data-ttu-id="e608e-426">**Pobieranie informacji o gnieździe UDP** (*nx_udp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-426">**UDP Socket Information Get** (*nx_udp_socket_info_get*)</span></span> |
| ![Ikona ustawienia interfejsu gniazda P D Socket](./media/user-guide/netx-events/image160.png)    | <span data-ttu-id="e608e-428">**Zestaw interfejsów gniazda UDP** (*nx_udp_socket_interface_set*)</span><span class="sxs-lookup"><span data-stu-id="e608e-428">**UDP Socket Interface Set** (*nx_udp_socket_interface_set*)</span></span> |
| ![Ikona pobierania portu gniazda P D](./media/user-guide/netx-events/image161.png)    | <span data-ttu-id="e608e-430">**Pobieranie portu gniazda UDP** (*nx_udp_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="e608e-430">**UDP Socket Port Get** (*nx_udp_socket_port_get*)</span></span> |
| ![Ikona odbioru w gnieździe U D P](./media/user-guide/netx-events/image162.png)    | <span data-ttu-id="e608e-432">**Odbieranie gniazda UDP** (*nx_udp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="e608e-432">**UDP Socket Receive** (*nx_udp_socket_receive*)</span></span> |
| ![Ikona powiadomienia o odebraniu gniazda P D](./media/user-guide/netx-events/image163.png)    | <span data-ttu-id="e608e-434">**Powiadomienie o odebraniu gniazda UDP** (*nx_udp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="e608e-434">**UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*)</span></span> |
| ![Ikona wysyłania w gnieździe u D P](./media/user-guide/netx-events/image164.png)    | <span data-ttu-id="e608e-436">**Wysyłanie gniazda UDP** (*nx_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="e608e-436">**UDP Socket Send** (*nx_udp_socket_send*)</span></span> |
| ![Ikona nieusuwania powiązania U gniazda P D](./media/user-guide/netx-events/image165.png)    | <span data-ttu-id="e608e-438">**Powiązanie UDP gniazda** (*nx_udp_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="e608e-438">**UDP Socket Unbind** (*nx_udp_socket_unbind*)</span></span> |
| ![Ikona wyodrębnienia źródła U D P](./media/user-guide/netx-events/image166.png)    | <span data-ttu-id="e608e-440">**Wyodrębnij Źródło UDP** (*nx_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="e608e-440">**UDP Source Extract** (*nx_udp_source_extract*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="e608e-441">Opisy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e608e-441">Event Descriptions</span></span>

<span data-ttu-id="e608e-442">Poniższe strony opisują zdarzenia śledzenia NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-442">The following pages describe the NetX Trace Events.</span></span>

### <a name="internal-arp-request-receive"></a><span data-ttu-id="e608e-443">Odbieranie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-443">Internal ARP Request Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="e608e-444">Odbieranie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-444">Internal ARP request receive</span></span>

<span data-ttu-id="e608e-445">**Ikona** ![ Ikona odbierania żądania wewnętrznego protokołu ARP](./media/user-guide/netx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-445">**Icon** ![Internal ARP request receive icon](./media/user-guide/netx-events/image1.png)</span></span>

<span data-ttu-id="e608e-446">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-446">**Description**</span></span>

<span data-ttu-id="e608e-447">To zdarzenie reprezentuje zdarzenie odbierania żądania wewnętrznego NetX ARP.</span><span class="sxs-lookup"><span data-stu-id="e608e-447">This event represents an internal NetX ARP request receive event.</span></span>

<span data-ttu-id="e608e-448">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-448">**Information Fields**</span></span>

- <span data-ttu-id="e608e-449">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-449">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-450">Pole informacji 2: źródłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-450">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="e608e-451">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-451">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-452">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-452">Info Field 4: Not used</span></span>

### <a name="internal-arp-request-send"></a><span data-ttu-id="e608e-453">Wysyłanie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-453">Internal ARP Request Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="e608e-454">Wysyłanie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-454">Internal ARP request send</span></span>

<span data-ttu-id="e608e-455">**Ikona** ![ Ikona wysyłania żądania wewnętrznego ARP](./media/user-guide/netx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-455">**Icon** ![Internal ARP request send icon](./media/user-guide/netx-events/image2.png)</span></span>

<span data-ttu-id="e608e-456">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-456">**Description**</span></span>

<span data-ttu-id="e608e-457">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania żądania NetX ARP.</span><span class="sxs-lookup"><span data-stu-id="e608e-457">This event represents an internal NetX ARP request send event.</span></span>

<span data-ttu-id="e608e-458">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-458">**Information Fields**</span></span>

- <span data-ttu-id="e608e-459">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-459">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-460">Pole informacji 2: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-460">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="e608e-461">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-461">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-462">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-462">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-receive"></a><span data-ttu-id="e608e-463">Odbieranie wewnętrznej odpowiedzi ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-463">Internal ARP Response Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="e608e-464">Odbieranie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-464">Internal ARP request receive</span></span>

<span data-ttu-id="e608e-465">**Ikona** ![ Ikona odbierania żądania wewnętrznego ARP](./media/user-guide/netx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-465">**Icon** ![The Internal ARP request receive icon](./media/user-guide/netx-events/image3.png)</span></span>

<span data-ttu-id="e608e-466">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-466">**Description**</span></span>

<span data-ttu-id="e608e-467">To zdarzenie reprezentuje zdarzenie odbioru wewnętrznej odpowiedzi NetX ARP.</span><span class="sxs-lookup"><span data-stu-id="e608e-467">This event represents an internal NetX ARP response receive event.</span></span>

<span data-ttu-id="e608e-468">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-468">**Information Fields**</span></span>

- <span data-ttu-id="e608e-469">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-469">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-470">Pole informacji 2: źródłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-470">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="e608e-471">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-471">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-472">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-472">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-send"></a><span data-ttu-id="e608e-473">Wysyłanie odpowiedzi wewnętrznego protokołu ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-473">Internal ARP Response Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="e608e-474">Wysyłanie żądania wewnętrznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-474">Internal ARP request send</span></span>

<span data-ttu-id="e608e-475">**Ikona** ![ Ikona wysyłania żądania wewnętrznego ARP](./media/user-guide/netx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-475">**Icon** ![The Internal ARP request send icon](./media/user-guide/netx-events/image4.png)</span></span>

<span data-ttu-id="e608e-476">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-476">**Description**</span></span>

<span data-ttu-id="e608e-477">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania odpowiedzi NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-477">This event represents an internal NetX response send event.</span></span>

<span data-ttu-id="e608e-478">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-478">**Information Fields**</span></span>

- <span data-ttu-id="e608e-479">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-479">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-480">Pole informacji 2: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-480">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="e608e-481">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-481">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-482">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-482">Info Field 4: Not used</span></span>

### <a name="internal-icmp-receive"></a><span data-ttu-id="e608e-483">Wewnętrzne odbieranie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-483">Internal ICMP Receive</span></span> 

#### <a name="internal-icmp-receive"></a><span data-ttu-id="e608e-484">Wewnętrzne odbieranie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-484">Internal ICMP receive</span></span>

<span data-ttu-id="e608e-485">**Ikona** ![ Ikona Odbierz wewnętrznej I C M P](./media/user-guide/netx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-485">**Icon** ![Internal I C M P receive icon](./media/user-guide/netx-events/image5.png)</span></span>

<span data-ttu-id="e608e-486">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-486">**Description**</span></span>

<span data-ttu-id="e608e-487">To zdarzenie reprezentuje wewnętrzne NetX zdarzenia odbierania protokołu ICMP.</span><span class="sxs-lookup"><span data-stu-id="e608e-487">This event represents an internal NetX ICMP receive event.</span></span>

<span data-ttu-id="e608e-488">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-488">**Information Fields**</span></span>

- <span data-ttu-id="e608e-489">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-489">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-490">Pole informacji 2: źródłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-490">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="e608e-491">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-491">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-492">Pole informacji 4: słowo 0 w nagłówku ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-492">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-icmp-send"></a><span data-ttu-id="e608e-493">Wewnętrzne wysyłanie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-493">Internal ICMP Send</span></span> 

#### <a name="internal-icmp-send"></a><span data-ttu-id="e608e-494">Wewnętrzne wysyłanie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-494">Internal ICMP send</span></span>

<span data-ttu-id="e608e-495">**Ikona** ![ Ikona wysyłania w wewnętrznej I C M P](./media/user-guide/netx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-495">**Icon** ![Internal I C M P send icon](./media/user-guide/netx-events/image6.png)</span></span>

<span data-ttu-id="e608e-496">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-496">**Description**</span></span>

<span data-ttu-id="e608e-497">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu ICMP NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-497">This event represents an internal NetX ICMP send event.</span></span>

<span data-ttu-id="e608e-498">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-498">**Information Fields**</span></span>

- <span data-ttu-id="e608e-499">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-499">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-500">Pole informacji 2: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-500">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="e608e-501">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-501">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-502">Pole informacji 4: słowo 0 w nagłówku ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-502">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-igmp-receive"></a><span data-ttu-id="e608e-503">Wewnętrzny odbiór IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-503">Internal IGMP Receive</span></span> 

#### <a name="internal-igmp-receive"></a><span data-ttu-id="e608e-504">Wewnętrzny odbiór IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-504">Internal IGMP receive</span></span>

<span data-ttu-id="e608e-505">**Ikona** ![ Wewnętrzna I G M P ikona Odbierz](./media/user-guide/netx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-505">**Icon** ![Internal I G M P receive icon](./media/user-guide/netx-events/image7.png)</span></span>

<span data-ttu-id="e608e-506">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-506">**Description**</span></span>

<span data-ttu-id="e608e-507">To zdarzenie reprezentuje wewnętrzne NetXe zdarzenie odbierania protokołu IGMP.</span><span class="sxs-lookup"><span data-stu-id="e608e-507">This event represents an internal NetX IGMP receive event.</span></span>

<span data-ttu-id="e608e-508">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-508">**Information Fields**</span></span>

- <span data-ttu-id="e608e-509">Pole informacji 1: wskaźnik adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-509">Info Field 1: IP Pointer</span></span>
- <span data-ttu-id="e608e-510">Pole informacji 2: źródłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-510">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="e608e-511">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-511">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-512">Pole informacji 4: słowo 0 w nagłówku IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-512">Info Field 4: Word 0 of IGMP header</span></span>

### <a name="internal-ip-receive"></a><span data-ttu-id="e608e-513">Wewnętrzny adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-513">Internal IP Receive</span></span> 

#### <a name="internal-ip-receive"></a><span data-ttu-id="e608e-514">Wewnętrzny adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-514">Internal IP receive</span></span>

<span data-ttu-id="e608e-515">**Ikona** ![ Ikona odbioru wewnętrznego I P](./media/user-guide/netx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-515">**Icon** ![Internal I P receive icon](./media/user-guide/netx-events/image8.png)</span></span>

<span data-ttu-id="e608e-516">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-516">**Description**</span></span>

<span data-ttu-id="e608e-517">To zdarzenie reprezentuje wewnętrzne NetX IP Receive.</span><span class="sxs-lookup"><span data-stu-id="e608e-517">This event represents an internal NetX IP receive event.</span></span>

<span data-ttu-id="e608e-518">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-518">**Information Fields**</span></span>

- <span data-ttu-id="e608e-519">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-519">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-520">Pole informacji 2: źródłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-520">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="e608e-521">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-521">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-522">Pole informacji 4: długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-522">Info Field 4: Packet length</span></span>

### <a name="internal-ip-send"></a><span data-ttu-id="e608e-523">Wewnętrzny wysyłanie adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-523">Internal IP Send</span></span>

#### <a name="internal-ip-send"></a><span data-ttu-id="e608e-524">Wewnętrzny wysyłanie adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-524">Internal IP send</span></span>

<span data-ttu-id="e608e-525">**Ikona** ![ Ikona wewnętrznej I P wysłania](./media/user-guide/netx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-525">**Icon** ![Internal I P send icon](./media/user-guide/netx-events/image9.png)</span></span>

<span data-ttu-id="e608e-526">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-526">**Description**</span></span>

<span data-ttu-id="e608e-527">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-527">This event represents an internal NetX IP send event.</span></span>

<span data-ttu-id="e608e-528">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-528">**Information Fields**</span></span>

- <span data-ttu-id="e608e-529">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-529">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-530">Pole informacji 2: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-530">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="e608e-531">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-531">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-532">Pole informacji 4: długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-532">Info Field 4: Packet length</span></span>

### <a name="internal-tcp-data-receive"></a><span data-ttu-id="e608e-533">Odbieranie danych wewnętrznych protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-533">Internal TCP Data Receive</span></span> 

#### <a name="internal-tcp-data-receive"></a><span data-ttu-id="e608e-534">Odbieranie danych wewnętrznych protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-534">Internal TCP Data Receive</span></span>

<span data-ttu-id="e608e-535">**Ikona** ![ Ikona odbierania danych wewnętrznych T C P](./media/user-guide/netx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-535">**Icon** ![Internal T C P data receive icon](./media/user-guide/netx-events/image10.png)</span></span>

<span data-ttu-id="e608e-536">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-536">**Description**</span></span>

<span data-ttu-id="e608e-537">To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania danych NetX TCP.</span><span class="sxs-lookup"><span data-stu-id="e608e-537">This event represents an internal NetX TCP data receive event.</span></span>

<span data-ttu-id="e608e-538">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-538">**Information Fields**</span></span>

- <span data-ttu-id="e608e-539">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-539">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-540">Pole informacji 2: źródłowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-540">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="e608e-541">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-541">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-542">Pole informacji 4: numer sekwencyjny odbioru</span><span class="sxs-lookup"><span data-stu-id="e608e-542">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-data-send"></a><span data-ttu-id="e608e-543">Wysyłanie danych wewnętrznych protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-543">Internal TCP data send</span></span> 

#### <a name="internal-tcp-data-send"></a><span data-ttu-id="e608e-544">Wysyłanie danych wewnętrznych protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-544">Internal TCP Data Send</span></span>

<span data-ttu-id="e608e-545">**Ikona** ![ Ikona wysyłania danych wewnętrznych T C P](./media/user-guide/netx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-545">**Icon** ![Internal T C P data send icon](./media/user-guide/netx-events/image11.png)</span></span>

<span data-ttu-id="e608e-546">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-546">**Description**</span></span>

<span data-ttu-id="e608e-547">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania danych NetX TCP.</span><span class="sxs-lookup"><span data-stu-id="e608e-547">This event represents an internal NetX TCP data send event.</span></span>

<span data-ttu-id="e608e-548">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-548">**Information Fields**</span></span>

- <span data-ttu-id="e608e-549">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-549">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-550">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-550">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-551">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-551">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-552">Pole informacji 4: numer sekwencyjny transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-552">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="e608e-553">Odbieranie wewnętrznego FIN TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-553">Internal TCP FIN Receive</span></span> 

#### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="e608e-554">Odbieranie wewnętrznego fin TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-554">Internal TCP fin receive</span></span>

<span data-ttu-id="e608e-555">**Ikona** ![ Ikona Odbierz wewnętrznej T C P r N](./media/user-guide/netx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-555">**Icon** ![Internal T C P F I N receive icon](./media/user-guide/netx-events/image12.png)</span></span>

<span data-ttu-id="e608e-556">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-556">**Description**</span></span>

<span data-ttu-id="e608e-557">To zdarzenie reprezentuje wewnętrzne zdarzenie odbioru NetX TCP FIN.</span><span class="sxs-lookup"><span data-stu-id="e608e-557">This event represents an internal NetX TCP FIN receive event.</span></span>

<span data-ttu-id="e608e-558">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-558">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-559">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-559">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-560">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-560">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-561">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-561">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-562">Pole informacji 4: numer sekwencyjny odbioru</span><span class="sxs-lookup"><span data-stu-id="e608e-562">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-fin-send"></a><span data-ttu-id="e608e-563">Wysyłanie wewnętrznego FIN protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-563">Internal TCP FIN Send</span></span> 

#### <a name="internal-tcp-fin-send"></a><span data-ttu-id="e608e-564">Wysyłanie wewnętrznego fin protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-564">Internal TCP fin send</span></span>

<span data-ttu-id="e608e-565">**Ikona** ![ Ikona wewnętrznej wysyłki P C I N](./media/user-guide/netx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-565">**Icon** ![Internal T C P F I N send icon](./media/user-guide/netx-events/image13.png)</span></span>

<span data-ttu-id="e608e-566">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-566">**Description**</span></span>

<span data-ttu-id="e608e-567">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania NetX TCP FIN.</span><span class="sxs-lookup"><span data-stu-id="e608e-567">This event represents an internal NetX TCP FIN send event.</span></span>

<span data-ttu-id="e608e-568">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-568">**Information Fields**</span></span>

- <span data-ttu-id="e608e-569">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-569">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-570">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-570">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-571">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-571">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-572">Pole informacji 4: numer sekwencyjny transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-572">Info Field 4:Transmit sequence number</span></span>

### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="e608e-573">Wewnętrzny odbieranie protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-573">Internal TCP RST Receive</span></span> 

#### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="e608e-574">Wewnętrzny odbieranie protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-574">Internal TCP RST receive</span></span>

<span data-ttu-id="e608e-575">**Ikona** ![ Ikona Odbierz wewnętrznego T C P R S T](./media/user-guide/netx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-575">**Icon** ![Internal T C P R S T receive icon](./media/user-guide/netx-events/image14.png)</span></span>

<span data-ttu-id="e608e-576">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-576">**Description**</span></span>

<span data-ttu-id="e608e-577">To zdarzenie reprezentuje wewnętrzne zdarzenie NetX resetowania protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="e608e-577">This event represents an internal NetX TCP reset receive event.</span></span>

<span data-ttu-id="e608e-578">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-578">**Information Fields**</span></span>

- <span data-ttu-id="e608e-579">Pole informacji 1: wskaźnik do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-579">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="e608e-580">Pole informacji 2: wskaźnik do gniazda.</span><span class="sxs-lookup"><span data-stu-id="e608e-580">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="e608e-581">Pole informacji 3: wskaźnik do pakietu.</span><span class="sxs-lookup"><span data-stu-id="e608e-581">Info Field 3: Pointer to packet.</span></span>
- <span data-ttu-id="e608e-582">Pole informacji 4: Odbierz numer sekwencyjny.</span><span class="sxs-lookup"><span data-stu-id="e608e-582">Info Field 4: Receive sequence number.</span></span>

### <a name="internal-tcp-rst-send"></a><span data-ttu-id="e608e-583">Wewnętrzny parametr TCP RST</span><span class="sxs-lookup"><span data-stu-id="e608e-583">Internal TCP RST Send</span></span> 

#### <a name="internal-tcp-rst-send"></a><span data-ttu-id="e608e-584">Wewnętrzny parametr TCP RST</span><span class="sxs-lookup"><span data-stu-id="e608e-584">Internal TCP RST send</span></span>

<span data-ttu-id="e608e-585">**Ikona** ![ Ikona wysyłania do wewnątrz T C P R S T](./media/user-guide/netx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-585">**Icon** ![Internal T C P R S T send icon](./media/user-guide/netx-events/image15.png)</span></span>

<span data-ttu-id="e608e-586">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-586">**Description**</span></span>

<span data-ttu-id="e608e-587">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu TCP NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-587">This event represents an internal NetX TCP reset send event.</span></span>

<span data-ttu-id="e608e-588">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-588">**Information Fields**</span></span>

- <span data-ttu-id="e608e-589">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-589">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-590">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-590">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-591">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-591">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-592">Pole informacji 4: numer sekwencyjny transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-592">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="e608e-593">Odbieranie wewnętrznego protokołu TCP SYN</span><span class="sxs-lookup"><span data-stu-id="e608e-593">Internal TCP SYN Receive</span></span> 

#### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="e608e-594">Odbieranie wewnętrznego protokołu TCP SYN</span><span class="sxs-lookup"><span data-stu-id="e608e-594">Internal TCP SYN receive</span></span>

<span data-ttu-id="e608e-595">**Ikona** ![ Ikona Odbierz wewnętrznej T C P S Y](./media/user-guide/netx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-595">**Icon** ![Internal T C P S Y N receive icon](./media/user-guide/netx-events/image16.png)</span></span>

<span data-ttu-id="e608e-596">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-596">**Description**</span></span>

<span data-ttu-id="e608e-597">To zdarzenie reprezentuje wewnętrzne zdarzenie odbioru NetX TCP SYN.</span><span class="sxs-lookup"><span data-stu-id="e608e-597">This event represents an internal NetX TCP SYN receive event.</span></span>

<span data-ttu-id="e608e-598">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-598">**Information Fields**</span></span>

- <span data-ttu-id="e608e-599">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-599">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-600">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-600">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-601">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-601">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-602">Pole informacji 4: numer sekwencyjny odbioru</span><span class="sxs-lookup"><span data-stu-id="e608e-602">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-syn-send"></a><span data-ttu-id="e608e-603">Wysyłanie wewnętrznego protokołu TCP SYN</span><span class="sxs-lookup"><span data-stu-id="e608e-603">Internal TCP SYN Send</span></span> 

#### <a name="internal-tcp-syn-send"></a><span data-ttu-id="e608e-604">Wysyłanie wewnętrznego protokołu TCP SYN</span><span class="sxs-lookup"><span data-stu-id="e608e-604">Internal TCP SYN send</span></span>

<span data-ttu-id="e608e-605">**Ikona** ![ Ikona wysyłania do wewnątrz T C P S Y](./media/user-guide/netx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-605">**Icon** ![Internal T C P S Y N send icon](./media/user-guide/netx-events/image17.png)</span></span>

<span data-ttu-id="e608e-606">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-606">**Description**</span></span>

<span data-ttu-id="e608e-607">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania synch NetX TCP.</span><span class="sxs-lookup"><span data-stu-id="e608e-607">This event represents an internal NetX TCP SYN send event.</span></span>

<span data-ttu-id="e608e-608">Pola informacji</span><span class="sxs-lookup"><span data-stu-id="e608e-608">Information Fields</span></span> 

- <span data-ttu-id="e608e-609">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-609">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-610">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-610">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-611">Pole informacji 3: wskaźnik do pakietu — pole informacji 4: numer sekwencyjny transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-611">Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number</span></span>

### <a name="internal-udp-receive"></a><span data-ttu-id="e608e-612">Odbieranie wewnętrznego protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-612">Internal UDP Receive</span></span> 

#### <a name="internal-udp-receive"></a><span data-ttu-id="e608e-613">Odbieranie wewnętrznego protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-613">Internal UDP receive</span></span>

<span data-ttu-id="e608e-614">**Ikona** ![ Wewnętrzna ikona Odbierz U D P](./media/user-guide/netx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-614">**Icon** ![Internal U D P receive icon](./media/user-guide/netx-events/image18.png)</span></span>

<span data-ttu-id="e608e-615">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-615">**Description**</span></span>

<span data-ttu-id="e608e-616">To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania protokołu UDP NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-616">This event represents an internal NetX UDP receive event.</span></span>

<span data-ttu-id="e608e-617">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-617">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-618">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-618">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-619">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-619">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-620">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-620">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-621">Pole informacji 4: słowo 0 w nagłówku UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-621">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-udp-send"></a><span data-ttu-id="e608e-622">Wewnętrzne wysyłanie UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-622">Internal UDP Send</span></span> 

#### <a name="internal-udp-send"></a><span data-ttu-id="e608e-623">Wewnętrzne wysyłanie UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-623">Internal UDP send</span></span>

<span data-ttu-id="e608e-624">**Ikona** ![ Wewnętrzna ikona wysyłania U D P](./media/user-guide/netx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-624">**Icon** ![Internal U D P send icon](./media/user-guide/netx-events/image19.png)</span></span>

<span data-ttu-id="e608e-625">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-625">**Description**</span></span>

<span data-ttu-id="e608e-626">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu UDP NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-626">This event represents an internal NetX UDP send event.</span></span>

<span data-ttu-id="e608e-627">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-627">**Information Fields**</span></span>

- <span data-ttu-id="e608e-628">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-628">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-629">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-629">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-630">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-630">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-631">Pole informacji 4: słowo 0 w nagłówku UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-631">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-rarp-receive"></a><span data-ttu-id="e608e-632">Wewnętrzny RARP odbierania</span><span class="sxs-lookup"><span data-stu-id="e608e-632">Internal RARP Receive</span></span> 

#### <a name="internal-rarp-receive"></a><span data-ttu-id="e608e-633">Wewnętrzny RARP odbierania</span><span class="sxs-lookup"><span data-stu-id="e608e-633">Internal RARP receive</span></span> 

<span data-ttu-id="e608e-634">**Ikona** ![ Ikona odbierania w języku R P](./media/user-guide/netx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-634">**Icon** ![Internal R A R P receive icon](./media/user-guide/netx-events/image20.png)</span></span>

<span data-ttu-id="e608e-635">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-635">**Description**</span></span>

<span data-ttu-id="e608e-636">To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania NetX RARP.</span><span class="sxs-lookup"><span data-stu-id="e608e-636">This event represents an internal NetX RARP receive event.</span></span>

<span data-ttu-id="e608e-637">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-637">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-638">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-638">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-639">Pole informacji 2: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-639">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="e608e-640">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-640">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-641">Pole informacji 4: słowo 1 w nagłówku RARP</span><span class="sxs-lookup"><span data-stu-id="e608e-641">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-rarp-send"></a><span data-ttu-id="e608e-642">Wewnętrzne wysyłanie RARP</span><span class="sxs-lookup"><span data-stu-id="e608e-642">Internal RARP Send</span></span> 

#### <a name="internal-rarp-send"></a><span data-ttu-id="e608e-643">Wewnętrzne wysyłanie RARP</span><span class="sxs-lookup"><span data-stu-id="e608e-643">Internal RARP send</span></span> 

<span data-ttu-id="e608e-644">**Ikona** ![ Wewnętrzna ikona wysyłania r A R P](./media/user-guide/netx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-644">**Icon** ![Internal R A R P send icon](./media/user-guide/netx-events/image21.png)</span></span>

<span data-ttu-id="e608e-645">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-645">**Description**</span></span>

<span data-ttu-id="e608e-646">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania NetX RARP.</span><span class="sxs-lookup"><span data-stu-id="e608e-646">This event represents an internal NetX RARP send event.</span></span>

<span data-ttu-id="e608e-647">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-647">**Information Fields**</span></span>

- <span data-ttu-id="e608e-648">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-648">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-649">Pole informacji 2: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-649">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="e608e-650">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-650">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-651">Pole informacji 4: słowo 1 w nagłówku RARP</span><span class="sxs-lookup"><span data-stu-id="e608e-651">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-tcp-retry"></a><span data-ttu-id="e608e-652">Wewnętrzna ponowna próba protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-652">Internal TCP Retry</span></span> 

#### <a name="internal-tcp-retry"></a><span data-ttu-id="e608e-653">Wewnętrzna ponowna próba protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-653">Internal TCP retry</span></span> 

<span data-ttu-id="e608e-654">**Ikona** ![ Ikona wewnętrznej ponownej próby T C P](./media/user-guide/netx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-654">**Icon** ![Internal T C P retry icon](./media/user-guide/netx-events/image22.png)</span></span>

<span data-ttu-id="e608e-655">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-655">**Description**</span></span>

<span data-ttu-id="e608e-656">To zdarzenie reprezentuje wewnętrzne zdarzenie ponowienia protokołu TCP NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-656">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="e608e-657">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-657">**Information Fields**</span></span>
- <span data-ttu-id="e608e-658">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-658">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-659">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-659">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-660">Pole informacji 3: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-660">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="e608e-661">Pole informacji 4: liczba ponownych prób</span><span class="sxs-lookup"><span data-stu-id="e608e-661">Info Field 4: Number of retries</span></span>

### <a name="internal-tcp-state-change"></a><span data-ttu-id="e608e-662">Zmiana stanu wewnętrznego protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-662">Internal TCP State Change</span></span> 

#### <a name="internal-tcp-state-change"></a><span data-ttu-id="e608e-663">Zmiana stanu wewnętrznego protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-663">Internal TCP state change</span></span> 

<span data-ttu-id="e608e-664">**Ikona** ![ Ikona wewnętrznej zmiany stanu T C P](./media/user-guide/netx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-664">**Icon** ![Internal T C P state change icon](./media/user-guide/netx-events/image23.png)</span></span>

<span data-ttu-id="e608e-665">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-665">**Description**</span></span>

<span data-ttu-id="e608e-666">To zdarzenie reprezentuje wewnętrzne zdarzenie zmiany stanu gniazda TCP NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-666">This event represents an internal NetX TCP socket state change event.</span></span>

<span data-ttu-id="e608e-667">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-667">**Information Fields**</span></span>

- <span data-ttu-id="e608e-668">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-668">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-669">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-669">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-670">Pole informacji 3: poprzedni stan</span><span class="sxs-lookup"><span data-stu-id="e608e-670">Info Field 3: Previous state</span></span>
- <span data-ttu-id="e608e-671">Pole informacji 4: nowy stan</span><span class="sxs-lookup"><span data-stu-id="e608e-671">Info Field 4: New state</span></span>

### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="e608e-672">Wysyłanie pakietów sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-672">Internal I/O Driver Packet Send</span></span> 

#### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="e608e-673">Wysyłanie pakietów sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-673">Internal I/O driver packet send</span></span>

<span data-ttu-id="e608e-674">**Ikona** ![ Ikona wysyłania pakietów sterowników wewnętrznych we/wy](./media/user-guide/netx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-674">**Icon** ![Internal I / O driver packet send icon](./media/user-guide/netx-events/image24.png)</span></span>

<span data-ttu-id="e608e-675">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-675">**Description**</span></span>

<span data-ttu-id="e608e-676">To zdarzenie reprezentuje zdarzenie wysyłania pakietu sterowników we/wy wewnętrznego NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-676">This event represents an internal NetX I/O driver packet send event.</span></span>

<span data-ttu-id="e608e-677">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-677">**Information Fields**</span></span>

- <span data-ttu-id="e608e-678">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-678">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-679">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-679">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-680">Pole informacji 3: rozmiar pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-680">Info Field 3: Packet size</span></span>
- <span data-ttu-id="e608e-681">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-681">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="e608e-682">Inicjowanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-682">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="e608e-683">Inicjowanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-683">Internal I/O driver initialize</span></span>

<span data-ttu-id="e608e-684">**Ikona** ![ Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-684">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/netx-events/image25.png)</span></span>

<span data-ttu-id="e608e-685">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-685">**Description**</span></span>

<span data-ttu-id="e608e-686">To zdarzenie reprezentuje zdarzenie inicjowania sterownika wewnętrznego NetX we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-686">This event represents an internal NetX I/O driver initialize event.</span></span>

<span data-ttu-id="e608e-687">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-687">**Information Fields**</span></span>

- <span data-ttu-id="e608e-688">Pole informacji 1: wskaźnik do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-688">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="e608e-689">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="e608e-689">Info Field 2: Not used.</span></span>
- <span data-ttu-id="e608e-690">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="e608e-690">Info Field 3: Not used.</span></span>
- <span data-ttu-id="e608e-691">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="e608e-691">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="e608e-692">Włączenie linku wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-692">Internal I/O Driver Link Enable</span></span> 

#### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="e608e-693">Włączenie linku wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-693">Internal I/O driver link enable</span></span>

<span data-ttu-id="e608e-694">**Ikona** ![ Ikona włączenia linku wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-694">**Icon** ![Internal I / O driver link enable icon](./media/user-guide/netx-events/image26.png)</span></span>

<span data-ttu-id="e608e-695">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-695">**Description**</span></span>

<span data-ttu-id="e608e-696">To zdarzenie reprezentuje zdarzenie włączenia łącza sterownika wewnętrznego NetX we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-696">This event represents an internal NetX I/O driver link enable event.</span></span>

<span data-ttu-id="e608e-697">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-697">**Information Fields**</span></span>

- <span data-ttu-id="e608e-698">Pole informacji 1: wskaźnik do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-698">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="e608e-699">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="e608e-699">Info Field 2: Not used.</span></span>
- <span data-ttu-id="e608e-700">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="e608e-700">Info Field 3: Not used.</span></span>
- <span data-ttu-id="e608e-701">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="e608e-701">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="e608e-702">Wyłączenie linku wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-702">Internal I/O Driver Link Disable</span></span> 

#### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="e608e-703">Wyłączenie linku wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-703">Internal I/O driver link disable</span></span>

<span data-ttu-id="e608e-704">**Ikona** ![ Ikona wyłączenia łącza sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-704">**Icon** ![Internal I / O driver link disable icon](./media/user-guide/netx-events/image27.png)</span></span>

<span data-ttu-id="e608e-705">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-705">**Description**</span></span>

<span data-ttu-id="e608e-706">To zdarzenie reprezentuje zdarzenie wyłączenia łącza sterownika wewnętrznego NetX we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-706">This event represents an internal NetX I/O driver link disable event.</span></span>

<span data-ttu-id="e608e-707">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-707">**Information Fields**</span></span>

- <span data-ttu-id="e608e-708">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-708">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-709">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-709">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-710">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-710">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-711">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-711">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="e608e-712">Emisja pakietu sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-712">Internal I/O Driver Packet Broadcast</span></span> 

#### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="e608e-713">Emisja pakietu sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-713">Internal I/O driver packet broadcast</span></span>

<span data-ttu-id="e608e-714">**Ikona** ![ Ikona transmisji pakietu sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-714">**Icon** ![Internal I / O driver packet broadcast icon](./media/user-guide/netx-events/image28.png)</span></span>

<span data-ttu-id="e608e-715">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-715">**Description**</span></span>

<span data-ttu-id="e608e-716">To zdarzenie reprezentuje zdarzenie emisji pakietów sterownika wewnętrznego NetX we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-716">This event represents an internal NetX I/O driver packet broadcast event.</span></span>

<span data-ttu-id="e608e-717">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-717">**Information Fields**</span></span>

- <span data-ttu-id="e608e-718">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-718">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-719">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-719">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-720">Pole informacji 3: rozmiar pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-720">Info Field 3: Packet size</span></span>
- <span data-ttu-id="e608e-721">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-721">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="e608e-722">Wysyłanie wewnętrznego sterownika we/wy ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-722">Internal I/O Driver ARP Send</span></span> 

#### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="e608e-723">Wysyłanie wewnętrznego sterownika we/wy ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-723">Internal I/O driver ARP send</span></span>

<span data-ttu-id="e608e-724">**Ikona** ![ Ikona wysyłania sterownika protokołu ARP wewnętrznej operacji we/wy](./media/user-guide/netx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-724">**Icon** ![Internal I / O driver ARP send icon](./media/user-guide/netx-events/image29.png)</span></span>

<span data-ttu-id="e608e-725">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-725">**Description**</span></span>

<span data-ttu-id="e608e-726">To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania sterownika NetX we/wy protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="e608e-726">This event represents an internal NetX I/O driver ARP send event.</span></span>

<span data-ttu-id="e608e-727">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-727">**Information Fields**</span></span>

- <span data-ttu-id="e608e-728">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-728">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-729">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-729">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-730">Pole informacji 3: rozmiar pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-730">Info Field 3: Packet size</span></span>
- <span data-ttu-id="e608e-731">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-731">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="e608e-732">Wysyłanie odpowiedzi do wewnętrznego sterownika we/wy ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-732">Internal I/O Driver ARP Response Send</span></span> 

#### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="e608e-733">Wysyłanie odpowiedzi do wewnętrznego sterownika we/wy ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-733">Internal I/O driver ARP response send</span></span>

<span data-ttu-id="e608e-734">**Ikona** ![ Ikona wysyłania odpowiedzi protokołu ARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-734">**Icon** ![Internal I / O driver ARP response send icon](./media/user-guide/netx-events/image30.png)</span></span>

<span data-ttu-id="e608e-735">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-735">**Description**</span></span>

<span data-ttu-id="e608e-736">To zdarzenie reprezentuje zdarzenie wysyłania odpowiedzi NetX we/wy wewnętrznego sterownika protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="e608e-736">This event represents an internal NetX I/O driver ARP response send event.</span></span>

<span data-ttu-id="e608e-737">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-737">**Information Fields**</span></span>

- <span data-ttu-id="e608e-738">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-738">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-739">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-739">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-740">Pole informacji 3: rozmiar pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-740">Info Field 3: Packet size</span></span>
- <span data-ttu-id="e608e-741">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-741">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="e608e-742">RARP wysyłania sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-742">Internal I/O Driver RARP Send</span></span> 

#### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="e608e-743">RARP wysyłania sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-743">Internal I/O driver RARP send</span></span>

<span data-ttu-id="e608e-744">**Ikona** ![ Ikona wysyłania RARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-744">**Icon** ![Internal I / O driver RARP send icon](./media/user-guide/netx-events/image31.png)</span></span>

<span data-ttu-id="e608e-745">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-745">**Description**</span></span>

<span data-ttu-id="e608e-746">To zdarzenie reprezentuje wewnętrzne NetX sterownika we/wy RARP wysyłanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e608e-746">This event represents an internal NetX I/O driver RARP send event.</span></span>

<span data-ttu-id="e608e-747">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-747">**Information Fields**</span></span>

- <span data-ttu-id="e608e-748">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-748">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-749">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-749">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-750">Pole informacji 3: rozmiar pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-750">Info Field 3: Packet size</span></span>
- <span data-ttu-id="e608e-751">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-751">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="e608e-752">Wewnętrzny sprzężenie multiemisji sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-752">Internal I/O Driver Multicast Join</span></span> 

#### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="e608e-753">Wewnętrzny sprzężenie multiemisji sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-753">Internal I/O driver multicast join</span></span>

<span data-ttu-id="e608e-754">**Ikona** ![ Ikona wewnętrznej sprzężenia multiemisji sterownika we/wy](./media/user-guide/netx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-754">**Icon** ![Internal I / O driver multicast join icon](./media/user-guide/netx-events/image32.png)</span></span>

<span data-ttu-id="e608e-755">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-755">**Description**</span></span>

<span data-ttu-id="e608e-756">To zdarzenie reprezentuje zdarzenie sprzężenia multiemisji wewnętrznego NetX we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-756">This event represents an internal NetX I/O driver multicast join event.</span></span>

<span data-ttu-id="e608e-757">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-757">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-758">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-758">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-759">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-759">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-760">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-760">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-761">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-761">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="e608e-762">Wyjście z wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-762">Internal I/O Driver Multicast Leave</span></span> 

#### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="e608e-763">Wyjście z wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-763">Internal I/O driver multicast leave</span></span>

<span data-ttu-id="e608e-764">**Ikona** ![ Ikona opuszczania wewnętrznego multiemisji sterownika we/wy](./media/user-guide/netx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-764">**Icon** ![Internal I / O driver multicast leave icon](./media/user-guide/netx-events/image33.png)</span></span>

<span data-ttu-id="e608e-765">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-765">**Description**</span></span>

<span data-ttu-id="e608e-766">To zdarzenie przedstawia wewnętrzne zdarzenie NetXa multiemisji sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-766">This event represents an internal NetX I/O driver multicast leave event.</span></span>

<span data-ttu-id="e608e-767">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-767">**Information Fields**</span></span>

- <span data-ttu-id="e608e-768">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-768">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-769">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-769">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-770">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-770">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-771">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-771">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-status"></a><span data-ttu-id="e608e-772">Stan wewnętrznego pobierania sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-772">Internal I/O Driver Get Status</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="e608e-773">Stan wewnętrznego pobierania sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-773">Internal I/O driver get status</span></span>

<span data-ttu-id="e608e-774">**Ikona** ![ Ikona stanu pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-774">**Icon** ![Internal I / O driver get status icon](./media/user-guide/netx-events/image34.png)</span></span>

<span data-ttu-id="e608e-775">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-775">**Description**</span></span>

<span data-ttu-id="e608e-776">To zdarzenie reprezentuje zdarzenie stanu NetX wewnętrznego sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-776">This event represents an internal NetX I/O driver get status event.</span></span>

<span data-ttu-id="e608e-777">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-777">**Information Fields**</span></span>

- <span data-ttu-id="e608e-778">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-778">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-779">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-779">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-780">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-780">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-781">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-781">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="e608e-782">Szybkość uzyskiwania sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-782">Internal I/O Driver Get Speed</span></span> 

#### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="e608e-783">Szybkość uzyskiwania sterownika wewnętrznego we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-783">Internal I/O driver get speed</span></span>

<span data-ttu-id="e608e-784">**Ikona** ![ Ikona szybkość pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-784">**Icon** ![Internal I / O driver get speed icon](./media/user-guide/netx-events/image35.png)</span></span>

<span data-ttu-id="e608e-785">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-785">**Description**</span></span>

<span data-ttu-id="e608e-786">To zdarzenie reprezentuje wewnętrzne zdarzenie pobierania sterownika NetX we/wy.</span><span class="sxs-lookup"><span data-stu-id="e608e-786">This event represents an internal NetX I/O driver get speed event.</span></span>

<span data-ttu-id="e608e-787">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-787">**Information Fields**</span></span>

- <span data-ttu-id="e608e-788">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-788">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-789">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-789">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-790">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-790">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-791">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-791">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="e608e-792">Wewnętrzny sterownik we/wy — dostęp do typu dupleksowego</span><span class="sxs-lookup"><span data-stu-id="e608e-792">Internal I/O Driver Get Duplex Type</span></span> 

#### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="e608e-793">Wewnętrzny sterownik we/wy — dostęp do typu dupleksowego</span><span class="sxs-lookup"><span data-stu-id="e608e-793">Internal I/O driver get duplex type</span></span>

<span data-ttu-id="e608e-794">**Ikona** ![ Wewnętrzny sterownik we/wy — ikona typu dupleksu](./media/user-guide/netx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-794">**Icon** ![Internal I / O driver get duplex type icon](./media/user-guide/netx-events/image36.png)</span></span>

<span data-ttu-id="e608e-795">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-795">**Description**</span></span>

<span data-ttu-id="e608e-796">To zdarzenie reprezentuje wewnętrzny sterownik we/wy NetX — zdarzenie typu dupleks.</span><span class="sxs-lookup"><span data-stu-id="e608e-796">This event represents an internal NetX I/O driver get duplex type event.</span></span>

<span data-ttu-id="e608e-797">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-797">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-798">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-798">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-799">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-799">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-800">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-800">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-801">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-801">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="e608e-802">Wystąpił błąd wewnętrzny sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-802">Internal I/O Driver Get Error Count</span></span>

#### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="e608e-803">Wystąpił błąd wewnętrzny sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-803">Internal I/O driver get error count</span></span>

<span data-ttu-id="e608e-804">**Ikona** ![ Ikona "Pobierz liczbę błędów" sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-804">**Icon** ![Internal I / O driver get error count icon](./media/user-guide/netx-events/image37.png)</span></span>

<span data-ttu-id="e608e-805">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-805">**Description**</span></span>

<span data-ttu-id="e608e-806">To zdarzenie reprezentuje wewnętrzny sterownik NetX we/wy dla licznika błędów.</span><span class="sxs-lookup"><span data-stu-id="e608e-806">This event represents an internal NetX I/O driver get error count event.</span></span>

<span data-ttu-id="e608e-807">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-807">**Information Fields**</span></span>

- <span data-ttu-id="e608e-808">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-808">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-809">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-809">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-810">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-810">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-811">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-811">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="e608e-812">Wewnętrzny sterownik we/wy — pobieranie liczby RX</span><span class="sxs-lookup"><span data-stu-id="e608e-812">Internal I/O Driver Get RX Count</span></span> 

#### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="e608e-813">Wewnętrzny sterownik we/wy — pobieranie liczby RX</span><span class="sxs-lookup"><span data-stu-id="e608e-813">Internal I/O driver get RX count</span></span>

<span data-ttu-id="e608e-814">**Ikona** ![ Ikona licznika odbierania dla sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-814">**Icon** ![Internal I / O driver get RX count icon](./media/user-guide/netx-events/image38.png)</span></span>

<span data-ttu-id="e608e-815">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-815">**Description**</span></span>

<span data-ttu-id="e608e-816">To zdarzenie reprezentuje NetX wewnętrzny sterownika wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="e608e-816">This event represents an internal NetX I/O driver get RX count event.</span></span>

<span data-ttu-id="e608e-817">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-817">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-818">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-818">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-819">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-819">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-820">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-820">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-821">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-821">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="e608e-822">Wewnętrzny sterownik we/wy — pobieranie liczby transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-822">Internal I/O Driver Get TX Count</span></span> 

#### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="e608e-823">Wewnętrzny sterownik we/wy — pobieranie liczby transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-823">Internal I/O driver get TX count</span></span>

<span data-ttu-id="e608e-824">**Ikona** ![ Ikona liczby odczytów wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-824">**Icon** ![Internal I / O driver get T X count icon](./media/user-guide/netx-events/image39.png)</span></span>

<span data-ttu-id="e608e-825">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-825">**Description**</span></span>

<span data-ttu-id="e608e-826">To zdarzenie reprezentuje NetX wewnętrzny sterownika wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="e608e-826">This event represents an internal NetX I/O driver get TX count event.</span></span>

<span data-ttu-id="e608e-827">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-827">**Information Fields**</span></span>

- <span data-ttu-id="e608e-828">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-828">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-829">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-829">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-830">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-830">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-831">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-831">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="e608e-832">Wewnętrzny sterownik we/wy — pobieranie błędów alokacji</span><span class="sxs-lookup"><span data-stu-id="e608e-832">Internal I/O Driver Get Allocation Errors</span></span> 

#### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="e608e-833">Wewnętrzny sterownik we/wy — pobieranie błędów alokacji</span><span class="sxs-lookup"><span data-stu-id="e608e-833">Internal I/O driver get allocation errors</span></span>

<span data-ttu-id="e608e-834">**Ikona** ![ Ikona wewnętrznego pobierania sterowników we/wy](./media/user-guide/netx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-834">**Icon** ![Internal I / O driver get allocation errors icon](./media/user-guide/netx-events/image40.png)</span></span>

<span data-ttu-id="e608e-835">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-835">**Description**</span></span>

<span data-ttu-id="e608e-836">To zdarzenie reprezentuje zdarzenie wewnętrznego pobierania sterownika we/wy NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-836">This event represents an internal NetX I/O driver get allocation errors event.</span></span>

<span data-ttu-id="e608e-837">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-837">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-838">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-838">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-839">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-839">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-840">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-840">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-841">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-841">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="e608e-842">Wewnętrzny sterownik we/wy — anulowanie inicjalizacji</span><span class="sxs-lookup"><span data-stu-id="e608e-842">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="e608e-843">Wewnętrzny sterownik we/wy — anulowanie inicjalizacji</span><span class="sxs-lookup"><span data-stu-id="e608e-843">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="e608e-844">**Ikona** ![ Ikona anulowania inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-844">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/netx-events/image41.png)</span></span>

<span data-ttu-id="e608e-845">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-845">**Description**</span></span>

<span data-ttu-id="e608e-846">To zdarzenie reprezentuje zdarzenie anulowania inicjalizacji wewnętrznego sterownika we/wy NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-846">This event represents an internal NetX I/O driver un-initialize event.</span></span>

<span data-ttu-id="e608e-847">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-847">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-848">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-848">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-849">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-849">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-850">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-850">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-851">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-851">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="e608e-852">Przetwarzanie Odroczone wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-852">Internal I/O Driver Deferred Processing</span></span> 

#### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="e608e-853">Przetwarzanie Odroczone wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="e608e-853">Internal I/O driver deferred processing</span></span> 

<span data-ttu-id="e608e-854">**Ikona** ![ Ikona przetwarzania odroczonego sterownika we/wy](./media/user-guide/netx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-854">**Icon** ![Internal I / O driver deferred processing icon](./media/user-guide/netx-events/image42.png)</span></span>

<span data-ttu-id="e608e-855">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-855">**Description**</span></span>

<span data-ttu-id="e608e-856">To zdarzenie przedstawia wewnętrzne zdarzenie przetwarzania odroczonego sterownika we/wy NetX.</span><span class="sxs-lookup"><span data-stu-id="e608e-856">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="e608e-857">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-857">**Information Fields**</span></span>

- <span data-ttu-id="e608e-858">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-858">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-859">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-859">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-860">Pole informacji 3: długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-860">Info Field 3: Packet length</span></span>
- <span data-ttu-id="e608e-861">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-861">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entries-invalidate"></a><span data-ttu-id="e608e-862">Unieważnianie wpisów dynamicznych ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-862">ARP Dynamic Entries Invalidate</span></span> 

#### <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="e608e-863">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="e608e-863">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="e608e-864">**Ikona** ![ Ikona unieważnienia wpisów dynamicznych R P](./media/user-guide/netx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-864">**Icon** ![A R P Dynamic Entries Invalidate icon](./media/user-guide/netx-events/image43.png)</span></span>

<span data-ttu-id="e608e-865">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-865">**Description**</span></span>

<span data-ttu-id="e608e-866">To zdarzenie reprezentuje unieważnienie wszystkich dynamicznych ARP w całości za pośrednictwem nx_arp_dynamic_entries_invalidate.</span><span class="sxs-lookup"><span data-stu-id="e608e-866">This event represents invalidating all dynamic ARP entires via nx_arp_dynamic_entries_invalidate.</span></span>

<span data-ttu-id="e608e-867">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-867">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-868">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-868">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-869">Pole informacji 2: wpisy unieważnione</span><span class="sxs-lookup"><span data-stu-id="e608e-869">Info Field 2: Entries invalidated</span></span>
- <span data-ttu-id="e608e-870">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-870">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-871">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-871">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entry-set"></a><span data-ttu-id="e608e-872">Dynamiczny zestaw wpisów ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-872">ARP Dynamic Entry Set</span></span> 

#### <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="e608e-873">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="e608e-873">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="e608e-874">**Ikona** ![ Ikona dynamicznego zestawu wpisów R P](./media/user-guide/netx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-874">**Icon** ![A R P Dynamic Entry Set icon](./media/user-guide/netx-events/image44.png)</span></span>

<span data-ttu-id="e608e-875">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-875">**Description**</span></span>

<span data-ttu-id="e608e-876">To zdarzenie reprezentuje ustawienie dynamicznego wpisu ARP za pośrednictwem nx_arp_dynamic_entry_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-876">This event represents setting a dynamic ARP entry via nx_arp_dynamic_entry_set.</span></span>

<span data-ttu-id="e608e-877">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-877">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-878">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-878">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-879">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-879">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-880">Pole informacji 3: adres fizyczny (MSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-880">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="e608e-881">Pole informacji 4: adres fizyczny (LSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-881">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-enable"></a><span data-ttu-id="e608e-882">Włączanie protokołu ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-882">ARP Enable</span></span> 

#### <a name="nx_arp_enable"></a><span data-ttu-id="e608e-883">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-883">nx_arp_enable</span></span>

<span data-ttu-id="e608e-884">**Ikona** ![ Ikona włączenia R P](./media/user-guide/netx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-884">**Icon** ![A R P enable icon](./media/user-guide/netx-events/image45.png)</span></span>

<span data-ttu-id="e608e-885">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-885">**Description**</span></span>

<span data-ttu-id="e608e-886">To zdarzenie reprezentuje włączenie protokołu ARP za pośrednictwem nx_arp_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-886">This event represents enabling ARP via nx_arp_enable.</span></span>

<span data-ttu-id="e608e-887">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-887">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-888">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-888">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-889">Pole informacji 2: wskaźnik pamięci pamięci podręcznej ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-889">Info Field 2: ARP cache memory pointer</span></span>
- <span data-ttu-id="e608e-890">Pole informacji 3: rozmiar pamięci podręcznej ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-890">Info Field 3: ARP cache memory size</span></span>
- <span data-ttu-id="e608e-891">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-891">Info Field 4: Not used</span></span>

### <a name="arp-gratuitous-send"></a><span data-ttu-id="e608e-892">Wysyłanie żądanie do protokołu ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-892">ARP Gratuitous Send</span></span> 

#### <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="e608e-893">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="e608e-893">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="e608e-894">**Ikona** ![ Ikona wysyłania na żądanie w języku R P](./media/user-guide/netx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-894">**Icon** ![A R P gratuitous send icon](./media/user-guide/netx-events/image46.png)</span></span>

<span data-ttu-id="e608e-895">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-895">**Description**</span></span>

<span data-ttu-id="e608e-896">To zdarzenie reprezentuje wysyłanie bezpłatnego protokołu ARP za pośrednictwem nx_arp_gratuitous_send.</span><span class="sxs-lookup"><span data-stu-id="e608e-896">This event represents a gratuitous ARP send via nx_arp_gratuitous_send.</span></span>

<span data-ttu-id="e608e-897">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-897">**Information Fields**</span></span>

- <span data-ttu-id="e608e-898">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-898">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-899">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-899">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-900">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-900">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-901">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-901">Info Field 4: Not used</span></span>

### <a name="arp-hardware-address-find"></a><span data-ttu-id="e608e-902">Znajdowanie adresu sprzętowego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-902">ARP Hardware Address Find</span></span> 

#### <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="e608e-903">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="e608e-903">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="e608e-904">**Ikona** ![ Ikona wyszukiwania adresu sprzętu R P](./media/user-guide/netx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-904">**Icon** ![A R P Hardware Address Find icon](./media/user-guide/netx-events/image47.png)</span></span>

<span data-ttu-id="e608e-905">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-905">**Description**</span></span>

<span data-ttu-id="e608e-906">To zdarzenie reprezentuje adres fizyczny za pośrednictwem nx_arp_hardware_address_find.</span><span class="sxs-lookup"><span data-stu-id="e608e-906">This event represents finding a physical address via nx_arp_hardware_address_find.</span></span>

<span data-ttu-id="e608e-907">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-907">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-908">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-908">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-909">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-909">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-910">Pole informacji 3: adres fizyczny (MSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-910">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="e608e-911">Pole informacji 4: adres fizyczny (LSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-911">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-information-get"></a><span data-ttu-id="e608e-912">Informacje o ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-912">ARP Information Get</span></span> 

#### <a name="nx_arp_info_get"></a><span data-ttu-id="e608e-913">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-913">nx_arp_info_get</span></span>

<span data-ttu-id="e608e-914">**Ikona** ![ Ikona Get języka R P informition](./media/user-guide/netx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-914">**Icon** ![A R P informition get icon](./media/user-guide/netx-events/image48.png)</span></span>

<span data-ttu-id="e608e-915">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-915">**Description**</span></span>

<span data-ttu-id="e608e-916">To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_arp_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-916">This event represents getting information via nx_arp_info_get.</span></span>

<span data-ttu-id="e608e-917">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-917">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-918">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-918">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-919">Pole informacji 2: podsiecit wysłane</span><span class="sxs-lookup"><span data-stu-id="e608e-919">Info Field 2: ARPs sent</span></span>
- <span data-ttu-id="e608e-920">Pole informacji 3: odpowiedzi ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-920">Info Field 3: ARP responses</span></span>
- <span data-ttu-id="e608e-921">Pole informacji 4: Odebrano podsiecit</span><span class="sxs-lookup"><span data-stu-id="e608e-921">Info Field 4: ARPs received</span></span>

### <a name="arp-ip-address-find"></a><span data-ttu-id="e608e-922">Znajdowanie adresów IP ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-922">ARP IP Address Find</span></span> 

#### <a name="nx_arp_ip_address_find"></a><span data-ttu-id="e608e-923">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="e608e-923">nx_arp_ip_address_find</span></span>

<span data-ttu-id="e608e-924">**Ikona** ![ Ikona wyszukiwania adresu R P I P](./media/user-guide/netx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-924">**Icon** ![A R P I P address find icon](./media/user-guide/netx-events/image49.png)</span></span>

<span data-ttu-id="e608e-925">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-925">**Description**</span></span>

<span data-ttu-id="e608e-926">To zdarzenie reprezentuje adres IP skojarzony z podanym adresem fizycznym za pośrednictwem nx_arp_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="e608e-926">This event represents finding an IP address associated with the supplied physical address via nx_arp_ip_address_find.</span></span>

<span data-ttu-id="e608e-927">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-927">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-928">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-928">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-929">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-929">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-930">Pole informacji 3: adres fizyczny (MSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-930">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="e608e-931">Pole informacji 4: adres fizyczny (LSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-931">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entry-create"></a><span data-ttu-id="e608e-932">Tworzenie wpisu statycznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-932">ARP Static Entry Create</span></span> 

#### <a name="nx_arp_static_entry_create"></a><span data-ttu-id="e608e-933">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="e608e-933">nx_arp_static_entry_create</span></span>

<span data-ttu-id="e608e-934">**Ikona** ![ Ikona tworzenia wpisu statycznego R P](./media/user-guide/netx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-934">**Icon** ![A R P static entry create icon](./media/user-guide/netx-events/image50.png)</span></span>

<span data-ttu-id="e608e-935">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-935">**Description**</span></span>

<span data-ttu-id="e608e-936">To zdarzenie reprezentuje tworzenie statycznego wpisu ARP za pośrednictwem nx_arp_static_entry_create.</span><span class="sxs-lookup"><span data-stu-id="e608e-936">This event represents creating a static ARP entry via nx_arp_static_entry_create.</span></span>

<span data-ttu-id="e608e-937">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-937">**Information Fields**</span></span>

- <span data-ttu-id="e608e-938">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-938">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-939">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-939">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-940">Pole informacji 3: adres fizyczny (MSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-940">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="e608e-941">Pole informacji 4: adres fizyczny (LSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-941">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entries-delete"></a><span data-ttu-id="e608e-942">Usuwanie wpisów statycznych ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-942">ARP Static Entries Delete</span></span> 

#### <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="e608e-943">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-943">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="e608e-944">**Ikona** ![ Ikona usuwania wpisów statycznych R P](./media/user-guide/netx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-944">**Icon** ![A R P static entries delete icon](./media/user-guide/netx-events/image51.png)</span></span>

<span data-ttu-id="e608e-945">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-945">**Description**</span></span>

<span data-ttu-id="e608e-946">To zdarzenie reprezentuje usunięcie wszystkich wpisów statycznych ARP za pośrednictwem nx_arp_static_entries_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-946">This event represents deleting all ARP static entries via nx_arp_static_entries_delete.</span></span>

<span data-ttu-id="e608e-947">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-947">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-948">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-948">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-949">Pole informacji 2: wpisy zostały usunięte</span><span class="sxs-lookup"><span data-stu-id="e608e-949">Info Field 2: Entries deleted</span></span>
- <span data-ttu-id="e608e-950">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-950">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-951">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-951">Info Field 4: Not used</span></span>

### <a name="arp-static-entry-delete"></a><span data-ttu-id="e608e-952">Usuwanie wpisu statycznego ARP</span><span class="sxs-lookup"><span data-stu-id="e608e-952">ARP Static Entry Delete</span></span> 

### <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="e608e-953">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-953">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="e608e-954">**Ikona** ![ Ikona usuwania wpisu statycznego R P](./media/user-guide/netx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-954">**Icon** ![A R P static entry delete icon](./media/user-guide/netx-events/image52.png)</span></span>

<span data-ttu-id="e608e-955">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-955">**Description**</span></span>

<span data-ttu-id="e608e-956">To zdarzenie reprezentuje usunięcie statycznego wpisu ARP za pośrednictwem nx_arp_static_entry_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-956">This event represents deleting a static ARP entry via nx_arp_static_entry_delete.</span></span>

<span data-ttu-id="e608e-957">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-957">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-958">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-958">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-959">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-959">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-960">Pole informacji 3: adres fizyczny (MSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-960">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="e608e-961">Pole informacji 4: adres fizyczny (LSW)</span><span class="sxs-lookup"><span data-stu-id="e608e-961">Info Field 4: Physical address (LSW)</span></span>

### <a name="duo-cache-entry-delete"></a><span data-ttu-id="e608e-962">Usuwanie wpisu pamięci podręcznej Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-962">Duo Cache Entry Delete</span></span> 

#### <a name="nxd_und_cache_entry_delete"></a><span data-ttu-id="e608e-963">nxd_und_cache_entry_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-963">nxd_und_cache_entry_delete</span></span>

<span data-ttu-id="e608e-964">**Ikona** ![ Ikona usuwania wpisu pamięci podręcznej Duo](./media/user-guide/netx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-964">**Icon** ![Duo cache entry delete icon](./media/user-guide/netx-events/image53.png)</span></span>

<span data-ttu-id="e608e-965">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-965">**Description**</span></span>

<span data-ttu-id="e608e-966">To zdarzenie reprezentuje usunięcie wpisu w tabeli pamięci podręcznej sąsiadów za pośrednictwem nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="e608e-966">This event represents deleting an entry in the neighbor cache table via nx_udp_socket_create.</span></span>

<span data-ttu-id="e608e-967">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-967">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-968">Pole informacji 1: czwarty (najmniej znaczący) wyraz adresu lokalnego linku IPv6 do usunięcia</span><span class="sxs-lookup"><span data-stu-id="e608e-968">Info Field 1: Fourth (least significant) word of the IPv6 link local address to delete</span></span>
- <span data-ttu-id="e608e-969">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-969">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-970">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-970">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-971">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-971">Info Field 4: Not used</span></span>

### <a name="duo-cache-entry-set"></a><span data-ttu-id="e608e-972">Zestaw wpisów pamięci podręcznej Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-972">Duo Cache Entry Set</span></span> 

#### <a name="nxd_nd_cache_entry_set"></a><span data-ttu-id="e608e-973">nxd_nd_cache_entry_set</span><span class="sxs-lookup"><span data-stu-id="e608e-973">nxd_nd_cache_entry_set</span></span>

<span data-ttu-id="e608e-974">**Ikona** ![ Ikona zestawu wpisów pamięci podręcznej Duo](./media/user-guide/netx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-974">**Icon** ![Duo cache entry set icon](./media/user-guide/netx-events/image54.png)</span></span>

<span data-ttu-id="e608e-975">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-975">**Description**</span></span>

<span data-ttu-id="e608e-976">To zdarzenie reprezentuje utworzenie wpisu pamięci podręcznej i dodanie go do tabeli pamięci podręcznej sąsiadów za pośrednictwem nxd_nd_cache_entry_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-976">This event represents creating a cache entry and adding to the neighbor cache table via nxd_nd_cache_entry_set.</span></span>

<span data-ttu-id="e608e-977">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-977">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-978">Pole informacji 1: czwarty (najmniej znaczący) wyraz adresu IPv6 do dodania</span><span class="sxs-lookup"><span data-stu-id="e608e-978">Info Field 1: Fourth (least significant) word of the IPv6 address to add</span></span>
- <span data-ttu-id="e608e-979">Pole informacji 2: adres fizyczny MSB</span><span class="sxs-lookup"><span data-stu-id="e608e-979">Info Field 2: Physical address msb</span></span>
- <span data-ttu-id="e608e-980">Pole informacji 3: adres fizyczny LSB</span><span class="sxs-lookup"><span data-stu-id="e608e-980">Info Field 3: Physical address lsb</span></span>
- <span data-ttu-id="e608e-981">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-981">Info Field 4: Not used</span></span>

### <a name="duo-cache-invalidate"></a><span data-ttu-id="e608e-982">Unieważnienie pamięci podręcznej Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-982">Duo Cache Invalidate</span></span> 

#### <a name="nxd_nd_cache_invalidate"></a><span data-ttu-id="e608e-983">nxd_nd_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="e608e-983">nxd_nd_cache_invalidate</span></span>

<span data-ttu-id="e608e-984">**Ikona** ![ Ikona unieważniania pamięci podręcznej Duo](./media/user-guide/netx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-984">**Icon** ![Duo cache invalidate icon](./media/user-guide/netx-events/image55.png)</span></span>

<span data-ttu-id="e608e-985">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-985">**Description**</span></span>

<span data-ttu-id="e608e-986">To zdarzenie reprezentuje unieważnienie całej tabeli pamięci podręcznej sąsiadów za pośrednictwem nxd_nd_cache_invalidate.</span><span class="sxs-lookup"><span data-stu-id="e608e-986">This event represents invalidating the entire neighbor cache table via nxd_nd_cache_invalidate.</span></span>

<span data-ttu-id="e608e-987">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-987">**Information Fields**</span></span>

- <span data-ttu-id="e608e-988">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-988">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-989">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-989">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-990">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-990">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-991">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-991">Info Field 4: Not used</span></span>

### <a name="duo-cache-ip-address-find"></a><span data-ttu-id="e608e-992">Znajdź adres IP pamięci podręcznej Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-992">Duo Cache IP Address Find</span></span> 

#### <a name="nxd_nd_cache_ip_address_find"></a><span data-ttu-id="e608e-993">nxd_nd_cache_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="e608e-993">nxd_nd_cache_ip_address_find</span></span>

<span data-ttu-id="e608e-994">**Ikona** ![ Ikona znajdowania pamięci podręcznej Duo I adresu](./media/user-guide/netx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-994">**Icon** ![Duo cache I P address find icon](./media/user-guide/netx-events/image56.png)</span></span>

<span data-ttu-id="e608e-995">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-995">**Description**</span></span>

<span data-ttu-id="e608e-996">To zdarzenie reprezentuje pobieranie adresu IP pasującego do podanego adresu fizycznego z tabeli pamięci podręcznej za pośrednictwem nxd_nd_cache_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="e608e-996">This event represents retrieving an IP address matching the supplied physical address from the cache table via nxd_nd_cache_ip_address_find.</span></span>

<span data-ttu-id="e608e-997">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-997">**Information Fields**</span></span>

- <span data-ttu-id="e608e-998">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-998">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-999">Pole informacji 2: czwarty (najmniej znaczący) wyraz adresu IPv6</span><span class="sxs-lookup"><span data-stu-id="e608e-999">Info Field 2: Fourth (least significant) word of the IPv6 address</span></span>
- <span data-ttu-id="e608e-1000">Pole informacji 3: adres fizyczny MSB</span><span class="sxs-lookup"><span data-stu-id="e608e-1000">Info Field 3: Physical address msb</span></span>
- <span data-ttu-id="e608e-1001">Pole informacji 4: adres fizyczny LSB</span><span class="sxs-lookup"><span data-stu-id="e608e-1001">Info Field 4: Physical address lsb</span></span>

### <a name="duo-icmp-enable"></a><span data-ttu-id="e608e-1002">Duo — Włączanie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1002">Duo ICMP Enable</span></span> 

#### <a name="nxd_icmp_enable"></a><span data-ttu-id="e608e-1003">nxd_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1003">nxd_icmp_enable</span></span>

<span data-ttu-id="e608e-1004">**Ikona** ![ Ikona włączania Duo I C M](./media/user-guide/netx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1004">**Icon** ![Duo I C M P enable icon](./media/user-guide/netx-events/image57.png)</span></span>

<span data-ttu-id="e608e-1005">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1005">**Description**</span></span>

<span data-ttu-id="e608e-1006">To zdarzenie reprezentuje usługi ICMPv4 i ICMPv6 włączone dla określonego wystąpienia IP za pośrednictwem nxd_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1006">This event represents ICMPv4 and ICMPv6 services being enabled on the specified IP instance via nxd_icmp_enable.</span></span>

<span data-ttu-id="e608e-1007">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1007">**Information Fields**</span></span>
- <span data-ttu-id="e608e-1008">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1008">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1009">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1009">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1010">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1010">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1011">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1011">Info Field 4: Not used</span></span>

### <a name="duo-icmp-ping"></a><span data-ttu-id="e608e-1012">Test ping protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1012">Duo ICMP Ping</span></span> 

#### <a name="nxd_icmp_ping"></a><span data-ttu-id="e608e-1013">nxd_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="e608e-1013">nxd_icmp_ping</span></span>

<span data-ttu-id="e608e-1014">**Ikona** ![ Ikona polecenia ping Duo I C M P](./media/user-guide/netx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1014">**Icon** ![Duo I C M P ping icon](./media/user-guide/netx-events/image58.png)</span></span>

<span data-ttu-id="e608e-1015">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1015">**Description**</span></span>

<span data-ttu-id="e608e-1016">To zdarzenie reprezentuje wysyłanie polecenia ping (żądanie echa) do hosta IPv6 za pośrednictwem nxd_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="e608e-1016">This event represents sending a ping (echo request) to an IPv6 host via nxd_icmp_ping.</span></span>

<span data-ttu-id="e608e-1017">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1017">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1018">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1018">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1019">Pole informacji 2: adres IPv6</span><span class="sxs-lookup"><span data-stu-id="e608e-1019">Info Field 2: IPv6 address</span></span>
- <span data-ttu-id="e608e-1020">Pole informacji 3: wskaźnik do ECHA danych</span><span class="sxs-lookup"><span data-stu-id="e608e-1020">Info Field 3: Pointer to echo data</span></span>
- <span data-ttu-id="e608e-1021">Pole informacji 4: rozmiar danych ECHA</span><span class="sxs-lookup"><span data-stu-id="e608e-1021">Info Field 4: Size of echo data</span></span>

### <a name="duo-ip-max-payload-size-find"></a><span data-ttu-id="e608e-1022">Maksymalny rozmiar ładunku w programie Duo — Znajdowanie</span><span class="sxs-lookup"><span data-stu-id="e608e-1022">Duo IP Max Payload Size Find</span></span> 

#### <a name="nxd_ip_max_payload_size"></a><span data-ttu-id="e608e-1023">nxd_ip_max_payload_size</span><span class="sxs-lookup"><span data-stu-id="e608e-1023">nxd_ip_max_payload_size</span></span>

<span data-ttu-id="e608e-1024">**Ikona** ![ Ikona wyszukiwania Duo I P z maksymalnym rozmiarem ładunku](./media/user-guide/netx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1024">**Icon** ![Duo I P max payload size find icon](./media/user-guide/netx-events/image59.png)</span></span>

<span data-ttu-id="e608e-1025">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1025">**Description**</span></span>

<span data-ttu-id="e608e-1026">To zdarzenie oblicza maksymalną liczbę ładunków, które może przenosić określony pakiet bez konieczności fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="e608e-1026">This event computes the max payload the specified packet can carry without requiring fragmentation.</span></span>

<span data-ttu-id="e608e-1027">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1027">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1028">Pole informacji 1: wskaźnik gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1028">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="e608e-1029">Pole informacji 2: adres IP elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1029">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="e608e-1030">Pole informacyjne 3: pole informacji o porcie równorzędnym 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1030">Info Field 3: Peer port Info Field 4: Not used</span></span>

### <a name="duo-ip-raw-packet-send"></a><span data-ttu-id="e608e-1031">Wysyłanie pakietów pierwotnych adresów IP Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1031">Duo IP Raw Packet Send</span></span> 

#### <a name="nxd_ip_max_packet_send"></a><span data-ttu-id="e608e-1032">nxd_ip_max_packet_send</span><span class="sxs-lookup"><span data-stu-id="e608e-1032">nxd_ip_max_packet_send</span></span>

<span data-ttu-id="e608e-1033">**Ikona** ![ Ikona odrzuconego wysyłania pakietów w programie Duo I](./media/user-guide/netx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1033">**Icon** ![Duo I P raw packet send icon](./media/user-guide/netx-events/image60.png)</span></span>

<span data-ttu-id="e608e-1034">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1034">**Description**</span></span>

<span data-ttu-id="e608e-1035">To zdarzenie reprezentuje wysyłanie pakietu pierwotnego adresu IP z określonego interfejsu sieciowego do podanego nxd_ip_raw_packet_send docelowego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-1035">This event represents sending a raw IP packet out the specified network interface to the supplied IP destination addressvia nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="e608e-1036">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1036">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1037">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1037">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1038">Pole informacji 2: wskaźnik do pakietu do wysłania</span><span class="sxs-lookup"><span data-stu-id="e608e-1038">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="e608e-1039">Pole informacji 3: wskaźnik do adresu docelowego</span><span class="sxs-lookup"><span data-stu-id="e608e-1039">Info Field 3: Pointer to destination address</span></span>
- <span data-ttu-id="e608e-1040">Pole informacji 4: Protokół pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1040">Info Field 4: Packet protocol</span></span>

### <a name="duo-ipv6-default-router-add"></a><span data-ttu-id="e608e-1041">Dodawanie domyślnego routera IPv6 Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1041">Duo IPv6 Default Router Add</span></span> 

#### <a name="nxd_ipv6_default_router_add"></a><span data-ttu-id="e608e-1042">nxd_ipv6_default_router_add</span><span class="sxs-lookup"><span data-stu-id="e608e-1042">nxd_ipv6_default_router_add</span></span>

<span data-ttu-id="e608e-1043">**Ikona** ![ Ikona dodawania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1043">**Icon** ![Duo I P v 6 default router add icon](./media/user-guide/netx-events/image61.png)</span></span>

<span data-ttu-id="e608e-1044">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1044">**Description**</span></span>

<span data-ttu-id="e608e-1045">To zdarzenie reprezentuje dodanie routera domyślnego do tabeli routingu IPv6 wystąpienia IP za pośrednictwem nxd_ipv6_default_router_add.</span><span class="sxs-lookup"><span data-stu-id="e608e-1045">This event represents adding a default router to the IP instance's IPv6 routing table via nxd_ipv6_default_router_add.</span></span>

<span data-ttu-id="e608e-1046">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1046">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1047">Pole informacji 1: wskaźnik do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-1047">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="e608e-1048">Pole informacji 2: docelowy adres sieciowy.</span><span class="sxs-lookup"><span data-stu-id="e608e-1048">Info Field 2: Destination Network address.</span></span>
- <span data-ttu-id="e608e-1049">Pole informacji 3: informacje o czasie życia.</span><span class="sxs-lookup"><span data-stu-id="e608e-1049">Info Field 3: Life time information.</span></span>
- <span data-ttu-id="e608e-1050">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="e608e-1050">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-default-router-delete"></a><span data-ttu-id="e608e-1051">Usuwanie domyślnego routera IPv6 w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1051">Duo IPv6 Default Router Delete</span></span> 

#### <a name="nxd_ipv6_default_router_delete"></a><span data-ttu-id="e608e-1052">nxd_ipv6_default_router_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-1052">nxd_ipv6_default_router_delete</span></span>

<span data-ttu-id="e608e-1053">**Ikona** ![ Ikona usuwania domyślnego routera Duo I v 6](./media/user-guide/netx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1053">**Icon** ![Duo I P v 6 default router delete icon](./media/user-guide/netx-events/image62.png)</span></span>

<span data-ttu-id="e608e-1054">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1054">**Description**</span></span>

<span data-ttu-id="e608e-1055">To zdarzenie reprezentuje usunięcie routera domyślnego z tabeli routingu IPv6 wystąpienia IP za pośrednictwem nxd_ipv6_default_router_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-1055">This event represents removing a default router from the IP instance's IPv6 routing table via nxd_ipv6_default_router_delete.</span></span>

<span data-ttu-id="e608e-1056">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1056">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1057">Pole informacji 1: wskaźnik do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-1057">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="e608e-1058">Pole informacji 2: czwarty wyraz (najmniej znaczący) domyślnego adresu IPv6 routera.</span><span class="sxs-lookup"><span data-stu-id="e608e-1058">Info Field 2: Fourth word (least significant) of the default router IPv6 address.</span></span>
- <span data-ttu-id="e608e-1059">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="e608e-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="e608e-1060">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="e608e-1060">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-enable"></a><span data-ttu-id="e608e-1061">Włącz protokół IPv6 w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1061">Duo IPv6 Enable</span></span> 

#### <a name="nxd_ipv6_enable"></a><span data-ttu-id="e608e-1062">nxd_ipv6_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1062">nxd_ipv6_enable</span></span>

<span data-ttu-id="e608e-1063">**Ikona** ![ Ikona włączania Duo I v 6](./media/user-guide/netx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1063">**Icon** ![Duo I P v 6 enable icon](./media/user-guide/netx-events/image63.png)</span></span>

<span data-ttu-id="e608e-1064">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1064">**Description**</span></span>

<span data-ttu-id="e608e-1065">To zdarzenie reprezentuje włączenie usług IPv6 w podanym wystąpieniu IP za pośrednictwem nxd_ipv6_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1065">This event represents enabling IPv6 services on the supplied IP instance via nxd_ipv6_enable.</span></span>

<span data-ttu-id="e608e-1066">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1066">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1067">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1067">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1068">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1068">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1069">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1069">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1070">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1070">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-global-address-get"></a><span data-ttu-id="e608e-1071">Pobieranie globalnego adresu IPv6 w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1071">Duo IPv6 Global Address Get</span></span> 

#### <a name="nxd_ipv6_global_address_get"></a><span data-ttu-id="e608e-1072">nxd_ipv6_global_address_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1072">nxd_ipv6_global_address_get</span></span>

<span data-ttu-id="e608e-1073">**Ikona** ![ Ikona uzyskiwania adresu globalnego Duo I P v 6](./media/user-guide/netx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1073">**Icon** ![Duo I P v 6 global address get icon](./media/user-guide/netx-events/image64.png)</span></span>

<span data-ttu-id="e608e-1074">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1074">**Description**</span></span>

<span data-ttu-id="e608e-1075">To zdarzenie reprezentuje pobieranie globalnego (podstawowego) adresu IP z wystąpienia adresu IP znajdującego się w indeksie 1 w tabeli interfejsu wystąpienia IP za pośrednictwem nxd_ipv6_global_address_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1075">This event represents retrieving the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_get.</span></span>

<span data-ttu-id="e608e-1076">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1076">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1077">Pole informacji 1: wskaźnik do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-1077">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="e608e-1078">Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu globalnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1078">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="e608e-1079">Pole informacji 3: długość prefiksu adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="e608e-1079">Info Field 3: IPv6 address prefix length.</span></span>
- <span data-ttu-id="e608e-1080">Pole informacji 4: indeks w tabeli interfejsów IP (1).</span><span class="sxs-lookup"><span data-stu-id="e608e-1080">Info Field 4: Index into IP interface table (1).</span></span>

### <a name="duo-ipv6-global-address-set"></a><span data-ttu-id="e608e-1081">Globalny zestaw adresów IPv6 w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1081">Duo IPv6 Global Address Set</span></span> 

#### <a name="nxd_ipv6_global_address_set"></a><span data-ttu-id="e608e-1082">nxd_ipv6_global_address_set</span><span class="sxs-lookup"><span data-stu-id="e608e-1082">nxd_ipv6_global_address_set</span></span>

<span data-ttu-id="e608e-1083">**Ikona** ![ Ikona zestawu adresów globalnych Duo I P v 6](./media/user-guide/netx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1083">**Icon** ![Duo I P v 6 global address set icon](./media/user-guide/netx-events/image65.png)</span></span>

<span data-ttu-id="e608e-1084">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1084">**Description**</span></span>

<span data-ttu-id="e608e-1085">To zdarzenie reprezentuje globalny (podstawowy) adres IP wystąpienia adresu IP znajdującego się w indeksie 1 w tabeli interfejsu wystąpienia IP za pośrednictwem nxd_ipv6_global_address_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-1085">This event represents setting the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_set.</span></span>

<span data-ttu-id="e608e-1086">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1086">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1087">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1087">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1088">Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu globalnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1088">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="e608e-1089">Pole informacji 3: długość prefiksu adresu IPv6</span><span class="sxs-lookup"><span data-stu-id="e608e-1089">Info Field 3: IPv6 address prefix length</span></span>
- <span data-ttu-id="e608e-1090">Pole informacji 4: indeksowanie w tabeli interfejsów IP (1)</span><span class="sxs-lookup"><span data-stu-id="e608e-1090">Info Field 4: Index into IP interface table (1)</span></span>

### <a name="duo-ipv6-initiate-dad-process"></a><span data-ttu-id="e608e-1091">Duo — inicjowanie procesu DAD</span><span class="sxs-lookup"><span data-stu-id="e608e-1091">Duo IPv6 Initiate Dad Process</span></span> 

#### <a name="nxd_ipv6_initiate_dad_process"></a><span data-ttu-id="e608e-1092">nxd_ipv6_initiate_dad_process</span><span class="sxs-lookup"><span data-stu-id="e608e-1092">nxd_ipv6_initiate_dad_process</span></span>

<span data-ttu-id="e608e-1093">**Ikona** ![ Duo I P v 6 — ikona inicjowania procesu DAD](./media/user-guide/netx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1093">**Icon** ![Duo I P v 6 initiate dad process icon](./media/user-guide/netx-events/image66.png)</span></span>

<span data-ttu-id="e608e-1094">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1094">**Description**</span></span>

<span data-ttu-id="e608e-1095">To zdarzenie reprezentuje rozpoczęcie procesu wykrywania zduplikowanych adresów (DAD), gdy do wystąpienia IP jest przypisany link lokalny lub adres IP interfejsu za pośrednictwem nxd_ipv6_initiate_dad_process.</span><span class="sxs-lookup"><span data-stu-id="e608e-1095">This event represents the start of the Duplicate Address Detection (DAD) process when the IP instance is assigned a link local or an IP interface address via nxd_ipv6_initiate_dad_process.</span></span>

<span data-ttu-id="e608e-1096">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1096">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1097">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1097">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1098">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1098">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1099">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1099">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1100">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1100">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-interface-address-get"></a><span data-ttu-id="e608e-1101">Pobieranie adresu interfejsu IPv6 w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1101">Duo IPv6 Interface Address Get</span></span> 

#### <a name="nxd_ipv6_interface_address_get"></a><span data-ttu-id="e608e-1102">nxd_ipv6_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1102">nxd_ipv6_interface_address_get</span></span>

<span data-ttu-id="e608e-1103">**Ikona** ![ Ikona uzyskiwania adresu interfejsu Duo I P v 6](./media/user-guide/netx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1103">**Icon** ![Duo I P v 6 interface address get icon](./media/user-guide/netx-events/image67.png)</span></span>

<span data-ttu-id="e608e-1104">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1104">**Description**</span></span>

<span data-ttu-id="e608e-1105">To zdarzenie reprezentuje pobieranie adresu IP i prefiksu w określonym indeksie w tabeli adresów interfejsu wystąpienia IP za pośrednictwem nxd_ipv6_interface_address_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1105">This event represents retrieving the IP address and prefix at the specified index into the IP instance interface address table via nxd_ipv6_interface_address_get.</span></span>

<span data-ttu-id="e608e-1106">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1106">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1107">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1107">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1108">Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu IPv6 do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="e608e-1108">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="e608e-1109">Pole informacji 4: indeks interfejsu w tabeli interfejsu wystąpienia protokołu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1109">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-interface-address-set"></a><span data-ttu-id="e608e-1110">Zestaw adresów interfejsu IPv6 w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1110">Duo IPv6 Interface Address Set</span></span> 

### <a name="nxd_ipv6_interface_address_set"></a><span data-ttu-id="e608e-1111">nxd_ipv6_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="e608e-1111">nxd_ipv6_interface_address_set</span></span>

<span data-ttu-id="e608e-1112">**Ikona** ![ Na ikonie "Duo I P v 6"](./media/user-guide/netx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1112">**Icon** ![Duo I P v 6 interface addresss et icon](./media/user-guide/netx-events/image68.png)</span></span>

<span data-ttu-id="e608e-1113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1113">**Description**</span></span>

<span data-ttu-id="e608e-1114">To zdarzenie reprezentuje ustawienie adresu IP i prefiksu w określonym indeksie w tabeli adresów interfejsu wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="e608e-1114">This event represents setting the IP address and prefix at the specified index into the IP instance interface address table.</span></span> <span data-ttu-id="e608e-1115">Niedozwolone w przypadku indeksu zerowego (łączny adres lokalny) za pośrednictwem nxd_ipv6_interface_address_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-1115">Not permitted on index zero (link local address) via nxd_ipv6_interface_address_set.</span></span>

<span data-ttu-id="e608e-1116">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1116">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1117">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1117">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1118">Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu IPv6 do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="e608e-1118">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="e608e-1119">Pole informacji 3: długość prefiksu</span><span class="sxs-lookup"><span data-stu-id="e608e-1119">Info Field 3: Prefix length</span></span>
- <span data-ttu-id="e608e-1120">Pole informacji 4: indeks interfejsu w tabeli interfejsu wystąpienia protokołu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1120">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-link-local-address-get"></a><span data-ttu-id="e608e-1121">Pobieranie adresu lokalnego linku do protokołu Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1121">Duo IPv6 Link Local Address Get</span></span> 

#### <a name="nxd_ipv6_linklocal_address_get"></a><span data-ttu-id="e608e-1122">nxd_ipv6_linklocal_address_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1122">nxd_ipv6_linklocal_address_get</span></span>

<span data-ttu-id="e608e-1123">**Ikona** ![ Ikona uzyskiwania adresu lokalnego linku Duo I P 6](./media/user-guide/netx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1123">**Icon** ![Duo I P v 6 link local address get icon](./media/user-guide/netx-events/image69.png)</span></span>

<span data-ttu-id="e608e-1124">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1124">**Description**</span></span>

<span data-ttu-id="e608e-1125">To zdarzenie reprezentuje pobieranie adresu lokalnego linku określonego wystąpienia IP za pośrednictwem nxd_ipv6_linklocal_address_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1125">This event represents retrieving the link local address of the specified IP instance via nxd_ipv6_linklocal_address_get.</span></span>

<span data-ttu-id="e608e-1126">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1126">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1127">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1127">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1128">Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu lokalnego łącza protokołu IP V6</span><span class="sxs-lookup"><span data-stu-id="e608e-1128">Info Field 2: Fourth word (least significant) of the IP v6 link local address</span></span>
- <span data-ttu-id="e608e-1129">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1129">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1130">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1130">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-link-local-address-set"></a><span data-ttu-id="e608e-1131">Link IPv6 w programie Duo — zestaw adresów lokalnych</span><span class="sxs-lookup"><span data-stu-id="e608e-1131">Duo IPv6 Link Local Address Set</span></span> 

#### <a name="nxd_ipv6_linklocal_address_set"></a><span data-ttu-id="e608e-1132">nxd_ipv6_linklocal_address_set</span><span class="sxs-lookup"><span data-stu-id="e608e-1132">nxd_ipv6_linklocal_address_set</span></span>

<span data-ttu-id="e608e-1133">**Ikona** ![ Ikona zestawu adresów lokalnych linku Duo I v 6](./media/user-guide/netx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1133">**Icon** ![Duo I P v 6 link local address set icon](./media/user-guide/netx-events/image70.png)</span></span>

<span data-ttu-id="e608e-1134">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1134">**Description**</span></span>

<span data-ttu-id="e608e-1135">To zdarzenie reprezentuje adres lokalny łącza wystąpienia IP za pośrednictwem nxd_ipv6_linklocal_address_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-1135">This event represents setting the link local address of the IP instance via nxd_ipv6_linklocal_address_set.</span></span>

<span data-ttu-id="e608e-1136">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1136">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1137">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1137">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1138">Pole informacji 2: czwarty (najmniej znaczący) wyraz adresu lokalnego linku IPv6</span><span class="sxs-lookup"><span data-stu-id="e608e-1138">Info Field 2: Fourth (least significant) word of the IPv6 link local address</span></span>
- <span data-ttu-id="e608e-1139">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1139">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1140">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1140">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-raw-packet-send"></a><span data-ttu-id="e608e-1141">Wysyłanie pakietów RAW protokołu IPv6 w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1141">Duo IPv6 Raw Packet Send</span></span> 

#### <a name="nxd_ipv6_raw_packet_send"></a><span data-ttu-id="e608e-1142">nxd_ipv6_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="e608e-1142">nxd_ipv6_raw_packet_send</span></span>

<span data-ttu-id="e608e-1143">**Ikona** ![ Ikona wysyłania pakietów pierwotnych Duo I v 6](./media/user-guide/netx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1143">**Icon** ![Duo I P v 6 raw packet send icon](./media/user-guide/netx-events/image71.png)</span></span>

<span data-ttu-id="e608e-1144">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1144">**Description**</span></span>

<span data-ttu-id="e608e-1145">To zdarzenie reprezentuje wysyłanie pakietu pierwotnego adresu IP za pośrednictwem podstawowego interfejsu IP do miejsca docelowego podać za pośrednictwem nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="e608e-1145">This event represents sending a raw IP packet through the primary IP interface to the speficied destination via nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="e608e-1146">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1146">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1147">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1147">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1148">Pole informacji 2: wskaźnik do pakietu do wysłania</span><span class="sxs-lookup"><span data-stu-id="e608e-1148">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="e608e-1149">Pole informacji 3: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1149">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="e608e-1150">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1150">Info Field 4: Not used</span></span>

### <a name="duo-tcp-socket-peer-info-get"></a><span data-ttu-id="e608e-1151">Pobieranie informacji o komunikacji równorzędnej gniazda TCP w programie Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1151">Duo TCP Socket Peer Info Get</span></span> 

#### <a name="nxd_tcp_socket_peer_info_get"></a><span data-ttu-id="e608e-1152">nxd_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1152">nxd_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="e608e-1153">**Ikona** ![ Ikona pobierania informacji o komunikacji równorzędnej z gniazdami w programie Duo T C](./media/user-guide/netx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1153">**Icon** ![Duo T C P socket peer info get icon](./media/user-guide/netx-events/image72.png)</span></span>

<span data-ttu-id="e608e-1154">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1154">**Description**</span></span>

<span data-ttu-id="e608e-1155">To zdarzenie wyodrębnia dane nadawcy z odebranego pakietu TCP w określonym gnieździe.</span><span class="sxs-lookup"><span data-stu-id="e608e-1155">This event extracts the sender data from a received TCP packet on the specified socket.</span></span> <span data-ttu-id="e608e-1156">Zwraca adres IP i port nadawcy.</span><span class="sxs-lookup"><span data-stu-id="e608e-1156">It returns the IP address and port of the sender.</span></span>

<span data-ttu-id="e608e-1157">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1157">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1158">Pole informacji 1: wskaźnik gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1158">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="e608e-1159">Pole informacji 2: adres IP elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1159">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="e608e-1160">Pole informacji 3: Port równorzędny</span><span class="sxs-lookup"><span data-stu-id="e608e-1160">Info Field 3: Peer port</span></span>
- <span data-ttu-id="e608e-1161">Pole informacji 4: dzierżawa o znacznym 32-bitowym adresie IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1161">Info Field 4: The lease significant 32-bit of the IP address</span></span>

### <a name="duo-tcp-socket-set-interface"></a><span data-ttu-id="e608e-1162">Interfejs zestawu gniazd TCP Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1162">Duo TCP Socket Set Interface</span></span> 

#### <a name="nxd_tcp_socket_set_interface"></a><span data-ttu-id="e608e-1163">nxd_tcp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="e608e-1163">nxd_tcp_socket_set_interface</span></span>

<span data-ttu-id="e608e-1164">**Ikona** ![ Ikona interfejsu zestawu gniazd w programie Duo T C](./media/user-guide/netx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1164">**Icon** ![Duo T C P socket set interface icon](./media/user-guide/netx-events/image73.png)</span></span>

<span data-ttu-id="e608e-1165">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1165">**Description**</span></span>

<span data-ttu-id="e608e-1166">To zdarzenie reprezentuje ustawienie interfejsu gniazda wychodzącego po połączeniu klienta z serwerem TCP na określonym adresie IP serwera za pośrednictwem nxd_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="e608e-1166">This event represents setting the outgoing socket interface after a client connects with a TCP server on the specified server IP address via nxd_tcp_client_socket_connect.</span></span>

<span data-ttu-id="e608e-1167">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1167">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1168">Pole informacji 1: wskaźnik do gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1168">Info Field 1: Pointer to TCP Socket</span></span>
- <span data-ttu-id="e608e-1169">Pole informacji 2: identyfikator interfejsu</span><span class="sxs-lookup"><span data-stu-id="e608e-1169">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="e608e-1170">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1170">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1171">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1171">Info Field 4: Not used</span></span>

### <a name="duo-udp-socket-send"></a><span data-ttu-id="e608e-1172">Wysłane gniazdo UDP Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1172">Duo UDP Socket Send</span></span> 

#### <a name="nxd_udp_socket_send"></a><span data-ttu-id="e608e-1173">nxd_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="e608e-1173">nxd_udp_socket_send</span></span>

<span data-ttu-id="e608e-1174">**Ikona** ![ Ikona wysyłania z gniazdem Duo U D P](./media/user-guide/netx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1174">**Icon** ![Duo U D P socket send icon](./media/user-guide/netx-events/image74.png)</span></span>

<span data-ttu-id="e608e-1175">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1175">**Description**</span></span>

<span data-ttu-id="e608e-1176">To zdarzenie reprezentuje wysłanie pakietu UDP za pośrednictwem określonego gniazda z wejściowym adresem IP i portem za pośrednictwem nxd_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="e608e-1176">This event represents sending a UDP packet through the specified socket with the input IP address and port via nxd_udp_socket_send.</span></span>

<span data-ttu-id="e608e-1177">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1177">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1178">Pole informacji 1: wskaźnik UDP gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1178">Info Field 1: Pointer UDP Socket</span></span>
- <span data-ttu-id="e608e-1179">Pole informacji 2: wskaźnik do pakietu UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1179">Info Field 2: Pointer to UDP packet</span></span>
- <span data-ttu-id="e608e-1180">Pole informacji 3: długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1180">Info Field 3: Packet length</span></span>
- <span data-ttu-id="e608e-1181">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1181">Info Field 4: Not used</span></span>


### <a name="duo-udp-socket-set-interface"></a><span data-ttu-id="e608e-1182">Interfejs zestawu gniazd UDP Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1182">Duo UDP Socket Set Interface</span></span> 

#### <a name="nxd_udp_socket_set_interface"></a><span data-ttu-id="e608e-1183">nxd_udp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="e608e-1183">nxd_udp_socket_set_interface</span></span>

<span data-ttu-id="e608e-1184">**Ikona** ![ Ikona interfejsu zestawu gniazd w programie Duo U D](./media/user-guide/netx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1184">**Icon** ![Duo U D P socket set interface icon](./media/user-guide/netx-events/image75.png)</span></span>

<span data-ttu-id="e608e-1185">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1185">**Description**</span></span>

<span data-ttu-id="e608e-1186">To zdarzenie reprezentuje ustawienie określonego interfejsu wychodzącego gniazda UDP do interfejsu odpowiadającego IDENTYFIKATORowi interfejsu wejściowego za pośrednictwem nxd_udp_socket_set_interface.</span><span class="sxs-lookup"><span data-stu-id="e608e-1186">This event represents setting the specified UDP socket outgoing interface to the interface corresponding to the input interface ID via nxd_udp_socket_set_interface.</span></span>

<span data-ttu-id="e608e-1187">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1187">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1188">Pole informacji 1: wskaźnik do gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1188">Info Field 1: Pointer to UDP Socket</span></span>
- <span data-ttu-id="e608e-1189">Pole informacji 2: identyfikator interfejsu</span><span class="sxs-lookup"><span data-stu-id="e608e-1189">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="e608e-1190">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1190">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1191">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1191">Info Field 4: Not used</span></span>

### <a name="duo-udp-source-extract"></a><span data-ttu-id="e608e-1192">Wyodrębnij Źródło UDP Duo</span><span class="sxs-lookup"><span data-stu-id="e608e-1192">Duo UDP Source Extract</span></span> 

#### <a name="nxd_udp_socket_extract"></a><span data-ttu-id="e608e-1193">nxd_udp_socket_extract</span><span class="sxs-lookup"><span data-stu-id="e608e-1193">nxd_udp_socket_extract</span></span>

<span data-ttu-id="e608e-1194">**Ikona** ![ Ikona wyodrębnienia źródła w usłudze Duo U D](./media/user-guide/netx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1194">**Icon** ![Duo U D P source extract icon](./media/user-guide/netx-events/image76.png)</span></span>

<span data-ttu-id="e608e-1195">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1195">**Description**</span></span>

<span data-ttu-id="e608e-1196">To zdarzenie reprezentuje wyodrębnienie adresu IP i portu źródłowego odebranego pakietu (IPv4 lub IPv6).</span><span class="sxs-lookup"><span data-stu-id="e608e-1196">This event represents extracting the IP address and source port of a received packet (either IPv4 or IPv6).</span></span> <span data-ttu-id="e608e-1197">Jeśli IPv6, czwarty wyraz (najmniej znaczący) adresu IP jest zwracany przez nxd_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="e608e-1197">If IPv6, the fourth word (least significant) of the IP address is returned via nxd_udp_source_extract.</span></span>

<span data-ttu-id="e608e-1198">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1198">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1199">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1199">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="e608e-1200">Pole informacji 2: wersja adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1200">Info Field 2: IP version</span></span>
- <span data-ttu-id="e608e-1201">Pole informacji 3: źródłowy adres IP (IPv4 lub IPv6)</span><span class="sxs-lookup"><span data-stu-id="e608e-1201">Info Field 3: Source IP address (IPv4 or IPv6)</span></span>
- <span data-ttu-id="e608e-1202">Pole informacji 4: Port źródłowy</span><span class="sxs-lookup"><span data-stu-id="e608e-1202">Info Field 4: Source port</span></span>

### <a name="icmp-enable"></a><span data-ttu-id="e608e-1203">Włączanie protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1203">ICMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="e608e-1204">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1204">nx_icmp_enable</span></span>

<span data-ttu-id="e608e-1205">**Ikona** ![ Ikona włączenia I C M](./media/user-guide/netx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1205">**Icon** ![I C M P enable icon](./media/user-guide/netx-events/image77.png)</span></span>

<span data-ttu-id="e608e-1206">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1206">**Description**</span></span>

<span data-ttu-id="e608e-1207">To zdarzenie reprezentuje włączenie protokołu ICMP za pośrednictwem nx_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1207">This event represents enabling ICMP via nx_icmp_enable.</span></span>

<span data-ttu-id="e608e-1208">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1208">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1209">Pole informacji 1: wskaźnik do wystąpienia IP l;</span><span class="sxs-lookup"><span data-stu-id="e608e-1209">Info Field 1: Pointer to the IP instance l;</span></span>
- <span data-ttu-id="e608e-1210">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1210">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1211">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1211">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1212">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1212">Info Field 4: Not used</span></span>

### <a name="icmp-information-get"></a><span data-ttu-id="e608e-1213">Informacje o protokole ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1213">ICMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="e608e-1214">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1214">nx_icmp_info_get</span></span>

<span data-ttu-id="e608e-1215">**Ikona** ![ I C M P informacje o ikonie](./media/user-guide/netx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1215">**Icon** ![I C M P information get icon](./media/user-guide/netx-events/image78.png)</span></span>

<span data-ttu-id="e608e-1216">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1216">**Description**</span></span>

<span data-ttu-id="e608e-1217">To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_icmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1217">This event represents getting information via nx_icmp_info_get.</span></span>

<span data-ttu-id="e608e-1218">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1218">**Information Fields**</span></span>
- <span data-ttu-id="e608e-1219">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1219">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1220">Pole informacji 2: wysłane polecenia ping</span><span class="sxs-lookup"><span data-stu-id="e608e-1220">Info Field 2: Pings sent</span></span>
- <span data-ttu-id="e608e-1221">Pole informacyjne 3: odpowiedzi ping</span><span class="sxs-lookup"><span data-stu-id="e608e-1221">Info Field 3: Ping responses</span></span>
- <span data-ttu-id="e608e-1222">Pole informacji 4: odebrane polecenia ping</span><span class="sxs-lookup"><span data-stu-id="e608e-1222">Info Field 4: Pings received</span></span>

### <a name="icmp-ping"></a><span data-ttu-id="e608e-1223">Polecenie ping protokołu ICMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1223">ICMP Ping</span></span> 

#### <a name="nx_icmp_ping"></a><span data-ttu-id="e608e-1224">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="e608e-1224">nx_icmp_ping</span></span>

<span data-ttu-id="e608e-1225">**Ikona** ![ I C M P ikona ping](./media/user-guide/netx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1225">**Icon** ![I C M P ping icon](./media/user-guide/netx-events/image79.png)</span></span>

<span data-ttu-id="e608e-1226">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1226">**Description**</span></span>

<span data-ttu-id="e608e-1227">To zdarzenie reprezentuje docelowy adres IP za pośrednictwem nx_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="e608e-1227">This event represents pinging a target IP address via nx_icmp_ping.</span></span>

<span data-ttu-id="e608e-1228">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1228">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1229">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1229">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1230">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1230">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-1231">Pole informacji 3: wskaźnik do danych</span><span class="sxs-lookup"><span data-stu-id="e608e-1231">Info Field 3: Pointer to data</span></span>
- <span data-ttu-id="e608e-1232">Pole informacji 4: rozmiar danych</span><span class="sxs-lookup"><span data-stu-id="e608e-1232">Info Field 4: Size of data</span></span>

### <a name="igmp-enable"></a><span data-ttu-id="e608e-1233">Włączanie IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1233">IGMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="e608e-1234">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1234">nx_icmp_enable</span></span>

<span data-ttu-id="e608e-1235">**Ikona** ![ Ikona włączenia I G M](./media/user-guide/netx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1235">**Icon** ![I G M P enable icon](./media/user-guide/netx-events/image80.png)</span></span>

<span data-ttu-id="e608e-1236">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1236">**Description**</span></span>

<span data-ttu-id="e608e-1237">To zdarzenie reprezentuje włączenie protokołu IGMP za pośrednictwem nx_igmp_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1237">This event represents enabling IGMP via nx_igmp_enable.</span></span>

<span data-ttu-id="e608e-1238">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1238">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1239">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1239">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1240">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1240">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1241">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1241">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1242">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1242">Info Field 4: Not used</span></span>

### <a name="igmp-information-get"></a><span data-ttu-id="e608e-1243">Informacje o protokole IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1243">IGMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="e608e-1244">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1244">nx_icmp_info_get</span></span>

<span data-ttu-id="e608e-1245">**Ikona** ![ Ikona uzyskiwania informacji o & G M](./media/user-guide/netx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1245">**Icon** ![I G M P information get icon](./media/user-guide/netx-events/image81.png)</span></span>

<span data-ttu-id="e608e-1246">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1246">**Description**</span></span>

<span data-ttu-id="e608e-1247">To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_igmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1247">This event represents getting information via nx_igmp_info_get.</span></span>

<span data-ttu-id="e608e-1248">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1248">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1249">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1249">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1250">Pole informacji 2: wysłane raporty</span><span class="sxs-lookup"><span data-stu-id="e608e-1250">Info Field 2: Reports sent</span></span>
- <span data-ttu-id="e608e-1251">Pole informacji 3: Odebrane kwerendy</span><span class="sxs-lookup"><span data-stu-id="e608e-1251">Info Field 3: Queries received</span></span>
- <span data-ttu-id="e608e-1252">Pole informacji 4: grupy dołączone</span><span class="sxs-lookup"><span data-stu-id="e608e-1252">Info Field 4: Groups joined</span></span>

### <a name="igmp-loopback-disable"></a><span data-ttu-id="e608e-1253">Wyłączenie sprzężenia zwrotnego protokołu IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1253">IGMP Loopback Disable</span></span> 

#### <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="e608e-1254">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="e608e-1254">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="e608e-1255">**Ikona** ![ Ikona wyłączenia sprzężenia zwrotnego I G M](./media/user-guide/netx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1255">**Icon** ![I G M P loopback disable icon](./media/user-guide/netx-events/image82.png)</span></span>

<span data-ttu-id="e608e-1256">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1256">**Description**</span></span>

<span data-ttu-id="e608e-1257">To zdarzenie reprezentuje wyłączenie sprzężenia zwrotnego protokołu IGMP za pośrednictwem nx_igmp_loopback_disable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1257">This event represents disabling IGMP loopback via nx_igmp_loopback_disable.</span></span>

<span data-ttu-id="e608e-1258">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1258">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1259">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1259">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1260">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1260">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1261">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1261">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1262">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1262">Info Field 4: Not used</span></span>

### <a name="igmp-loopback-enable"></a><span data-ttu-id="e608e-1263">Włączanie sprzężenia zwrotnego protokołu IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1263">IGMP Loopback Enable</span></span> 

#### <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="e608e-1264">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1264">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="e608e-1265">**Ikona** ![ Ikona włączania sprzężenia zwrotnego M P](./media/user-guide/netx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1265">**Icon** ![I G M P loopback enable icon](./media/user-guide/netx-events/image83.png)</span></span>

<span data-ttu-id="e608e-1266">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1266">**Description**</span></span>

<span data-ttu-id="e608e-1267">To zdarzenie reprezentuje włączenie sprzężenia zwrotnego protokołu IGMP za pośrednictwem nx_igmp_loopback_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1267">This event represents enabling IGMP loopback via nx_igmp_loopback_enable.</span></span>

<span data-ttu-id="e608e-1268">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1268">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1269">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1269">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1270">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1270">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1271">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1271">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1272">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1272">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-join"></a><span data-ttu-id="e608e-1273">Sprzężenie multiemisji IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1273">IGMP Multicast Join</span></span> 

#### <a name="nx_igmp_multicast_join"></a><span data-ttu-id="e608e-1274">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="e608e-1274">nx_igmp_multicast_join</span></span>

<span data-ttu-id="e608e-1275">**Ikona** ![ Ikona sprzężenia multiemisji I G M](./media/user-guide/netx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1275">**Icon** ![I G M P multicast join icon](./media/user-guide/netx-events/image84.png)</span></span>

<span data-ttu-id="e608e-1276">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1276">**Description**</span></span>

<span data-ttu-id="e608e-1277">To zdarzenie reprezentuje grupę multiemisji za pośrednictwem nx_igmp_multicast_join.</span><span class="sxs-lookup"><span data-stu-id="e608e-1277">This event represents joining a multicast group via nx_igmp_multicast_join.</span></span>

<span data-ttu-id="e608e-1278">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1278">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1279">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1279">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1280">Pole informacji 2: adres IP grupy</span><span class="sxs-lookup"><span data-stu-id="e608e-1280">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="e608e-1281">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1281">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1282">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1282">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-leave"></a><span data-ttu-id="e608e-1283">Wyjście z multiemisji IGMP</span><span class="sxs-lookup"><span data-stu-id="e608e-1283">IGMP Multicast Leave</span></span> 

#### <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="e608e-1284">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="e608e-1284">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="e608e-1285">**Ikona** ![ Ikona urlopu multiemisji I G M](./media/user-guide/netx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1285">**Icon** ![I G M P multicast leave icon](./media/user-guide/netx-events/image85.png)</span></span>

<span data-ttu-id="e608e-1286">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1286">**Description**</span></span>

<span data-ttu-id="e608e-1287">To zdarzenie oznacza opuszczenie grupy multiemisji za pośrednictwem nx_igmp_multicast_leave.</span><span class="sxs-lookup"><span data-stu-id="e608e-1287">This event represents leaving a multicast group via nx_igmp_multicast_leave.</span></span>

<span data-ttu-id="e608e-1288">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1288">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1289">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1289">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1290">Pole informacji 2: adres IP grupy</span><span class="sxs-lookup"><span data-stu-id="e608e-1290">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="e608e-1291">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1291">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1292">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1292">Info Field 4: Not used</span></span>

### <a name="ip-address-change-notify"></a><span data-ttu-id="e608e-1293">Powiadomienie o zmianie adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1293">IP Address Change Notify</span></span> 

#### <a name="nx_ip_address_change_notify"></a><span data-ttu-id="e608e-1294">nx_ip_address_change_notify</span><span class="sxs-lookup"><span data-stu-id="e608e-1294">nx_ip_address_change_notify</span></span>

<span data-ttu-id="e608e-1295">**Ikona** ![ Ikona powiadomienia o zmianie adresu](./media/user-guide/netx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1295">**Icon** ![I P address change notify icon](./media/user-guide/netx-events/image86.png)</span></span>

<span data-ttu-id="e608e-1296">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1296">**Description**</span></span>

<span data-ttu-id="e608e-1297">To zdarzenie reprezentuje rejestrację dla powiadomienia o zmianie adresu IP za pośrednictwem nx_ip_address_change_notify.</span><span class="sxs-lookup"><span data-stu-id="e608e-1297">This event represents registering for IP change notification via nx_ip_address_change_notify.</span></span>

<span data-ttu-id="e608e-1298">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1298">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1299">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1299">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1300">Pole informacji 2: wskaźnik funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1300">Info Field 2: Callback function pointer</span></span>
- <span data-ttu-id="e608e-1301">Pole informacji 3: dodatkowy wskaźnik informacji</span><span class="sxs-lookup"><span data-stu-id="e608e-1301">Info Field 3: Additional information pointer</span></span>
- <span data-ttu-id="e608e-1302">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1302">Info Field 4: Not used</span></span>

### <a name="ip-address-get"></a><span data-ttu-id="e608e-1303">Pobieranie adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1303">IP Address Get</span></span> 

#### <a name="nx_ip_address_get"></a><span data-ttu-id="e608e-1304">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1304">nx_ip_address_get</span></span>

<span data-ttu-id="e608e-1305">**Ikona** ![ Ikona pobierania adresu](./media/user-guide/netx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1305">**Icon** ![I P address get icon](./media/user-guide/netx-events/image87.png)</span></span>

<span data-ttu-id="e608e-1306">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1306">**Description**</span></span>

<span data-ttu-id="e608e-1307">To zdarzenie reprezentuje pobieranie adresu IP za pośrednictwem nx_ip_address_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1307">This event represents getting the IP address via nx_ip_address_get.</span></span>

<span data-ttu-id="e608e-1308">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1308">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1309">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1309">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1310">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1310">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-1311">Pole informacji 3: Maska sieci</span><span class="sxs-lookup"><span data-stu-id="e608e-1311">Info Field 3: Network mask</span></span>
- <span data-ttu-id="e608e-1312">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1312">Info Field 4: Not used</span></span>

### <a name="ip-address-set"></a><span data-ttu-id="e608e-1313">Zestaw adresów IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1313">IP Address Set</span></span> 

#### <a name="nx_ip_address_set"></a><span data-ttu-id="e608e-1314">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="e608e-1314">nx_ip_address_set</span></span>

<span data-ttu-id="e608e-1315">**Ikona** ![ Ikona zestawu adresów I P](./media/user-guide/netx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1315">**Icon** ![I P address set icon](./media/user-guide/netx-events/image88.png)</span></span>

<span data-ttu-id="e608e-1316">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1316">**Description**</span></span>

<span data-ttu-id="e608e-1317">To zdarzenie reprezentuje ustawienie adresu IP za pośrednictwem nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-1317">This event represents setting the IP address via nx_ip_address_set.</span></span>

<span data-ttu-id="e608e-1318">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1318">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1319">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1319">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1320">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1320">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-1321">Pole informacji 3: Maska sieci</span><span class="sxs-lookup"><span data-stu-id="e608e-1321">Info Field 3: Network mask</span></span>
- <span data-ttu-id="e608e-1322">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1322">Info Field 4: Not used</span></span>

### <a name="ip-create"></a><span data-ttu-id="e608e-1323">Tworzenie adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1323">IP Create</span></span> 

#### <a name="nx_ip_create"></a><span data-ttu-id="e608e-1324">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="e608e-1324">nx_ip_create</span></span>

<span data-ttu-id="e608e-1325">**Ikona** ![ Ikona tworzenia](./media/user-guide/netx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1325">**Icon** ![I P create icon](./media/user-guide/netx-events/image89.png)</span></span>

<span data-ttu-id="e608e-1326">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1326">**Description**</span></span>

<span data-ttu-id="e608e-1327">To zdarzenie reprezentuje Tworzenie wystąpienia adresu IP za pośrednictwem nx_ip_create.</span><span class="sxs-lookup"><span data-stu-id="e608e-1327">This event represents creating an IP instance via nx_ip_create.</span></span>

<span data-ttu-id="e608e-1328">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1328">**Information Fields**</span></span> 
- <span data-ttu-id="e608e-1329">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1329">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1330">Pole informacji 2: adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1330">Info Field 2: IP address</span></span>
- <span data-ttu-id="e608e-1331">Pole informacji 3: Maska sieci</span><span class="sxs-lookup"><span data-stu-id="e608e-1331">Info Field 3: Network mask</span></span>
- <span data-ttu-id="e608e-1332">Pole informacji 4: domyślny wskaźnik puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1332">Info Field 4: Default packet pool pointer</span></span>

### <a name="ip-delete"></a><span data-ttu-id="e608e-1333">Usuwanie adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1333">IP Delete</span></span> 

#### <a name="nx_ip_delete"></a><span data-ttu-id="e608e-1334">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-1334">nx_ip_delete</span></span>

<span data-ttu-id="e608e-1335">**Ikona** ![ Ikona usuwania](./media/user-guide/netx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1335">**Icon** ![I P delete icon](./media/user-guide/netx-events/image90.png)</span></span>

<span data-ttu-id="e608e-1336">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1336">**Description**</span></span>

<span data-ttu-id="e608e-1337">To zdarzenie reprezentuje usunięcie wystąpienia adresu IP za pośrednictwem nx_ip_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-1337">This event represents deleting an IP instance via nx_ip_delete.</span></span>

<span data-ttu-id="e608e-1338">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1338">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1339">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1339">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1340">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1340">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1341">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1341">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1342">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1342">Info Field 4: Not used</span></span>

### <a name="ip-driver-direct-command"></a><span data-ttu-id="e608e-1343">Polecenie sterownika IP Direct</span><span class="sxs-lookup"><span data-stu-id="e608e-1343">IP Driver Direct Command</span></span> 

#### <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="e608e-1344">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="e608e-1344">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="e608e-1345">**Ikona** ![ Ikona poleceń I P sterownika](./media/user-guide/netx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1345">**Icon** ![I P driver direct command icon](./media/user-guide/netx-events/image91.png)</span></span>

<span data-ttu-id="e608e-1346">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1346">**Description**</span></span>

<span data-ttu-id="e608e-1347">To zdarzenie reprezentuje polecenie bezpośredniego sterownika we/wy za pośrednictwem nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="e608e-1347">This event represents a direct I/O driver command via nx_ip_driver_direct_command.</span></span>

<span data-ttu-id="e608e-1348">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1348">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1349">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1349">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1350">Pole informacji 2: Sterownik polecenie</span><span class="sxs-lookup"><span data-stu-id="e608e-1350">Info Field 2: Driver command</span></span>
- <span data-ttu-id="e608e-1351">Pole informacji 3: wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e608e-1351">Info Field 3: Return value</span></span>
- <span data-ttu-id="e608e-1352">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1352">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-disable"></a><span data-ttu-id="e608e-1353">Wyłączanie przekazywania adresów IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1353">IP Forwarding Disable</span></span> 

#### <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="e608e-1354">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="e608e-1354">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="e608e-1355">**Ikona** ![ Ikona wyłączonego przesyłania dalej](./media/user-guide/netx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1355">**Icon** ![I P forwarding disable icon](./media/user-guide/netx-events/image92.png)</span></span>

<span data-ttu-id="e608e-1356">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1356">**Description**</span></span>

<span data-ttu-id="e608e-1357">To zdarzenie przedstawia wyłączenie przesyłania dalej adresów IP za pośrednictwem nx_ip_forwarding_disable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1357">This event represents disabling IP forwarding via nx_ip_forwarding_disable.</span></span>

<span data-ttu-id="e608e-1358">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1358">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1359">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1359">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1360">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1360">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1361">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1361">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1362">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1362">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-enable"></a><span data-ttu-id="e608e-1363">Włączanie przekazywania adresów IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1363">IP Forwarding Enable</span></span> 

#### <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="e608e-1364">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1364">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="e608e-1365">**Ikona** ![ Ikona włączania przesyłania dalej](./media/user-guide/netx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1365">**Icon** ![I P forwarding enable icon](./media/user-guide/netx-events/image93.png)</span></span>

<span data-ttu-id="e608e-1366">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1366">**Description**</span></span>

<span data-ttu-id="e608e-1367">To zdarzenie reprezentuje włączenie przekazywania adresów IP za pośrednictwem nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1367">This event represents enabling IP forwarding via nx_ip_forwarding_enable.</span></span>

<span data-ttu-id="e608e-1368">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1368">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1369">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1369">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1370">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1370">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1371">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1371">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1372">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1372">Info Field 4: Not used</span></span>

### <a name="ip-fragment-disable"></a><span data-ttu-id="e608e-1373">Wyłączenie fragmentu adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1373">IP Fragment Disable</span></span> 

#### <a name="nx_ip_fragment_disable"></a><span data-ttu-id="e608e-1374">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="e608e-1374">nx_ip_fragment_disable</span></span>

<span data-ttu-id="e608e-1375">**Ikona** ![ Ikona wyłączenia fragmentu](./media/user-guide/netx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1375">**Icon** ![I P fragment disable icon](./media/user-guide/netx-events/image94.png)</span></span>

<span data-ttu-id="e608e-1376">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1376">**Description**</span></span>

<span data-ttu-id="e608e-1377">To zdarzenie przedstawia wyłączenie fragmentacji adresów IP za pośrednictwem nx_ip_fragment_disable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1377">This event represents disabling IP fragmenting via nx_ip_fragment_disable.</span></span>

<span data-ttu-id="e608e-1378">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1378">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1379">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1379">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1380">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1380">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1381">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1381">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1382">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1382">Info Field 4: Not used</span></span>

### <a name="ip-fragment-enable"></a><span data-ttu-id="e608e-1383">Włączanie fragmentu adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1383">IP Fragment Enable</span></span> 

#### <a name="nx_ip_fragment_enable"></a><span data-ttu-id="e608e-1384">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1384">nx_ip_fragment_enable</span></span>

<span data-ttu-id="e608e-1385">**Ikona** ![ Ikona włączenia fragmentu](./media/user-guide/netx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1385">**Icon** ![I P fragment enable icon](./media/user-guide/netx-events/image95.png)</span></span>

<span data-ttu-id="e608e-1386">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1386">**Description**</span></span>

<span data-ttu-id="e608e-1387">To zdarzenie reprezentuje włączenie fragmentacji adresów IP za pośrednictwem nx_ip_fragment_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1387">This event represents enabling IP fragmenting via nx_ip_fragment_enable.</span></span>

<span data-ttu-id="e608e-1388">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1388">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1389">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1389">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1390">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1390">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1391">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1391">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1392">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1392">Info Field 4: Not used</span></span>

### <a name="ip-gateway-address-set"></a><span data-ttu-id="e608e-1393">Zestaw adresów IP bramy</span><span class="sxs-lookup"><span data-stu-id="e608e-1393">IP Gateway Address Set</span></span> 

#### <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="e608e-1394">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="e608e-1394">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="e608e-1395">**Ikona** ![ Ikona zestawu adresów bramy I](./media/user-guide/netx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1395">**Icon** ![I P gateway address set icon](./media/user-guide/netx-events/image96.png)</span></span>

<span data-ttu-id="e608e-1396">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1396">**Description**</span></span>

<span data-ttu-id="e608e-1397">To zdarzenie reprezentuje ustawienie adresu IP bramy za pośrednictwem nx_ip_gateway_address_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-1397">This event represents setting the gateway IP address via nx_ip_gateway_address_set.</span></span>

<span data-ttu-id="e608e-1398">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1398">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1399">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1399">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1400">Pole informacji 2: adres IP bramy</span><span class="sxs-lookup"><span data-stu-id="e608e-1400">Info Field 2: Gateway IP address</span></span>
- <span data-ttu-id="e608e-1401">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1401">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1402">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1402">Info Field 4: Not used</span></span>

### <a name="ip-information-get"></a><span data-ttu-id="e608e-1403">Pobieranie informacji o adresie IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1403">IP Information Get</span></span> 

#### <a name="nx_ip_info_get"></a><span data-ttu-id="e608e-1404">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1404">nx_ip_info_get</span></span>

<span data-ttu-id="e608e-1405">**Ikona** ![ Ikona uzyskiwania informacji](./media/user-guide/netx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1405">**Icon** ![I P information get icon](./media/user-guide/netx-events/image97.png)</span></span>

<span data-ttu-id="e608e-1406">**Opis** To zdarzenie reprezentuje informacje o uzyskiwaniu adresu IP za pośrednictwem nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1406">**Description** This event represents getting IP information via nx_ip_info_get.</span></span>

<span data-ttu-id="e608e-1407">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1407">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1408">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1408">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1409">Pole informacji 2: Wysłane bajty IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1409">Info Field 2: IP bytes sent</span></span>
- <span data-ttu-id="e608e-1410">Pole informacji 3: Odebrane bajty IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1410">Info Field 3: IP bytes received</span></span>
- <span data-ttu-id="e608e-1411">Pole informacji 4: porzucone pakiety IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1411">Info Field 4: IP packets dropped</span></span>

### <a name="ip-interface-attach"></a><span data-ttu-id="e608e-1412">Dołączanie interfejsu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1412">IP Interface Attach</span></span> 

#### <a name="nx_interface_attach"></a><span data-ttu-id="e608e-1413">nx_interface_attach</span><span class="sxs-lookup"><span data-stu-id="e608e-1413">nx_interface_attach</span></span>

<span data-ttu-id="e608e-1414">**Ikona** ![ P Iterface ikona dołączania](./media/user-guide/netx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1414">**Icon** ![I P iterface attach icon](./media/user-guide/netx-events/image98.png)</span></span>

<span data-ttu-id="e608e-1415">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1415">**Description**</span></span>

<span data-ttu-id="e608e-1416">To zdarzenie reprezentuje pomocniczy interfejs sieciowy, który jest dołączany do wystąpienia IP za pośrednictwem nx_ip_interface_attach.</span><span class="sxs-lookup"><span data-stu-id="e608e-1416">This event represents a secondary network interface being attached to the IP instance via nx_ip_interface_attach.</span></span>

<span data-ttu-id="e608e-1417">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1417">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1418">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1418">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1419">Pole informacji 2: adres IP interfejsu</span><span class="sxs-lookup"><span data-stu-id="e608e-1419">Info Field 2: Interface IP Address</span></span>
- <span data-ttu-id="e608e-1420">Pole informacji 3: indeksowanie w tabeli interfejsów IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1420">Info Field 3: Index into IP interface table</span></span>
- <span data-ttu-id="e608e-1421">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1421">Info Field 4: Not used</span></span>

### <a name="ip-interface-info-get"></a><span data-ttu-id="e608e-1422">Pobieranie informacji o interfejsie IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1422">IP Interface Info Get</span></span> 

#### <a name="nx_ip_interface_info_get"></a><span data-ttu-id="e608e-1423">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1423">nx_ip_interface_info_get</span></span>

<span data-ttu-id="e608e-1424">**Ikona** ![ Ikona uzyskiwania informacji o interfejsie IP](./media/user-guide/netx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1424">**Icon** ![ IP interface info get icon](./media/user-guide/netx-events/image99.png)</span></span>

<span data-ttu-id="e608e-1425">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1425">**Description**</span></span>

<span data-ttu-id="e608e-1426">To zdarzenie reprezentuje informacje pobrane z określonego interfejsu sieciowego za pośrednictwem nx_ip_interface_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1426">This event represents information retrieved from the specified network interface via nx_ip_interface_info_get.</span></span>

<span data-ttu-id="e608e-1427">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1427">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1428">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1428">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1429">Pole informacji 2: adres IP interfejsu</span><span class="sxs-lookup"><span data-stu-id="e608e-1429">Info Field 2: Interface IP address</span></span>
- <span data-ttu-id="e608e-1430">Pole informacyjne 3: adres MAC interfejsu MSB</span><span class="sxs-lookup"><span data-stu-id="e608e-1430">Info Field 3: Interface MAC address msb</span></span>
- <span data-ttu-id="e608e-1431">Pole informacji 4: adres MAC interfejsu LSB</span><span class="sxs-lookup"><span data-stu-id="e608e-1431">Info Field 4: Interface MAC address lsb</span></span>

### <a name="ip-raw-packet-disable"></a><span data-ttu-id="e608e-1432">Wyłączanie pierwotnego pakietu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1432">IP Raw Packet Disable</span></span> 

#### <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="e608e-1433">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="e608e-1433">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="e608e-1434">**Ikona** ![ Ikona wyłączania pakietów pierwotnych](./media/user-guide/netx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1434">**Icon** ![I P raw packet disable icon](./media/user-guide/netx-events/image100.png)</span></span>

<span data-ttu-id="e608e-1435">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1435">**Description**</span></span>

<span data-ttu-id="e608e-1436">To zdarzenie reprezentuje wyłączenie komunikacji pakietów pierwotnych adresów IP za pośrednictwem nx_ip_raw_packet_disable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1436">This event represents disabling raw IP packet communication via nx_ip_raw_packet_disable.</span></span>

<span data-ttu-id="e608e-1437">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1437">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1438">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1438">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1439">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1439">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1440">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1440">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1441">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1441">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-enable"></a><span data-ttu-id="e608e-1442">Włączanie pakietów pierwotnych adresów IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1442">IP Raw Packet Enable</span></span> 

#### <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="e608e-1443">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1443">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="e608e-1444">**Ikona** ![ Ikona włączenia pakietu RAW](./media/user-guide/netx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1444">**Icon** ![I P raw packet enable icon](./media/user-guide/netx-events/image101.png)</span></span>

<span data-ttu-id="e608e-1445">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1445">**Description**</span></span>

<span data-ttu-id="e608e-1446">To zdarzenie reprezentuje włączenie komunikacji pakietów pierwotnych adresów IP za pośrednictwem nx_ip_raw_packet_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1446">This event represents enabling raw IP packet communication via nx_ip_raw_packet_enable.</span></span>

<span data-ttu-id="e608e-1447">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1447">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1448">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1448">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1449">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1449">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1450">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1450">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1451">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1451">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-receive"></a><span data-ttu-id="e608e-1452">Odbieranie pakietów pierwotnych adresów IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1452">IP Raw Packet Receive</span></span> 

#### <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="e608e-1453">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="e608e-1453">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="e608e-1454">**Ikona** ![ Ikona odbierania pakietów RAW](./media/user-guide/netx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1454">**Icon** ![I P raw packet receive icon](./media/user-guide/netx-events/image102.png)</span></span>

<span data-ttu-id="e608e-1455">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1455">**Description**</span></span>

<span data-ttu-id="e608e-1456">To zdarzenie reprezentuje pakiet Raw IP za pośrednictwem nx_ip_raw_packet_receive.</span><span class="sxs-lookup"><span data-stu-id="e608e-1456">This event represents receiving a raw IP packet via nx_ip_raw_packet_receive.</span></span>

<span data-ttu-id="e608e-1457">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1457">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1458">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1458">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1459">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1459">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-1460">Pole informacji 3: opcja oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1460">Info Field 3: Wait option</span></span>
- <span data-ttu-id="e608e-1461">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1461">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-send"></a><span data-ttu-id="e608e-1462">Wysyłanie pakietów Raw IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1462">IP Raw Packet Send</span></span> 

#### <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="e608e-1463">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="e608e-1463">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="e608e-1464">**Ikona** ![ Ikona wysyłania pakietów RAW](./media/user-guide/netx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1464">**Icon** ![I P raw packet send icon](./media/user-guide/netx-events/image103.png)</span></span>

<span data-ttu-id="e608e-1465">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1465">**Description**</span></span>

<span data-ttu-id="e608e-1466">To zdarzenie reprezentuje wysyłanie pakietów pierwotnych adresów IP za pośrednictwem nx_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="e608e-1466">This event represents sending a raw IP packet via nx_ip_raw_packet_send.</span></span>

<span data-ttu-id="e608e-1467">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1467">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1468">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1468">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1469">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1469">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-1470">Pole informacji 3: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1470">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="e608e-1471">Pole informacji 4: typ usługi</span><span class="sxs-lookup"><span data-stu-id="e608e-1471">Info Field 4: Type of service</span></span>

### <a name="ip-static-route-add"></a><span data-ttu-id="e608e-1472">Dodawanie statycznej trasy IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1472">IP Static Route Add</span></span> 

#### <a name="nx_ip_static_route_add"></a><span data-ttu-id="e608e-1473">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="e608e-1473">nx_ip_static_route_add</span></span>

<span data-ttu-id="e608e-1474">**Ikona** ![ Ikona dodawania trasy statycznej](./media/user-guide/netx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1474">**Icon** ![I P static route add icon](./media/user-guide/netx-events/image104.png)</span></span>

<span data-ttu-id="e608e-1475">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1475">**Description**</span></span>

<span data-ttu-id="e608e-1476">To zdarzenie reprezentuje trasę statyczną dodawaną do tabeli routingu wystąpień IP za pośrednictwem nx_ip_static_route_add.</span><span class="sxs-lookup"><span data-stu-id="e608e-1476">This event represents a static route being added to the IP instance routing table via nx_ip_static_route_add.</span></span>

<span data-ttu-id="e608e-1477">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1477">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1478">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1478">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1479">Pole informacji 2: adres sieciowy</span><span class="sxs-lookup"><span data-stu-id="e608e-1479">Info Field 2: Network address</span></span>
- <span data-ttu-id="e608e-1480">Pole informacji 3: Maska sieci</span><span class="sxs-lookup"><span data-stu-id="e608e-1480">Info Field 3: Network mask</span></span>
- <span data-ttu-id="e608e-1481">Pole informacji 4: Następny przeskok</span><span class="sxs-lookup"><span data-stu-id="e608e-1481">Info Field 4: Next hop</span></span>

### <a name="ip-static-route-delete"></a><span data-ttu-id="e608e-1482">Usuwanie statycznej trasy IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1482">IP Static Route Delete</span></span> 

#### <a name="nx_ip_static_route_delete"></a><span data-ttu-id="e608e-1483">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-1483">nx_ip_static_route_delete</span></span>

<span data-ttu-id="e608e-1484">**Ikona** ![ & P static Rute Delete Icon](./media/user-guide/netx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1484">**Icon** ![I P static rute delete icon](./media/user-guide/netx-events/image105.png)</span></span>

<span data-ttu-id="e608e-1485">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1485">**Description**</span></span>

<span data-ttu-id="e608e-1486">To zdarzenie reprezentuje trasę statyczną usuwaną z tabeli routingu wystąpień IP za pośrednictwem nx_ip_static_route_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-1486">This event represents a static route being removed from the IP instance routing table via nx_ip_static_route_delete.</span></span>

<span data-ttu-id="e608e-1487">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1487">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1488">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1488">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1489">Pole informacji 2: adres sieciowy</span><span class="sxs-lookup"><span data-stu-id="e608e-1489">Info Field 2: Network address</span></span>
- <span data-ttu-id="e608e-1490">Pole informacji 3: Maska sieci</span><span class="sxs-lookup"><span data-stu-id="e608e-1490">Info Field 3: Network mask</span></span>
- <span data-ttu-id="e608e-1491">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1491">Info Field 4: Not used</span></span>

### <a name="ip-status-check"></a><span data-ttu-id="e608e-1492">Sprawdzenie stanu adresów IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1492">IP Status Check</span></span> 

#### <a name="nx_ip_status_check"></a><span data-ttu-id="e608e-1493">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="e608e-1493">nx_ip_status_check</span></span>

<span data-ttu-id="e608e-1494">**Ikona** ![ Ikona sprawdzania stanu P](./media/user-guide/netx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1494">**Icon** ![I P status check icon](./media/user-guide/netx-events/image106.png)</span></span>

<span data-ttu-id="e608e-1495">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1495">**Description**</span></span>

<span data-ttu-id="e608e-1496">To zdarzenie reprezentuje sprawdzenie stanu IP za pośrednictwem nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="e608e-1496">This event represents checking for an IP status via nx_ip_status_check.</span></span>

<span data-ttu-id="e608e-1497">Pola informacji</span><span class="sxs-lookup"><span data-stu-id="e608e-1497">Information Fields</span></span> 

- <span data-ttu-id="e608e-1498">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1498">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="e608e-1499">Pole informacji 2: żądany stan</span><span class="sxs-lookup"><span data-stu-id="e608e-1499">Info Field 2: Requested status</span></span>
- <span data-ttu-id="e608e-1500">Pole informacji 3: rzeczywisty stan</span><span class="sxs-lookup"><span data-stu-id="e608e-1500">Info Field 3: Actual status</span></span>
- <span data-ttu-id="e608e-1501">Pole informacji 4: opcja oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1501">Info Field 4: Wait option</span></span>

### <a name="ipsec-enable"></a><span data-ttu-id="e608e-1502">Włączanie protokołu IPSEC</span><span class="sxs-lookup"><span data-stu-id="e608e-1502">IPSEC Enable</span></span> 

#### <a name="nx_ipsec_enable"></a><span data-ttu-id="e608e-1503">nx_ipsec_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1503">nx_ipsec_enable</span></span>

<span data-ttu-id="e608e-1504">**Ikona** ![ Ikona włączenia I S E C](./media/user-guide/netx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1504">**Icon** ![I P S E C enable icon](./media/user-guide/netx-events/image107.png)</span></span>

<span data-ttu-id="e608e-1505">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1505">**Description**</span></span>

<span data-ttu-id="e608e-1506">To zdarzenie reprezentuje włączenie usług IPSec w podanym wystąpieniu IP za pośrednictwem nx_ipsec_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1506">This event represents enabling IPSec services on the supplied IP instance via nx_ipsec_enable.</span></span>

<span data-ttu-id="e608e-1507">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1507">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1508">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1508">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1509">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1509">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1510">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1510">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1511">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1511">Info Field 4: Not used</span></span>

### <a name="packet-allocate"></a><span data-ttu-id="e608e-1512">Przydział pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1512">Packet Allocate</span></span> 

#### <a name="nx_packet_allocate"></a><span data-ttu-id="e608e-1513">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="e608e-1513">nx_packet_allocate</span></span>

<span data-ttu-id="e608e-1514">**Ikona** ![ Ikona alokacji pakietów](./media/user-guide/netx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1514">**Icon** ![Packet allocate icon](./media/user-guide/netx-events/image108.png)</span></span>

<span data-ttu-id="e608e-1515">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1515">**Description**</span></span>

<span data-ttu-id="e608e-1516">To zdarzenie reprezentuje przydzielenie pakietu za pośrednictwem nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="e608e-1516">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="e608e-1517">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1517">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1518">Pole informacji 1: wskaźnik do puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1518">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="e608e-1519">Pole informacji 2: wskaźnik do przydzielenia pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1519">Info Field 2: Pointer to packet allocated</span></span>
- <span data-ttu-id="e608e-1520">Pole informacji 3: typ pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1520">Info Field 3: Packet type</span></span>
- <span data-ttu-id="e608e-1521">Pole informacji 4: dostępne pakiety</span><span class="sxs-lookup"><span data-stu-id="e608e-1521">Info Field 4: Available packets</span></span>

### <a name="packet-copy"></a><span data-ttu-id="e608e-1522">Kopiowanie pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1522">Packet Copy</span></span> 

#### <a name="nx_packet_copy"></a><span data-ttu-id="e608e-1523">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="e608e-1523">nx_packet_copy</span></span>

<span data-ttu-id="e608e-1524">**Ikona** ![ Ikona CPY pakietu](./media/user-guide/netx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1524">**Icon** ![Packet cpy icon](./media/user-guide/netx-events/image109.png)</span></span>

<span data-ttu-id="e608e-1525">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1525">**Description**</span></span>

<span data-ttu-id="e608e-1526">To zdarzenie reprezentuje kopiowanie pakietu za pośrednictwem nx_packet_copy.</span><span class="sxs-lookup"><span data-stu-id="e608e-1526">This event represents copying a packet via nx_packet_copy.</span></span>

<span data-ttu-id="e608e-1527">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1527">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1528">Pole informacji 2: Nowy wskaźnik pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1528">Info Field 2: New packet pointer</span></span>
- <span data-ttu-id="e608e-1529">Pole informacji 3: wskaźnik do puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1529">Info Field 3: Pointer to packet pool</span></span>
- <span data-ttu-id="e608e-1530">Pole informacji 4: opcja oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1530">Info Field 4: Wait option</span></span>

### <a name="packet-data-append"></a><span data-ttu-id="e608e-1531">Dołączanie danych pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1531">Packet Data Append</span></span> 

#### <a name="nx_packet_data_append"></a><span data-ttu-id="e608e-1532">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="e608e-1532">nx_packet_data_append</span></span>

<span data-ttu-id="e608e-1533">**Ikona** ![ Ikona dołączania danych pakietu](./media/user-guide/netx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1533">**Icon** ![Packet data append icon](./media/user-guide/netx-events/image110.png)</span></span>

<span data-ttu-id="e608e-1534">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1534">**Description**</span></span>

<span data-ttu-id="e608e-1535">To zdarzenie reprezentuje dołączenie danych do pakietu za pośrednictwem nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="e608e-1535">This event represents appending data to a packet via nx_packet_data_append.</span></span>

<span data-ttu-id="e608e-1536">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1536">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1537">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1537">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="e608e-1538">Pole informacji 2: wskaźnik do danych</span><span class="sxs-lookup"><span data-stu-id="e608e-1538">Info Field 2: Pointer to data</span></span>
- <span data-ttu-id="e608e-1539">Pole informacji 3: rozmiar danych</span><span class="sxs-lookup"><span data-stu-id="e608e-1539">Info Field 3: Size of data</span></span>
- <span data-ttu-id="e608e-1540">Pole informacji 4: wskaźnik do puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1540">Info Field 4: Pointer to packet pool</span></span>

### <a name="packet-data-extract-offset"></a><span data-ttu-id="e608e-1541">Przesunięcie wyodrębniania danych pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1541">Packet Data Extract Offset</span></span> 

#### <a name="nx_udp_source_extract_offset"></a><span data-ttu-id="e608e-1542">nx_udp_source_extract_offset</span><span class="sxs-lookup"><span data-stu-id="e608e-1542">nx_udp_source_extract_offset</span></span>

<span data-ttu-id="e608e-1543">**Ikona** ![ Ikona przesunięcia wyodrębniania danych pakietu](./media/user-guide/netx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1543">**Icon** ![Packet data extract offset icon](./media/user-guide/netx-events/image111.png)</span></span>

<span data-ttu-id="e608e-1544">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1544">**Description**</span></span>

<span data-ttu-id="e608e-1545">To zdarzenie reprezentuje dane pakietu, które są wyodrębniane do podanego buforu z pakietu za pośrednictwem nx_udp_source_extract_offset.</span><span class="sxs-lookup"><span data-stu-id="e608e-1545">This event represents packet data that is extracted into a supplied buffer from a packet via nx_udp_source_extract_offset.</span></span>

<span data-ttu-id="e608e-1546">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1546">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1547">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1547">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="e608e-1548">Pole informacji 2: rozmiar określonego buforu</span><span class="sxs-lookup"><span data-stu-id="e608e-1548">Info Field 2: Size of specified buffer</span></span>
- <span data-ttu-id="e608e-1549">Pole informacji 3: liczba skopiowanych bajtów</span><span class="sxs-lookup"><span data-stu-id="e608e-1549">Info Field 3: Number of bytes copied</span></span>
- <span data-ttu-id="e608e-1550">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1550">Info Field 4: Not used</span></span>

### <a name="packet-data-retrieve"></a><span data-ttu-id="e608e-1551">Pobieranie danych pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1551">Packet Data Retrieve</span></span> 

#### <a name="nx_packet_data_retrieve"></a><span data-ttu-id="e608e-1552">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="e608e-1552">nx_packet_data_retrieve</span></span>

<span data-ttu-id="e608e-1553">**Ikona** ![ Ikona pobierania danych pakietu](./media/user-guide/netx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1553">**Icon** ![Packet data retrieve icon](./media/user-guide/netx-events/image112.png)</span></span>

<span data-ttu-id="e608e-1554">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1554">**Description**</span></span>

<span data-ttu-id="e608e-1555">To zdarzenie reprezentuje pobieranie danych z pakietu za pośrednictwem nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="e608e-1555">This event represents retrieving data from a packet via nx_packet_data_retrieve.</span></span>

<span data-ttu-id="e608e-1556">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1556">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1557">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1557">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="e608e-1558">Pole informacji 2: wskaźnik do początku buforu</span><span class="sxs-lookup"><span data-stu-id="e608e-1558">Info Field 2: Pointer to start of buffer</span></span>
- <span data-ttu-id="e608e-1559">Pole informacji 3: liczba skopiowanych bajtów</span><span class="sxs-lookup"><span data-stu-id="e608e-1559">Info Field 3: Bytes copied</span></span>
- <span data-ttu-id="e608e-1560">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1560">Info Field 4: Not used</span></span>

### <a name="packet-length-get"></a><span data-ttu-id="e608e-1561">Pobieranie długości pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1561">Packet Length Get</span></span> 

#### <a name="nx_packet_length_get"></a><span data-ttu-id="e608e-1562">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1562">nx_packet_length_get</span></span>

<span data-ttu-id="e608e-1563">**Ikona** ![ Ikona pobierania długości pakietu](./media/user-guide/netx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1563">**Icon** ![Packet length get icon](./media/user-guide/netx-events/image113.png)</span></span>

<span data-ttu-id="e608e-1564">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1564">**Description**</span></span>

<span data-ttu-id="e608e-1565">To zdarzenie reprezentuje długość pakietu za pośrednictwem nx_packet_length_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1565">This event represents getting the length of a packet via nx_packet_length_get.</span></span>

<span data-ttu-id="e608e-1566">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1566">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1567">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1567">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="e608e-1568">Pole informacji 2: długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1568">Info Field 2: Packet length</span></span>
- <span data-ttu-id="e608e-1569">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1569">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1570">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1570">Info Field 4: Not used</span></span>

### <a name="packet-pool-create"></a><span data-ttu-id="e608e-1571">Tworzenie puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1571">Packet Pool Create</span></span> 

#### <a name="nx_packet_pool_create"></a><span data-ttu-id="e608e-1572">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="e608e-1572">nx_packet_pool_create</span></span>

<span data-ttu-id="e608e-1573">**Ikona** ![ Ikona tworzenia puli pakietów](./media/user-guide/netx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1573">**Icon** ![Packet pool create icon](./media/user-guide/netx-events/image114.png)</span></span>

<span data-ttu-id="e608e-1574">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1574">**Description**</span></span>

<span data-ttu-id="e608e-1575">To zdarzenie reprezentuje Tworzenie puli pakietów za pośrednictwem nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="e608e-1575">This event represents creating a packet pool via nx_packet_pool_create.</span></span>

<span data-ttu-id="e608e-1576">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1576">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1577">Pole informacji 1: wskaźnik do puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1577">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="e608e-1578">Pole informacji 2: rozmiar ładunku pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1578">Info Field 2: Packet payload size</span></span>
- <span data-ttu-id="e608e-1579">Pole informacji 3: wskaźnik do obszaru pamięci puli</span><span class="sxs-lookup"><span data-stu-id="e608e-1579">Info Field 3: Pointer to pool memory area</span></span>
- <span data-ttu-id="e608e-1580">Pole informacji 4: rozmiar obszaru pamięci puli</span><span class="sxs-lookup"><span data-stu-id="e608e-1580">Info Field 4: Size of pool memory area</span></span>

### <a name="packet-pool-delete"></a><span data-ttu-id="e608e-1581">Usuwanie puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1581">Packet Pool Delete</span></span> 

#### <a name="nx_packet_pool_delete"></a><span data-ttu-id="e608e-1582">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-1582">nx_packet_pool_delete</span></span>

<span data-ttu-id="e608e-1583">**Ikona** ![ Ikona usuwania puli pakietów](./media/user-guide/netx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1583">**Icon** ![Packet pool delete icon](./media/user-guide/netx-events/image115.png)</span></span>

<span data-ttu-id="e608e-1584">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1584">**Description**</span></span>

<span data-ttu-id="e608e-1585">To zdarzenie reprezentuje Usuwanie puli pakietów za pośrednictwem nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-1585">This event represents deleting a packet pool via nx_packet_pool_delete.</span></span>

<span data-ttu-id="e608e-1586">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1586">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1587">Pole informacji 1: wskaźnik do puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1587">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="e608e-1588">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1588">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1589">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1589">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1590">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1590">Info Field 4: Not used</span></span>

#### <a name="packet-pool-information-get"></a><span data-ttu-id="e608e-1591">Pobieranie informacji o puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1591">Packet Pool Information Get</span></span> 

#### <a name="nx_packet_pool_info_get"></a><span data-ttu-id="e608e-1592">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1592">nx_packet_pool_info_get</span></span>

<span data-ttu-id="e608e-1593">**Ikona** ![ Ikona pobierania informacji o puli pakietów](./media/user-guide/netx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1593">**Icon** ![Packet pool information get icon](./media/user-guide/netx-events/image116.png)</span></span>

<span data-ttu-id="e608e-1594">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1594">**Description**</span></span>

<span data-ttu-id="e608e-1595">To zdarzenie reprezentuje informacje o puli pakietów za pośrednictwem nx_packet_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1595">This event represents getting packet pool information via nx_packet_pool_info_get.</span></span>

<span data-ttu-id="e608e-1596">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1596">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1597">Pole informacji 1: wskaźnik do puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1597">Info Field 1: Pointer to packet pool</span></span>
- <span data-ttu-id="e608e-1598">Pole informacji 2: całkowita liczba pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1598">Info Field 2: Total packets</span></span>
- <span data-ttu-id="e608e-1599">Pole informacji 3: dostępne pakiety</span><span class="sxs-lookup"><span data-stu-id="e608e-1599">Info Field 3: Available packets</span></span>
- <span data-ttu-id="e608e-1600">Pole informacji 4: puste żądania</span><span class="sxs-lookup"><span data-stu-id="e608e-1600">Info Field 4: Empty requests</span></span>

### <a name="packet-release"></a><span data-ttu-id="e608e-1601">Wydanie pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1601">Packet Release</span></span> 

#### <a name="nx_packet_data_release"></a><span data-ttu-id="e608e-1602">nx_packet_data_release</span><span class="sxs-lookup"><span data-stu-id="e608e-1602">nx_packet_data_release</span></span>

<span data-ttu-id="e608e-1603">**Ikona** ![ Ikona wydania pakietu](./media/user-guide/netx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1603">**Icon** ![Packet release icon](./media/user-guide/netx-events/image117.png)</span></span>

<span data-ttu-id="e608e-1604">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1604">**Description**</span></span>

<span data-ttu-id="e608e-1605">To zdarzenie reprezentuje wydanie pakietu za pośrednictwem nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="e608e-1605">This event represents releasing a packet via nx_packet_release.</span></span>

<span data-ttu-id="e608e-1606">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1606">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1607">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1607">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="e608e-1608">Pole informacji 2: stan pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1608">Info Field 2: Packet status</span></span>
- <span data-ttu-id="e608e-1609">Pole informacji 3: dostępne pakiety</span><span class="sxs-lookup"><span data-stu-id="e608e-1609">Info Field 3: Available packets</span></span>
- <span data-ttu-id="e608e-1610">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1610">Info Field 4: Not used</span></span>

### <a name="packet-transmit-release"></a><span data-ttu-id="e608e-1611">Wydanie transmisji pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1611">Packet Transmit Release</span></span> 

#### <a name="nx_packet_transmit_release"></a><span data-ttu-id="e608e-1612">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="e608e-1612">nx_packet_transmit_release</span></span>

<span data-ttu-id="e608e-1613">**Ikona** ![ Ikona wydania transmisji pakietu](./media/user-guide/netx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1613">**Icon** ![Packet transmit release icon](./media/user-guide/netx-events/image118.png)</span></span>

<span data-ttu-id="e608e-1614">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1614">**Description**</span></span>

<span data-ttu-id="e608e-1615">To zdarzenie reprezentuje zwalnianie pakietu nadawczego za pośrednictwem nx_packet_transmit_release.</span><span class="sxs-lookup"><span data-stu-id="e608e-1615">This event represents releasing a transmit packet via nx_packet_transmit_release.</span></span>

<span data-ttu-id="e608e-1616">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1616">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1617">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1617">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="e608e-1618">Pole informacji 2: stan pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1618">Info Field 2: Packet status</span></span>
- <span data-ttu-id="e608e-1619">Pole informacji 3: dostępne pakiety</span><span class="sxs-lookup"><span data-stu-id="e608e-1619">Info Field 3: Available packets</span></span>
- <span data-ttu-id="e608e-1620">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1620">Info Field 4: Not used</span></span>

### <a name="rarp-disable"></a><span data-ttu-id="e608e-1621">RARP wyłączyć</span><span class="sxs-lookup"><span data-stu-id="e608e-1621">RARP Disable</span></span> 

#### <a name="nx_rarp_disable"></a><span data-ttu-id="e608e-1622">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="e608e-1622">nx_rarp_disable</span></span>

<span data-ttu-id="e608e-1623">**Ikona** ![ Ikona wyłączenia r P](./media/user-guide/netx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1623">**Icon** ![R A R P disable icon](./media/user-guide/netx-events/image119.png)</span></span>

<span data-ttu-id="e608e-1624">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1624">**Description**</span></span>

<span data-ttu-id="e608e-1625">To zdarzenie przedstawia wyłączenie RARP za pośrednictwem nx_rarp_disable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1625">This event represents disabling RARP via nx_rarp_disable.</span></span>

<span data-ttu-id="e608e-1626">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1626">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1627">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1627">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1628">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1628">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1629">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1629">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1630">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1630">Info Field 4: Not used</span></span>

### <a name="rarp-enable"></a><span data-ttu-id="e608e-1631">Włącz RARP</span><span class="sxs-lookup"><span data-stu-id="e608e-1631">RARP Enable</span></span> 

#### <a name="nx_rarp_enable"></a><span data-ttu-id="e608e-1632">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1632">nx_rarp_enable</span></span>

<span data-ttu-id="e608e-1633">**Ikona** ![ Ikona włączenia języka r P](./media/user-guide/netx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1633">**Icon** ![R A R P enable icon](./media/user-guide/netx-events/image120.png)</span></span>

<span data-ttu-id="e608e-1634">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1634">**Description**</span></span>

<span data-ttu-id="e608e-1635">To zdarzenie reprezentuje włączenie RARP za pośrednictwem nx_rarp_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1635">This event represents enabling RARP via nx_rarp_enable.</span></span>

<span data-ttu-id="e608e-1636">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1636">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1637">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1637">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1638">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1638">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1639">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1639">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1640">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1640">Info Field 4: Not used</span></span>

### <a name="rarp-information-get"></a><span data-ttu-id="e608e-1641">RARP informacje</span><span class="sxs-lookup"><span data-stu-id="e608e-1641">RARP Information Get</span></span> 

#### <a name="nx_rarp_info_get"></a><span data-ttu-id="e608e-1642">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1642">nx_rarp_info_get</span></span>

<span data-ttu-id="e608e-1643">**Ikona** ![ Ikona uzyskiwania informacji o języku r P](./media/user-guide/netx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1643">**Icon** ![R A R P information get icon](./media/user-guide/netx-events/image121.png)</span></span>

<span data-ttu-id="e608e-1644">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1644">**Description**</span></span>

<span data-ttu-id="e608e-1645">To zdarzenie reprezentuje informacje o pobieraniu RARP za pośrednictwem nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1645">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="e608e-1646">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1646">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1647">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1647">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1648">Pole informacji 2: wysłane żądania</span><span class="sxs-lookup"><span data-stu-id="e608e-1648">Info Field 2: Requests sent</span></span>
- <span data-ttu-id="e608e-1649">Pole informacji 3: odebrane odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="e608e-1649">Info Field 3: Responses received</span></span>
- <span data-ttu-id="e608e-1650">Pole informacji 4: nieprawidłowe odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="e608e-1650">Info Field 4: Invalid responses</span></span>

### <a name="system-initialize"></a><span data-ttu-id="e608e-1651">Inicjowanie systemu</span><span class="sxs-lookup"><span data-stu-id="e608e-1651">System Initialize</span></span> 

#### <a name="nx_system_initialize"></a><span data-ttu-id="e608e-1652">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="e608e-1652">nx_system_initialize</span></span>

<span data-ttu-id="e608e-1653">**Ikona** ![ Ikona inicjowania systemu](./media/user-guide/netx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1653">**Icon** ![System initialize icon](./media/user-guide/netx-events/image122.png)</span></span>

<span data-ttu-id="e608e-1654">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1654">**Description**</span></span>

<span data-ttu-id="e608e-1655">To zdarzenie reprezentuje inicjalizację NetX za pośrednictwem nx_system_initialize.</span><span class="sxs-lookup"><span data-stu-id="e608e-1655">This event represents initializing NetX via nx_system_initialize.</span></span>

<span data-ttu-id="e608e-1656">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1656">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1657">Pole informacji 1: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1657">Info Field 1: Not used</span></span>
- <span data-ttu-id="e608e-1658">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1658">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1659">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1659">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1660">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1660">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-bind"></a><span data-ttu-id="e608e-1661">Powiązanie gniazda klienta TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1661">TCP Client Socket Bind</span></span> 

#### <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="e608e-1662">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="e608e-1662">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="e608e-1663">**Ikona** ![ Ikona powiązania gniazda klienta T P](./media/user-guide/netx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1663">**Icon** ![T  P client socket bind icon](./media/user-guide/netx-events/image123.png)</span></span>

<span data-ttu-id="e608e-1664">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1664">**Description**</span></span>

<span data-ttu-id="e608e-1665">To zdarzenie reprezentuje powiązanie gniazda klienta z portem za pośrednictwem nx_tcp_client_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="e608e-1665">This event represents binding a client socket to a port via nx_tcp_client_socket_bind.</span></span>

<span data-ttu-id="e608e-1666">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1666">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1667">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1667">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1668">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1668">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1669">Pole informacji 3: żądany port</span><span class="sxs-lookup"><span data-stu-id="e608e-1669">Info Field 3: Port requested</span></span>
- <span data-ttu-id="e608e-1670">Pole informacji 4: opcja oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1670">Info Field 4: Wait option</span></span>

### <a name="tcp-client-socket-connect"></a><span data-ttu-id="e608e-1671">Połączenie gniazda klienta TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1671">TCP Client Socket Connect</span></span> 

#### <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="e608e-1672">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="e608e-1672">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="e608e-1673">**Ikona** ![ Ikona połączenia z gniazdem klienta T C P](./media/user-guide/netx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1673">**Icon** ![T C P client socket connect icon](./media/user-guide/netx-events/image124.png)</span></span>

<span data-ttu-id="e608e-1674">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1674">**Description**</span></span>

<span data-ttu-id="e608e-1675">To zdarzenie reprezentuje połączenie gniazda klienta za pośrednictwem nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="e608e-1675">This event represents making a client socket connection via nx_tcp_client_socket_connect.</span></span>

<span data-ttu-id="e608e-1676">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1676">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1677">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1677">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1678">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1678">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1679">Pole informacji 3: adres IP serwera</span><span class="sxs-lookup"><span data-stu-id="e608e-1679">Info Field 3: Server IP address</span></span>
- <span data-ttu-id="e608e-1680">Pole informacji 4: żądany port serwera</span><span class="sxs-lookup"><span data-stu-id="e608e-1680">Info Field 4: Server port requested</span></span>

### <a name="tcp-client-socket-port-get"></a><span data-ttu-id="e608e-1681">Pobieranie portu gniazda klienta TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1681">TCP Client Socket Port Get</span></span> 

#### <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="e608e-1682">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1682">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="e608e-1683">**Ikona** ![ Ikona pobierania portu gniazda klienta T C P](./media/user-guide/netx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1683">**Icon** ![T C P client socket port get icon](./media/user-guide/netx-events/image125.png)</span></span>

<span data-ttu-id="e608e-1684">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1684">**Description**</span></span>

<span data-ttu-id="e608e-1685">To zdarzenie reprezentuje numer portu gniazda klienta za pośrednictwem nx_tcp_client_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1685">This event represents getting the client socket port number via nx_tcp_client_socket_port_get.</span></span>

<span data-ttu-id="e608e-1686">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1686">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1687">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1687">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1688">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1688">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1689">Pole informacji 3: numer portu</span><span class="sxs-lookup"><span data-stu-id="e608e-1689">Info Field 3: Port number</span></span>
- <span data-ttu-id="e608e-1690">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1690">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-unbind"></a><span data-ttu-id="e608e-1691">Niepowiązanie gniazda klienta TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1691">TCP Client Socket Unbind</span></span> 

#### <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="e608e-1692">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="e608e-1692">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="e608e-1693">**Ikona** ![ Ikona usuwania powiązania gniazda klienta T C P](./media/user-guide/netx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1693">**Icon** ![T C P client socket unbind icon](./media/user-guide/netx-events/image126.png)</span></span>

<span data-ttu-id="e608e-1694">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1694">**Description**</span></span>

<span data-ttu-id="e608e-1695">To zdarzenie reprezentuje powiązanie portu skojarzonego z gniazdem za pośrednictwem nx_tcp_client_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="e608e-1695">This event represents unbinding the port associated with the socket via nx_tcp_client_socket_unbind.</span></span>

<span data-ttu-id="e608e-1696">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1696">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1697">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1697">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1698">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1698">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1699">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1699">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1700">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1700">Info Field 4: Not used</span></span>

### <a name="tcp-enable"></a><span data-ttu-id="e608e-1701">Włączanie protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1701">TCP Enable</span></span> 

#### <a name="nx_tcp_enable"></a><span data-ttu-id="e608e-1702">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1702">nx_tcp_enable</span></span>

<span data-ttu-id="e608e-1703">**Ikona** ![ Ikona włączenia P C](./media/user-guide/netx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1703">**Icon** ![T C P enable icon](./media/user-guide/netx-events/image127.png)</span></span>

<span data-ttu-id="e608e-1704">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1704">**Description**</span></span>

<span data-ttu-id="e608e-1705">To zdarzenie reprezentuje włączenie protokołu TCP za pośrednictwem nx_tcp_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1705">This event represents enabling TCP via nx_tcp_enable.</span></span>

<span data-ttu-id="e608e-1706">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1706">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1707">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1707">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1708">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1708">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1709">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1709">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1710">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1710">Info Field 4: Not used</span></span>

###  <a name="tcp-free-port-find-tcp-free-port-find"></a><span data-ttu-id="e608e-1711">Bezpłatny port TCP Znajdź bezpłatny port TCP Znajdź</span><span class="sxs-lookup"><span data-stu-id="e608e-1711">TCP Free Port Find TCP Free Port Find</span></span> 

#### <a name="nx_tcp_free_port_find"></a><span data-ttu-id="e608e-1712">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="e608e-1712">nx_tcp_free_port_find</span></span>

<span data-ttu-id="e608e-1713">**Ikona** ![ Ikona wyszukiwania bezpłatny port T CP](./media/user-guide/netx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1713">**Icon** ![T  CP free port find icon](./media/user-guide/netx-events/image128.png)</span></span>

<span data-ttu-id="e608e-1714">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1714">**Description**</span></span>

<span data-ttu-id="e608e-1715">To zdarzenie reprezentuje bezpłatny port TCP za pośrednictwem nx_tcp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="e608e-1715">This event represents finding a free TCP port via nx_tcp_free_port_find.</span></span>

<span data-ttu-id="e608e-1716">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1716">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1717">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1717">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1718">Pole informacji 2: uruchamianie numeru portu wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1718">Info Field 2: Starting search port number</span></span>
- <span data-ttu-id="e608e-1719">Pole informacji 3: numer wolnego portu</span><span class="sxs-lookup"><span data-stu-id="e608e-1719">Info Field 3: Free port number</span></span>
- <span data-ttu-id="e608e-1720">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1720">Info Field 4: Not used</span></span>

###  <a name="tcp-infomation-get"></a><span data-ttu-id="e608e-1721">Pobieranie informacji TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1721">TCP Infomation Get</span></span> 

#### <a name="nx_tcp_info_get"></a><span data-ttu-id="e608e-1722">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1722">nx_tcp_info_get</span></span>

<span data-ttu-id="e608e-1723">**Ikona** ![ Ikona pobierania informacji T C P](./media/user-guide/netx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1723">**Icon** ![T C P infomation get icon](./media/user-guide/netx-events/image129.png)</span></span>

<span data-ttu-id="e608e-1724">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1724">**Description**</span></span>

<span data-ttu-id="e608e-1725">To zdarzenie reprezentuje pobieranie informacji TCP dla określonego wystąpienia IP za pośrednictwem nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1725">This event represents retrieving TCP information for the specified IP instance via nx_tcp_info_get.</span></span>

<span data-ttu-id="e608e-1726">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1726">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1727">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1727">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1728">Pole informacji 2: liczba wysłanych bajtów</span><span class="sxs-lookup"><span data-stu-id="e608e-1728">Info Field 2: Number of bytes sent</span></span>
- <span data-ttu-id="e608e-1729">Pole informacji 3: liczba odebranych bajtów</span><span class="sxs-lookup"><span data-stu-id="e608e-1729">Info Field 3: Number of bytes received</span></span>
- <span data-ttu-id="e608e-1730">Pole informacji 4: Liczba nieprawidłowych pakietów</span><span class="sxs-lookup"><span data-stu-id="e608e-1730">Info Field 4: Number of invalid packets</span></span>

###  <a name="tcp-server-socket-accept"></a><span data-ttu-id="e608e-1731">Akceptowanie gniazda serwera TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1731">TCP Server Socket Accept</span></span> 

#### <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="e608e-1732">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="e608e-1732">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="e608e-1733">**Ikona** ![ Ikona akceptowania gniazda serwera T C P](./media/user-guide/netx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1733">**Icon** ![T C P server socket accept icon](./media/user-guide/netx-events/image130.png)</span></span>

<span data-ttu-id="e608e-1734">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1734">**Description**</span></span>

<span data-ttu-id="e608e-1735">To zdarzenie reprezentuje skonfigurowanie gniazda serwera po odebraniu żądania połączenia aktywnego za pośrednictwem nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="e608e-1735">This event represents setting up the server socket after an active connection request was received via nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="e608e-1736">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1736">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1737">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1737">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1738">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1738">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1739">Pole informacji 3: opcja oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1739">Info Field 3: Wait option</span></span>
- <span data-ttu-id="e608e-1740">Pole informacji 4: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1740">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-listen"></a><span data-ttu-id="e608e-1741">Nasłuchiwanie gniazda serwera TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1741">TCP Server Socket Listen</span></span> 

#### <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="e608e-1742">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="e608e-1742">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="e608e-1743">**Ikona** ![ Ikona lsten T C P Server Socket](./media/user-guide/netx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1743">**Icon** ![T C P server socket lsten icon](./media/user-guide/netx-events/image131.png)</span></span>

<span data-ttu-id="e608e-1744">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1744">**Description**</span></span>

<span data-ttu-id="e608e-1745">To zdarzenie przedstawia rejestrowanie żądania Listen i gniazda serwera dla określonego portu TCP za pośrednictwem nx_tcp_server_socket_listen.</span><span class="sxs-lookup"><span data-stu-id="e608e-1745">This event represents register a listen request and a server socket for the specified TCP port via nx_tcp_server_socket_listen.</span></span>

<span data-ttu-id="e608e-1746">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1746">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1747">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1747">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1748">Pole informacji 2: numer portu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1748">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="e608e-1749">Pole informacji 3: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1749">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1750">Pole informacji 4: Maksymalna liczba połączeń, które można umieścić w kolejce</span><span class="sxs-lookup"><span data-stu-id="e608e-1750">Info Field 4: Maximum number of connections that can be queued</span></span>

###  <a name="tcp-server-socket-relisten"></a><span data-ttu-id="e608e-1751">Gniazdo serwera TCP, nasłuchiwanie</span><span class="sxs-lookup"><span data-stu-id="e608e-1751">TCP Server Socket Relisten</span></span> 

#### <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="e608e-1752">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="e608e-1752">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="e608e-1753">**Ikona** ![ Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1753">**Icon** ![T C P server socket relisten icon](./media/user-guide/netx-events/image132.png)</span></span>

<span data-ttu-id="e608e-1754">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1754">**Description**</span></span>

<span data-ttu-id="e608e-1755">To zdarzenie reprezentuje inne gniazdo serwera dla istniejącego żądania nasłuchiwania na określonym porcie TCP za pośrednictwem nx_tcp_server_socket_relisten.</span><span class="sxs-lookup"><span data-stu-id="e608e-1755">This event represents register another server socket for an existing listen request on the specified TCP port via nx_tcp_server_socket_relisten.</span></span>

<span data-ttu-id="e608e-1756">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1756">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1757">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1757">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1758">Pole informacji 2: numer portu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1758">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="e608e-1759">Pole informacji 3: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1759">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1760">Pole informacji 4: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1760">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-unaccept"></a><span data-ttu-id="e608e-1761">Nieakceptowanie gniazda serwera TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1761">TCP Server Socket Unaccept</span></span> 

#### <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="e608e-1762">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="e608e-1762">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="e608e-1763">**Ikona** ![ Ikona nieakceptowania gniazda serwera T C P](./media/user-guide/netx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1763">**Icon** ![T C P server socket unaccept icon](./media/user-guide/netx-events/image133.png)</span></span>

<span data-ttu-id="e608e-1764">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1764">**Description**</span></span>

<span data-ttu-id="e608e-1765">To zdarzenie reprezentuje usunięcie gniazda serwera ze skojarzenia z portem, który uzyskuje wcześniejsze połączenie pasywne za pośrednictwem nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="e608e-1765">This event represents removing the server socket from association with the port receiving an earlier passive connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="e608e-1766">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1766">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1767">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1767">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1768">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1768">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1769">Pole informacji 3: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1769">Info Field 3: Socket state</span></span>
- <span data-ttu-id="e608e-1770">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1770">Info Field 4: Not used</span></span>

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a><span data-ttu-id="e608e-1771">Niesłuchane gniazdo serwera TCP gniazda serwera TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1771">TCP Server Socket Unlisten TCP Server Socket Unlisten</span></span> 

#### <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="e608e-1772">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="e608e-1772">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="e608e-1773">**Ikona** ![ Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1773">**Icon** ![T C P server socket unlisten icon](./media/user-guide/netx-events/image134.png)</span></span>

<span data-ttu-id="e608e-1774">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1774">**Description**</span></span>

<span data-ttu-id="e608e-1775">To zdarzenie reprezentuje usunięcie poprzedniego żądania nasłuchiwania dla określonego portu TCP za pośrednictwem nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="e608e-1775">This event represents removing a previous listen request for the specified TCP port via nx_tcp_server_socket_unlisten.</span></span>

<span data-ttu-id="e608e-1776">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1776">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1777">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1777">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1778">Pole informacji 2: numer portu TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1778">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="e608e-1779">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1779">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1780">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1780">Info Field 4: Not used</span></span>

### <a name="tcp-socket-bytes-available"></a><span data-ttu-id="e608e-1781">Dostępne bajty gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1781">TCP Socket Bytes Available</span></span> 

#### <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="e608e-1782">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="e608e-1782">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="e608e-1783">**Ikona** ![ Ikona dostępnych bajtów gniazda T C](./media/user-guide/netx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1783">**Icon** ![T C P socket bytes available icon](./media/user-guide/netx-events/image135.png)</span></span>

<span data-ttu-id="e608e-1784">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1784">**Description**</span></span>

<span data-ttu-id="e608e-1785">To zdarzenie reprezentuje liczbę aktualnie dostępnych bajtów w określonym gnieździe odbioru TCP za pośrednictwem nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="e608e-1785">This event represents the number of bytes currently available on the specified TCP receiving socket via nx_tcp_socket_bytes_available.</span></span>

<span data-ttu-id="e608e-1786">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1786">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1787">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1787">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1788">Pole informacji 2: wskaźnik do gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1788">Info Field 2: Pointer to TCP socket</span></span>
- <span data-ttu-id="e608e-1789">Pole informacji 3: bajty odebrane w gnieździe</span><span class="sxs-lookup"><span data-stu-id="e608e-1789">Info Field 3: Bytes received on the socket</span></span>
- <span data-ttu-id="e608e-1790">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1790">Info Field 4: Not used</span></span>

### <a name="tcp-socket-create"></a><span data-ttu-id="e608e-1791">Tworzenie gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1791">TCP Socket Create</span></span> 

#### <a name="nx_tcp_socket_create"></a><span data-ttu-id="e608e-1792">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="e608e-1792">nx_tcp_socket_create</span></span>

<span data-ttu-id="e608e-1793">**Ikona** ![ Ikona tworzenia gniazda T C P](./media/user-guide/netx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1793">**Icon** ![T C P socket create icon](./media/user-guide/netx-events/image136.png)</span></span>

<span data-ttu-id="e608e-1794">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1794">**Description**</span></span>

<span data-ttu-id="e608e-1795">To zdarzenie reprezentuje tworzenie gniazda TCP za pośrednictwem nx_tcp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="e608e-1795">This event represents creating a TCP socket via nx_tcp_socket_create.</span></span>

<span data-ttu-id="e608e-1796">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1796">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1797">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1797">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1798">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1798">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1799">Pole informacji 3: typ usługi</span><span class="sxs-lookup"><span data-stu-id="e608e-1799">Info Field 3: Type of service</span></span>
- <span data-ttu-id="e608e-1800">Pole informacji 4: rozmiar okna odbierania</span><span class="sxs-lookup"><span data-stu-id="e608e-1800">Info Field 4: Receive window size</span></span>

### <a name="tcp-socket-delete"></a><span data-ttu-id="e608e-1801">Usuwanie gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1801">TCP Socket Delete</span></span> 

#### <a name="nx_tcp_socket_delete"></a><span data-ttu-id="e608e-1802">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-1802">nx_tcp_socket_delete</span></span>

<span data-ttu-id="e608e-1803">**Ikona** ![ Ikona usuwania gniazda T C P](./media/user-guide/netx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1803">**Icon** ![T C P socket delete icon](./media/user-guide/netx-events/image137.png)</span></span>

<span data-ttu-id="e608e-1804">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1804">**Description**</span></span>

<span data-ttu-id="e608e-1805">To zdarzenie reprezentuje usunięcie gniazda za pośrednictwem nx_tcp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-1805">This event represents deleting a socket via nx_tcp_socket_delete.</span></span>

<span data-ttu-id="e608e-1806">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1806">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1807">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1807">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1808">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1808">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1809">Pole informacji 3: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1809">Info Field 3: Socket state</span></span>
- <span data-ttu-id="e608e-1810">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1810">Info Field 4: Not used</span></span>

### <a name="tcp-socket-disconnect"></a><span data-ttu-id="e608e-1811">Połączenie gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1811">TCP Socket Disconnect</span></span> 

#### <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="e608e-1812">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="e608e-1812">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="e608e-1813">**Ikona** ![ Ikona rozłączenia gniazda T C P](./media/user-guide/netx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1813">**Icon** ![T C P socket disconnect icon](./media/user-guide/netx-events/image138.png)</span></span>

<span data-ttu-id="e608e-1814">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1814">**Description**</span></span>

<span data-ttu-id="e608e-1815">To zdarzenie reprezentuje odłączenie gniazda za pośrednictwem nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="e608e-1815">This event represents disconnecting a socket via nx_tcp_socket_disconnect.</span></span>

<span data-ttu-id="e608e-1816">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1816">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1817">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1817">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1818">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1818">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1819">Pole informacji 3: opcja oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1819">Info Field 3: Wait option</span></span>
- <span data-ttu-id="e608e-1820">Pole informacji 4: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1820">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-information-get"></a><span data-ttu-id="e608e-1821">Pobieranie informacji o gnieździe TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1821">TCP Socket Information Get</span></span> 

#### <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="e608e-1822">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1822">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="e608e-1823">**Ikona** ![ Ikona uzyskiwania informacji o gnieździe T C P](./media/user-guide/netx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1823">**Icon** ![T C P socket information get icon](./media/user-guide/netx-events/image139.png)</span></span>

<span data-ttu-id="e608e-1824">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1824">**Description**</span></span>

<span data-ttu-id="e608e-1825">To zdarzenie reprezentuje informacje o gnieździe za pośrednictwem nx_tcp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1825">This event represents getting information about a socket via nx_tcp_socket_info_get.</span></span>

<span data-ttu-id="e608e-1826">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1826">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1827">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1827">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1828">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1828">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1829">Pole informacji 3: Bajty wysłane przez to gniazdo</span><span class="sxs-lookup"><span data-stu-id="e608e-1829">Info Field 3: Bytes sent through this socket</span></span>
- <span data-ttu-id="e608e-1830">Pole informacji 4: bajty odebrane przez to gniazdo</span><span class="sxs-lookup"><span data-stu-id="e608e-1830">Info Field 4: Bytes received through this socket</span></span>

### <a name="tcp-socket-mss-get"></a><span data-ttu-id="e608e-1831">Pobieranie z gniazda TCP Socket</span><span class="sxs-lookup"><span data-stu-id="e608e-1831">TCP Socket MSS Get</span></span> 

#### <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="e608e-1832">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1832">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="e608e-1833">**Ikona** ![ T C P gniazdo M S S Uzyskaj ikonę](./media/user-guide/netx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1833">**Icon** ![T C P socket M S S get icon](./media/user-guide/netx-events/image140.png)</span></span>

<span data-ttu-id="e608e-1834">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1834">**Description**</span></span>

<span data-ttu-id="e608e-1835">To zdarzenie reprezentuje pobieranie danych o przełączeniu gniazda za pośrednictwem nx_tcp_socket_mss_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1835">This event represents getting the socket's MSS via nx_tcp_socket_mss_get.</span></span>

<span data-ttu-id="e608e-1836">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1836">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1837">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1837">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1838">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1838">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1839">Pole informacji 3: maksymalny rozmiar segmentu (Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e608e-1839">Info Field 3: Maximum Segment Size (MSS)</span></span>
- <span data-ttu-id="e608e-1840">Pole informacji 4: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1840">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-peer-get"></a><span data-ttu-id="e608e-1841">Pobieranie elementu równorzędnego w gnieździe TCP Socket</span><span class="sxs-lookup"><span data-stu-id="e608e-1841">TCP Socket MSS Peer Get</span></span> 

#### <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="e608e-1842">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1842">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="e608e-1843">**Ikona** ![ Ikona pobierania elementów równorzędnych T C P Socket M s](./media/user-guide/netx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1843">**Icon** ![T C P socket M S S peer get icon](./media/user-guide/netx-events/image141.png)</span></span>

<span data-ttu-id="e608e-1844">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1844">**Description**</span></span>

<span data-ttu-id="e608e-1845">To zdarzenie reprezentuje wartość parametru "/średnika" elementu równorzędnego gniazda za pośrednictwem nx_tcp_socket_mss_peer_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1845">This event represents getting the MSS value of the socket's peer via nx_tcp_socket_mss_peer_get.</span></span>

<span data-ttu-id="e608e-1846">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1846">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1847">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1847">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1848">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1848">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1849">Pole informacji 3: rozmiar elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1849">Info Field 3: Peer's MSS</span></span>
- <span data-ttu-id="e608e-1850">Pole informacji 4: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1850">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-set"></a><span data-ttu-id="e608e-1851">Zestaw o wartościach sieciowych TCP Socket</span><span class="sxs-lookup"><span data-stu-id="e608e-1851">TCP Socket MSS Set</span></span> 

#### <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="e608e-1852">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="e608e-1852">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="e608e-1853">**Ikona** ![ Ikona zestawu M S w gnieździe T C](./media/user-guide/netx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1853">**Icon** ![T C P socket M S S set icon](./media/user-guide/netx-events/image142.png)</span></span>

<span data-ttu-id="e608e-1854">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1854">**Description**</span></span>

<span data-ttu-id="e608e-1855">To zdarzenie reprezentuje ustawienie parametru o przełączeniu gniazda za pośrednictwem nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-1855">This event represents setting a socket's MSS via nx_tcp_socket_mss_set.</span></span>

<span data-ttu-id="e608e-1856">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1856">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1857">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1857">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1858">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1858">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1859">Pole informacji 3: profilowanie</span><span class="sxs-lookup"><span data-stu-id="e608e-1859">Info Field 3: MSS</span></span>
- <span data-ttu-id="e608e-1860">Pole informacji 4: stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1860">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-peer-info-get"></a><span data-ttu-id="e608e-1861">Pobieranie informacji o komunikacji równorzędnej gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1861">TCP Socket Peer Info Get</span></span> 

#### <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="e608e-1862">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1862">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="e608e-1863">**Ikona** ![ Ikona pobierania informacji o komunikacji równorzędnej gniazda T C](./media/user-guide/netx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1863">**Icon** ![T C P socket peer info get icon](./media/user-guide/netx-events/image143.png)</span></span>

<span data-ttu-id="e608e-1864">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1864">**Description**</span></span>

<span data-ttu-id="e608e-1865">To zdarzenie reprezentuje informacje pobrane z gniazda TCP dotyczące elementu równorzędnego (np. >łączenia hosta) i portu IP za pośrednictwem nx_tcp_socket_peer_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1865">This event represents information retrieved from the TCP socket regarding the peer (e.g. >connecting host) IP address and port via nx_tcp_socket_peer_info_get.</span></span>

<span data-ttu-id="e608e-1866">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1866">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1867">Pole informacji 1: wskaźnik do gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1867">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="e608e-1868">Pole informacji 2: adres IP elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1868">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="e608e-1869">Pole informacji 3: numer portu elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="e608e-1869">Info Field 3: Peer port number</span></span>
- <span data-ttu-id="e608e-1870">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1870">Info Field 4: Not used</span></span>

### <a name="tcp-socket-receive"></a><span data-ttu-id="e608e-1871">Odbieranie gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1871">TCP Socket Receive</span></span> 

#### <a name="nx_tcp_socket_receive"></a><span data-ttu-id="e608e-1872">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="e608e-1872">nx_tcp_socket_receive</span></span>

<span data-ttu-id="e608e-1873">**Ikona** ![ Ikona odbioru gniazda T C P](./media/user-guide/netx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1873">**Icon** ![T C P socket receive icon](./media/user-guide/netx-events/image144.png)</span></span>

<span data-ttu-id="e608e-1874">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1874">**Description**</span></span>

<span data-ttu-id="e608e-1875">To zdarzenie reprezentuje dane odebrane z gniazda za pośrednictwem nx_tcp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="e608e-1875">This event represents receiving data from a socket via nx_tcp_socket_receive.</span></span>

<span data-ttu-id="e608e-1876">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1876">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1877">Pole informacji 1: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1877">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1878">Pole informacji 2: wskaźnik do odebranego pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1878">Info Field 2: Pointer to received packet</span></span>
- <span data-ttu-id="e608e-1879">Pole informacji 3: Odebrano długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1879">Info Field 3: Received packet length</span></span>
- <span data-ttu-id="e608e-1880">Pole informacji 4: numer sekwencyjny odbioru</span><span class="sxs-lookup"><span data-stu-id="e608e-1880">Info Field 4: Receive sequence number</span></span>

### <a name="tcp-socket-receive-notify"></a><span data-ttu-id="e608e-1881">Powiadomienie o odebraniu gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1881">TCP Socket Receive Notify</span></span> 

#### <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="e608e-1882">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="e608e-1882">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="e608e-1883">**Ikona** ![ Ikona powiadomienia o odebraniu gniazda T C P](./media/user-guide/netx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1883">**Icon** ![T C P socket receive notify icon](./media/user-guide/netx-events/image145.png)</span></span>

<span data-ttu-id="e608e-1884">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1884">**Description**</span></span>

<span data-ttu-id="e608e-1885">To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego powiadomienia o odebraniu dla gniazda za pośrednictwem nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="e608e-1885">This event represents registering a receive notify callback for a socket via nx_tcp_socket_receive_notify.</span></span>

<span data-ttu-id="e608e-1886">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1886">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1887">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1887">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1888">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1888">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1889">Pole informacji 3: wskaźnik otrzymywania powiadomienia o wywołaniu zwrotnym pole 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1889">Info Field 3: Pointer to receive notify callback Info Field 4: Not used</span></span>

### <a name="tcp-socket-send"></a><span data-ttu-id="e608e-1890">Wysyłanie gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1890">TCP Socket Send</span></span> 

#### <a name="nx_tcp_socket_send"></a><span data-ttu-id="e608e-1891">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="e608e-1891">nx_tcp_socket_send</span></span>

<span data-ttu-id="e608e-1892">**Ikona** ![ Ikona wysyłania gniazda T C P](./media/user-guide/netx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1892">**Icon** ![T C P socket send icon](./media/user-guide/netx-events/image146.png)</span></span>

<span data-ttu-id="e608e-1893">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1893">**Description**</span></span>

<span data-ttu-id="e608e-1894">To zdarzenie reprezentuje wysyłanie danych w gnieździe za pośrednictwem nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="e608e-1894">This event represents sending data on a socket via nx_tcp_socket_send.</span></span>

<span data-ttu-id="e608e-1895">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1895">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1896">Pole informacji 1: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1896">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1897">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1897">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-1898">Pole informacji 3: długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-1898">Info Field 3: Length of packet</span></span>
- <span data-ttu-id="e608e-1899">Pole informacji 4: numer sekwencyjny transmisji</span><span class="sxs-lookup"><span data-stu-id="e608e-1899">Info Field 4: Transmit sequence number</span></span>

### <a name="tcp-socket-state-wait"></a><span data-ttu-id="e608e-1900">Oczekiwanie na stan gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1900">TCP Socket State Wait</span></span> 

#### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="e608e-1901">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="e608e-1901">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="e608e-1902">**Ikona** ![ Ikona oczekiwania stanu gniazda T C P](./media/user-guide/netx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1902">**Icon** ![T C P socket state wait icon](./media/user-guide/netx-events/image147.png)</span></span>

<span data-ttu-id="e608e-1903">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1903">**Description**</span></span>

<span data-ttu-id="e608e-1904">To zdarzenie reprezentuje oczekiwanie, aż gniazdo wprowadzi określony stan za pośrednictwem nx_tcp_socket_state_wait.</span><span class="sxs-lookup"><span data-stu-id="e608e-1904">This event represents waiting for a socket to enter a particular state via nx_tcp_socket_state_wait.</span></span>

<span data-ttu-id="e608e-1905">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1905">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1906">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1906">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1907">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1907">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1908">Pole informacji 3: żądany stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1908">Info Field 3: Desired socket state</span></span>
- <span data-ttu-id="e608e-1909">Pole informacji 4: poprzedni stan gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1909">Info Field 4: Previous socket state</span></span>

### <a name="tcp-socket-transmit-configure"></a><span data-ttu-id="e608e-1910">Konfigurowanie transmisji gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1910">TCP Socket Transmit Configure</span></span> 

#### <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="e608e-1911">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="e608e-1911">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="e608e-1912">**Ikona** ![ Ikona wysyłania gniazda sieciowego T C P](./media/user-guide/netx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1912">**Icon** ![T C P socket transmit configure icon](./media/user-guide/netx-events/image148.png)</span></span>

<span data-ttu-id="e608e-1913">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1913">**Description**</span></span>

<span data-ttu-id="e608e-1914">To zdarzenie reprezentuje konfigurację opcji przesyłania dla gniazda za pośrednictwem nx_tcp_socket_transmit_configure.</span><span class="sxs-lookup"><span data-stu-id="e608e-1914">This event represents configuring the transmit options for a socket via nx_tcp_socket_transmit_configure.</span></span>

<span data-ttu-id="e608e-1915">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1915">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1916">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1916">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1917">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1917">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1918">Pole informacji 3: przekazywanie głębokości kolejki</span><span class="sxs-lookup"><span data-stu-id="e608e-1918">Info Field 3: Transmit queue depth</span></span>
- <span data-ttu-id="e608e-1919">Pole informacji 4: wartość limitu czasu</span><span class="sxs-lookup"><span data-stu-id="e608e-1919">Info Field 4: Timeout value</span></span>

### <a name="tcp-socket-window-update-notify-set"></a><span data-ttu-id="e608e-1920">Zestaw powiadomień o aktualizacji okna gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1920">TCP Socket Window Update Notify Set</span></span> 

#### <a name="nx_tcp_window_update_notify_set"></a><span data-ttu-id="e608e-1921">nx_tcp_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="e608e-1921">nx_tcp_window_update_notify_set</span></span>

<span data-ttu-id="e608e-1922">**Ikona** ![ Ikona zestawu powiadomień o aktualizacji okna gniazda T C](./media/user-guide/netx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1922">**Icon** ![T C P socket window update notify set icon](./media/user-guide/netx-events/image149.png)</span></span>

<span data-ttu-id="e608e-1923">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1923">**Description**</span></span>

<span data-ttu-id="e608e-1924">To zdarzenie reprezentuje gniazdo TCP odbierające powiadomienie o zwiększeniu okna odbierania hosta zdalnego za pośrednictwem nx_tcp_window_update_notify_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-1924">This event represents a TCP socket receiving notification of an increase in the remote host receive window via nx_tcp_window_update_notify_set.</span></span>

<span data-ttu-id="e608e-1925">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1925">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1926">Pole informacji 1: wskaźnik do gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="e608e-1926">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="e608e-1927">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1927">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1928">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1928">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1929">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1929">Info Field 4: Not used</span></span>

### <a name="udp-enable"></a><span data-ttu-id="e608e-1930">Włączanie protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1930">UDP Enable</span></span> 

#### <a name="nx_udp_enable"></a><span data-ttu-id="e608e-1931">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1931">nx_udp_enable</span></span>

<span data-ttu-id="e608e-1932">**Ikona** ![ Ikona włączenia u D P](./media/user-guide/netx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1932">**Icon** ![U D P enable icon](./media/user-guide/netx-events/image150.png)</span></span>

<span data-ttu-id="e608e-1933">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1933">**Description**</span></span>

<span data-ttu-id="e608e-1934">To zdarzenie reprezentuje włączenie protokołu UDP za pośrednictwem nx_udp_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1934">This event represents enabling UDP via nx_udp_enable.</span></span>

<span data-ttu-id="e608e-1935">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1935">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1936">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1936">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1937">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1937">Info Field 2: Not used</span></span>
- <span data-ttu-id="e608e-1938">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1938">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1939">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1939">Info Field 4: Not used</span></span>

### <a name="udp-free-port-find"></a><span data-ttu-id="e608e-1940">Znajdowanie portów bezpłatnych UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1940">UDP Free Port Find</span></span> 

#### <a name="nx_udp_free_port_find"></a><span data-ttu-id="e608e-1941">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="e608e-1941">nx_udp_free_port_find</span></span>

<span data-ttu-id="e608e-1942">**Ikona** ![ Ikona Znajdź bezpłatny port U D P](./media/user-guide/netx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1942">**Icon** ![U D P free port find icon](./media/user-guide/netx-events/image151.png)</span></span>

<span data-ttu-id="e608e-1943">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1943">**Description**</span></span>

<span data-ttu-id="e608e-1944">To zdarzenie reprezentuje bezpłatny port UDP za pośrednictwem nx_udp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="e608e-1944">This event represents finding a free UDP port via nx_udp_free_port_find.</span></span>

<span data-ttu-id="e608e-1945">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1945">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1946">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1946">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1947">Pole informacji 2: uruchamianie portu w celu wyszukania</span><span class="sxs-lookup"><span data-stu-id="e608e-1947">Info Field 2: Starting port to search from</span></span>
- <span data-ttu-id="e608e-1948">Pole informacji 3: Port bezpłatny</span><span class="sxs-lookup"><span data-stu-id="e608e-1948">Info Field 3: Free port</span></span>
- <span data-ttu-id="e608e-1949">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1949">Info Field 4: Not used</span></span>

### <a name="udp-information-get"></a><span data-ttu-id="e608e-1950">Pobieranie informacji o UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1950">UDP Information Get</span></span> 

#### <a name="nx_udp_info_get"></a><span data-ttu-id="e608e-1951">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-1951">nx_udp_info_get</span></span>

<span data-ttu-id="e608e-1952">**Ikona** ![ Ikona pobierania informacji u D P](./media/user-guide/netx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1952">**Icon** ![U D P information get icon](./media/user-guide/netx-events/image152.png)</span></span>

<span data-ttu-id="e608e-1953">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1953">**Description**</span></span>

<span data-ttu-id="e608e-1954">To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-1954">This event represents getting information via nx_udp_info_get.</span></span>

<span data-ttu-id="e608e-1955">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1955">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1956">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1956">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1957">Pole informacji 2: Wysłane bajty UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1957">Info Field 2: UDP bytes sent</span></span>
- <span data-ttu-id="e608e-1958">Pole informacji 3: Odebrane bajty UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1958">Info Field 3: UDP bytes received</span></span>
- <span data-ttu-id="e608e-1959">Pole informacji 4: nieprawidłowe pakiety</span><span class="sxs-lookup"><span data-stu-id="e608e-1959">Info Field 4: Invalid packets</span></span>

### <a name="udp-socket-bind"></a><span data-ttu-id="e608e-1960">Powiązanie gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1960">UDP Socket Bind</span></span> 

#### <a name="nx_udp_socket_bind"></a><span data-ttu-id="e608e-1961">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="e608e-1961">nx_udp_socket_bind</span></span>

<span data-ttu-id="e608e-1962">**Ikona** ![ Ikona powiązania z gniazdem u D P](./media/user-guide/netx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1962">**Icon** ![U D P socket bind icon](./media/user-guide/netx-events/image153.png)</span></span>

<span data-ttu-id="e608e-1963">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1963">**Description**</span></span>

<span data-ttu-id="e608e-1964">To zdarzenie reprezentuje połączenie gniazda UDP z portem za pośrednictwem nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="e608e-1964">This event represents binding a UDP socket to a port via nx_udp_socket_bind.</span></span>

<span data-ttu-id="e608e-1965">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1965">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1966">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1966">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1967">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1967">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1968">Pole informacji 3: numer portu</span><span class="sxs-lookup"><span data-stu-id="e608e-1968">Info Field 3: Port number</span></span>
- <span data-ttu-id="e608e-1969">Pole informacji 4: opcja oczekiwania</span><span class="sxs-lookup"><span data-stu-id="e608e-1969">Info Field 4: Wait option</span></span>

### <a name="udp-socket-bytes-available"></a><span data-ttu-id="e608e-1970">Dostępne bajty gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1970">UDP Socket Bytes Available</span></span> 

#### <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="e608e-1971">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="e608e-1971">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="e608e-1972">**Ikona** ![ Ikona U-D P Sockets available](./media/user-guide/netx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1972">**Icon** ![U D P socket bytes available icon](./media/user-guide/netx-events/image154.png)</span></span>

<span data-ttu-id="e608e-1973">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1973">**Description**</span></span>

<span data-ttu-id="e608e-1974">To zdarzenie reprezentuje bieżącą liczbę bajtów odebranych w gnieździe UDP za pośrednictwem nx_udp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="e608e-1974">This event represents the current number of bytes received on the UDP socket via nx_udp_socket_bytes_available.</span></span>

<span data-ttu-id="e608e-1975">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1975">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1976">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1976">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1977">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1977">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1978">Pole informacji 3: bajty odebrane w gnieździe</span><span class="sxs-lookup"><span data-stu-id="e608e-1978">Info Field 3: Bytes received on socket</span></span>
- <span data-ttu-id="e608e-1979">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1979">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-disable"></a><span data-ttu-id="e608e-1980">Wyłączenie sumy kontrolnej gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1980">UDP Socket Checksum Disable</span></span> 

#### <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="e608e-1981">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="e608e-1981">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="e608e-1982">**Ikona** ![ Ikona wyłączenia sumy kontrolnej P D w gnieździe](./media/user-guide/netx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1982">**Icon** ![U D P socket checksum disable icon](./media/user-guide/netx-events/image155.png)</span></span>

<span data-ttu-id="e608e-1983">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1983">**Description**</span></span>

<span data-ttu-id="e608e-1984">To zdarzenie przedstawia wyłączenie sumy kontrolnej dla danych w gnieździe UDP za pośrednictwem nx_udp_socket_checksum_disable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1984">This event represents disabling the checksum for data on a UDP socket via nx_udp_socket_checksum_disable.</span></span>

<span data-ttu-id="e608e-1985">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1985">**Information Fields**</span></span> 

- <span data-ttu-id="e608e-1986">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1986">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1987">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1987">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1988">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1988">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1989">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1989">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-enable"></a><span data-ttu-id="e608e-1990">Włączono sumę kontrolną gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-1990">UDP Socket Checksum Enable</span></span> 

#### <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="e608e-1991">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="e608e-1991">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="e608e-1992">**Ikona** ![ Ikona włączenia sumy kontrolnej w gnieździe u D P](./media/user-guide/netx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-1992">**Icon** ![U D P socket checksum enable icon](./media/user-guide/netx-events/image156.png)</span></span>

<span data-ttu-id="e608e-1993">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-1993">**Description**</span></span>

<span data-ttu-id="e608e-1994">To zdarzenie reprezentuje włączenie przetwarzania sumy kontrolnej w gnieździe za pośrednictwem nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="e608e-1994">This event represents enabling checksum processing on a socket via nx_udp_socket_checksum_enable.</span></span>

<span data-ttu-id="e608e-1995">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-1995">**Information Fields**</span></span>

- <span data-ttu-id="e608e-1996">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-1996">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-1997">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-1997">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-1998">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1998">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-1999">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-1999">Info Field 4: Not used</span></span>

### <a name="udp-socket-create"></a><span data-ttu-id="e608e-2000">Tworzenie gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2000">UDP Socket Create</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="e608e-2001">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="e608e-2001">nx_udp_socket_create</span></span>

<span data-ttu-id="e608e-2002">**Ikona** ![ Ikona tworzenia gniazda P D](./media/user-guide/netx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2002">**Icon** ![U D P socket create icon](./media/user-guide/netx-events/image157.png)</span></span>

<span data-ttu-id="e608e-2003">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2003">**Description**</span></span>

<span data-ttu-id="e608e-2004">To zdarzenie reprezentuje tworzenie gniazda UDP za pośrednictwem nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="e608e-2004">This event represents creating a UDP socket via nx_udp_socket_create.</span></span>

<span data-ttu-id="e608e-2005">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2005">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2006">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2006">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-2007">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-2007">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-2008">Pole informacji 3: typ usługi</span><span class="sxs-lookup"><span data-stu-id="e608e-2008">Info Field 3: Type of service</span></span>
- <span data-ttu-id="e608e-2009">Pole informacji 4: Maksymalna Kolejka odbierania</span><span class="sxs-lookup"><span data-stu-id="e608e-2009">Info Field 4: Maximum receive queue</span></span>

### <a name="udp-socket-delete-event"></a><span data-ttu-id="e608e-2010">Zdarzenie usunięcia gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2010">UDP Socket Delete Event</span></span> 

#### <a name="nx_udp_socket_delete-event"></a><span data-ttu-id="e608e-2011">zdarzenie nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="e608e-2011">nx_udp_socket_delete event</span></span>

<span data-ttu-id="e608e-2012">**Ikona** ![ Ikona zdarzenia usuwania gniazda P D](./media/user-guide/netx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2012">**Icon** ![U D P socket delete event icon](./media/user-guide/netx-events/image158.png)</span></span>

<span data-ttu-id="e608e-2013">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2013">**Description**</span></span>

<span data-ttu-id="e608e-2014">To zdarzenie przedstawia usuwanie gniazda UDP za pośrednictwem nx_udp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="e608e-2014">This event represents deleting a UDP socket via nx_udp_socket_delete.</span></span>

<span data-ttu-id="e608e-2015">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2015">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2016">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2016">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-2017">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-2017">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-2018">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2018">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-2019">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2019">Info Field 4: Not used</span></span>

### <a name="udp-socket-information-get-event"></a><span data-ttu-id="e608e-2020">Zdarzenie pobierania informacji o gnieździe UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2020">UDP Socket Information Get Event</span></span> 

#### <a name="nx_udp_socket_info_get-event"></a><span data-ttu-id="e608e-2021">zdarzenie nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="e608e-2021">nx_udp_socket_info_get event</span></span>

<span data-ttu-id="e608e-2022">**Ikona** ![ Ikona zdarzenia odczytaj informacje o gnieździe U D P](./media/user-guide/netx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2022">**Icon** ![U D P socket information get event icon](./media/user-guide/netx-events/image159.png)</span></span>

<span data-ttu-id="e608e-2023">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2023">**Description**</span></span>

<span data-ttu-id="e608e-2024">To zdarzenie reprezentuje informacje o gnieździe UDP za pośrednictwem nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-2024">This event represents getting information about a UDP socket via nx_udp_socket_info_get.</span></span>

<span data-ttu-id="e608e-2025">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2025">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2026">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2026">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-2027">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-2027">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-2028">Pole informacji 3: Bajty wysłane przez gniazdo</span><span class="sxs-lookup"><span data-stu-id="e608e-2028">Info Field 3: Bytes sent through socket</span></span>
- <span data-ttu-id="e608e-2029">Pole informacji 4: bajty odebrane przez gniazdo</span><span class="sxs-lookup"><span data-stu-id="e608e-2029">Info Field 4: Bytes received through socket</span></span>

### <a name="udp-socket-interface-set"></a><span data-ttu-id="e608e-2030">Zestaw interfejsów gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2030">UDP Socket Interface Set</span></span> 

#### <a name="nx_udp_socket_interface_set-event"></a><span data-ttu-id="e608e-2031">zdarzenie nx_udp_socket_interface_set</span><span class="sxs-lookup"><span data-stu-id="e608e-2031">nx_udp_socket_interface_set event</span></span>

<span data-ttu-id="e608e-2032">**Ikona** ![ Ikona ustawienia interfejsu gniazda P D Socket](./media/user-guide/netx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2032">**Icon** ![U D P socket interface set icon](./media/user-guide/netx-events/image160.png)</span></span>

<span data-ttu-id="e608e-2033">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2033">**Description**</span></span>

<span data-ttu-id="e608e-2034">To zdarzenie reprezentuje ustawienie interfejsu wychodzącego określonego gniazda UDP z określonym interfejsem za pośrednictwem nx_udp_socket_interface_set.</span><span class="sxs-lookup"><span data-stu-id="e608e-2034">This event represents setting the outgoing interface of the specified UDP socket with the specified interface via nx_udp_socket_interface_set.</span></span>

<span data-ttu-id="e608e-2035">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2035">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2036">Pole informacji 1: wskaźnik do gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2036">Info Field 1: Pointer to UDP socket</span></span>
- <span data-ttu-id="e608e-2037">Pole informacji 2: indeks odpowiadający interfejsowi gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-2037">Info Field 2: Index corresponding to the interface for the socket</span></span>
- <span data-ttu-id="e608e-2038">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2038">Info Field 3: Not used</span></span>
- <span data-ttu-id="e608e-2039">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2039">Info Field 4: Not used</span></span>

### <a name="udp-socket-port-get"></a><span data-ttu-id="e608e-2040">Pobieranie portu gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2040">UDP Socket Port Get</span></span> 

#### <a name="nx_udp_socket_port_get"></a><span data-ttu-id="e608e-2041">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="e608e-2041">nx_udp_socket_port_get</span></span>

<span data-ttu-id="e608e-2042">**Ikona** ![ Ikona pobierania portu gniazda P D](./media/user-guide/netx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2042">**Icon** ![U D P socket port get icon](./media/user-guide/netx-events/image161.png)</span></span>

<span data-ttu-id="e608e-2043">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2043">**Description**</span></span>

<span data-ttu-id="e608e-2044">To zdarzenie reprezentuje pobieranie portu UDP, z którym powiązana jest określone gniazdo UDP za pośrednictwem nx_udp_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="e608e-2044">This event represents retrieving the UDP port the specified UDP socket is bound to via nx_udp_socket_port_get.</span></span>

<span data-ttu-id="e608e-2045">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2045">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2046">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2046">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-2047">Pole informacji 2: wskaźnik do gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2047">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="e608e-2048">Pole informacji 3: numer portu</span><span class="sxs-lookup"><span data-stu-id="e608e-2048">Info Field 3: Port number</span></span>
- <span data-ttu-id="e608e-2049">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2049">Info Field 4: Not used</span></span>

### <a name="udp-socket-receive"></a><span data-ttu-id="e608e-2050">Odbieranie gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2050">UDP Socket Receive</span></span> 

#### <a name="nx_udp_socket_receive"></a><span data-ttu-id="e608e-2051">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="e608e-2051">nx_udp_socket_receive</span></span>

<span data-ttu-id="e608e-2052">**Ikona** ![ Ikona odbioru w gnieździe U D P](./media/user-guide/netx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2052">**Icon** ![U D P socket receive icon](./media/user-guide/netx-events/image162.png)</span></span>

<span data-ttu-id="e608e-2053">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2053">**Description**</span></span>

<span data-ttu-id="e608e-2054">To zdarzenie reprezentuje dane odebrane w określonym gnieździe UDP za pośrednictwem nx_udp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="e608e-2054">This event represents receiving data on the specified UDP socket via nx_udp_socket_receive.</span></span>

<span data-ttu-id="e608e-2055">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2055">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2056">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2056">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-2057">Pole informacji 2: wskaźnik do gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2057">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="e608e-2058">Pole informacji 3: wskaźnik do odebranego pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-2058">Info Field 3: Pointer to received packet</span></span>
- <span data-ttu-id="e608e-2059">Pole informacji 4: Odebrano rozmiar pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-2059">Info Field 4: Received packet size</span></span>

### <a name="udp-socket-receive-notify"></a><span data-ttu-id="e608e-2060">Powiadomienie o odebraniu gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2060">UDP Socket Receive Notify</span></span> 

#### <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="e608e-2061">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="e608e-2061">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="e608e-2062">**Ikona** ![ Ikona powiadomienia o odebraniu gniazda P ](./media/user-guide/netx-events/image163.png) D </span><span class="sxs-lookup"><span data-stu-id="e608e-2062">**Icon** ![U D P socket receive notify icon](./media/user-guide/netx-events/image163.png)s **Description**</span></span>

<span data-ttu-id="e608e-2063">To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego powiadomienia o odebraniu za pośrednictwem nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="e608e-2063">This event represents registering a receive notify callback via nx_udp_socket_receive_notify.</span></span>

<span data-ttu-id="e608e-2064">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2064">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2065">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2065">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-2066">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-2066">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-2067">Pole informacyjne 3: wskaźnik otrzymywania informacji o funkcji powiadamiania 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2067">Info Field 3: Pointer to receive notify function Info Field 4: Not used</span></span>

### <a name="udp-socket-send"></a><span data-ttu-id="e608e-2068">Wysyłanie gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2068">UDP Socket Send</span></span> 

#### <a name="nx_udp_socket_send"></a><span data-ttu-id="e608e-2069">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="e608e-2069">nx_udp_socket_send</span></span>

<span data-ttu-id="e608e-2070">**Ikona** ![ Ikona wysyłania w gnieździe u D P](./media/user-guide/netx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2070">**Icon** ![U D P socket send icon](./media/user-guide/netx-events/image164.png)</span></span>

<span data-ttu-id="e608e-2071">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2071">**Description**</span></span>

<span data-ttu-id="e608e-2072">To zdarzenie reprezentuje wysyłanie danych za pośrednictwem gniazda UDP za pośrednictwem nx_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="e608e-2072">This event represents sending data through a UDP socket via nx_udp_socket_send.</span></span>

<span data-ttu-id="e608e-2073">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2073">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2074">Pole informacji 1: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-2074">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="e608e-2075">Pole informacji 2: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-2075">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="e608e-2076">Pole informacji 3: długość pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-2076">Info Field 3: Packet length</span></span>
- <span data-ttu-id="e608e-2077">Pole informacji 4: docelowy adres IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2077">Info Field 4: Destination IP address</span></span>

### <a name="udp-socket-unbind"></a><span data-ttu-id="e608e-2078">Niepowiązanie gniazda UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2078">UDP Socket Unbind</span></span> 

#### <a name="nx_udp_socket_unbind"></a><span data-ttu-id="e608e-2079">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="e608e-2079">nx_udp_socket_unbind</span></span>

<span data-ttu-id="e608e-2080">**Ikona** ![ Ikona nieusuwania powiązania U gniazda P D](./media/user-guide/netx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2080">**Icon** ![U D P socket unbind icon](./media/user-guide/netx-events/image165.png)</span></span>

<span data-ttu-id="e608e-2081">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2081">**Description**</span></span>

<span data-ttu-id="e608e-2082">To zdarzenie reprezentuje powiązanie portu UDP z gniazdem za pośrednictwem nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="e608e-2082">This event represents unbinding a UDP port with a socket via nx_udp_socket_unbind.</span></span>

<span data-ttu-id="e608e-2083">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2083">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2084">Pole informacji 1: wskaźnik do wystąpienia adresu IP</span><span class="sxs-lookup"><span data-stu-id="e608e-2084">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="e608e-2085">Pole informacji 2: wskaźnik do gniazda</span><span class="sxs-lookup"><span data-stu-id="e608e-2085">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="e608e-2086">Pole informacji 3: numer portu</span><span class="sxs-lookup"><span data-stu-id="e608e-2086">Info Field 3: Port number</span></span>
- <span data-ttu-id="e608e-2087">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2087">Info Field 4: Not used</span></span>

### <a name="udp-source-extract"></a><span data-ttu-id="e608e-2088">Wyodrębnij Źródło UDP</span><span class="sxs-lookup"><span data-stu-id="e608e-2088">UDP Source Extract</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="e608e-2089">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="e608e-2089">nx_udp_socket_create</span></span>

<span data-ttu-id="e608e-2090">**Ikona** ![ Ikona wyodrębnienia źródła U D P](./media/user-guide/netx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="e608e-2090">**Icon** ![U D P source extract icon](./media/user-guide/netx-events/image166.png)</span></span>

<span data-ttu-id="e608e-2091">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e608e-2091">**Description**</span></span>

<span data-ttu-id="e608e-2092">To zdarzenie reprezentuje adres IP i numer portu odebranego pakietu UDP za pośrednictwem nx_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="e608e-2092">This event represents getting the IP address and port number of a received UDP packet via nx_udp_source_extract.</span></span>

<span data-ttu-id="e608e-2093">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="e608e-2093">**Information Fields**</span></span>

- <span data-ttu-id="e608e-2094">Pole informacji 1: wskaźnik do pakietu</span><span class="sxs-lookup"><span data-stu-id="e608e-2094">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="e608e-2095">Pole informacji 2: adres IP nadawcy</span><span class="sxs-lookup"><span data-stu-id="e608e-2095">Info Field 2: Sender's IP address</span></span>
- <span data-ttu-id="e608e-2096">Pole informacji 3: numer portu nadawcy</span><span class="sxs-lookup"><span data-stu-id="e608e-2096">Info Field 3: Sender's port number</span></span>
- <span data-ttu-id="e608e-2097">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="e608e-2097">Info Field 4: Not used</span></span>