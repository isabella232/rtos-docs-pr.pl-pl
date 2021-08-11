---
title: Rozdział 8 — Azure RTOS śledzenia NetX
description: Ten rozdział zawiera opis Azure RTOS NetX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f785b421ffc6d588080eb45a50dad949daf1ca6a9bf36770110f0450cd465bf1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116805297"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>Rozdział 8 — Azure RTOS śledzenia NetX

Ten rozdział zawiera opis Azure RTOS NetX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

Poniżej znajduje się lista zdarzeń NetX wyświetlanych przez traceX.

| Ikona                                           | Znaczenie                 |
| -------------------------------- | ------------------------------------- |
| ![Ikona odbierania żądania wewnętrznego żądania R P](./media/user-guide/netx-events/image1.png)    | Odbieranie wewnętrznego żądania ARP |
| ![Ikona wewnętrznego wysyłania żądania R P](./media/user-guide/netx-events/image2.png)    | Wewnętrzne wysyłanie żądania ARP |
| ![Ikona odbierania wewnętrznej odpowiedzi R P](./media/user-guide/netx-events/image3.png)    | Odbieranie wewnętrznej odpowiedzi ARP |
| ![Ikona wewnętrznego wysyłania odpowiedzi R P](./media/user-guide/netx-events/image4.png)    | Wewnętrzne wysyłanie odpowiedzi ARP |
| ![Ikona odbierania we/wy](./media/user-guide/netx-events/image5.png)    | Wewnętrzne odbieranie ICMP |
| ![Ikona wysyłania wewnętrznego folderu I M P](./media/user-guide/netx-events/image6.png)    | Wewnętrzne wysyłanie ICMP |
| ![Wewnętrzna ikona odbierania NetX I G M P](./media/user-guide/netx-events/image7.png)    | Wewnętrzne odbieranie IGMP NetX |
| ![Ikona odbierania wewnętrznego komputera IP](./media/user-guide/netx-events/image8.png)    | Odbieranie wewnętrznego adresu IP |
| ![Ikona wewnętrznego wysyłania IP](./media/user-guide/netx-events/image9.png)    | Wewnętrzne wysyłanie adresów IP |
| ![Ikona odbierania danych wewnętrznych T C P](./media/user-guide/netx-events/image10.png)    | Wewnętrzne odbieranie danych TCP |
| ![Ikona wewnętrznego wysyłania danych T C P](./media/user-guide/netx-events/image11.png)    | Wewnętrzne wysyłanie danych TCP |
| ![Wewnętrzna ikona odbierania T C P FIN](./media/user-guide/netx-events/image12.png)    | Wewnętrzne odbieranie danych FIN protokołu TCP |
| ![Ikona wewnętrznego wysyłania T C P F I N](./media/user-guide/netx-events/image13.png)    | Wewnętrzne wysyłanie danych FIN protokołu TCP |
| ![Wewnętrzna ikona odbierania T C P R S T](./media/user-guide/netx-events/image14.png)    | Wewnętrzne odbieranie RST protokołu TCP |
| ![Ikona wewnętrznego wysyłania T C P R S T](./media/user-guide/netx-events/image15.png)    | Wewnętrzne wysyłanie RST protokołu TCP |
| ![Wewnętrzna ikona odbierania T C P S Y N](./media/user-guide/netx-events/image16.png)    | Wewnętrzne odbieranie SYN protokołu TCP |
| ![Ikona wewnętrznego wysyłania T C P S Y N](./media/user-guide/netx-events/image17.png)    | Wewnętrzne wysyłanie SYN protokołu TCP |
| ![Ikona odbierania wewnętrznego zestawu danych](./media/user-guide/netx-events/image18.png)    | Wewnętrzne odbieranie protokołu UDP |
| ![Ikona wewnętrznego wysyłania UD P](./media/user-guide/netx-events/image19.png)    | Wewnętrzne wysyłanie UDP |
| ![Wewnętrzna ikona odbierania R A R P](./media/user-guide/netx-events/image20.png)    | Wewnętrzne odbieranie RARP |
| ![Wewnętrzna ikona wysyłania R A R P](./media/user-guide/netx-events/image21.png)    | Wewnętrzne wysyłanie RARP |
| ![Ikona wewnętrznego ponawiania próby T C P](./media/user-guide/netx-events/image22.png)    | Wewnętrzne ponawianie próby protokołu TCP |
| ![Ikona wewnętrznej zmiany stanu T C P](./media/user-guide/netx-events/image23.png)    | Wewnętrzna zmiana stanu TCP |
| ![Ikona wewnętrznego wysyłania pakietów sterowników we/wy](./media/user-guide/netx-events/image24.png)    | Wysyłanie pakietów sterowników we/wy wewnętrznego |
| ![Ikonę](./media/user-guide/netx-events/image25.png)    | Inicjowanie wewnętrznego sterownika We/Wy |
| ![Ikona Inicjowanie wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image26.png)    | Włączanie wewnętrznego połączenia sterownika We/Wy |
| ![Ikona wyłączania linku wewnętrznego we/wy dla sterownika](./media/user-guide/netx-events/image27.png)    | Wyłącz link do wewnętrznego sterownika we/wy |
| ![Ikona rozgłaszeń pakietów sterowników we/wy wewnętrznych](./media/user-guide/netx-events/image28.png)    | Emisja wewnętrznego pakietu sterowników we/wy |
| ![Ikona wysyłania ARP wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image29.png)    | Wysyłanie ARP sterownika we/wy wewnętrznego |
| ![Ikona wysyłania odpowiedzi ARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image30.png)    | Wysyłanie odpowiedzi ARP sterownika we/wy wewnętrznego |
| ![Ikona wysyłania RARP wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image31.png)    | Wysyłanie RARP sterownika we/wy wewnętrznego |
| ![Ikona dołączania do multiemisji sterowników we/wy](./media/user-guide/netx-events/image32.png)    | Sprzężenia multiemisji sterownika wewnętrznego we/wy |
| ![Ikona pozostaw wewnętrzny sterownik we/wy multiemisji](./media/user-guide/netx-events/image33.png)    | Pozostawienie wewnętrznego sterownika we/wy do multiemisji |
| ![Ikona Pobierz stan wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image34.png)    | Uzyskiwanie stanu wewnętrznego sterownika we/wy |
| ![Ikona Get Speed wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image35.png)    | Szybkość pobierania wewnętrznego sterownika we/wy |
| ![Ikona Pobierz dwukierunkowy typ sterownika we/wy](./media/user-guide/netx-events/image36.png)    | Wewnętrzny sterownik we/wy pobierz typ dwukierunkowy |
| ![Ikona Liczby błędów get wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image37.png)    | Liczba błędów get wewnętrznego sterownika we/wy |
| ![Ikona Pobierz liczbę rx sterowników wewnętrznych we/wy](./media/user-guide/netx-events/image38.png)    | Wewnętrzny sterownik we/wy pobierz liczbę rx |
| ![Ikona Pobierz liczbę TX sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image39.png)    | Wewnętrzny sterownik we/wy pobierz liczbę TX |
| ![Ikona błędów alokacji get sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image40.png)    | Błędy alokacji wewnętrznego sterownika we/wy |
| ![Ikona Cofają inicjowanie sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image41.png)    | Cofnie zainicjowanie wewnętrznego sterownika We/Wy |
| ![Ikona wewnętrznego przetwarzania sterowników odroczonych we/wy](./media/user-guide/netx-events/image42.png)    | Odroczone przetwarzanie sterowników we/wy wewnętrznego |
| ![Ikona unieważniaj wpisy dynamiczne R P](./media/user-guide/netx-events/image43.png)    | **Nieprawidłowe wpisy dynamiczne ARP** (*nx_arp_dynamic_entries_invalidate*) |
| ![Ikona dynamicznego zestawu wpisów R P](./media/user-guide/netx-events/image44.png)    | **Dynamiczny zestaw wpisów ARP** *(nx_arp_dynamic_entry_set*) |
| ![Ikona włączania aplikacji R P](./media/user-guide/netx-events/image45.png)    | **Włączanie ARP** *(nx_arp_enable*) |
| ![Ikona wysyłania szosowego R P](./media/user-guide/netx-events/image46.png)    | **ARP Send (** *nx_arp_gratuitous_send*) |
| ![Ikona Znajdź adres sprzętowy R P](./media/user-guide/netx-events/image47.png)    | **Znajdowanie adresów sprzętowych ARP** (*nx_arp_hardware_address_find*) |
| ![Ikona Pobierz informacje o P](./media/user-guide/netx-events/image48.png)    | **ARP Information Get** (*nx_arp_info_get*) |
| ![Ikona Znajdź adres IP R P](./media/user-guide/netx-events/image49.png)    | **Znajdowanie adresu IP protokołu ARP** (*nx_arp_ip_address_find*) |
| ![Ikona tworzenia statycznego wpisu R P](./media/user-guide/netx-events/image50.png)    | **Tworzenie statycznego wpisu ARP** (*nx_arp_static_entry_create*) |
| ![Ikona usuwania statycznych wpisów R P](./media/user-guide/netx-events/image51.png)    | **Usuwanie statycznych wpisów ARP** (*nx_arp_static_entries_delete*) |
| ![Ikona usuwania statycznego wpisu R P](./media/user-guide/netx-events/image52.png)    | **Usuwanie statycznego wpisu ARP** (*nx_arp_static_entry_delete*) |
| ![Ikona usuwania wpisu pamięci podręcznej Duo](./media/user-guide/netx-events/image53.png)    | **Usuwanie wpisu pamięci podręcznej Duo** Cache *(nxd_nd_cache_entry_delete*) |
| ![Ikona zestawu wpisów pamięci podręcznej Duo](./media/user-guide/netx-events/image54.png)    | **Zestaw wpisów pamięci podręcznej Duo** (*nxd_nd_cache_entry_set*) |
| ![Ikona Unieważnij pamięć podręczną Duo Cache](./media/user-guide/netx-events/image55.png)    | **Invalidate pamięci podręcznej Duo** (*nxd_nd_cache_invalidate*) |
| ![Ikona Znajdź adres I P pamięci podręcznej Duo Cache](./media/user-guide/netx-events/image56.png)    | **Znajdź adres IP pamięci podręcznej Duo** (*nxd_nd_cache_ip_address_find*) |
| ![Ikona włączania aplikacji Duo I C M P](./media/user-guide/netx-events/image57.png)    | **Duo ICMP Enable** (*nxd_icmp_enable*) |
| ![Duo I C M P I P v 6 Ikona ping](./media/user-guide/netx-events/image58.png)    | **Duo ICMP IPv6 Ping** (*nxd_icmp_ping*) |
| ![Ikona Znajdź maksymalny rozmiar ładunku Aplikacji Duo I P](./media/user-guide/netx-events/image59.png)    | **Znajdź maksymalny rozmiar ładunku adresu IP Duo** (*nx_max_payload_size_find*) |
| ![Ikona wysyłania nieprzetworzonych pakietów Duo I P](./media/user-guide/netx-events/image60.png)    | **Nieprzetworzonych pakietów IP Duo** (*nxd_ip_raw_packet_send*) |
| ![Ikona dodawania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image61.png)    | **Dodawanie domyślnego routera IPv6** duo (*nxd_ipv6_default_router_add*) |
| ![Ikona usuwania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image62.png)    | **Usuwanie domyślnego routera IPv6 duo** *(nxd_ipv6_default_router_delete)* |
| ![Ikona włączania aplikacji Duo I P v 6](./media/user-guide/netx-events/image63.png)    | **Włączanie protokołu IPv6 w aplikacji Duo** *(nxd_ipv6_enable)* |
| ![Ikona Get adresu globalnego Duo I P v 6](./media/user-guide/netx-events/image64.png)    | **Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*) |
| ![Ikona globalnego zestawu adresów Duo I P v 6](./media/user-guide/netx-events/image65.png)    | **Globalny zestaw adresów IPv6 duo** (*nxd_ipv6_global_address_set*) |
| ![Ikona Inicjowanie procesu w aplikacji Duo I P v 6](./media/user-guide/netx-events/image66.png)    | **Duo IPv6 Initiate Process** (*nxd_ipv6_initiate_dad_process*) |
| ![Ikona Pobierz adres interfejsu Aplikacji Duo I P v 6](./media/user-guide/netx-events/image67.png)    | **Pobierz adres interfejsu IPv6 duo** (*nxd_ipv6_interface_address_get*) |
| ![Ikona zestawu adresów interfejsu Duo I P v 6](./media/user-guide/netx-events/image68.png)    | **Zestaw adresów interfejsu IPv6 duo** (*nxd_ipv6_interface_address_set*) |
| ![Ikona Pobierz adres lokalny w aplikacji Duo I P v 6 Link](./media/user-guide/netx-events/image69.png)    | **Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*) |
| ![Ikona zestawu adresów lokalnych w aplikacji Duo I P v 6 Link](./media/user-guide/netx-events/image70.png)    | **Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*) |
| ![Ikona nieprzetworzonych pakietów Duo I P v 6](./media/user-guide/netx-events/image71.png)    | **Nieprzetworzone wysyłanie pakietów IPv6 w aplikacji Duo** (*nxd_ipv6_raw_packet_send)* |
| ![Ikona Pobierz informacje o elementu równorzędnego gniazda Duo T C P](./media/user-guide/netx-events/image72.png)    | **Informacje o komunikacji równorzędnej gniazda TCP Duo get** (*nxd_tcp_socket_peer_info_get*) |
| ![Ikona zestawu gniazd Duo T C P Socket Set Interface](./media/user-guide/netx-events/image73.png)    | **Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*) |
| ![Ikona wysyłania gniazda Aplikacji Duo U D P](./media/user-guide/netx-events/image74.png)    | **Duo UDP Socket Send** (*nxd_udp_socket_send*) |
| ![Ikona interfejsu zestawu gniazd Duo U D P](./media/user-guide/netx-events/image75.png)    | **Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*) |
| ![Ikona wyodrębniania źródła aplikacji Duo U D P](./media/user-guide/netx-events/image76.png)    | **Wyodrębnianie źródła UDP duo** (*nxd_udp_source_extract*) |
| ![Ikona włączania aplikacji I C M P](./media/user-guide/netx-events/image77.png)    | **Włączanie ICMP** (*nx_icmp_enable*) |
| ![Ikona Pobierz informacje o języku C M P](./media/user-guide/netx-events/image78.png)    | **Uzyskiwanie informacji OCMP** (*nx_icmp_info_get*) |
| ![Ikona ping I C M P](./media/user-guide/netx-events/image79.png)    | **ICMP Ping** (*nx_icmp_ping*) |
| ![Ikona włączania aplikacji I G M P](./media/user-guide/netx-events/image80.png)    | **Włącz IGMP** (*nx_igmp_enable*) |
| ![Ikona Pobierz informacje o aplikacji I G M P](./media/user-guide/netx-events/image81.png)    | **Uzyskiwanie informacji OGMP** (*nx_igmp_info_get*) |
| ![Ikona wyłączania sprzężenia zwrotnego I G M P Loopback](./media/user-guide/netx-events/image82.png)    | **Wyłączenie sprzężenia zwrotnego IGMP** (*nx_igmp_loopback_disable*) |
| ![Ikona włączania sprzężenia zwrotnego I G M P Loopback](./media/user-guide/netx-events/image83.png)    | **Włączanie sprzężenia zwrotnego IGMP** (*nx_igmp_loopback_enable*) |
| ![Ikona dołączania do multiemisji I G M P](./media/user-guide/netx-events/image84.png)    | **Sprzężenia multiemisji IGMP** (*nx_igmp_multicast_join*) |
| ![Ikona opuszczania multiemisji I G M P](./media/user-guide/netx-events/image85.png)    | **Pozostawienie multiemisji IGMP** (*nx_igmp_multicast_leave*) |
| ![Ikona Powiadamianie o zmianie adresu IP](./media/user-guide/netx-events/image86.png)    | **Powiadomienie o zmianie adresu IP** (*nx_ip_address_change_notify*) |
| ![Ikona Uzyskiwanie adresu IP](./media/user-guide/netx-events/image87.png)    | **Uzyskiwanie adresu IP** *(nx_ip_address_get*) |
| ![Ikona Zestaw adresów IP](./media/user-guide/netx-events/image88.png)    | **Zestaw adresów IP** *(nx_ip_address_set*) |
| ![Ikona Tworzenia we/wy](./media/user-guide/netx-events/image89.png)    | **Tworzenie adresu IP** *(nx_ip_create*) |
| ![Ikona I P Delete](./media/user-guide/netx-events/image90.png)    | **Usuwanie adresu IP** *(nx_ip_delete*) |
| ![Ikona Bezpośrednie polecenie sterownika I P](./media/user-guide/netx-events/image91.png)    | **Bezpośrednie polecenie sterownika IP** (*nx_ip_driver_direct_command*) |
| ![Ikona Wyłączania przekazywania we/wy](./media/user-guide/netx-events/image92.png)    | **Wyłączanie przekazywania adresów IP** *(nx_ip_forwarding_disable*) |
| ![Ikona Włącz przekazywanie I P](./media/user-guide/netx-events/image93.png)    | **Włącz przekazywanie IP** (*nx_ip_forwarding_enable*) |
| ![Ikona wyłączania fragmentu I P](./media/user-guide/netx-events/image94.png)    | **Wyłączanie fragmentu adresu IP** (*nx_ip_fragment_disable*) |
| ![Ikona włączania fragmentu IP](./media/user-guide/netx-events/image95.png)    | **Włączanie fragmentu adresu IP** (*nx_ip_fragment_enable*)  |
| ![Ikona zestawu adresów bramy IP](./media/user-guide/netx-events/image96.png)    | **Zestaw adresów bramy IP** *(nx_ip_gateway_address_set*) |
| ![Ikona Pobierz informacje o P](./media/user-guide/netx-events/image97.png)    | **Uzyskiwanie informacji o adresie IP** *(nx_ip_info_get*) |
| ![Ikona dołączania interfejsu I P](./media/user-guide/netx-events/image98.png)    | **Dołączanie interfejsu IP** *(nx_ip_interface_attach*) |
| ![Ikona Pobierz informacje o interfejsie I P](./media/user-guide/netx-events/image99.png)    | **Uzyskiwanie informacji o interfejsie IP** *(nx_ip_interface_info_get*) |
| ![Ikona wyłączania nieprzetworzonych pakietów I P](./media/user-guide/netx-events/image100.png)    | **Wyłącz nieprzetworzonych pakietów IP** *(nx_ip_raw_packet_disable*) |
| ![Ikona Włączania pakietu nieprzetworzonych pakietów I P](./media/user-guide/netx-events/image101.png)    | **Włączanie nieprzetworzonych pakietów IP** *(nx_ip_raw_packet_enable*) |
| ![Ikona odbierania nieprzetworzonych pakietów I P](./media/user-guide/netx-events/image102.png)    | **Odbieranie nieprzetworzonych pakietów IP** *(nx_ip_raw_packet_receive*) |
| ![Ikona wyślij nieprzetworzonych pakietów IP](./media/user-guide/netx-events/image103.png)    | **Wysyłanie nieprzetworzonych pakietów IP** *(nx_ip_raw_packet_send*) |
| ![Ikona Dodaj trasę statyczną IP](./media/user-guide/netx-events/image104.png)    | **Dodawanie statycznej trasy IP** *(nx_ip_static_route_add*) |
| ![Ikona Usuń trasę statyczną IP](./media/user-guide/netx-events/image105.png)    | **Usuwanie tras statycznych adresów IP** *(nx_ip_static_route_delete)* |
| ![Ikona sprawdzania stanu IP](./media/user-guide/netx-events/image106.png)    | **Sprawdzanie stanu adresu IP** *(nx_ip_status_check*)|
| ![Ikona włączania aplikacji I PS E C](./media/user-guide/netx-events/image107.png)    | **Włączanie protokołu IPSEC** *(nx_ipsec_enable)* |
| ![Ikona Przydzielanie pakietów](./media/user-guide/netx-events/image108.png)    | **Przydzielanie pakietów** *(nx_packet_allocate*) |
| ![Ikona kopiowania pakietów](./media/user-guide/netx-events/image109.png)    | **Kopiowanie pakietów** *(nx_packet_copy*) |
| ![Ikona Dołączanie danych pakietu](./media/user-guide/netx-events/image110.png)    | **Dołączanie danych pakietów** (*nx_packet_data_append*) |
| ![Ikona przesunięcia wyodrębniania danych pakietu](./media/user-guide/netx-events/image111.png)    | **Przesunięcie wyodrębniania danych pakietu** (*nx_packet_data_extract_offset*) |
| ![Ikona Pobieranie danych pakietu](./media/user-guide/netx-events/image112.png)    | **Pobieranie danych pakietów** *(nx_packet_data_retrieve*) |
| ![Ikona Pobierz długość pakietu](./media/user-guide/netx-events/image113.png)    | **Get długości pakietu** (*nx_packet_length_get*) |
| ![Ikona Tworzenia puli pakietów](./media/user-guide/netx-events/image114.png)    | **Tworzenie puli pakietów** (*nx_packet_pool_create*) |
| ![Ikona Usuwania puli pakietów](./media/user-guide/netx-events/image115.png)    | **Usuwanie puli pakietów** *(nx_packet_pool_delete*) |
| ![Ikona Pobierz informacje o puli pakietów](./media/user-guide/netx-events/image116.png)    | **Informacje o puli pakietów get** (*nx_packet_pool_info_get*) |
| ![Ikona Wydania pakietu](./media/user-guide/netx-events/image117.png)    | **Wydanie pakietu** (*nx_packet_release*) |
| ![Ikona wydania przekazywania pakietów](./media/user-guide/netx-events/image118.png)    | **Wydanie przekazywania pakietów** *(nx_packet_transmit_release*) |
| ![Ikona wyłączania plików R A R P](./media/user-guide/netx-events/image119.png)    | **RaRP Disable** *(nx_rarp_disable*) |
| ![Ikona włączania R A R P](./media/user-guide/netx-events/image120.png)    | **Włączenie funkcji RARP** *(nx_rarp_enable*) |
| ![Ikona Pobierz informacje o R A R P](./media/user-guide/netx-events/image121.png)    | **RaRP Information Get** (*nx_rarp_info_get*) |
| ![Ikona Inicjowanie systemu](./media/user-guide/netx-events/image122.png)    | **Inicjowanie systemu** (*nx_system_initialize*) |
| ![Ikona powiązania gniazda klienta T C P](./media/user-guide/netx-events/image123.png)    | **Powiązanie gniazda klienta TCP** *(nx_tcp_client_socket_bind*) |
| ![Ikona gniazda klienta T C P Połączenie](./media/user-guide/netx-events/image124.png)    | **Gniazda klienta TCP Połączenie** (*nx_tcp_client_socket_connect*) |
| ![Ikona Pobierz port gniazda klienta T C P](./media/user-guide/netx-events/image125.png)    | **Pobierz port gniazda klienta TCP** (*nx_tcp_client_socket_port_get*) |
| ![Ikona unbind gniazda klienta T C P](./media/user-guide/netx-events/image126.png)    | **Unbind gniazda klienta TCP** (*nx_tcp_client_socket_unbind*) |
| ![Ikona włączania T C P](./media/user-guide/netx-events/image127.png)    | **Włączenie protokołu TCP** *(nx_tcp_enable*) |
| ![Ikona Znajdź bezpłatny port T C P](./media/user-guide/netx-events/image128.png)    | **Znajdowanie wolnego portu TCP** *(nx_tcp_free_port_find*) |
| ![Ikona Pobierz informacje T C P](./media/user-guide/netx-events/image129.png)    | **Tcp Information Get** (*nx_tcp_info_get*) |
| ![Ikona akceptowania gniazda serwera T C P](./media/user-guide/netx-events/image130.png)    | **Akceptowanie gniazd serwera TCP** *(nx_tcp_server_socket_accept*) |
| ![Ikona nasłuchiwać gniazda serwera T C P](./media/user-guide/netx-events/image131.png)    | **Nasłuchiwać** gniazd serwera TCP (*nx_tcp_server_socket_listen*) |
| ![Ikona reliktu gniazda serwera T C P](./media/user-guide/netx-events/image132.png)    | **TCP Server Socket Relikt** (*nx_tcp_server_socket_relisten*) |
| ![Ikona Nieakceptuj gniazda serwera T C P](./media/user-guide/netx-events/image133.png)    | **Nieakceptuj gniazda serwera TCP** (*nx_tcp_server_socket_unaccept*) |
| ![Ikona unlisten gniazda serwera T C P](./media/user-guide/netx-events/image134.png)    | **Unlisten gniazda serwera TCP** (*nx_tcp_server_socket_unlisten*) |
| ![Ikona Dostępne bajty gniazda T C P](./media/user-guide/netx-events/image135.png)    | **Dostępne bajty gniazd TCP** *(nx_tcp_socket_bytes_available*) |
| ![Ikona tworzenia gniazda T C P](./media/user-guide/netx-events/image136.png)    | **Tworzenie gniazda TCP** *(nx_tcp_socket_create*) |
| ![Ikona usuwania gniazda T C P](./media/user-guide/netx-events/image137.png)    | **Usuwanie gniazda TCP** *(nx_tcp_socket_delete*) |
| ![Ikona rozłączania gniazda T C P](./media/user-guide/netx-events/image138.png)    | **Rozłączanie gniazd TCP** *(nx_tcp_socket_disconnect*) |
| ![Ikona Pobierz informacje o gniazdach T C P](./media/user-guide/netx-events/image139.png)    | **Tcp Socket Information Get** (*nx_tcp_socket_info_get*) |
| ![T C P Socket MSS Pobierz ikona](./media/user-guide/netx-events/image140.png)    | **Tcp Socket MSS Get** (*nx_tcp_socket_mss_get*) |
| ![Ikona pobierz elementu równorzędnego MSS gniazda T C P](./media/user-guide/netx-events/image141.png)    | **Tcp Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*) |
| ![Ikona zestawu gniazd T C P MSS](./media/user-guide/netx-events/image142.png)    | **Zestaw MSS gniazd TCP** *(nx_tcp_socket_mss_set*) |
| ![Ikona Pobierz informacje o gnieździe T C P Socket Peer](./media/user-guide/netx-events/image143.png)    | **Uzyskiwanie informacji o równorzędnych gniazdach TCP** (*nx_tcp_socket_peer_info_get*) |
| ![Ikona odbierania gniazda T C P](./media/user-guide/netx-events/image144.png)    | **Odbieranie gniazda TCP** *(nx_tcp_socket_receive*) |
| ![Ikona powiadomienia o otrzymaniu gniazda T C P](./media/user-guide/netx-events/image145.png)    | **Powiadomienie o odbierania gniazd TCP** (*nx_tcp_socket_receive_notify*) |
| ![Ikona wysyłania gniazda T C P](./media/user-guide/netx-events/image146.png)    | **Wysyłanie gniazda TCP** *(nx_tcp_socket_send*) |
| ![Ikona T C P Socket State Wait](./media/user-guide/netx-events/image147.png)    | **Oczekiwanie na stan gniazda TCP** *(nx_tcp_socket_state_wait*) |
| ![Ikona konfigurowania przesyłania gniazda T C P](./media/user-guide/netx-events/image148.png)    | **Konfigurowanie przesyłania gniazda TCP** *(nx_tcp_socket_transmit_configure*) |
| ![Ikona powiadamiania o aktualizacji okna T C P socket Window Notify Set](./media/user-guide/netx-events/image149.png)    | **Zestaw powiadomiń o aktualizacji okien gniazd** TCP (*nx_tcp_socket_window_update_notify_set*)  |
| ![Ikona włączania aplikacji JD P](./media/user-guide/netx-events/image150.png)    | **Włączanie protokołu UDP** *(nx_udp_enable*) |
| ![Ikona Znajdź bezpłatny port](./media/user-guide/netx-events/image151.png)    | **Znajdowanie bezpłatnego portu UDP** (*nx_udp_free_port_find*) |
| ![Ikona Pobierz informacje o UD P](./media/user-guide/netx-events/image152.png)    | **UDP Information Get** (*nx_udp_info_get*) |
| ![Ikona powiązania gniazda UD P](./media/user-guide/netx-events/image153.png)    | **Powiązanie gniazda UDP** (*nx_udp_socket_bind*) |
| ![Ikona liczba dostępnych bajtów gniazda U D P](./media/user-guide/netx-events/image154.png)    | **Dostępne bajty gniazd UDP** (*nx_udp_socket_bytes_available*) |
| ![Ikona wyłączania sumy kontrolnej gniazda U D P](./media/user-guide/netx-events/image155.png)    | **Wyłącz sumy kontrolne gniazda UDP** (*nx_udp_socket_checksum_disable*) |
| ![Ikona włączania sumy kontrolnej gniazda U D P](./media/user-guide/netx-events/image156.png)    | **Włączanie sumy kontrolnej gniazda UDP** *(nx_udp_socket_checksum_enable)* |
| ![Ikona Tworzenia gniazda U D P](./media/user-guide/netx-events/image157.png)    | **Tworzenie gniazda UDP** (*nx_udp_socket_create*) |
| ![Ikona usuwania gniazda U D P](./media/user-guide/netx-events/image158.png)    | **Usuwanie gniazda UDP** *(nx_udp_socket_delete*) |
| ![Ikona Pobierz informacje o gniazdach U](./media/user-guide/netx-events/image159.png)    | **UDP Socket Information Get** (*nx_udp_socket_info_get*) |
| ![Ikona zestawu interfejsów gniazd U D P](./media/user-guide/netx-events/image160.png)    | **Zestaw interfejsów gniazd UDP** (*nx_udp_socket_interface_set*) |
| ![Ikona Pobierz port gniazda U D P](./media/user-guide/netx-events/image161.png)    | **UDP Socket Port Get** (*nx_udp_socket_port_get*) |
| ![Ikona odbierania gniazda U D P](./media/user-guide/netx-events/image162.png)    | **Odbieranie gniazda UDP** (*nx_udp_socket_receive*) |
| ![Ikona odbierania powiadomienia gniazda U D P](./media/user-guide/netx-events/image163.png)    | **Powiadomienie o odbierce gniazda UDP** (*nx_udp_socket_receive_notify*) |
| ![Ikona wysyłania gniazda U D P](./media/user-guide/netx-events/image164.png)    | **UDP Socket Send** (*nx_udp_socket_send*) |
| ![Ikona unbind gniazda U D P](./media/user-guide/netx-events/image165.png)    | **UDP Socket Unbind** *(nx_udp_socket_unbind*) |
| ![Ikona wyodrębniania źródła UD P](./media/user-guide/netx-events/image166.png)    | **Wyodrębnianie źródła UDP** (*nx_udp_source_extract*) |

## <a name="event-descriptions"></a>Opisy zdarzeń

Na poniższych stronach opisano zdarzenia śledzenia NetX.

### <a name="internal-arp-request-receive"></a>Odbieranie wewnętrznego żądania ARP 

#### <a name="internal-arp-request-receive"></a>Odbieranie wewnętrznego żądania ARP

**Ikona** ![ Ikona odbierania wewnętrznego żądania ARP](./media/user-guide/netx-events/image1.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odbierania wewnętrznego żądania ARP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Source IP address (Pole informacyjne 2: źródłowy adres IP)
- Info Field 3: Pointer to packet (Pole informacyjne 3: wskaźnik do pakietu)
- Pole informacji 4: nie jest używane

### <a name="internal-arp-request-send"></a>Wewnętrzne wysyłanie żądania ARP 

#### <a name="internal-arp-request-send"></a>Wewnętrzne wysyłanie żądania ARP

**Ikona** ![ Ikona wysyłania wewnętrznego żądania ARP](./media/user-guide/netx-events/image2.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania żądania ARP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: docelowy adres IP
- Info Field 3: Pointer to packet (Pole informacyjne 3: wskaźnik do pakietu)
- Pole informacji 4: nie jest używane

### <a name="internal-arp-response-receive"></a>Odbieranie wewnętrznej odpowiedzi ARP 

#### <a name="internal-arp-request-receive"></a>Odbieranie wewnętrznego żądania ARP

**Ikona** ![ Ikona odbierania wewnętrznego żądania ARP](./media/user-guide/netx-events/image3.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odbierania wewnętrznej odpowiedzi ARP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Source IP address (Pole informacyjne 2: źródłowy adres IP)
- Info Field 3: Pointer to packet (Pole informacyjne 3: wskaźnik do pakietu)
- Pole informacji 4: nie jest używane

### <a name="internal-arp-response-send"></a>Wewnętrzne wysyłanie odpowiedzi ARP 

#### <a name="internal-arp-request-send"></a>Wewnętrzne wysyłanie żądania ARP

**Ikona** ![ Ikona wysyłania wewnętrznego żądania ARP](./media/user-guide/netx-events/image4.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania odpowiedzi NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: docelowy adres IP
- Info Field 3: Pointer to packet (Pole informacyjne 3: wskaźnik do pakietu)
- Pole informacji 4: nie jest używane

### <a name="internal-icmp-receive"></a>Wewnętrzne odbieranie ICMP 

#### <a name="internal-icmp-receive"></a>Wewnętrzne odbieranie ICMP

**Ikona** ![ Ikona odbierania wewnętrznego folderu I M P](./media/user-guide/netx-events/image5.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania ICMP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Source IP address (Pole informacyjne 2: źródłowy adres IP)
- Info Field 3: Pointer to packet (Pole informacyjne 3: wskaźnik do pakietu)
- Info Field 4: Word 0 of ICMP header (Pole informacyjne 4: wyraz 0 nagłówka ICMP)

### <a name="internal-icmp-send"></a>Wewnętrzne wysyłanie ICMP 

#### <a name="internal-icmp-send"></a>Wewnętrzne wysyłanie ICMP

**Ikona** ![ Ikona wysyłania wewnętrznego folderu I M P](./media/user-guide/netx-events/image6.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania ICMP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: docelowy adres IP
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4: Wyraz 0 nagłówka ICMP

### <a name="internal-igmp-receive"></a>Wewnętrzne odbieranie IGMP 

#### <a name="internal-igmp-receive"></a>Wewnętrzne odbieranie IGMP

**Ikona** ![ Ikona odbierania danych wewnętrznych I G M P](./media/user-guide/netx-events/image7.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania IGMP NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik IP
- Pole informacji 2: źródłowy adres IP
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4: Wyraz 0 nagłówka IGMP

### <a name="internal-ip-receive"></a>Odbieranie wewnętrznego adresu IP 

#### <a name="internal-ip-receive"></a>Odbieranie wewnętrznego adresu IP

**Ikona** ![ Ikona odbierania wewnętrznych wiadomości I P](./media/user-guide/netx-events/image8.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odbierania wewnętrznego adresu IP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: źródłowy adres IP
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacyjne 4: Długość pakietu

### <a name="internal-ip-send"></a>Wewnętrzne wysyłanie adresów IP

#### <a name="internal-ip-send"></a>Wewnętrzne wysyłanie adresów IP

**Ikona** ![ Ikona wewnętrznego wysyłania we/wy](./media/user-guide/netx-events/image9.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania adresów IP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: docelowy adres IP
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacyjne 4: Długość pakietu

### <a name="internal-tcp-data-receive"></a>Wewnętrzne odbieranie danych TCP 

#### <a name="internal-tcp-data-receive"></a>Wewnętrzne odbieranie danych TCP

**Ikona** ![ Ikona odbierania danych wewnętrznych T C P](./media/user-guide/netx-events/image10.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania danych TCP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: źródłowy adres IP
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacyjne 4: Numer sekwencji odbioru

### <a name="internal-tcp-data-send"></a>Wewnętrzne wysyłanie danych TCP 

#### <a name="internal-tcp-data-send"></a>Wewnętrzne wysyłanie danych TCP

**Ikona** ![ Ikona wewnętrznego wysyłania danych T C P](./media/user-guide/netx-events/image11.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania danych TCP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacyjne 4: Numer sekwencji przesyłania

### <a name="internal-tcp-fin-receive"></a>Wewnętrzne odbieranie danych FIN protokołu TCP 

#### <a name="internal-tcp-fin-receive"></a>Wewnętrzne odbieranie z fina PROTOKOŁU TCP

**Ikona** ![ Ikona odbierania wewnętrznego T C P F I N](./media/user-guide/netx-events/image12.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania protokołu TCP NETX.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacyjne 4: Numer sekwencji odbioru

### <a name="internal-tcp-fin-send"></a>Wewnętrzne wysyłanie danych FIN protokołu TCP 

#### <a name="internal-tcp-fin-send"></a>Wewnętrzne wysyłanie danych fin protokołu TCP

**Ikona** ![ Ikona wewnętrznego wysyłania T C P F I N](./media/user-guide/netx-events/image13.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu TCP NETX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4:Numer sekwencji przesyłania

### <a name="internal-tcp-rst-receive"></a>Wewnętrzne odbieranie RST protokołu TCP 

#### <a name="internal-tcp-rst-receive"></a>Wewnętrzne odbieranie RST protokołu TCP

**Ikona** ![ Wewnętrzna ikona odbierania T C P R S T](./media/user-guide/netx-events/image14.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania resetowania protokołu TCP NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP.
- Pole informacji 2: wskaźnik do gniazda.
- Pole informacji 3: Wskaźnik do pakietu.
- Pole informacji 4: Odbierz numer sekwencji.

### <a name="internal-tcp-rst-send"></a>Wewnętrzne wysyłanie RST protokołu TCP 

#### <a name="internal-tcp-rst-send"></a>Wewnętrzne wysyłanie RST protokołu TCP

**Ikona** ![ Wewnętrzna ikona wysyłania T C P R S T](./media/user-guide/netx-events/image15.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania resetowania protokołu TCP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacyjne 4: Numer sekwencji przesyłania

### <a name="internal-tcp-syn-receive"></a>Wewnętrzne odbieranie SYN protokołu TCP 

#### <a name="internal-tcp-syn-receive"></a>Wewnętrzne odbieranie protokołu TCP SYN

**Ikona** ![ Wewnętrzna ikona odbierania T C P S Y N](./media/user-guide/netx-events/image16.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania protokołu TCP NETX SYN.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacyjne 4: Numer sekwencji odbioru

### <a name="internal-tcp-syn-send"></a>Wewnętrzne wysyłanie SYN protokołu TCP 

#### <a name="internal-tcp-syn-send"></a>Wewnętrzne wysyłanie protokołu TCP SYN

**Ikona** ![ Wewnętrzna ikona wysyłania T C P S Y N](./media/user-guide/netx-events/image17.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania PROTOKOŁU TCP NETX SYN.

Pola informacji 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number

### <a name="internal-udp-receive"></a>Wewnętrzne odbieranie protokołu UDP 

#### <a name="internal-udp-receive"></a>Wewnętrzne odbieranie protokołu UDP

**Ikona** ![ Ikona odbierania wewnętrznego UD P](./media/user-guide/netx-events/image18.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania protokołu UDP NetX.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4: Wyraz 0 nagłówka UDP

### <a name="internal-udp-send"></a>Wewnętrzne wysyłanie UDP 

#### <a name="internal-udp-send"></a>Wewnętrzne wysyłanie UDP

**Ikona** ![ Ikona wewnętrznego wysyłania UD P](./media/user-guide/netx-events/image19.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu UDP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4: Wyraz 0 nagłówka UDP

### <a name="internal-rarp-receive"></a>Wewnętrzne odbieranie RARP 

#### <a name="internal-rarp-receive"></a>Wewnętrzne odbieranie rarp 

**Ikona** ![ Wewnętrzna ikona odbierania R A R P](./media/user-guide/netx-events/image20.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania RARP NetX.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: docelowy adres IP
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4: wyraz 1 nagłówka RARP

### <a name="internal-rarp-send"></a>Wewnętrzne wysyłanie RARP 

#### <a name="internal-rarp-send"></a>Wewnętrzne wysyłanie RARP 

**Ikona** ![ Wewnętrzna ikona wysyłania R A R P](./media/user-guide/netx-events/image21.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania RARP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: docelowy adres IP
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4: wyraz 1 nagłówka RARP

### <a name="internal-tcp-retry"></a>Wewnętrzne ponawianie próby tcp 

#### <a name="internal-tcp-retry"></a>Wewnętrzne ponawianie próby tcp 

**Ikona** ![ Ikona ponawiania wewnętrznego T C P](./media/user-guide/netx-events/image22.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie ponawiania netx tcp.

**Pola informacji**
- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Pointer to packet (Pole informacji 3: wskaźnik do pakietu)
- Pole informacji 4: Liczba ponownych prób

### <a name="internal-tcp-state-change"></a>Wewnętrzna zmiana stanu TCP 

#### <a name="internal-tcp-state-change"></a>Wewnętrzna zmiana stanu TCP 

**Ikona** ![ Ikona zmiany stanu wewnętrznego T C P](./media/user-guide/netx-events/image23.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie zmiany stanu gniazda TCP NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Pole informacji 3: Poprzedni stan
- Pole informacji 4: Nowy stan

### <a name="internal-io-driver-packet-send"></a>Wewnętrzne wysyłanie pakietów sterowników we/wy 

#### <a name="internal-io-driver-packet-send"></a>Wewnętrzne wysyłanie pakietów sterowników We/Wy

**Ikona** ![ Ikona wysyłania wewnętrznego pakietu sterowników We/Wy](./media/user-guide/netx-events/image24.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania pakietów we/wy wewnętrznego sterownika NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacji 2: wskaźnik do pakietu)
- Pole informacji 3: Rozmiar pakietu
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika We/Wy

**Ikona** ![ Ikona inicjowania wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image25.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania wewnętrznego sterownika We/Wy NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-link-enable"></a>Włączanie linku wewnętrznego sterownika We/Wy 

#### <a name="internal-io-driver-link-enable"></a>Włączanie linku wewnętrznego sterownika We/Wy

**Ikona** ![ Ikona włączania linku wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image26.png)

**Opis**

To zdarzenie reprezentuje zdarzenie włączania linku wewnętrznego sterownika NetX We/Wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-link-disable"></a>Wyłącz link wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-link-disable"></a>Wyłącz link do wewnętrznego sterownika We/Wy

**Ikona** ![ Ikona wyłączania linku wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image27.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wyłączania linku wewnętrznego sterownika NetX We/Wy.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-packet-broadcast"></a>Emisja wewnętrznego pakietu sterowników we/wy 

#### <a name="internal-io-driver-packet-broadcast"></a>Emisja pakietów wewnętrznych sterowników We/Wy

**Ikona** ![ Ikona emisji wewnętrznego pakietu sterowników We/Wy](./media/user-guide/netx-events/image28.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie emisji pakietów we/wy sterownika NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacji 2: wskaźnik do pakietu)
- Pole informacji 3: Rozmiar pakietu
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-arp-send"></a>Wysyłanie ARP wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-arp-send"></a>Wysyłanie ARP wewnętrznego sterownika we/wy

**Ikona** ![ Ikona wysyłania ARP wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image29.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania ARP wewnętrznego sterownika We/Wy NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacji 2: wskaźnik do pakietu)
- Pole informacji 3: Rozmiar pakietu
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-arp-response-send"></a>Wysyłanie odpowiedzi ARP wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-arp-response-send"></a>Wysyłanie odpowiedzi ARP wewnętrznego sterownika we/wy

**Ikona** ![ Ikona wysyłania odpowiedzi ARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image30.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania odpowiedzi ARP wewnętrznego sterownika NetX We/Wy.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacji 2: wskaźnik do pakietu)
- Pole informacji 3: Rozmiar pakietu
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-rarp-send"></a>Wysyłanie RARP wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-rarp-send"></a>Wysyłanie RARP wewnętrznego sterownika we/wy

**Ikona** ![ Ikona wysyłania we/wy sterownika RARP](./media/user-guide/netx-events/image31.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania WE/Wy wewnętrznego sterownika NetX RARP.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacji 2: wskaźnik do pakietu)
- Pole informacji 3: Rozmiar pakietu
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-multicast-join"></a>Sprzężenia multiemisji sterownika wewnętrznego we/wy 

#### <a name="internal-io-driver-multicast-join"></a>Sprzężenia multiemisji sterownika wewnętrznego we/wy

**Ikona** ![ Ikona sprzężenia wieloemisji sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image32.png)

**Opis**

To zdarzenie reprezentuje zdarzenie sprzężenia we/wy wewnętrznego sterownika NetX multiemisji.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-multicast-leave"></a>Pozostawienie wewnętrznego sterownika we/wy do multiemisji 

#### <a name="internal-io-driver-multicast-leave"></a>Pozostawienie wewnętrznego sterownika we/wy do multiemisji

**Ikona** ![ Ikona opuszczania wieloemisji sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image33.png)

**Opis**

To zdarzenie reprezentuje zdarzenie opuszczenia wieloemisji sterownika We/Wy wewnętrznego sterownika NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-get-status"></a>Uzyskiwanie stanu wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-get-status"></a>Uzyskiwanie stanu wewnętrznego sterownika we/wy

**Ikona** ![ Ikona pobierz stan wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image34.png)

**Opis**

To zdarzenie reprezentuje zdarzenie stanu wewnętrznego sterownika We/Wy NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-get-speed"></a>Szybkość pobierania wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-get-speed"></a>Szybkość pobierania wewnętrznego sterownika we/wy

**Ikona** ![ Ikona get speed dla wewnętrznego sterownika We/Wy](./media/user-guide/netx-events/image35.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get speed wewnętrznego sterownika NetX We/Wy.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="internal-io-driver-get-duplex-type"></a>Wewnętrzny sterownik we/wy pobierz typ dwukierunkowy 

#### <a name="internal-io-driver-get-duplex-type"></a>Wewnętrzny sterownik we/wy pobierz typ dwukierunkowy

**Ikona** ![ Wewnętrzny sterownik We/Wy pobierz ikonę typu dwukierunkowego](./media/user-guide/netx-events/image36.png)

**Opis**

To zdarzenie reprezentuje zdarzenie typu dwukierunkowego wewnętrznego sterownika We/Wy NetX.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="internal-io-driver-get-error-count"></a>Liczba błędów get wewnętrznego sterownika we/wy

#### <a name="internal-io-driver-get-error-count"></a>Liczba błędów dla sterownika wewnętrznego we/wy

**Ikona** ![ Ikona liczby błędów dla sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image37.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wewnętrznego sterownika We/Wy NetX get error count.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="internal-io-driver-get-rx-count"></a>Wewnętrzny sterownik we/wy pobierz liczbę rx 

#### <a name="internal-io-driver-get-rx-count"></a>Wewnętrzny sterownik we/wy pobierz liczbę rx

**Ikona** ![ Sterownik wewnętrzny we/wy pobierz ikonę liczby rx](./media/user-guide/netx-events/image38.png)

**Opis**

To zdarzenie reprezentuje wewnętrzny sterownik We/Wy NetX, który ma zdarzenie zliczania rx.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="internal-io-driver-get-tx-count"></a>Wewnętrzny sterownik we/wy pobierz liczbę TX 

#### <a name="internal-io-driver-get-tx-count"></a>Wewnętrzny sterownik we/wy pobierz liczbę TX

**Ikona** ![ Ikona zliczania T X sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image39.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zliczania TX wewnętrznego sterownika We/Wy NetX.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="internal-io-driver-get-allocation-errors"></a>Błędy alokacji wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-get-allocation-errors"></a>Wewnętrzne błędy alokacji sterownika we/wy

**Ikona** ![ Ikona błędów alokacji dla sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image40.png)

**Opis**

To zdarzenie reprezentuje zdarzenie błędów alokacji wewnętrznego sterownika We/Wy NetX.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="internal-io-driver-un-initialize"></a>Cofnie zainicjowanie wewnętrznego sterownika We/Wy 

#### <a name="internal-io-driver-un-initialize"></a>Cofniesz inicjowanie wewnętrznego sterownika We/Wy 

**Ikona** ![ Ikona cofnia inicjowania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image41.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania wewnętrznego sterownika We/Wy NetX.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="internal-io-driver-deferred-processing"></a>Odroczone przetwarzanie sterowników we/wy wewnętrznego 

#### <a name="internal-io-driver-deferred-processing"></a>Odroczone przetwarzanie sterowników we/wy wewnętrznego 

**Ikona** ![ Ikona odroczonego przetwarzania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image42.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wewnętrznego przetwarzania odroczonego sterownika NetX We/Wy.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacyjne 2: wskaźnik do pakietu)
- Pole informacyjne 3: Długość pakietu
- Pole informacji 4: nie jest używane

### <a name="arp-dynamic-entries-invalidate"></a>Unieważnienie wpisów dynamicznych ARP 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**Ikona** ![ Ikona unieważniaj wpisy dynamiczne R P](./media/user-guide/netx-events/image43.png)

**Opis**

To zdarzenie reprezentuje unieważnienie wszystkich dynamicznych całych ARP za pośrednictwem nx_arp_dynamic_entries_invalidate.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Wpisy unieważnione
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="arp-dynamic-entry-set"></a>Dynamiczny zestaw wpisów ARP 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**Ikona** ![ Ikona dynamicznego zestawu wpisów R P](./media/user-guide/netx-events/image44.png)

**Opis**

To zdarzenie reprezentuje ustawienie dynamicznego wpisu ARP za pośrednictwem nx_arp_dynamic_entry_set.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacyjne 2: adres IP
- Pole informacji 3: Adres fizyczny (MSW)
- Pole informacyjne 4: Adres fizyczny (LSW)

### <a name="arp-enable"></a>Włączanie ARP 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**Ikona** ![ Ikona włączania dla komputera R P](./media/user-guide/netx-events/image45.png)

**Opis**

To zdarzenie reprezentuje włączanie ARP za pośrednictwem nx_arp_enable.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: ARP cache memory pointer (Pole informacyjne 2: wskaźnik pamięci podręcznej ARP)
- Pole informacyjne 3: Rozmiar pamięci podręcznej ARP
- Pole informacji 4: nie jest używane

### <a name="arp-gratuitous-send"></a>ARP Wysłać chłaniowa 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**Ikona** ![ Ikona wysyłania nieukońcowego R P](./media/user-guide/netx-events/image46.png)

**Opis**

To zdarzenie reprezentuje niesłabnące wysyłanie ARP za pośrednictwem nx_arp_gratuitous_send.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="arp-hardware-address-find"></a>Znajdowanie adresu sprzętowego ARP 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**Ikona** ![ Ikona Znajdź adres sprzętowy R P](./media/user-guide/netx-events/image47.png)

**Opis**

To zdarzenie reprezentuje znalezienie adresu fizycznego za pośrednictwem nx_arp_hardware_address_find.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP
- Pole informacji 3: Adres fizyczny (MSW)
- Pole informacji 4: Adres fizyczny (LSW)

### <a name="arp-information-get"></a>Uzyskiwanie informacji ORP 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**Ikona** ![ Ikona get informition R P](./media/user-guide/netx-events/image48.png)

**Opis**

To zdarzenie reprezentuje uzyskiwanie informacji za pośrednictwem nx_arp_info_get.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Wysłane APS
- Pole informacji 3: odpowiedzi ARP
- Pole informacji 4: Odebrano APS

### <a name="arp-ip-address-find"></a>Znajdowanie adresu IP usługi ARP 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**Ikona** ![ Ikona znajdź adres R P I P](./media/user-guide/netx-events/image49.png)

**Opis**

To zdarzenie reprezentuje znalezienie adresu IP skojarzonego z dostarczonym adresem fizycznym za pośrednictwem nx_arp_ip_address_find.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP
- Pole informacji 3: Adres fizyczny (MSW)
- Pole informacji 4: Adres fizyczny (LSW)

### <a name="arp-static-entry-create"></a>Tworzenie statycznego wpisu ARP 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**Ikona** ![ Ikona tworzenia statycznego wpisu R P](./media/user-guide/netx-events/image50.png)

**Opis**

To zdarzenie reprezentuje tworzenie statycznego wpisu ARP za pośrednictwem nx_arp_static_entry_create.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP
- Pole informacji 3: Adres fizyczny (MSW)
- Pole informacji 4: Adres fizyczny (LSW)

### <a name="arp-static-entries-delete"></a>Usuwanie statycznych wpisów ARP 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**Ikona** ![ Ikona usuwania statycznych wpisów R P](./media/user-guide/netx-events/image51.png)

**Opis**

To zdarzenie reprezentuje usunięcie wszystkich statycznych wpisów ARP za pośrednictwem nx_arp_static_entries_delete.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Wpisy usunięte
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="arp-static-entry-delete"></a>Usuwanie statycznego wpisu ARP 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**Ikona** ![ Ikona usuwania statycznego wpisu R P](./media/user-guide/netx-events/image52.png)

**Opis**

To zdarzenie reprezentuje usunięcie statycznego wpisu ARP za pośrednictwem nx_arp_static_entry_delete.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP
- Pole informacji 3: Adres fizyczny (MSW)
- Pole informacji 4: Adres fizyczny (LSW)

### <a name="duo-cache-entry-delete"></a>Usuwanie wpisu pamięci podręcznej Duo Cache 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**Ikona** ![ Ikona usuwania wpisu pamięci podręcznej Duo](./media/user-guide/netx-events/image53.png)

**Opis**

To zdarzenie reprezentuje usunięcie wpisu w tabeli pamięci podręcznej sąsiadów za pośrednictwem nx_udp_socket_create.

**Pola informacji** 

- Pole informacji 1: czwarty (najmniej znaczący) wyraz adresu lokalnego linku IPv6 do usunięcia
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="duo-cache-entry-set"></a>Zestaw wpisów pamięci podręcznej Duo 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**Ikona** ![ Ikona zestawu wpisów pamięci podręcznej Duo](./media/user-guide/netx-events/image54.png)

**Opis**

To zdarzenie reprezentuje tworzenie wpisu pamięci podręcznej i dodawanie do tabeli pamięci podręcznej sąsiada za pośrednictwem nxd_nd_cache_entry_set.

**Pola informacji** 

- Pole informacji 1: czwarty (najmniej znaczący) wyraz adresu IPv6 do dodania
- Pole informacji 2: Adres fizyczny msb
- Pole informacji 3: Adres fizyczny lsb
- Pole informacji 4: Nie używane

### <a name="duo-cache-invalidate"></a>Unieważnij pamięć podręczną Duo Cache 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**Ikona** ![ Ikona unieważnień pamięci podręcznej Duo](./media/user-guide/netx-events/image55.png)

**Opis**

To zdarzenie reprezentuje unieważnienie całej tabeli pamięci podręcznej sąsiadów za pośrednictwem nxd_nd_cache_invalidate.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="duo-cache-ip-address-find"></a>Znajdowanie adresu IP pamięci podręcznej Duo 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**Ikona** ![ Ikona znajdź adres I P pamięci podręcznej Duo](./media/user-guide/netx-events/image56.png)

**Opis**

To zdarzenie reprezentuje pobieranie adresu IP pasującego do podanego adresu fizycznego z tabeli pamięci podręcznej za pośrednictwem nxd_nd_cache_ip_address_find.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: czwarty (najmniej znaczący) wyraz adresu IPv6
- Pole informacji 3: Adres fizyczny msb
- Pole informacji 4: Adres fizyczny lsb

### <a name="duo-icmp-enable"></a>Duo ICMP Enable 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**Ikona** ![ Ikona włączania aplikacji Duo I C M P](./media/user-guide/netx-events/image57.png)

**Opis**

To zdarzenie reprezentuje usługi ICMPv4 i ICMPv6 włączone w określonym wystąpieniu adresu IP za pośrednictwem nxd_icmp_enable.

**Pola informacji**
- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="duo-icmp-ping"></a>Duo ICMP Ping 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**Ikona** ![ Ikona ping aplikacji Duo I C M P](./media/user-guide/netx-events/image58.png)

**Opis**

To zdarzenie reprezentuje wysyłanie polecenia ping (żądanie echa) do hosta IPv6 za pośrednictwem nxd_icmp_ping.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IPv6
- Info Field 3: Pointer to echo data (Pole informacji 3: wskaźnik do danych echa)
- Pole informacji 4: Rozmiar danych echa

### <a name="duo-ip-max-payload-size-find"></a>Znajdowanie maksymalnego rozmiaru ładunku adresu IP aplikacji Duo 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**Ikona** ![ Ikona znajdź maksymalny rozmiar ładunku Aplikacji Duo I P](./media/user-guide/netx-events/image59.png)

**Opis**

To zdarzenie oblicza maksymalny ładunek, który określony pakiet może przenosić bez konieczności fragmentacji.

**Pola informacji**

- Info Field 1: Socket pointer (Pole informacji 1: wskaźnik gniazda)
- Pole informacji 2: Adres IP elementu równorzędnego
- Info Field 3: Peer port Info Field 4: Not used

### <a name="duo-ip-raw-packet-send"></a>Nieprzetworzone pakiety IP Duo 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**Ikona** ![ Ikona wysyłania nieprzetworzonych pakietów Duo I P](./media/user-guide/netx-events/image60.png)

**Opis**

To zdarzenie reprezentuje wysyłanie nieprzetworzonych pakietów IP z określonego interfejsu sieciowego do podanego adresu docelowego IPvia nxd_ip_raw_packet_send.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet to send (Wskaźnik do pakietu do wysłania)
- Info Field 3: Pointer to destination address (Pole informacji 3: wskaźnik do adresu docelowego)
- Pole informacji 4: Protokół pakietów

### <a name="duo-ipv6-default-router-add"></a>Dodawanie domyślnego routera IPv6 w aplikacji Duo 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**Ikona** ![ Ikona dodawania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image61.png)

**Opis**

To zdarzenie reprezentuje dodanie domyślnego routera do tabeli routingu IPv6 wystąpienia adresu IP za pośrednictwem nxd_ipv6_default_router_add.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP.
- Pole informacji 2: docelowy adres sieciowy.
- Pole informacji 3: Informacje o czasie życia.
- Pole informacji 4: nie jest używane.

### <a name="duo-ipv6-default-router-delete"></a>Usuwanie domyślnego routera IPv6 duo 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**Ikona** ![ Ikona usuwania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image62.png)

**Opis**

To zdarzenie reprezentuje usunięcie domyślnego routera z tabeli routingu IPv6 wystąpienia adresu IP za pośrednictwem nxd_ipv6_default_router_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP.
- Pole informacji 2: czwarty wyraz (najmniej znaczący) domyślnego adresu IPv6 routera.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="duo-ipv6-enable"></a>Włączanie protokołu IPv6 w aplikacji Duo 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**Ikona** ![ Ikona włączania aplikacji Duo I P v 6](./media/user-guide/netx-events/image63.png)

**Opis**

To zdarzenie reprezentuje włączanie usług IPv6 dla podanego wystąpienia adresu IP za pośrednictwem nxd_ipv6_enable.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="duo-ipv6-global-address-get"></a>Duo IPv6 Global Address Get 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**Ikona** ![ Ikona get adresu globalnego Duo I P v 6](./media/user-guide/netx-events/image64.png)

**Opis**

To zdarzenie reprezentuje pobieranie globalnego (podstawowego) adresu IP w wystąpieniu ip umieszczonym w indeksie 1 w tabeli interfejsu wystąpienia adresu IP za pośrednictwem nxd_ipv6_global_address_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP.
- Pole informacji 2: Czwarte słowo (najmniej znaczące) adresu globalnego
- Pole informacji 3: Długość prefiksu adresu IPv6.
- Pole informacji 4: indeksowanie w tabeli interfejsu IP (1).

### <a name="duo-ipv6-global-address-set"></a>Globalny zestaw adresów IPv6 duo 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**Ikona** ![ Ikona globalnego zestawu adresów Duo I P v 6](./media/user-guide/netx-events/image65.png)

**Opis**

To zdarzenie reprezentuje ustawienie globalnego (podstawowego) adresu IP w wystąpieniu ip umieszczonym w indeksie 1 w tabeli interfejsu wystąpienia adresu IP za pośrednictwem nxd_ipv6_global_address_set.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Czwarte słowo (najmniej znaczące) adresu globalnego
- Pole informacji 3: Długość prefiksu adresu IPv6
- Pole informacji 4: indeksowanie w tabeli interfejsu IP (1)

### <a name="duo-ipv6-initiate-dad-process"></a>Proces inicjowania protokołu IPv6 aplikacji Duo 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**Ikona** ![ Ikona procesu inicjowania aplikacji Duo I P v 6](./media/user-guide/netx-events/image66.png)

**Opis**

To zdarzenie reprezentuje początek procesu wykrywania zduplikowanych adresów (ETHERNET, Duplicate Address Detection) po przypisaniu do wystąpienia adresu IP lokalnego linku lub adresu interfejsu IP za pośrednictwem nxd_ipv6_initiate_dad_process.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="duo-ipv6-interface-address-get"></a>Uzyskiwanie adresu interfejsu IPv6 aplikacji Duo 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**Ikona** ![ Ikona get adresu interfejsu Duo I P v 6](./media/user-guide/netx-events/image67.png)

**Opis**

To zdarzenie reprezentuje pobieranie adresu IP i prefiksu z określonego indeksu do tabeli adresów interfejsu wystąpienia IP za pośrednictwem nxd_ipv6_interface_address_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacyjne 2: Czwarty wyraz (najmniej znaczący) adresu IPv6 do zwrócenia
- Info Field 4: Index of interface into the IP instance interface table (Pole informacyjne 4: indeks interfejsu w tabeli interfejsu wystąpienia adresu IP)

### <a name="duo-ipv6-interface-address-set"></a>Zestaw adresów interfejsu IPv6 aplikacji Duo 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**Ikona** ![ Duo I P v 6 interface addresss et icon (Adresi interfejsu i ikona interfejsu Duo I P v 6)](./media/user-guide/netx-events/image68.png)

**Opis**

To zdarzenie reprezentuje ustawienie adresu IP i prefiksu w określonym indeksie w tabeli adresów interfejsu wystąpienia IP. Niedozwolone w indeksie zero (adres lokalny linku) za pośrednictwem nxd_ipv6_interface_address_set.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacyjne 2: Czwarty wyraz (najmniej znaczący) adresu IPv6 do zwrócenia
- Pole informacyjne 3: Długość prefiksu
- Info Field 4: Index of interface into the IP instance interface table (Pole informacyjne 4: indeks interfejsu w tabeli interfejsu wystąpienia adresu IP)

### <a name="duo-ipv6-link-local-address-get"></a>Pobierz adres lokalny połączenia iPv6 aplikacji Duo 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**Ikona** ![ Ikona pobierz adres lokalny linku Duo I P v 6](./media/user-guide/netx-events/image69.png)

**Opis**

To zdarzenie reprezentuje pobieranie lokalnego adresu linku określonego wystąpienia adresu IP za pośrednictwem nxd_ipv6_linklocal_address_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Czwarty wyraz (najmniej znaczący) adresu lokalnego linku IP w wersji 6
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="duo-ipv6-link-local-address-set"></a>Zestaw adresów lokalnych połączenia IPv6 aplikacji Duo 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**Ikona** ![ Ikona zestawu adresów lokalnych połączenia Duo I P v 6](./media/user-guide/netx-events/image70.png)

**Opis**

To zdarzenie reprezentuje ustawienie lokalnego adresu linku wystąpienia adresu IP za pośrednictwem nxd_ipv6_linklocal_address_set.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacyjne 2: czwarty (najmniej znaczący) wyraz adresu lokalnego linku IPv6
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="duo-ipv6-raw-packet-send"></a>Wysyłaj nieprzetworzone pakiety IPv6 aplikacji Duo 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**Ikona** ![ Ikona wysyłania nieprzetworzonych pakietów Duo I P v 6](./media/user-guide/netx-events/image71.png)

**Opis**

To zdarzenie reprezentuje wysyłanie nieprzetworzonych pakietów IP za pośrednictwem podstawowego interfejsu IP do miejsca docelowego za pośrednictwem nxd_ip_raw_packet_send.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet to send (Pole informacyjne 2: wskaźnik do pakietu do wysłania)
- Pole informacji 3: docelowy adres IP
- Pole informacji 4: nie jest używane

### <a name="duo-tcp-socket-peer-info-get"></a>Pobierz informacje o węzłochach równorzędnych gniazda TCP Duo 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**Ikona** ![ Ikona pobierz informacje o gnieździe gniazda Duo T C P](./media/user-guide/netx-events/image72.png)

**Opis**

To zdarzenie wyodrębnia dane nadawcy z odebranego pakietu TCP na określonym gnieździe. Zwraca adres IP i port nadawcy.

**Pola informacji**

- Info Field 1: Socket pointer (Pole informacyjne 1: wskaźnik gniazda)
- Pole informacji 2: Adres IP elementu równorzędnego
- Info Field 3: Peer port (Pole informacji 3: port elementu równorzędnego)
- Pole informacji 4: znacząca dzierżawa 32-bitowego adresu IP

### <a name="duo-tcp-socket-set-interface"></a>Interfejs zestawu gniazd TCP Duo 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**Ikona** ![ Ikona interfejsu zestawu gniazd Duo T C P](./media/user-guide/netx-events/image73.png)

**Opis**

To zdarzenie reprezentuje ustawienie interfejsu gniazda wychodzącego, gdy klient łączy się z serwerem TCP na określonym adresie IP serwera za pośrednictwem nxd_tcp_client_socket_connect.

**Pola informacji** 

- Info Field 1: Pointer to TCP Socket
- Pole informacji 2: Identyfikator interfejsu
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="duo-udp-socket-send"></a>Duo UDP Socket Send 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**Ikona** ![ Ikona wysyłania gniazda Duo U D P](./media/user-guide/netx-events/image74.png)

**Opis**

To zdarzenie reprezentuje wysyłanie pakietu UDP za pośrednictwem określonego gniazda z wejściowym adresem IP i portem za pośrednictwem nxd_udp_socket_send.

**Pola informacji** 

- Info Field 1: Pointer UDP Socket
- Info Field 2: Pointer to UDP packet (Pole informacyjne 2: wskaźnik do pakietu UDP)
- Pole informacyjne 3: Długość pakietu
- Pole informacji 4: nie jest używane


### <a name="duo-udp-socket-set-interface"></a>Interfejs zestawu gniazd UDP firmy Duo 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**Ikona** ![ Ikona interfejsu zestawu gniazd Duo U D P](./media/user-guide/netx-events/image75.png)

**Opis**

To zdarzenie reprezentuje ustawienie określonego interfejsu wychodzącego gniazda UDP na interfejs odpowiadający identyfikatorowi interfejsu wejściowego za pośrednictwem nxd_udp_socket_set_interface.

**Pola informacji** 

- Info Field 1: Pointer to UDP Socket
- Pole informacji 2: Identyfikator interfejsu
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="duo-udp-source-extract"></a>Wyodrębnianie źródła UDP firmy Duo 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**Ikona** ![ Ikona wyodrębniania źródła aplikacji Duo U D P](./media/user-guide/netx-events/image76.png)

**Opis**

To zdarzenie reprezentuje wyodrębnianie adresu IP i portu źródłowego odebranego pakietu (IPv4 lub IPv6). W przypadku protokołu IPv6 czwarty wyraz (najmniej znaczący) adresu IP jest zwracany za pośrednictwem nxd_udp_source_extract.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do pakietu
- Pole informacyjne 2: wersja adresu IP
- Pole informacji 3: źródłowy adres IP (IPv4 lub IPv6)
- Pole informacji 4: port źródłowy

### <a name="icmp-enable"></a>Włączanie ICMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikona** ![ Ikona włączania aplikacji I C M P](./media/user-guide/netx-events/image77.png)

**Opis**

To zdarzenie reprezentuje włączanie ICMP za pośrednictwem nx_icmp_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP l;
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="icmp-information-get"></a>Uzyskiwanie informacji OCMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikona** ![ Ikona pobierz informacje o języku C M P](./media/user-guide/netx-events/image78.png)

**Opis**

To zdarzenie reprezentuje uzyskiwanie informacji za pośrednictwem nx_icmp_info_get.

**Pola informacji**
- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Wysłane polecenia ping
- Pole informacji 3: Odpowiedzi ping
- Pole informacji 4: Odebrano polecenia ping

### <a name="icmp-ping"></a>ICMP Ping 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**Ikona** ![ Ikona ping I C M P](./media/user-guide/netx-events/image79.png)

**Opis**

To zdarzenie reprezentuje polecenie ping dla docelowego adresu IP za pośrednictwem nx_icmp_ping.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP
- Info Field 3: Pointer to data (Pole informacji 3: wskaźnik do danych)
- Info Field 4: Size of data (Pole informacji 4: rozmiar danych)

### <a name="igmp-enable"></a>Włączanie IGMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikona** ![ Ikona włączania aplikacji I G M P](./media/user-guide/netx-events/image80.png)

**Opis**

To zdarzenie reprezentuje włączanie IGMP za pośrednictwem nx_igmp_enable.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="igmp-information-get"></a>Uzyskiwanie informacji OGMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikona** ![ Ikona pobierz informacje o aplikacji I G M P](./media/user-guide/netx-events/image81.png)

**Opis**

To zdarzenie reprezentuje uzyskiwanie informacji za pośrednictwem nx_igmp_info_get.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Wysłane raporty
- Pole informacji 3: Odebrane zapytania
- Pole informacji 4: Grupy przyłączone

### <a name="igmp-loopback-disable"></a>Wyłączanie sprzężenia zwrotnego IGMP 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**Ikona** ![ Ikona wyłączania sprzężenia zwrotnego sprzężenia zwrotnego I G M](./media/user-guide/netx-events/image82.png)

**Opis**

To zdarzenie reprezentuje wyłączenie sprzężenia zwrotnego IGMP za pośrednictwem nx_igmp_loopback_disable.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="igmp-loopback-enable"></a>Włączanie sprzężenia zwrotnego IGMP 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**Ikona** ![ Ikona włączania sprzężenia zwrotnego sprzężenia zwrotnego I G M](./media/user-guide/netx-events/image83.png)

**Opis**

To zdarzenie reprezentuje włączanie sprzężenia zwrotnego IGMP za pośrednictwem nx_igmp_loopback_enable.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="igmp-multicast-join"></a>Sprzężenia multiemisji IGMP 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**Ikona** ![ Ikona dołączania do multiemisji I G M P](./media/user-guide/netx-events/image84.png)

**Opis**

To zdarzenie reprezentuje dołączenie do grupy multiemisji za pośrednictwem nx_igmp_multicast_join.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP grupy
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="igmp-multicast-leave"></a>Pozostawienie multiemisji IGMP 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**Ikona** ![ Ikona opuszczania multiemisji I G M P](./media/user-guide/netx-events/image85.png)

**Opis**

To zdarzenie reprezentuje opuszczenie grupy multiemisji za pośrednictwem nx_igmp_multicast_leave.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP grupy
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-address-change-notify"></a>Powiadomienie o zmianie adresu IP 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**Ikona** ![ Ikona powiadamiania o zmianie adresu IP](./media/user-guide/netx-events/image86.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie w celu powiadamiania o zmianie adresu IP za pośrednictwem nx_ip_address_change_notify.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Callback function pointer (Pole informacji 2: wskaźnik funkcji wywołania zwrotnego)
- Info Field 3: Additional information pointer (Pole informacyjne 3: dodatkowy wskaźnik informacji)
- Pole informacji 4: Nie używane

### <a name="ip-address-get"></a>Uzyskiwanie adresu IP 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**Ikona** ![ Ikona pobierz adres IP](./media/user-guide/netx-events/image87.png)

**Opis**

To zdarzenie reprezentuje uzyskanie adresu IP za pośrednictwem nx_ip_address_get.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacyjne 2: adres IP
- Pole informacyjne 3: Maska sieci
- Pole informacji 4: Nie używane

### <a name="ip-address-set"></a>Zestaw adresów IP 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**Ikona** ![ Ikona zestawu adresów IP](./media/user-guide/netx-events/image88.png)

**Opis**

To zdarzenie reprezentuje ustawienie adresu IP za pośrednictwem nx_ip_address_set.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacyjne 2: adres IP
- Pole informacyjne 3: Maska sieci
- Pole informacji 4: Nie używane

### <a name="ip-create"></a>Tworzenie adresu IP 

#### <a name="nx_ip_create"></a>nx_ip_create

**Ikona** ![ Ikona tworzenia we/wy](./media/user-guide/netx-events/image89.png)

**Opis**

To zdarzenie reprezentuje tworzenie wystąpienia adresu IP za pośrednictwem nx_ip_create.

**Pola informacji** 
- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacyjne 2: adres IP
- Pole informacyjne 3: Maska sieci
- Info Field 4: Default packet pool pointer (Pole informacyjne 4: domyślny wskaźnik puli pakietów)

### <a name="ip-delete"></a>Usuwanie adresu IP 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**Ikona** ![ Ikona usuwania I P](./media/user-guide/netx-events/image90.png)

**Opis**

To zdarzenie reprezentuje usunięcie wystąpienia adresu IP za pośrednictwem nx_ip_delete.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-driver-direct-command"></a>Bezpośrednie polecenie sterownika IP 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**Ikona** ![ Ikona bezpośredniego polecenia sterownika I P](./media/user-guide/netx-events/image91.png)

**Opis**

To zdarzenie reprezentuje bezpośrednie polecenie sterownika We/Wy za pośrednictwem nx_ip_driver_direct_command.

**Pola informacji** 

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Driver Command (Pole informacji 2: sterownik)
- Info Field 3: Return value (Pole informacji 3: wartość zwracana)
- Pole informacji 4: Nie używane

### <a name="ip-forwarding-disable"></a>Wyłączanie przekazywania IP 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**Ikona** ![ Ikona wyłączania przekazywania I P](./media/user-guide/netx-events/image92.png)

**Opis**

To zdarzenie reprezentuje wyłączenie przekazywania IP za pośrednictwem nx_ip_forwarding_disable.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-forwarding-enable"></a>Włączanie przekazywania IP 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**Ikona** ![ Ikona włączania przekazywania I P](./media/user-guide/netx-events/image93.png)

**Opis**

To zdarzenie reprezentuje włączanie przekazywania IP za pośrednictwem nx_ip_forwarding_enable.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-fragment-disable"></a>Wyłączanie fragmentu adresu IP 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**Ikona** ![ Ikona wyłączania fragmentu I P](./media/user-guide/netx-events/image94.png)

**Opis**

To zdarzenie reprezentuje wyłączenie fragmentowania adresów IP za pośrednictwem nx_ip_fragment_disable.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-fragment-enable"></a>Włączanie fragmentu adresu IP 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**Ikona** ![ Ikona włączania fragmentu IP](./media/user-guide/netx-events/image95.png)

**Opis**

To zdarzenie reprezentuje włączanie fragmentowania adresów IP za pośrednictwem nx_ip_fragment_enable.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-gateway-address-set"></a>Zestaw adresów bramy IP 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**Ikona** ![ Ikona zestawu adresów bramy IP](./media/user-guide/netx-events/image96.png)

**Opis**

To zdarzenie reprezentuje ustawienie adresu IP bramy za pośrednictwem nx_ip_gateway_address_set.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacyjne 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Gateway IP address (Pole informacyjne 2: adres IP bramy)
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-information-get"></a>Uzyskiwanie informacji o adresie IP 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**Ikona** ![ Ikona uzyskiwanie informacji o P](./media/user-guide/netx-events/image97.png)

**Opis** To zdarzenie reprezentuje uzyskiwanie informacji o adresie IP za pośrednictwem nx_ip_info_get.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: wysłane bajty IP
- Pole informacji 3: odebrane bajty IP
- Pole informacji 4: porzucone pakiety IP

### <a name="ip-interface-attach"></a>Dołączanie interfejsu IP 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**Ikona** ![ Ikona dołączania iterface I P](./media/user-guide/netx-events/image98.png)

**Opis**

To zdarzenie reprezentuje pomocniczy interfejs sieciowy dołączony do wystąpienia adresu IP za pośrednictwem nx_ip_interface_attach.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP interfejsu
- Pole informacji 3: indeksowanie w tabeli interfejsu IP
- Pole informacji 4: Nie używane

### <a name="ip-interface-info-get"></a>Uzyskiwanie informacji o interfejsie IP 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**Ikona** ![ Ikona pobierz informacje o interfejsie IP](./media/user-guide/netx-events/image99.png)

**Opis**

To zdarzenie reprezentuje informacje pobrane z określonego interfejsu sieciowego za pośrednictwem nx_ip_interface_info_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: adres IP interfejsu
- Pole informacji 3: adres MAC interfejsu msb
- Pole informacji 4: adres MAC interfejsu lsb

### <a name="ip-raw-packet-disable"></a>Wyłącz nieprzetworzonych pakietów IP 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**Ikona** ![ Ikona wyłączania nieprzetworzonych pakietów I P](./media/user-guide/netx-events/image100.png)

**Opis**

To zdarzenie reprezentuje wyłączenie pierwotnej komunikacji pakietów IP za pośrednictwem nx_ip_raw_packet_disable.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-raw-packet-enable"></a>Włączanie nieprzetworzonych pakietów IP 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**Ikona** ![ Ikona włączania nieprzetworzonych pakietów I P](./media/user-guide/netx-events/image101.png)

**Opis**

To zdarzenie reprezentuje włączanie pierwotnej komunikacji pakietów IP za pośrednictwem nx_ip_raw_packet_enable.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="ip-raw-packet-receive"></a>Odbieranie nieprzetworzonych pakietów IP 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**Ikona** ![ Ikona odbierania nieprzetworzonych pakietów I P](./media/user-guide/netx-events/image102.png)

**Opis**

To zdarzenie reprezentuje odbieranie nieprzetworzonych pakietów IP za pośrednictwem nx_ip_raw_packet_receive.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacji 2: wskaźnik do pakietu)
- Pole informacji 3: opcja oczekiwania
- Pole informacji 4: Nie używane

### <a name="ip-raw-packet-send"></a>Wysyłanie nieprzetworzonych pakietów IP 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**Ikona** ![ Ikona wysyłania nieprzetworzonych pakietów I P](./media/user-guide/netx-events/image103.png)

**Opis**

To zdarzenie reprezentuje wysyłanie nieprzetworzonych pakietów IP za pośrednictwem nx_ip_raw_packet_send.

**Pola informacji**

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to packet (Pole informacji 2: wskaźnik do pakietu)
- Pole informacji 3: docelowy adres IP
- Info Field 4: Type of service (Pole informacji 4: typ usługi)

### <a name="ip-static-route-add"></a>Dodawanie statycznej trasy IP 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**Ikona** ![ Ikona dodawania trasy statycznej I P](./media/user-guide/netx-events/image104.png)

**Opis**

To zdarzenie reprezentuje trasę statyczną, która jest dodawana do tabeli routingu wystąpienia adresu IP za pośrednictwem nx_ip_static_route_add.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Adres sieciowy
- Pole informacji 3: Maska sieci
- Pole informacji 4: Następny przeskok

### <a name="ip-static-route-delete"></a>Usuwanie tras statycznych adresów IP 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**Ikona** ![ Ikona usuwania statycznej trasy trasy I P](./media/user-guide/netx-events/image105.png)

**Opis**

To zdarzenie reprezentuje trasę statyczną usuwaną z tabeli routingu wystąpienia adresu IP za pośrednictwem nx_ip_static_route_delete.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Adres sieciowy
- Pole informacji 3: Maska sieci
- Pole informacji 4: Nie używane

### <a name="ip-status-check"></a>Sprawdzanie stanu adresu IP 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**Ikona** ![ Ikona sprawdzania stanu we/wy](./media/user-guide/netx-events/image106.png)

**Opis**

To zdarzenie reprezentuje sprawdzanie stanu adresu IP za pośrednictwem nx_ip_status_check.

Pola informacji 

- Info Field 1: Pointer to the IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Żądany stan
- Pole informacji 3: Stan rzeczywisty
- Pole informacji 4: opcja oczekiwania

### <a name="ipsec-enable"></a>Włączanie protokołu IPSEC 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**Ikona** ![ Ikona włączania aplikacji I P S E C](./media/user-guide/netx-events/image107.png)

**Opis**

To zdarzenie reprezentuje włączanie usług IPSec dla podanego wystąpienia adresu IP za pośrednictwem nx_ipsec_enable.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="packet-allocate"></a>Przydzielanie pakietów 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**Ikona** ![ Ikona przydzielania pakietów](./media/user-guide/netx-events/image108.png)

**Opis**

To zdarzenie reprezentuje przydzielanie pakietu za pośrednictwem nx_packet_allocate.

**Pola informacji**

- Info Field 1: Pointer to the packet pool (Pole informacji 1: wskaźnik do puli pakietów)
- Info Field 2: Pointer to packet allocated (Pole informacji 2: wskaźnik do przydzielonych pakietów)
- Pole informacji 3: Typ pakietu
- Pole informacji 4: Dostępne pakiety

### <a name="packet-copy"></a>Kopiowanie pakietów 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**Ikona** ![ Ikona cpy pakietu](./media/user-guide/netx-events/image109.png)

**Opis**

To zdarzenie reprezentuje kopiowanie pakietu za pośrednictwem nx_packet_copy.

**Pola informacji**

- Info Field 2: New packet pointer (Pole informacyjne 2: nowy wskaźnik pakietów)
- Info Field 3: Pointer to packet pool (Pole informacji 3: wskaźnik do puli pakietów)
- Pole informacji 4: opcja oczekiwania

### <a name="packet-data-append"></a>Dołączanie danych pakietów 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**Ikona** ![ Ikona dołączania danych pakietu](./media/user-guide/netx-events/image110.png)

**Opis**

To zdarzenie reprezentuje dołączanie danych do pakietu za pośrednictwem nx_packet_data_append.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Info Field 2: Pointer to data (Pole informacji 2: wskaźnik do danych)
- Info Field 3: Size of data (Pole informacji 3: rozmiar danych)
- Info Field 4: Pointer to packet pool (Pole informacji 4: wskaźnik do puli pakietów)

### <a name="packet-data-extract-offset"></a>Przesunięcie wyodrębniania danych pakietów 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**Ikona** ![ Ikona przesunięcia wyodrębniania danych pakietu](./media/user-guide/netx-events/image111.png)

**Opis**

To zdarzenie reprezentuje dane pakietu wyodrębnione do dostarczonego buforu z pakietu za pośrednictwem nx_udp_source_extract_offset.

**Pola informacji**

- Info Field 1: Pointer to packet (Pole informacji 1: wskaźnik do pakietu)
- Pole informacji 2: rozmiar określonego buforu
- Pole informacji 3: liczba skopiowanych bajtów
- Pole informacji 4: Nie używane

### <a name="packet-data-retrieve"></a>Pobieranie danych pakietów 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**Ikona** ![ Ikona pobierania danych pakietów](./media/user-guide/netx-events/image112.png)

**Opis**

To zdarzenie reprezentuje pobieranie danych z pakietu za pośrednictwem nx_packet_data_retrieve.

**Pola informacji** 

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: Wskaźnik do rozpoczęcia buforu
- Pole informacji 3: skopiowane bajty
- Pole informacji 4: Nie używane

### <a name="packet-length-get"></a>Uzyskiwanie długości pakietu 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**Ikona** ![ Ikona pobierz długość pakietu](./media/user-guide/netx-events/image113.png)

**Opis**

To zdarzenie reprezentuje pobieranie długości pakietu za pośrednictwem nx_packet_length_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacyjne 2: Długość pakietu
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="packet-pool-create"></a>Tworzenie puli pakietów 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**Ikona** ![ Ikona tworzenia puli pakietów](./media/user-guide/netx-events/image114.png)

**Opis**

To zdarzenie reprezentuje tworzenie puli pakietów za pośrednictwem nx_packet_pool_create.

**Pola informacji** 

- Info Field 1: Pointer to the packet pool (Pole informacji 1: wskaźnik do puli pakietów)
- Pole informacyjne 2: Rozmiar ładunku pakietu
- Info Field 3: Pointer to pool memory area (Pole informacji 3: wskaźnik do obszaru pamięci puli)
- Pole informacji 4: Rozmiar obszaru pamięci puli

### <a name="packet-pool-delete"></a>Usuwanie puli pakietów 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**Ikona** ![ Ikona usuwania puli pakietów](./media/user-guide/netx-events/image115.png)

**Opis**

To zdarzenie reprezentuje usunięcie puli pakietów za pośrednictwem nx_packet_pool_delete.

**Pola informacji** 

- Info Field 1: Pointer to the packet pool (Pole informacji 1: wskaźnik do puli pakietów)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

#### <a name="packet-pool-information-get"></a>Uzyskiwanie informacji o puli pakietów 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**Ikona** ![ Ikona pobierz informacje o puli pakietów](./media/user-guide/netx-events/image116.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o puli pakietów za pośrednictwem nx_packet_pool_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do puli pakietów
- Pole informacji 2: Łączna liczba pakietów
- Pole informacji 3: Dostępne pakiety
- Pole informacji 4: Puste żądania

### <a name="packet-release"></a>Wydanie pakietu 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**Ikona** ![ Ikona wydania pakietu](./media/user-guide/netx-events/image117.png)

**Opis**

To zdarzenie reprezentuje wydanie pakietu za pośrednictwem nx_packet_release.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: Stan pakietu
- Pole informacji 3: Dostępne pakiety
- Pole informacji 4: Nie używane

### <a name="packet-transmit-release"></a>Wydanie przekazywania pakietów 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**Ikona** ![ Ikona wydania przekazywania pakietów](./media/user-guide/netx-events/image118.png)

**Opis**

To zdarzenie reprezentuje wydanie pakietu transmisji za pośrednictwem nx_packet_transmit_release.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: Stan pakietu
- Pole informacji 3: Dostępne pakiety
- Pole informacji 4: Nie używane

### <a name="rarp-disable"></a>Wyłączanie rarp 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**Ikona** ![ Ikona wyłączania plików R A R P](./media/user-guide/netx-events/image119.png)

**Opis**

To zdarzenie reprezentuje wyłączenie funkcji RARP za pośrednictwem nx_rarp_disable.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="rarp-enable"></a>Włączanie rarp 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**Ikona** ![ Ikona włączania R A R P](./media/user-guide/netx-events/image120.png)

**Opis**

To zdarzenie reprezentuje włączanie rarp za pośrednictwem nx_rarp_enable.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="rarp-information-get"></a>Uzyskiwanie informacji RARP 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**Ikona** ![ Ikona pobierz informacje o R A R P](./media/user-guide/netx-events/image121.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji RARP za pośrednictwem nx_rarp_info_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Wysłane żądania
- Pole informacji 3: Odebrane odpowiedzi
- Pole informacji 4: Nieprawidłowe odpowiedzi

### <a name="system-initialize"></a>Inicjowanie systemu 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**Ikona** ![ Ikona inicjowania systemu](./media/user-guide/netx-events/image122.png)

**Opis**

To zdarzenie reprezentuje inicjowanie netx za pośrednictwem nx_system_initialize.

**Pola informacji**

- Pole informacji 1: Nie używane
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="tcp-client-socket-bind"></a>Powiązanie gniazda klienta TCP 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**Ikona** ![ Ikona powiązania gniazda klienta T P](./media/user-guide/netx-events/image123.png)

**Opis**

To zdarzenie reprezentuje powiązanie gniazda klienta z portem za pośrednictwem nx_tcp_client_socket_bind.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Pole informacji 3: Żądany port
- Pole informacji 4: opcja oczekiwania

### <a name="tcp-client-socket-connect"></a>Gniazda klienta TCP Połączenie 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**Ikona** ![ Ikona połączenia gniazda klienta T C P](./media/user-guide/netx-events/image124.png)

**Opis**

To zdarzenie reprezentuje tworzenie połączenia gniazda klienta za pośrednictwem nx_tcp_client_socket_connect.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Pole informacji 3: adres IP serwera
- Pole informacji 4: Żądany port serwera

### <a name="tcp-client-socket-port-get"></a>Uzyskiwanie portu gniazda klienta TCP 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**Ikona** ![ Ikona get portu gniazda klienta T C P](./media/user-guide/netx-events/image125.png)

**Opis**

To zdarzenie reprezentuje pobieranie numeru portu gniazda klienta za pośrednictwem nx_tcp_client_socket_port_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Pole informacji 3: numer portu
- Pole informacji 4: Nie używane

### <a name="tcp-client-socket-unbind"></a>Odłączone gniazdo klienta TCP 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**Ikona** ![ Ikona bez powiązywu gniazda klienta T C P](./media/user-guide/netx-events/image126.png)

**Opis**

To zdarzenie reprezentuje odłączenie portu skojarzonego z gniazdem za pośrednictwem nx_tcp_client_socket_unbind.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="tcp-enable"></a>Włączanie protokołu TCP 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**Ikona** ![ Ikona włączania języka T C P](./media/user-guide/netx-events/image127.png)

**Opis**

To zdarzenie reprezentuje włączanie protokołu TCP za pośrednictwem nx_tcp_enable.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>Znajdowanie wolnego portu TCP w celu znalezienia wolnego portu TCP 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**Ikona** ![ Ikona znajdowanie bezpłatnego portu T CP](./media/user-guide/netx-events/image128.png)

**Opis**

To zdarzenie reprezentuje znalezienie wolnego portu TCP za pośrednictwem nx_tcp_free_port_find.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Początkowy numer portu wyszukiwania
- Info Field 3: Free port number (Pole informacji 3: bezpłatny numer portu)
- Pole informacji 4: Nie używane

###  <a name="tcp-infomation-get"></a>Uzyskiwanie informacji o protokole TCP 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**Ikona** ![ Ikona pobierz informacje t C P](./media/user-guide/netx-events/image129.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji TCP dla określonego wystąpienia adresu IP za pośrednictwem nx_tcp_info_get.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: liczba wysłanych bajtów
- Pole informacji 3: liczba odebranych bajtów
- Pole informacji 4: Liczba nieprawidłowych pakietów

###  <a name="tcp-server-socket-accept"></a>Akceptowanie gniazda serwera TCP 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**Ikona** ![ Ikona akceptowania gniazda serwera T C P](./media/user-guide/netx-events/image130.png)

**Opis**

To zdarzenie reprezentuje konfigurowanie gniazda serwera po otrzymaniu aktywnego żądania połączenia za pośrednictwem nx_tcp_server_socket_accept.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Pole informacji 3: opcja oczekiwania
- Pole informacji 4: stan gniazda

###  <a name="tcp-server-socket-listen"></a>Nasłuchiwać gniazd serwera TCP 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**Ikona** ![ Ikona gniazda serwera T C P](./media/user-guide/netx-events/image131.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie żądania nasłuchiania i gniazda serwera dla określonego portu TCP za pośrednictwem nx_tcp_server_socket_listen.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: numer portu TCP
- Info Field 3: Pointer to socket (Pole informacji 3: wskaźnik do gniazda)
- Pole informacji 4: Maksymalna liczba połączeń, które można dodać do kolejki

###  <a name="tcp-server-socket-relisten"></a>Relikt gniazda serwera TCP 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**Ikona** ![ Ikona reliktu gniazda serwera T C P](./media/user-guide/netx-events/image132.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie innego gniazda serwera dla istniejącego żądania nasłuchiwać na określonym porcie TCP za pośrednictwem nx_tcp_server_socket_relisten.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: numer portu TCP
- Info Field 3: Pointer to socket (Pole informacji 3: wskaźnik do gniazda)
- Pole informacji 4: stan gniazda

###  <a name="tcp-server-socket-unaccept"></a>Nieakceptuj gniazda serwera TCP 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**Ikona** ![ Ikona nieakceptywu gniazda serwera T C P](./media/user-guide/netx-events/image133.png)

**Opis**

To zdarzenie reprezentuje usunięcie gniazda serwera z skojarzenia z portem odbierający wcześniejsze połączenie pasywne za pośrednictwem nx_tcp_server_socket_unaccept.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Pole informacji 3: stan gniazda
- Pole informacji 4: Nie używane

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>TCP Server Socket Unlisten TCP Server Socket Unlisten 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**Ikona** ![ Ikona unlisten gniazda serwera T C P](./media/user-guide/netx-events/image134.png)

**Opis**

To zdarzenie reprezentuje usunięcie poprzedniego żądania nasłuchiwać dla określonego portu TCP za pośrednictwem nx_tcp_server_socket_unlisten.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: numer portu TCP
- Pole informacji 3: Nie używane
- Pole informacji 4: Nie używane

### <a name="tcp-socket-bytes-available"></a>Liczba dostępnych bajtów gniazd TCP 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**Ikona** ![ Ikona dostępnych bajtów gniazda T C P](./media/user-guide/netx-events/image135.png)

**Opis**

To zdarzenie reprezentuje liczbę bajtów obecnie dostępnych na określonym gnieździe odbierających TCP za pośrednictwem nx_tcp_socket_bytes_available.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to TCP socket (Pole informacji 2: wskaźnik do gniazda TCP)
- Pole informacji 3: bajty odebrane na gnieździe
- Pole informacji 4: Nie używane

### <a name="tcp-socket-create"></a>Tworzenie gniazda TCP 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**Ikona** ![ Ikona tworzenia gniazda T C P](./media/user-guide/netx-events/image136.png)

**Opis**

To zdarzenie reprezentuje tworzenie gniazda TCP za pośrednictwem nx_tcp_socket_create.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacji 2: wskaźnik do gniazda)
- Info Field 3: Type of service (Pole informacji 3: typ usługi)
- Pole informacji 4: rozmiar okna odbierania

### <a name="tcp-socket-delete"></a>Usuwanie gniazda TCP 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**Ikona** ![ Ikona usuwania gniazda T C P](./media/user-guide/netx-events/image137.png)

**Opis**

To zdarzenie reprezentuje usunięcie gniazda za pośrednictwem nx_tcp_socket_delete.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Socket state (Pole informacyjne 3: stan gniazda)
- Pole informacji 4: Nie używane

### <a name="tcp-socket-disconnect"></a>Rozłączanie gniazda TCP 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**Ikona** ![ Ikona rozłączania gniazda T C P](./media/user-guide/netx-events/image138.png)

**Opis**

To zdarzenie reprezentuje rozłączenie gniazda za pośrednictwem nx_tcp_socket_disconnect.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Pole informacji 3: Opcja oczekiwania
- Info Field 4: Socket state (Pole informacyjne 4: stan gniazda)

### <a name="tcp-socket-information-get"></a>Uzyskiwanie informacji o gniazdach TCP 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**Ikona** ![ Ikona pobierz informacje o gnieździe T C P](./media/user-guide/netx-events/image139.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o gnieździe za pośrednictwem nx_tcp_socket_info_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Pole informacyjne 3: bajty wysyłane przez to gniazdo
- Pole informacji 4: bajty odebrane za pośrednictwem tego gniazda

### <a name="tcp-socket-mss-get"></a>TCP Socket MSS Get 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**Ikona** ![ Ikona get T C P socket M S S](./media/user-guide/netx-events/image140.png)

**Opis**

To zdarzenie reprezentuje pobieranie usługi MSS gniazda za pośrednictwem nx_tcp_socket_mss_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Pole informacyjne 3: maksymalny rozmiar segmentu (MSS)
- Info Field 4: Socket state (Pole informacyjne 4: stan gniazda)

### <a name="tcp-socket-mss-peer-get"></a>TCP Socket MSS Peer Get 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**Ikona** ![ Ikona pobierz elementu równorzędnego T C P socket M S S](./media/user-guide/netx-events/image141.png)

**Opis**

To zdarzenie reprezentuje pobieranie wartości MSS elementu równorzędnego gniazda za pośrednictwem nx_tcp_socket_mss_peer_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Peer's MSS
- Info Field 4: Socket state (Pole informacyjne 4: stan gniazda)

### <a name="tcp-socket-mss-set"></a>Zestaw MSS gniazd TCP 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**Ikona** ![ Ikona zestawu T C P socket M S S](./media/user-guide/netx-events/image142.png)

**Opis**

To zdarzenie reprezentuje ustawienie usługi MSS gniazda za pośrednictwem nx_tcp_socket_mss_set.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Pole informacji 3: MSS
- Info Field 4: Socket state (Pole informacyjne 4: stan gniazda)

### <a name="tcp-socket-peer-info-get"></a>Uzyskiwanie informacji o równorzędnych gniazdach TCP 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**Ikona** ![ Ikona pobierz informacje o gnieździe T C P](./media/user-guide/netx-events/image143.png)

**Opis**

To zdarzenie reprezentuje informacje pobrane z gniazda TCP dotyczące adresu IP i portu elementu równorzędnego (np. >hosta) za pośrednictwem nx_tcp_socket_peer_info_get.

**Pola informacji**

- Info Field 1: Pointer to TCP socket (Pole informacji 1: wskaźnik do gniazda TCP)
- Pole informacji 2: Adres IP elementu równorzędnego
- Info Field 3: Peer port number (Pole informacji 3: numer portu elementu równorzędnego)
- Pole informacji 4: Nie używane

### <a name="tcp-socket-receive"></a>Odbieranie gniazda TCP 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**Ikona** ![ Ikona odbierania gniazda T C P](./media/user-guide/netx-events/image144.png)

**Opis**

To zdarzenie reprezentuje odbieranie danych z gniazda za pośrednictwem nx_tcp_socket_receive.

**Pola informacji**

- Info Field 1: Pointer to socket (Pole informacyjne 1: wskaźnik do gniazda)
- Info Field 2: Pointer to received packet (Pole informacyjne 2: wskaźnik do odebranego pakietu)
- Pole informacyjne 3: Odebrano długość pakietu
- Info Field 4: Receive sequence number (Pole informacyjne 4: odbierz numer sekwencji)

### <a name="tcp-socket-receive-notify"></a>Powiadomienie o odbierania gniazda TCP 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**Ikona** ![ Ikona powiadamiania o otrzymaniu gniazda T C P](./media/user-guide/netx-events/image145.png)

**Opis**

To zdarzenie reprezentuje rejestrowanie wywołania zwrotnego powiadomienia o odbierania dla gniazda za pośrednictwem nx_tcp_socket_receive_notify.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Pointer to receive notify callback Info Field 4: Not used

### <a name="tcp-socket-send"></a>Wysyłanie gniazda TCP 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**Ikona** ![ Ikona wysyłania gniazda T C P](./media/user-guide/netx-events/image146.png)

**Opis**

To zdarzenie reprezentuje wysyłanie danych na gniazdo za pośrednictwem nx_tcp_socket_send.

**Pola informacji**

- Info Field 1: Pointer to socket (Pole informacyjne 1: wskaźnik do gniazda)
- Info Field 2: Pointer to packet (Pole informacyjne 2: wskaźnik do pakietu)
- Info Field 3: Length of packet (Pole informacyjne 3: długość pakietu)
- Pole informacyjne 4: Numer sekwencji przesyłania

### <a name="tcp-socket-state-wait"></a>Oczekiwanie na stan gniazda TCP 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**Ikona** ![ Ikona oczekiwania na stan gniazda T C P](./media/user-guide/netx-events/image147.png)

**Opis**

To zdarzenie reprezentuje oczekiwanie na wprowadzenie określonego stanu przez gniazdo za pośrednictwem nx_tcp_socket_state_wait.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Desired socket state (Pole informacji 3: żądany stan gniazda)
- Info Field 4: Previous socket state (Pole informacji 4: poprzedni stan gniazda)

### <a name="tcp-socket-transmit-configure"></a>Konfigurowanie przesyłania gniazda TCP 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**Ikona** ![ Ikona konfigurowania przesyłania gniazda T C P](./media/user-guide/netx-events/image148.png)

**Opis**

To zdarzenie reprezentuje konfigurowanie opcji przesyłania dla gniazda za pośrednictwem nx_tcp_socket_transmit_configure.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Transmit queue depth (Pole informacyjne 3: Głębokość kolejki przesyłania)
- Info Field 4: Timeout value (Pole informacyjne 4: wartość limitu czasu)

### <a name="tcp-socket-window-update-notify-set"></a>Zestaw powiadomiń o aktualizacji okna gniazd TCP 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**Ikona** ![ Ikona powiadamiania zestawu powiadomiń aktualizacji okna T C P gniazda](./media/user-guide/netx-events/image149.png)

**Opis**

To zdarzenie reprezentuje gniazdo TCP odbierające powiadomienie o zwiększeniu okna odbierania hosta zdalnego za pośrednictwem nx_tcp_window_update_notify_set.

**Pola informacji** 

- Pole informacyjne 1: wskaźnik do gniazda TCP
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="udp-enable"></a>Włączanie protokołu UDP 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**Ikona** ![ Ikona włączania aplikacji UD P](./media/user-guide/netx-events/image150.png)

**Opis**

To zdarzenie reprezentuje włączanie protokołu UDP za pośrednictwem nx_udp_enable.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: Nie używane
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="udp-free-port-find"></a>Znajdowanie bezpłatnego portu UDP 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**Ikona** ![ Ikona znajdź bezpłatny port](./media/user-guide/netx-events/image151.png)

**Opis**

To zdarzenie reprezentuje znalezienie wolnego portu UDP za pośrednictwem nx_udp_free_port_find.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Starting port to search from
- Info Field 3: Free port (Pole informacyjne 3: bezpłatny port)
- Pole informacji 4: nie jest używane

### <a name="udp-information-get"></a>Uzyskiwanie informacji O UDP 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**Ikona** ![ Ikona pobierz informacje o UD P](./media/user-guide/netx-events/image152.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_udp_info_get.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Pole informacji 2: wysłane bajty UDP
- Pole informacji 3: odebrane bajty UDP
- Pole informacji 4: Nieprawidłowe pakiety

### <a name="udp-socket-bind"></a>Powiązanie gniazda UDP 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**Ikona** ![ Ikona powiązania gniazda UD P](./media/user-guide/netx-events/image153.png)

**Opis**

To zdarzenie reprezentuje powiązanie gniazda UDP z portem za pośrednictwem nx_udp_socket_bind.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Port number (Pole informacyjne 3: numer portu)
- Pole informacji 4: Opcja oczekiwania

### <a name="udp-socket-bytes-available"></a>Liczba dostępnych bajtów gniazd UDP 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**Ikona** ![ Ikona dostępnych bajtów gniazda U D P](./media/user-guide/netx-events/image154.png)

**Opis**

To zdarzenie reprezentuje bieżącą liczbę bajtów odebranych na gnieździe UDP za pośrednictwem nx_udp_socket_bytes_available.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Bytes received on socket (Pole informacji 3: bajty odebrane na gnieździe)
- Pole informacji 4: nie jest używane

### <a name="udp-socket-checksum-disable"></a>Wyłącz sumy kontrolne gniazda UDP 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**Ikona** ![ Ikona wyłączania sumy kontrolnej gniazda U D P](./media/user-guide/netx-events/image155.png)

**Opis**

To zdarzenie reprezentuje wyłączenie sumy kontrolnej dla danych na gnieździe UDP za pośrednictwem nx_udp_socket_checksum_disable.

**Pola informacji** 

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="udp-socket-checksum-enable"></a>Włączanie sumy kontrolnej gniazda UDP 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**Ikona** ![ Ikona włączania sumy kontrolnej gniazda U D P](./media/user-guide/netx-events/image156.png)

**Opis**

To zdarzenie reprezentuje włączanie przetwarzania sumy kontrolnej na gnieździe za pośrednictwem nx_udp_socket_checksum_enable.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="udp-socket-create"></a>Tworzenie gniazda UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikona** ![ Ikona tworzenia gniazda U D P](./media/user-guide/netx-events/image157.png)

**Opis**

To zdarzenie reprezentuje tworzenie gniazda UDP za pośrednictwem nx_udp_socket_create.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Type of service (Pole informacji 3: typ usługi)
- Info Field 4: Maximum receive queue (Pole informacyjne 4: maksymalna kolejka odbierania)

### <a name="udp-socket-delete-event"></a>Zdarzenie usuwania gniazda UDP 

#### <a name="nx_udp_socket_delete-event"></a>nx_udp_socket_delete zdarzeń

**Ikona** ![ Ikona zdarzenia usuwania gniazda U D P](./media/user-guide/netx-events/image158.png)

**Opis**

To zdarzenie reprezentuje usunięcie gniazda UDP za pośrednictwem nx_udp_socket_delete.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="udp-socket-information-get-event"></a>Zdarzenie get informacji o gnieździe UDP 

#### <a name="nx_udp_socket_info_get-event"></a>nx_udp_socket_info_get zdarzeń

**Ikona** ![ Informacje o gnieździe U D P pobierz ikonę zdarzenia](./media/user-guide/netx-events/image159.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji o gnieździe UDP za pośrednictwem nx_udp_socket_info_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Bytes sent through socket (Pole informacji 3: bajty wysyłane za pośrednictwem gniazda)
- Pole informacji 4: Bajty odebrane za pośrednictwem gniazda

### <a name="udp-socket-interface-set"></a>Zestaw interfejsów gniazd UDP 

#### <a name="nx_udp_socket_interface_set-event"></a>nx_udp_socket_interface_set zdarzeń

**Ikona** ![ Ikona zestawu interfejsów gniazd U D P](./media/user-guide/netx-events/image160.png)

**Opis**

To zdarzenie reprezentuje ustawienie interfejsu wychodzącego określonego gniazda UDP z określonym interfejsem za pośrednictwem nx_udp_socket_interface_set.

**Pola informacji**

- Info Field 1: Pointer to UDP socket (Pole informacyjne 1: wskaźnik do gniazda UDP)
- Pole informacyjne 2: indeks odpowiadający interfejsowi gniazda
- Pole informacji 3: Nie używane
- Pole informacji 4: nie jest używane

### <a name="udp-socket-port-get"></a>Uzyskiwanie portu gniazda UDP 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**Ikona** ![ Ikona pobierz port gniazda U D P](./media/user-guide/netx-events/image161.png)

**Opis**

To zdarzenie reprezentuje pobieranie portu UDP, z który jest powiązane określone gniazdo UDP za pośrednictwem nx_udp_socket_port_get.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to UDP socket (Pole informacyjne 2: wskaźnik do gniazda UDP)
- Info Field 3: Port number (Pole informacyjne 3: numer portu)
- Pole informacji 4: nie jest używane

### <a name="udp-socket-receive"></a>Odbieranie gniazda UDP 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**Ikona** ![ Ikona odbierania gniazda UD P](./media/user-guide/netx-events/image162.png)

**Opis**

To zdarzenie reprezentuje odbieranie danych na określonym gnieździe UDP za pośrednictwem nx_udp_socket_receive.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to UDP socket (Pole informacyjne 2: wskaźnik do gniazda UDP)
- Info Field 3: Pointer to received packet (Pole informacyjne 3: wskaźnik do odebranego pakietu)
- Pole informacji 4: Odebrano rozmiar pakietu

### <a name="udp-socket-receive-notify"></a>Powiadomienie o odbierce gniazda UDP 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**Ikona** ![ Gniazdo U D P odbiera ikonę powiadamiania ](./media/user-guide/netx-events/image163.png) w **opisie**

To zdarzenie reprezentuje rejestrowanie wywołania zwrotnego powiadomienia o odbierania za pośrednictwem nx_udp_socket_receive_notify.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Pointer to receive notify function Info Field 4: Not used (Pole informacji 3: wskaźnik do odbierania informacji o funkcji powiadamiania, pole 4: nie jest używane)

### <a name="udp-socket-send"></a>UDP Socket Send 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**Ikona** ![ Ikona wysyłania gniazda U D P](./media/user-guide/netx-events/image164.png)

**Opis**

To zdarzenie reprezentuje wysyłanie danych za pośrednictwem gniazda UDP za pośrednictwem nx_udp_socket_send.

**Pola informacji**

- Info Field 1: Pointer to socket (Pole informacyjne 1: wskaźnik do gniazda)
- Info Field 2: Pointer to packet (Pole informacyjne 2: wskaźnik do pakietu)
- Pole informacyjne 3: Długość pakietu
- Info Field 4: Destination IP address (Pole informacji 4: docelowy adres IP)

### <a name="udp-socket-unbind"></a>UDP Socket Unbind 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**Ikona** ![ Ikona unbind gniazda U D P](./media/user-guide/netx-events/image165.png)

**Opis**

To zdarzenie reprezentuje unbinding port UDP z gniazda za pośrednictwem nx_udp_socket_unbind.

**Pola informacji**

- Info Field 1: Pointer to IP instance (Pole informacji 1: wskaźnik do wystąpienia adresu IP)
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda)
- Info Field 3: Port number (Pole informacyjne 3: numer portu)
- Pole informacji 4: nie jest używane

### <a name="udp-source-extract"></a>Wyodrębnianie źródła UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikona** ![ Ikona wyodrębniania źródła UD P](./media/user-guide/netx-events/image166.png)

**Opis**

To zdarzenie reprezentuje uzyskanie adresu IP i numeru portu odebranego pakietu UDP za pośrednictwem nx_udp_source_extract.

**Pola informacji**

- Info Field 1: Pointer to packet (Pole informacyjne 1: wskaźnik do pakietu)
- Pole informacyjne 2: adres IP nadawcy
- Pole informacyjne 3: Numer portu nadawcy
- Pole informacji 4: nie jest używane