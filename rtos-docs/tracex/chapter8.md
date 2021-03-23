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
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>Rozdział 8 — zdarzenia śledzenia usługi Azure RTO NetX

Ten rozdział zawiera opis zdarzeń usługi Azure RTO NetX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

Poniżej znajduje się lista zdarzeń NetX wyświetlanych przez TraceX.

| Ikona                                           | Znaczenie                 |
| -------------------------------- | ------------------------------------- |
| ![Ikona odbierania żądania w języku R P](./media/user-guide/netx-events/image1.png)    | Odbieranie żądania wewnętrznego ARP |
| ![Wewnętrzna ikona wysyłania żądania R P](./media/user-guide/netx-events/image2.png)    | Wysyłanie żądania wewnętrznego ARP |
| ![Wewnętrzna ikona odbioru odpowiedzi R P](./media/user-guide/netx-events/image3.png)    | Odbieranie wewnętrznej odpowiedzi ARP |
| ![Wewnętrzna ikona wysyłania odpowiedzi R P](./media/user-guide/netx-events/image4.png)    | Wysyłanie odpowiedzi wewnętrznego protokołu ARP |
| ![Ikona Odbierz wewnętrznej I C M P](./media/user-guide/netx-events/image5.png)    | Wewnętrzne odbieranie protokołu ICMP |
| ![Ikona wysyłania w wewnętrznej I C M P](./media/user-guide/netx-events/image6.png)    | Wewnętrzne wysyłanie protokołu ICMP |
| ![Wewnętrzna NetX I G M P ikona odbioru](./media/user-guide/netx-events/image7.png)    | NetX IGMP — odbieranie |
| ![Ikona odbioru wewnętrznego I P](./media/user-guide/netx-events/image8.png)    | Wewnętrzny adres IP |
| ![Ikona wewnętrznej I P wysłania](./media/user-guide/netx-events/image9.png)    | Wewnętrzny wysyłanie adresu IP |
| ![Ikona odbierania danych wewnętrznych T C P](./media/user-guide/netx-events/image10.png)    | Odbieranie danych wewnętrznych protokołu TCP |
| ![Ikona wysyłania danych wewnętrznych T C P](./media/user-guide/netx-events/image11.png)    | Wysyłanie danych wewnętrznych protokołu TCP |
| ![Ikona odbierania noty wewnętrznej T C P](./media/user-guide/netx-events/image12.png)    | Odbieranie wewnętrznego FIN TCP |
| ![Ikona wewnętrznej wysyłki P C I N](./media/user-guide/netx-events/image13.png)    | Wysyłanie wewnętrznego FIN protokołu TCP |
| ![Ikona Odbierz wewnętrznego T C P R S T](./media/user-guide/netx-events/image14.png)    | Wewnętrzny odbieranie protokołu TCP |
| ![Ikona wysyłania do wewnątrz T C P R S T](./media/user-guide/netx-events/image15.png)    | Wewnętrzny parametr TCP RST |
| ![Ikona Odbierz wewnętrznej T C P S Y](./media/user-guide/netx-events/image16.png)    | Odbieranie wewnętrznego protokołu TCP SYN |
| ![Ikona wysyłania do wewnątrz T C P S Y](./media/user-guide/netx-events/image17.png)    | Wysyłanie wewnętrznego protokołu TCP SYN |
| ![Wewnętrzna ikona Odbierz U D P](./media/user-guide/netx-events/image18.png)    | Odbieranie wewnętrznego protokołu UDP |
| ![Wewnętrzna ikona wysyłania U D P](./media/user-guide/netx-events/image19.png)    | Wewnętrzne wysyłanie UDP |
| ![Ikona odbierania w języku R P](./media/user-guide/netx-events/image20.png)    | Wewnętrzny RARP odbierania |
| ![Wewnętrzna ikona wysyłania r A R P](./media/user-guide/netx-events/image21.png)    | Wewnętrzne wysyłanie RARP |
| ![Ikona wewnętrznej ponownej próby T C P](./media/user-guide/netx-events/image22.png)    | Wewnętrzna ponowna próba protokołu TCP |
| ![Ikona wewnętrznej zmiany stanu T C P](./media/user-guide/netx-events/image23.png)    | Zmiana stanu wewnętrznego protokołu TCP |
| ![Ikona wysyłania pakietów sterowników wewnętrznych we/wy](./media/user-guide/netx-events/image24.png)    | Wysyłanie pakietów sterownika wewnętrznego we/wy |
| ![ikona](./media/user-guide/netx-events/image25.png)    | Inicjowanie wewnętrznego sterownika we/wy |
| ![Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image26.png)    | Włączenie linku wewnętrznego sterownika we/wy |
| ![Ikona wyłączenia łącza sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image27.png)    | Wyłączenie linku wewnętrznego sterownika we/wy |
| ![Ikona transmisji pakietu sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image28.png)    | Emisja pakietu sterownika wewnętrznego we/wy |
| ![Ikona wysyłania sterownika protokołu ARP wewnętrznej operacji we/wy](./media/user-guide/netx-events/image29.png)    | Wysyłanie wewnętrznego sterownika we/wy ARP |
| ![Ikona wysyłania odpowiedzi protokołu ARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image30.png)    | Wysyłanie odpowiedzi do wewnętrznego sterownika we/wy ARP |
| ![Ikona wysyłania RARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image31.png)    | RARP wysyłania sterownika wewnętrznego we/wy |
| ![Ikona wewnętrznej sprzężenia multiemisji sterownika we/wy](./media/user-guide/netx-events/image32.png)    | Wewnętrzny sprzężenie multiemisji sterownika we/wy |
| ![Ikona opuszczania wewnętrznego multiemisji sterownika we/wy](./media/user-guide/netx-events/image33.png)    | Wyjście z wewnętrznego sterownika we/wy |
| ![Ikona stanu pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image34.png)    | Stan wewnętrznego pobierania sterownika we/wy |
| ![Ikona szybkość pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image35.png)    | Szybkość uzyskiwania sterownika wewnętrznego we/wy |
| ![Wewnętrzny sterownik we/wy — ikona typu dupleksu](./media/user-guide/netx-events/image36.png)    | Wewnętrzny sterownik we/wy — dostęp do typu dupleksowego |
| ![Ikona "Pobierz liczbę błędów" sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image37.png)    | Wystąpił błąd wewnętrzny sterownika we/wy |
| ![Ikona licznika odbierania dla sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image38.png)    | Wewnętrzny sterownik we/wy — pobieranie liczby RX |
| ![Ikona licznika wysyłania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image39.png)    | Wewnętrzny sterownik we/wy — pobieranie liczby transmisji |
| ![Ikona wewnętrznego pobierania sterowników we/wy](./media/user-guide/netx-events/image40.png)    | Wewnętrzny sterownik we/wy — pobieranie błędów alokacji |
| ![Ikona anulowania inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image41.png)    | Wewnętrzny sterownik we/wy — anulowanie inicjalizacji |
| ![Ikona przetwarzania odroczonego sterownika we/wy](./media/user-guide/netx-events/image42.png)    | Przetwarzanie Odroczone wewnętrznego sterownika we/wy |
| ![Ikona unieważnienia wpisów dynamicznych R P](./media/user-guide/netx-events/image43.png)    | **Unieważnienie wpisów dynamicznych ARP** (*nx_arp_dynamic_entries_invalidate*) |
| ![Ikona dynamicznego zestawu wpisów R P](./media/user-guide/netx-events/image44.png)    | **Dynamiczny zestaw wpisów ARP** (*nx_arp_dynamic_entry_set*) |
| ![Ikona włączenia R P](./media/user-guide/netx-events/image45.png)    | **Włączanie protokołu ARP** (*nx_arp_enable*) |
| ![Ikona wysyłania na żądanie w języku R P](./media/user-guide/netx-events/image46.png)    | **Wysyłanie na żądanie protokołu ARP** (*nx_arp_gratuitous_send*) |
| ![Ikona wyszukiwania adresu sprzętu R P](./media/user-guide/netx-events/image47.png)    | **Znajdowanie adresu sprzętowego ARP** (*nx_arp_hardware_address_find*) |
| ![Ikona pobierania informacji R P](./media/user-guide/netx-events/image48.png)    | **Pobieranie informacji o ARP** (*nx_arp_info_get*) |
| ![Ikona wyszukiwania adresu IP R P](./media/user-guide/netx-events/image49.png)    | **Znajdź adres IP ARP** (*nx_arp_ip_address_find*) |
| ![Ikona tworzenia wpisu statycznego R P](./media/user-guide/netx-events/image50.png)    | **Tworzenie wpisu statycznego ARP** (*nx_arp_static_entry_create*) |
| ![Ikona usuwania wpisów statycznych R P](./media/user-guide/netx-events/image51.png)    | **Usuwanie wpisów statycznych ARP** (*nx_arp_static_entries_delete*) |
| ![Ikona usuwania wpisu statycznego R P](./media/user-guide/netx-events/image52.png)    | **Usuwanie wpisu statycznego ARP** (*nx_arp_static_entry_delete*) |
| ![Ikona usuwania wpisu pamięci podręcznej Duo](./media/user-guide/netx-events/image53.png)    | **Usuwanie wpisu pamięci podręcznej Duo** (*nxd_nd_cache_entry_delete*) |
| ![Ikona zestawu wpisów pamięci podręcznej Duo](./media/user-guide/netx-events/image54.png)    | **Zestaw wpisów pamięci podręcznej Duo** (*nxd_nd_cache_entry_set*) |
| ![Ikona unieważniania pamięci podręcznej Duo](./media/user-guide/netx-events/image55.png)    | **Unieważnienie pamięci podręcznej Duo** (*nxd_nd_cache_invalidate*) |
| ![Ikona znajdowania pamięci podręcznej Duo I adresu](./media/user-guide/netx-events/image56.png)    | **Znajdź adres IP pamięci podręcznej Duo** (*nxd_nd_cache_ip_address_find*) |
| ![Ikona włączania Duo I C M](./media/user-guide/netx-events/image57.png)    | **Włącz protokół ICMP** (*nxd_icmp_enable*) w programie Duo |
| ![Duo I C M P I P 6 ikona ping](./media/user-guide/netx-events/image58.png)    | **Żądanie ping protokołu ICMP IPv6** (*nxd_icmp_ping*) |
| ![Ikona wyszukiwania Duo I P z maksymalnym rozmiarem ładunku](./media/user-guide/netx-events/image59.png)    | **Maksymalny rozmiar ładunku** w programie Duo — znajdź (*nx_max_payload_size_find*) |
| ![Ikona odrzuconego wysyłania pakietów w programie Duo I](./media/user-guide/netx-events/image60.png)    | **Wysyłanie pakietów Raw IP** (*nxd_ip_raw_packet_send*) w programie Duo |
| ![Ikona dodawania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image61.png)    | **Dodatek do domyślnego routera IPv6** w programie Duo (*nxd_ipv6_default_router_add*) |
| ![Ikona usuwania domyślnego routera Duo I v 6](./media/user-guide/netx-events/image62.png)    | **Domyślne usunięcie routera IPv6** w programie Duo (*nxd_ipv6_default_router_delete)* |
| ![Ikona włączania Duo I v 6](./media/user-guide/netx-events/image63.png)    | **Włącz protokół IPv6** w programie Duo (*nxd_ipv6_enable)* |
| ![Ikona uzyskiwania adresu globalnego Duo I P v 6](./media/user-guide/netx-events/image64.png)    | **Pobieranie globalnego adresu IPv6** (*nxd_ipv6_global_address_get*) w programie Duo |
| ![Ikona zestawu adresów globalnych Duo I P v 6](./media/user-guide/netx-events/image65.png)    | **Globalny zestaw adresów IPv6** (*nxd_ipv6_global_address_set*) w programie Duo |
| ![Duo I P v 6 — ikona inicjowania procesu DAD](./media/user-guide/netx-events/image66.png)    | **Zainicjowanie procesu DAD przez protokół IPv6** (*nxd_ipv6_initiate_dad_process*) |
| ![Ikona uzyskiwania adresu interfejsu Duo I P v 6](./media/user-guide/netx-events/image67.png)    | **Uzyskaj adres interfejsu IPv6** (*nxd_ipv6_interface_address_get*) w programie Duo |
| ![Ikona zestawu adresów interfejsu Duo I v 6](./media/user-guide/netx-events/image68.png)    | **Zestaw adresów interfejsu IPv6** (*nxd_ipv6_interface_address_set*) Duo |
| ![Ikona uzyskiwania adresu lokalnego linku Duo I P 6](./media/user-guide/netx-events/image69.png)    | **Pobieranie adresu lokalnego linku do protokołu Duo** (*nxd_ipv6_linklocal_address_get*) |
| ![Ikona zestawu adresów lokalnych linku Duo I v 6](./media/user-guide/netx-events/image70.png)    | **Zestaw adresów IPv6 linku Duo** (*nxd_ipv6_linklocal_address_set*) |
| ![Ikona wysyłania pakietów pierwotnych Duo I v 6](./media/user-guide/netx-events/image71.png)    | **Wysyłanie pakietów RAW IPv6** (*nxd_ipv6_raw_packet_send)* w programie Duo |
| ![Ikona pobierania informacji o komunikacji równorzędnej z gniazdami w programie Duo T C](./media/user-guide/netx-events/image72.png)    | **Pobieranie informacji o komunikacji równorzędnej gniazda TCP** (*nxd_tcp_socket_peer_info_get*) |
| ![Ikona interfejsu zestawu gniazd w programie Duo T C](./media/user-guide/netx-events/image73.png)    | **Interfejs zestawu gniazd TCP Duo** (*nxd_tcp_socket_set_interface*) |
| ![Ikona wysyłania z gniazdem Duo U D P](./media/user-guide/netx-events/image74.png)    | (*Nxd_udp_socket_send*) **Duo — wysyłanie gniazda UDP** |
| ![Ikona interfejsu zestawu gniazd w programie Duo U D](./media/user-guide/netx-events/image75.png)    | **Interfejs zestawu gniazd UDP Duo** (*nxd_udp_socket_set_interface*) |
| ![Ikona wyodrębnienia źródła w usłudze Duo U D](./media/user-guide/netx-events/image76.png)    | **Wyodrębnij Źródło UDP Duo** (*nxd_udp_source_extract*) |
| ![Ikona włączenia I C M](./media/user-guide/netx-events/image77.png)    | **Włączanie protokołu ICMP** (*nx_icmp_enable*) |
| ![I C M P informacje o ikonie](./media/user-guide/netx-events/image78.png)    | **Informacje o protokole ICMP** (*nx_icmp_info_get*) |
| ![I C M P ikona ping](./media/user-guide/netx-events/image79.png)    | **Polecenie ping protokołu ICMP** (*nx_icmp_ping*) |
| ![Ikona włączenia I G M](./media/user-guide/netx-events/image80.png)    | **Włączanie IGMP** (*nx_igmp_enable*) |
| ![Ikona uzyskiwania informacji o & G M](./media/user-guide/netx-events/image81.png)    | **Informacje o** protokole IGMP (*nx_igmp_info_get*) |
| ![Ikona wyłączenia sprzężenia zwrotnego I G M](./media/user-guide/netx-events/image82.png)    | **Wyłączenie sprzężenia zwrotnego protokołu IGMP** (*nx_igmp_loopback_disable*) |
| ![Ikona włączania sprzężenia zwrotnego M P](./media/user-guide/netx-events/image83.png)    | **Włączanie sprzężenia zwrotnego protokołu IGMP** (*nx_igmp_loopback_enable*) |
| ![Ikona sprzężenia multiemisji I G M](./media/user-guide/netx-events/image84.png)    | **Sprzężenie multiemisyjne IGMP** (*nx_igmp_multicast_join*) |
| ![Ikona urlopu multiemisji I G M](./media/user-guide/netx-events/image85.png)    | **Wyjście z multiemisji IGMP** (*nx_igmp_multicast_leave*) |
| ![Ikona powiadomienia o zmianie adresu](./media/user-guide/netx-events/image86.png)    | **Powiadomienie o zmianie adresu IP** (*nx_ip_address_change_notify*) |
| ![Ikona pobierania adresu](./media/user-guide/netx-events/image87.png)    | **Pobieranie adresu IP** (*nx_ip_address_get*) |
| ![Ikona zestawu adresów I P](./media/user-guide/netx-events/image88.png)    | **Zestaw adresów IP** (*nx_ip_address_set*) |
| ![Ikona tworzenia](./media/user-guide/netx-events/image89.png)    | **Tworzenie adresu IP** (*nx_ip_create*) |
| ![Ikona usuwania](./media/user-guide/netx-events/image90.png)    | **Usuwanie adresu IP** (*nx_ip_delete*) |
| ![Ikona poleceń I P sterownika](./media/user-guide/netx-events/image91.png)    | **Polecenie bezpośredniego sterownika IP** (*nx_ip_driver_direct_command*) |
| ![Ikona wyłączonego przesyłania dalej](./media/user-guide/netx-events/image92.png)    | **Wyłączenie przesyłania dalej IP** (*nx_ip_forwarding_disable*) |
| ![Ikona włączania przesyłania dalej](./media/user-guide/netx-events/image93.png)    | **Włączanie przekazywania adresów IP** (*nx_ip_forwarding_enable*) |
| ![Ikona wyłączenia fragmentu](./media/user-guide/netx-events/image94.png)    | **Wyłączenie fragmentu IP** (*nx_ip_fragment_disable*) |
| ![Ikona włączenia fragmentu](./media/user-guide/netx-events/image95.png)    | **Włączanie fragmentu IP** (*nx_ip_fragment_enable*)  |
| ![Ikona zestawu adresów bramy I](./media/user-guide/netx-events/image96.png)    | **Zestaw adresów IP Gateway** (*nx_ip_gateway_address_set*) |
| ![Ikona uzyskiwania informacji](./media/user-guide/netx-events/image97.png)    | **Pobieranie informacji o adresie IP** (*nx_ip_info_get*) |
| ![Ikona dołączania interfejsu I P](./media/user-guide/netx-events/image98.png)    | **Dołączanie interfejsu IP** (*nx_ip_interface_attach*) |
| ![Ikona uzyskiwania informacji o interfejsie](./media/user-guide/netx-events/image99.png)    | **Pobieranie informacji o interfejsie IP** (*nx_ip_interface_info_get*) |
| ![Ikona wyłączania pakietów pierwotnych](./media/user-guide/netx-events/image100.png)    | **Wyłączanie pierwotnego pakietu IP** (*nx_ip_raw_packet_disable*) |
| ![Ikona włączenia pakietu RAW](./media/user-guide/netx-events/image101.png)    | **Włącz pierwotny pakiet IP** (*nx_ip_raw_packet_enable*) |
| ![Ikona odbierania pakietów RAW](./media/user-guide/netx-events/image102.png)    | **Odbieranie pakietów pierwotnych adresów IP** (*nx_ip_raw_packet_receive*) |
| ![Ikona wysyłania pakietów RAW](./media/user-guide/netx-events/image103.png)    | **Wysyłanie pakietów Raw IP** (*nx_ip_raw_packet_send*) |
| ![Ikona dodawania trasy statycznej](./media/user-guide/netx-events/image104.png)    | **Dodawanie statycznej trasy IP** (*nx_ip_static_route_add*) |
| ![Ikona usuwania trasy statycznej](./media/user-guide/netx-events/image105.png)    | **Usuwanie statycznej trasy IP** (*nx_ip_static_route_delete)* |
| ![Ikona sprawdzania stanu P](./media/user-guide/netx-events/image106.png)    | **Sprawdzenie stanu IP** (*nx_ip_status_check*)|
| ![Ikona włączenia I S E C](./media/user-guide/netx-events/image107.png)    | **Włączanie protokołu IPSec** (*nx_ipsec_enable)* |
| ![Ikona alokacji pakietów](./media/user-guide/netx-events/image108.png)    | **Przydział pakietu** (*nx_packet_allocate*) |
| ![Ikona kopiowania pakietów](./media/user-guide/netx-events/image109.png)    | **Kopiowanie pakietów** (*nx_packet_copy*) |
| ![Ikona dołączania danych pakietu](./media/user-guide/netx-events/image110.png)    | **Dołączanie danych pakietu** (*nx_packet_data_append*) |
| ![Ikona przesunięcia wyodrębniania danych pakietu](./media/user-guide/netx-events/image111.png)    | **Przesunięcie wyodrębniania danych pakietu** (*nx_packet_data_extract_offset*) |
| ![Ikona pobierania danych pakietu](./media/user-guide/netx-events/image112.png)    | **Pobieranie danych pakietu** (*nx_packet_data_retrieve*) |
| ![Ikona pobierania długości pakietu](./media/user-guide/netx-events/image113.png)    | **Pobieranie długości pakietu** (*nx_packet_length_get*) |
| ![Ikona tworzenia puli pakietów](./media/user-guide/netx-events/image114.png)    | **Tworzenie puli pakietów** (*nx_packet_pool_create*) |
| ![Ikona usuwania puli pakietów](./media/user-guide/netx-events/image115.png)    | **Usuwanie puli pakietów** (*nx_packet_pool_delete*) |
| ![Ikona pobierania informacji o puli pakietów](./media/user-guide/netx-events/image116.png)    | **Pobieranie informacji o puli pakietów** (*nx_packet_pool_info_get*) |
| ![Ikona wydania pakietu](./media/user-guide/netx-events/image117.png)    | **Wydanie pakietów** (*nx_packet_release*) |
| ![Ikona wydania transmisji pakietu](./media/user-guide/netx-events/image118.png)    | **Wydanie transmisji pakietów** (*nx_packet_transmit_release*) |
| ![Ikona wyłączenia r P](./media/user-guide/netx-events/image119.png)    | **RARP Wyłącz** (*nx_rarp_disable*) |
| ![Ikona włączenia języka r P](./media/user-guide/netx-events/image120.png)    | **Włącz RARP** (*nx_rarp_enable*) |
| ![Ikona uzyskiwania informacji o języku r P](./media/user-guide/netx-events/image121.png)    | **RARP informacji** (*nx_rarp_info_get*) |
| ![Ikona inicjowania systemu](./media/user-guide/netx-events/image122.png)    | **Inicjowanie systemu** (*nx_system_initialize*) |
| ![Ikona powiązania gniazda klienta T C P](./media/user-guide/netx-events/image123.png)    | **Powiązanie gniazda klienta TCP** (*nx_tcp_client_socket_bind*) |
| ![Ikona połączenia z gniazdem klienta T C P](./media/user-guide/netx-events/image124.png)    | **Połączenie gniazda klienta TCP** (*nx_tcp_client_socket_connect*) |
| ![Ikona pobierania portu gniazda klienta T C P](./media/user-guide/netx-events/image125.png)    | **Pobieranie portu gniazda klienta TCP** (*nx_tcp_client_socket_port_get*) |
| ![Ikona usuwania powiązania gniazda klienta T C P](./media/user-guide/netx-events/image126.png)    | **Niepowiązanie gniazda klienta TCP** (*nx_tcp_client_socket_unbind*) |
| ![Ikona włączenia P C](./media/user-guide/netx-events/image127.png)    | **Włączanie protokołu TCP** (*nx_tcp_enable*) |
| ![Ikona wyszukiwania wolnego portu T C P](./media/user-guide/netx-events/image128.png)    | **Znajdź port bezpłatny TCP** (*nx_tcp_free_port_find*) |
| ![Ikona pobierania informacji T C P](./media/user-guide/netx-events/image129.png)    | **Pobieranie informacji o protokole TCP** (*nx_tcp_info_get*) |
| ![Ikona akceptowania gniazda serwera T C P](./media/user-guide/netx-events/image130.png)    | **Akceptowanie gniazda serwera TCP** (*nx_tcp_server_socket_accept*) |
| ![Ikona nasłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image131.png)    | **Nasłuchiwanie gniazda serwera TCP** (*nx_tcp_server_socket_listen*) |
| ![Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image132.png)    | **Przesłuchiwanie gniazda serwera TCP** (*nx_tcp_server_socket_relisten*) |
| ![Ikona nieakceptowania gniazda serwera T C P](./media/user-guide/netx-events/image133.png)    | **Nieakceptowanie gniazda serwera TCP** (*nx_tcp_server_socket_unaccept*) |
| ![Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image134.png)    | **Odsłuchiwanie gniazda serwera TCP** (*nx_tcp_server_socket_unlisten*) |
| ![Ikona dostępnych bajtów gniazda T C](./media/user-guide/netx-events/image135.png)    | **Dostępne bajty gniazda TCP** (*nx_tcp_socket_bytes_available*) |
| ![Ikona tworzenia gniazda T C P](./media/user-guide/netx-events/image136.png)    | **Tworzenie gniazda TCP** (*nx_tcp_socket_create*) |
| ![Ikona usuwania gniazda T C P](./media/user-guide/netx-events/image137.png)    | **Usuwanie gniazda TCP** (*nx_tcp_socket_delete*) |
| ![Ikona rozłączenia gniazda T C P](./media/user-guide/netx-events/image138.png)    | **Odłączanie gniazda TCP** (*nx_tcp_socket_disconnect*) |
| ![Ikona uzyskiwania informacji o gnieździe T C P](./media/user-guide/netx-events/image139.png)    | **Pobieranie informacji o gnieździe TCP** (*nx_tcp_socket_info_get*) |
| ![Ikona pobierania o przełączeniu do gniazda T C P](./media/user-guide/netx-events/image140.png)    | **Pobieranie z gniazda TCP** (w *nx_tcp_socket_mss_get*) |
| ![Ikona pobierania elementu równorzędnego w gnieździe T C P Socket](./media/user-guide/netx-events/image141.png)    | **Pobieranie elementu równorzędnego** (*Nx_tcp_socket_mss_peer_get*) w gnieździe TCP Socket |
| ![Ikona zestawu o wzgnieździe T C P Socket](./media/user-guide/netx-events/image142.png)    | Zestaw (*nx_tcp_socket_mss_set*) **gniazda TCP** |
| ![Ikona pobierania informacji o komunikacji równorzędnej gniazda T C](./media/user-guide/netx-events/image143.png)    | **Pobieranie informacji o komunikacji równorzędnej gniazda TCP** (*nx_tcp_socket_peer_info_get*) |
| ![Ikona odbioru gniazda T C P](./media/user-guide/netx-events/image144.png)    | **Odbieranie gniazda TCP** (*nx_tcp_socket_receive*) |
| ![Ikona powiadomienia o odebraniu gniazda T C P](./media/user-guide/netx-events/image145.png)    | **Powiadomienie o odebraniu gniazda TCP** (*nx_tcp_socket_receive_notify*) |
| ![Ikona wysyłania gniazda T C P](./media/user-guide/netx-events/image146.png)    | **Wysyłanie gniazda TCP** (*nx_tcp_socket_send*) |
| ![Ikona oczekiwania stanu gniazda T C P](./media/user-guide/netx-events/image147.png)    | **Oczekiwanie stanu gniazda TCP** (*nx_tcp_socket_state_wait*) |
| ![Ikona wysyłania gniazda sieciowego T C P](./media/user-guide/netx-events/image148.png)    | **Konfigurowanie transmisji gniazda TCP** (*nx_tcp_socket_transmit_configure*) |
| ![Ikona zestawu powiadomień o aktualizacji okna gniazda T C](./media/user-guide/netx-events/image149.png)    | **Zestaw powiadomień o aktualizacji okna gniazda TCP** (*nx_tcp_socket_window_update_notify_set*)  |
| ![Ikona włączenia u D P](./media/user-guide/netx-events/image150.png)    | **Włączanie protokołu UDP** (*nx_udp_enable*) |
| ![Ikona Znajdź bezpłatny port U D P](./media/user-guide/netx-events/image151.png)    | **Znajdowanie portów bezpłatnych UDP** (*nx_udp_free_port_find*) |
| ![Ikona pobierania informacji u D P](./media/user-guide/netx-events/image152.png)    | **Pobieranie informacji o UDP** (*nx_udp_info_get*) |
| ![Ikona powiązania z gniazdem u D P](./media/user-guide/netx-events/image153.png)    | **Powiązanie gniazda UDP** (*nx_udp_socket_bind*) |
| ![Ikona U-D P Sockets available](./media/user-guide/netx-events/image154.png)    | **Dostępne bajty gniazda UDP** (*nx_udp_socket_bytes_available*) |
| ![Ikona wyłączenia sumy kontrolnej P D w gnieździe](./media/user-guide/netx-events/image155.png)    | **Wyłącz sumę kontrolną gniazda UDP** (*nx_udp_socket_checksum_disable*) |
| ![Ikona włączenia sumy kontrolnej w gnieździe u D P](./media/user-guide/netx-events/image156.png)    | **Włącz sumę kontrolną gniazda UDP** *(nx_udp_socket_checksum_enable)* |
| ![Ikona tworzenia gniazda P D](./media/user-guide/netx-events/image157.png)    | **Tworzenie gniazda UDP** (*nx_udp_socket_create*) |
| ![Ikona "Usuń" u gniazda P D](./media/user-guide/netx-events/image158.png)    | **Usuwanie gniazda UDP** (*nx_udp_socket_delete*) |
| ![Ikona uzyskiwania informacji o gnieździe U D](./media/user-guide/netx-events/image159.png)    | **Pobieranie informacji o gnieździe UDP** (*nx_udp_socket_info_get*) |
| ![Ikona ustawienia interfejsu gniazda P D Socket](./media/user-guide/netx-events/image160.png)    | **Zestaw interfejsów gniazda UDP** (*nx_udp_socket_interface_set*) |
| ![Ikona pobierania portu gniazda P D](./media/user-guide/netx-events/image161.png)    | **Pobieranie portu gniazda UDP** (*nx_udp_socket_port_get*) |
| ![Ikona odbioru w gnieździe U D P](./media/user-guide/netx-events/image162.png)    | **Odbieranie gniazda UDP** (*nx_udp_socket_receive*) |
| ![Ikona powiadomienia o odebraniu gniazda P D](./media/user-guide/netx-events/image163.png)    | **Powiadomienie o odebraniu gniazda UDP** (*nx_udp_socket_receive_notify*) |
| ![Ikona wysyłania w gnieździe u D P](./media/user-guide/netx-events/image164.png)    | **Wysyłanie gniazda UDP** (*nx_udp_socket_send*) |
| ![Ikona nieusuwania powiązania U gniazda P D](./media/user-guide/netx-events/image165.png)    | **Powiązanie UDP gniazda** (*nx_udp_socket_unbind*) |
| ![Ikona wyodrębnienia źródła U D P](./media/user-guide/netx-events/image166.png)    | **Wyodrębnij Źródło UDP** (*nx_udp_source_extract*) |

## <a name="event-descriptions"></a>Opisy zdarzeń

Poniższe strony opisują zdarzenia śledzenia NetX.

### <a name="internal-arp-request-receive"></a>Odbieranie żądania wewnętrznego ARP 

#### <a name="internal-arp-request-receive"></a>Odbieranie żądania wewnętrznego ARP

**Ikona** ![ Ikona odbierania żądania wewnętrznego protokołu ARP](./media/user-guide/netx-events/image1.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odbierania żądania wewnętrznego NetX ARP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: źródłowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: nieużywane

### <a name="internal-arp-request-send"></a>Wysyłanie żądania wewnętrznego ARP 

#### <a name="internal-arp-request-send"></a>Wysyłanie żądania wewnętrznego ARP

**Ikona** ![ Ikona wysyłania żądania wewnętrznego ARP](./media/user-guide/netx-events/image2.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania żądania NetX ARP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: docelowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: nieużywane

### <a name="internal-arp-response-receive"></a>Odbieranie wewnętrznej odpowiedzi ARP 

#### <a name="internal-arp-request-receive"></a>Odbieranie żądania wewnętrznego ARP

**Ikona** ![ Ikona odbierania żądania wewnętrznego ARP](./media/user-guide/netx-events/image3.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odbioru wewnętrznej odpowiedzi NetX ARP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: źródłowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: nieużywane

### <a name="internal-arp-response-send"></a>Wysyłanie odpowiedzi wewnętrznego protokołu ARP 

#### <a name="internal-arp-request-send"></a>Wysyłanie żądania wewnętrznego ARP

**Ikona** ![ Ikona wysyłania żądania wewnętrznego ARP](./media/user-guide/netx-events/image4.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania odpowiedzi NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: docelowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: nieużywane

### <a name="internal-icmp-receive"></a>Wewnętrzne odbieranie protokołu ICMP 

#### <a name="internal-icmp-receive"></a>Wewnętrzne odbieranie protokołu ICMP

**Ikona** ![ Ikona Odbierz wewnętrznej I C M P](./media/user-guide/netx-events/image5.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne NetX zdarzenia odbierania protokołu ICMP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: źródłowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: słowo 0 w nagłówku ICMP

### <a name="internal-icmp-send"></a>Wewnętrzne wysyłanie protokołu ICMP 

#### <a name="internal-icmp-send"></a>Wewnętrzne wysyłanie protokołu ICMP

**Ikona** ![ Ikona wysyłania w wewnętrznej I C M P](./media/user-guide/netx-events/image6.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu ICMP NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: docelowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: słowo 0 w nagłówku ICMP

### <a name="internal-igmp-receive"></a>Wewnętrzny odbiór IGMP 

#### <a name="internal-igmp-receive"></a>Wewnętrzny odbiór IGMP

**Ikona** ![ Wewnętrzna I G M P ikona Odbierz](./media/user-guide/netx-events/image7.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne NetXe zdarzenie odbierania protokołu IGMP.

**Pola informacji**

- Pole informacji 1: wskaźnik adresu IP
- Pole informacji 2: źródłowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: słowo 0 w nagłówku IGMP

### <a name="internal-ip-receive"></a>Wewnętrzny adres IP 

#### <a name="internal-ip-receive"></a>Wewnętrzny adres IP

**Ikona** ![ Ikona odbioru wewnętrznego I P](./media/user-guide/netx-events/image8.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne NetX IP Receive.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: źródłowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: długość pakietu

### <a name="internal-ip-send"></a>Wewnętrzny wysyłanie adresu IP

#### <a name="internal-ip-send"></a>Wewnętrzny wysyłanie adresu IP

**Ikona** ![ Ikona wewnętrznej I P wysłania](./media/user-guide/netx-events/image9.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu IP NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: docelowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: długość pakietu

### <a name="internal-tcp-data-receive"></a>Odbieranie danych wewnętrznych protokołu TCP 

#### <a name="internal-tcp-data-receive"></a>Odbieranie danych wewnętrznych protokołu TCP

**Ikona** ![ Ikona odbierania danych wewnętrznych T C P](./media/user-guide/netx-events/image10.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania danych NetX TCP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: źródłowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: numer sekwencyjny odbioru

### <a name="internal-tcp-data-send"></a>Wysyłanie danych wewnętrznych protokołu TCP 

#### <a name="internal-tcp-data-send"></a>Wysyłanie danych wewnętrznych protokołu TCP

**Ikona** ![ Ikona wysyłania danych wewnętrznych T C P](./media/user-guide/netx-events/image11.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania danych NetX TCP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: numer sekwencyjny transmisji

### <a name="internal-tcp-fin-receive"></a>Odbieranie wewnętrznego FIN TCP 

#### <a name="internal-tcp-fin-receive"></a>Odbieranie wewnętrznego fin TCP

**Ikona** ![ Ikona Odbierz wewnętrznej T C P r N](./media/user-guide/netx-events/image12.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbioru NetX TCP FIN.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: numer sekwencyjny odbioru

### <a name="internal-tcp-fin-send"></a>Wysyłanie wewnętrznego FIN protokołu TCP 

#### <a name="internal-tcp-fin-send"></a>Wysyłanie wewnętrznego fin protokołu TCP

**Ikona** ![ Ikona wewnętrznej wysyłki P C I N](./media/user-guide/netx-events/image13.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania NetX TCP FIN.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: numer sekwencyjny transmisji

### <a name="internal-tcp-rst-receive"></a>Wewnętrzny odbieranie protokołu TCP 

#### <a name="internal-tcp-rst-receive"></a>Wewnętrzny odbieranie protokołu TCP

**Ikona** ![ Ikona Odbierz wewnętrznego T C P R S T](./media/user-guide/netx-events/image14.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie NetX resetowania protokołu TCP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP.
- Pole informacji 2: wskaźnik do gniazda.
- Pole informacji 3: wskaźnik do pakietu.
- Pole informacji 4: Odbierz numer sekwencyjny.

### <a name="internal-tcp-rst-send"></a>Wewnętrzny parametr TCP RST 

#### <a name="internal-tcp-rst-send"></a>Wewnętrzny parametr TCP RST

**Ikona** ![ Ikona wysyłania do wewnątrz T C P R S T](./media/user-guide/netx-events/image15.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu TCP NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: numer sekwencyjny transmisji

### <a name="internal-tcp-syn-receive"></a>Odbieranie wewnętrznego protokołu TCP SYN 

#### <a name="internal-tcp-syn-receive"></a>Odbieranie wewnętrznego protokołu TCP SYN

**Ikona** ![ Ikona Odbierz wewnętrznej T C P S Y](./media/user-guide/netx-events/image16.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbioru NetX TCP SYN.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: numer sekwencyjny odbioru

### <a name="internal-tcp-syn-send"></a>Wysyłanie wewnętrznego protokołu TCP SYN 

#### <a name="internal-tcp-syn-send"></a>Wysyłanie wewnętrznego protokołu TCP SYN

**Ikona** ![ Ikona wysyłania do wewnątrz T C P S Y](./media/user-guide/netx-events/image17.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania synch NetX TCP.

Pola informacji 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu — pole informacji 4: numer sekwencyjny transmisji

### <a name="internal-udp-receive"></a>Odbieranie wewnętrznego protokołu UDP 

#### <a name="internal-udp-receive"></a>Odbieranie wewnętrznego protokołu UDP

**Ikona** ![ Wewnętrzna ikona Odbierz U D P](./media/user-guide/netx-events/image18.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania protokołu UDP NetX.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: słowo 0 w nagłówku UDP

### <a name="internal-udp-send"></a>Wewnętrzne wysyłanie UDP 

#### <a name="internal-udp-send"></a>Wewnętrzne wysyłanie UDP

**Ikona** ![ Wewnętrzna ikona wysyłania U D P](./media/user-guide/netx-events/image19.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania protokołu UDP NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: słowo 0 w nagłówku UDP

### <a name="internal-rarp-receive"></a>Wewnętrzny RARP odbierania 

#### <a name="internal-rarp-receive"></a>Wewnętrzny RARP odbierania 

**Ikona** ![ Ikona odbierania w języku R P](./media/user-guide/netx-events/image20.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie odbierania NetX RARP.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: docelowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: słowo 1 w nagłówku RARP

### <a name="internal-rarp-send"></a>Wewnętrzne wysyłanie RARP 

#### <a name="internal-rarp-send"></a>Wewnętrzne wysyłanie RARP 

**Ikona** ![ Wewnętrzna ikona wysyłania r A R P](./media/user-guide/netx-events/image21.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania NetX RARP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: docelowy adres IP
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: słowo 1 w nagłówku RARP

### <a name="internal-tcp-retry"></a>Wewnętrzna ponowna próba protokołu TCP 

#### <a name="internal-tcp-retry"></a>Wewnętrzna ponowna próba protokołu TCP 

**Ikona** ![ Ikona wewnętrznej ponownej próby T C P](./media/user-guide/netx-events/image22.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie ponowienia protokołu TCP NetX.

**Pola informacji**
- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik do pakietu
- Pole informacji 4: liczba ponownych prób

### <a name="internal-tcp-state-change"></a>Zmiana stanu wewnętrznego protokołu TCP 

#### <a name="internal-tcp-state-change"></a>Zmiana stanu wewnętrznego protokołu TCP 

**Ikona** ![ Ikona wewnętrznej zmiany stanu T C P](./media/user-guide/netx-events/image23.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie zmiany stanu gniazda TCP NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: poprzedni stan
- Pole informacji 4: nowy stan

### <a name="internal-io-driver-packet-send"></a>Wysyłanie pakietów sterownika wewnętrznego we/wy 

#### <a name="internal-io-driver-packet-send"></a>Wysyłanie pakietów sterownika wewnętrznego we/wy

**Ikona** ![ Ikona wysyłania pakietów sterowników wewnętrznych we/wy](./media/user-guide/netx-events/image24.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania pakietu sterowników we/wy wewnętrznego NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: rozmiar pakietu
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika we/wy

**Ikona** ![ Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image25.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania sterownika wewnętrznego NetX we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-link-enable"></a>Włączenie linku wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-link-enable"></a>Włączenie linku wewnętrznego sterownika we/wy

**Ikona** ![ Ikona włączenia linku wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image26.png)

**Opis**

To zdarzenie reprezentuje zdarzenie włączenia łącza sterownika wewnętrznego NetX we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-link-disable"></a>Wyłączenie linku wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-link-disable"></a>Wyłączenie linku wewnętrznego sterownika we/wy

**Ikona** ![ Ikona wyłączenia łącza sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image27.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wyłączenia łącza sterownika wewnętrznego NetX we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-packet-broadcast"></a>Emisja pakietu sterownika wewnętrznego we/wy 

#### <a name="internal-io-driver-packet-broadcast"></a>Emisja pakietu sterownika wewnętrznego we/wy

**Ikona** ![ Ikona transmisji pakietu sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image28.png)

**Opis**

To zdarzenie reprezentuje zdarzenie emisji pakietów sterownika wewnętrznego NetX we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: rozmiar pakietu
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-arp-send"></a>Wysyłanie wewnętrznego sterownika we/wy ARP 

#### <a name="internal-io-driver-arp-send"></a>Wysyłanie wewnętrznego sterownika we/wy ARP

**Ikona** ![ Ikona wysyłania sterownika protokołu ARP wewnętrznej operacji we/wy](./media/user-guide/netx-events/image29.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie wysyłania sterownika NetX we/wy protokołu ARP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: rozmiar pakietu
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-arp-response-send"></a>Wysyłanie odpowiedzi do wewnętrznego sterownika we/wy ARP 

#### <a name="internal-io-driver-arp-response-send"></a>Wysyłanie odpowiedzi do wewnętrznego sterownika we/wy ARP

**Ikona** ![ Ikona wysyłania odpowiedzi protokołu ARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image30.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania odpowiedzi NetX we/wy wewnętrznego sterownika protokołu ARP.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: rozmiar pakietu
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-rarp-send"></a>RARP wysyłania sterownika wewnętrznego we/wy 

#### <a name="internal-io-driver-rarp-send"></a>RARP wysyłania sterownika wewnętrznego we/wy

**Ikona** ![ Ikona wysyłania RARP sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image31.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne NetX sterownika we/wy RARP wysyłanie zdarzenia.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: rozmiar pakietu
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-multicast-join"></a>Wewnętrzny sprzężenie multiemisji sterownika we/wy 

#### <a name="internal-io-driver-multicast-join"></a>Wewnętrzny sprzężenie multiemisji sterownika we/wy

**Ikona** ![ Ikona wewnętrznej sprzężenia multiemisji sterownika we/wy](./media/user-guide/netx-events/image32.png)

**Opis**

To zdarzenie reprezentuje zdarzenie sprzężenia multiemisji wewnętrznego NetX we/wy.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-multicast-leave"></a>Wyjście z wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-multicast-leave"></a>Wyjście z wewnętrznego sterownika we/wy

**Ikona** ![ Ikona opuszczania wewnętrznego multiemisji sterownika we/wy](./media/user-guide/netx-events/image33.png)

**Opis**

To zdarzenie przedstawia wewnętrzne zdarzenie NetXa multiemisji sterownika we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-get-status"></a>Stan wewnętrznego pobierania sterownika we/wy 

#### <a name="internal-io-driver-get-status"></a>Stan wewnętrznego pobierania sterownika we/wy

**Ikona** ![ Ikona stanu pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image34.png)

**Opis**

To zdarzenie reprezentuje zdarzenie stanu NetX wewnętrznego sterownika we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-get-speed"></a>Szybkość uzyskiwania sterownika wewnętrznego we/wy 

#### <a name="internal-io-driver-get-speed"></a>Szybkość uzyskiwania sterownika wewnętrznego we/wy

**Ikona** ![ Ikona szybkość pobierania sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image35.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie pobierania sterownika NetX we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-get-duplex-type"></a>Wewnętrzny sterownik we/wy — dostęp do typu dupleksowego 

#### <a name="internal-io-driver-get-duplex-type"></a>Wewnętrzny sterownik we/wy — dostęp do typu dupleksowego

**Ikona** ![ Wewnętrzny sterownik we/wy — ikona typu dupleksu](./media/user-guide/netx-events/image36.png)

**Opis**

To zdarzenie reprezentuje wewnętrzny sterownik we/wy NetX — zdarzenie typu dupleks.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-get-error-count"></a>Wystąpił błąd wewnętrzny sterownika we/wy

#### <a name="internal-io-driver-get-error-count"></a>Wystąpił błąd wewnętrzny sterownika we/wy

**Ikona** ![ Ikona "Pobierz liczbę błędów" sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image37.png)

**Opis**

To zdarzenie reprezentuje wewnętrzny sterownik NetX we/wy dla licznika błędów.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-get-rx-count"></a>Wewnętrzny sterownik we/wy — pobieranie liczby RX 

#### <a name="internal-io-driver-get-rx-count"></a>Wewnętrzny sterownik we/wy — pobieranie liczby RX

**Ikona** ![ Ikona licznika odbierania dla sterownika wewnętrznego we/wy](./media/user-guide/netx-events/image38.png)

**Opis**

To zdarzenie reprezentuje NetX wewnętrzny sterownika wejścia/wyjścia.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-get-tx-count"></a>Wewnętrzny sterownik we/wy — pobieranie liczby transmisji 

#### <a name="internal-io-driver-get-tx-count"></a>Wewnętrzny sterownik we/wy — pobieranie liczby transmisji

**Ikona** ![ Ikona liczby odczytów wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image39.png)

**Opis**

To zdarzenie reprezentuje NetX wewnętrzny sterownika wejścia/wyjścia.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-get-allocation-errors"></a>Wewnętrzny sterownik we/wy — pobieranie błędów alokacji 

#### <a name="internal-io-driver-get-allocation-errors"></a>Wewnętrzny sterownik we/wy — pobieranie błędów alokacji

**Ikona** ![ Ikona wewnętrznego pobierania sterowników we/wy](./media/user-guide/netx-events/image40.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wewnętrznego pobierania sterownika we/wy NetX.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-un-initialize"></a>Wewnętrzny sterownik we/wy — anulowanie inicjalizacji 

#### <a name="internal-io-driver-un-initialize"></a>Wewnętrzny sterownik we/wy — anulowanie inicjalizacji 

**Ikona** ![ Ikona anulowania inicjowania wewnętrznego sterownika we/wy](./media/user-guide/netx-events/image41.png)

**Opis**

To zdarzenie reprezentuje zdarzenie anulowania inicjalizacji wewnętrznego sterownika we/wy NetX.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="internal-io-driver-deferred-processing"></a>Przetwarzanie Odroczone wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-deferred-processing"></a>Przetwarzanie Odroczone wewnętrznego sterownika we/wy 

**Ikona** ![ Ikona przetwarzania odroczonego sterownika we/wy](./media/user-guide/netx-events/image42.png)

**Opis**

To zdarzenie przedstawia wewnętrzne zdarzenie przetwarzania odroczonego sterownika we/wy NetX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: długość pakietu
- Pole informacji 4: nieużywane

### <a name="arp-dynamic-entries-invalidate"></a>Unieważnianie wpisów dynamicznych ARP 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**Ikona** ![ Ikona unieważnienia wpisów dynamicznych R P](./media/user-guide/netx-events/image43.png)

**Opis**

To zdarzenie reprezentuje unieważnienie wszystkich dynamicznych ARP w całości za pośrednictwem nx_arp_dynamic_entries_invalidate.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wpisy unieważnione
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="arp-dynamic-entry-set"></a>Dynamiczny zestaw wpisów ARP 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**Ikona** ![ Ikona dynamicznego zestawu wpisów R P](./media/user-guide/netx-events/image44.png)

**Opis**

To zdarzenie reprezentuje ustawienie dynamicznego wpisu ARP za pośrednictwem nx_arp_dynamic_entry_set.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: adres fizyczny (MSW)
- Pole informacji 4: adres fizyczny (LSW)

### <a name="arp-enable"></a>Włączanie protokołu ARP 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**Ikona** ![ Ikona włączenia R P](./media/user-guide/netx-events/image45.png)

**Opis**

To zdarzenie reprezentuje włączenie protokołu ARP za pośrednictwem nx_arp_enable.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik pamięci pamięci podręcznej ARP
- Pole informacji 3: rozmiar pamięci podręcznej ARP
- Pole informacji 4: nieużywane

### <a name="arp-gratuitous-send"></a>Wysyłanie żądanie do protokołu ARP 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**Ikona** ![ Ikona wysyłania na żądanie w języku R P](./media/user-guide/netx-events/image46.png)

**Opis**

To zdarzenie reprezentuje wysyłanie bezpłatnego protokołu ARP za pośrednictwem nx_arp_gratuitous_send.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="arp-hardware-address-find"></a>Znajdowanie adresu sprzętowego ARP 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**Ikona** ![ Ikona wyszukiwania adresu sprzętu R P](./media/user-guide/netx-events/image47.png)

**Opis**

To zdarzenie reprezentuje adres fizyczny za pośrednictwem nx_arp_hardware_address_find.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: adres fizyczny (MSW)
- Pole informacji 4: adres fizyczny (LSW)

### <a name="arp-information-get"></a>Informacje o ARP 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**Ikona** ![ Ikona Get języka R P informition](./media/user-guide/netx-events/image48.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_arp_info_get.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: podsiecit wysłane
- Pole informacji 3: odpowiedzi ARP
- Pole informacji 4: Odebrano podsiecit

### <a name="arp-ip-address-find"></a>Znajdowanie adresów IP ARP 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**Ikona** ![ Ikona wyszukiwania adresu R P I P](./media/user-guide/netx-events/image49.png)

**Opis**

To zdarzenie reprezentuje adres IP skojarzony z podanym adresem fizycznym za pośrednictwem nx_arp_ip_address_find.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: adres fizyczny (MSW)
- Pole informacji 4: adres fizyczny (LSW)

### <a name="arp-static-entry-create"></a>Tworzenie wpisu statycznego ARP 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**Ikona** ![ Ikona tworzenia wpisu statycznego R P](./media/user-guide/netx-events/image50.png)

**Opis**

To zdarzenie reprezentuje tworzenie statycznego wpisu ARP za pośrednictwem nx_arp_static_entry_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: adres fizyczny (MSW)
- Pole informacji 4: adres fizyczny (LSW)

### <a name="arp-static-entries-delete"></a>Usuwanie wpisów statycznych ARP 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**Ikona** ![ Ikona usuwania wpisów statycznych R P](./media/user-guide/netx-events/image51.png)

**Opis**

To zdarzenie reprezentuje usunięcie wszystkich wpisów statycznych ARP za pośrednictwem nx_arp_static_entries_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wpisy zostały usunięte
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="arp-static-entry-delete"></a>Usuwanie wpisu statycznego ARP 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**Ikona** ![ Ikona usuwania wpisu statycznego R P](./media/user-guide/netx-events/image52.png)

**Opis**

To zdarzenie reprezentuje usunięcie statycznego wpisu ARP za pośrednictwem nx_arp_static_entry_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: adres fizyczny (MSW)
- Pole informacji 4: adres fizyczny (LSW)

### <a name="duo-cache-entry-delete"></a>Usuwanie wpisu pamięci podręcznej Duo 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**Ikona** ![ Ikona usuwania wpisu pamięci podręcznej Duo](./media/user-guide/netx-events/image53.png)

**Opis**

To zdarzenie reprezentuje usunięcie wpisu w tabeli pamięci podręcznej sąsiadów za pośrednictwem nx_udp_socket_create.

**Pola informacji** 

- Pole informacji 1: czwarty (najmniej znaczący) wyraz adresu lokalnego linku IPv6 do usunięcia
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-cache-entry-set"></a>Zestaw wpisów pamięci podręcznej Duo 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**Ikona** ![ Ikona zestawu wpisów pamięci podręcznej Duo](./media/user-guide/netx-events/image54.png)

**Opis**

To zdarzenie reprezentuje utworzenie wpisu pamięci podręcznej i dodanie go do tabeli pamięci podręcznej sąsiadów za pośrednictwem nxd_nd_cache_entry_set.

**Pola informacji** 

- Pole informacji 1: czwarty (najmniej znaczący) wyraz adresu IPv6 do dodania
- Pole informacji 2: adres fizyczny MSB
- Pole informacji 3: adres fizyczny LSB
- Pole informacji 4: nieużywane

### <a name="duo-cache-invalidate"></a>Unieważnienie pamięci podręcznej Duo 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**Ikona** ![ Ikona unieważniania pamięci podręcznej Duo](./media/user-guide/netx-events/image55.png)

**Opis**

To zdarzenie reprezentuje unieważnienie całej tabeli pamięci podręcznej sąsiadów za pośrednictwem nxd_nd_cache_invalidate.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-cache-ip-address-find"></a>Znajdź adres IP pamięci podręcznej Duo 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**Ikona** ![ Ikona znajdowania pamięci podręcznej Duo I adresu](./media/user-guide/netx-events/image56.png)

**Opis**

To zdarzenie reprezentuje pobieranie adresu IP pasującego do podanego adresu fizycznego z tabeli pamięci podręcznej za pośrednictwem nxd_nd_cache_ip_address_find.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: czwarty (najmniej znaczący) wyraz adresu IPv6
- Pole informacji 3: adres fizyczny MSB
- Pole informacji 4: adres fizyczny LSB

### <a name="duo-icmp-enable"></a>Duo — Włączanie protokołu ICMP 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**Ikona** ![ Ikona włączania Duo I C M](./media/user-guide/netx-events/image57.png)

**Opis**

To zdarzenie reprezentuje usługi ICMPv4 i ICMPv6 włączone dla określonego wystąpienia IP za pośrednictwem nxd_icmp_enable.

**Pola informacji**
- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-icmp-ping"></a>Test ping protokołu ICMP 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**Ikona** ![ Ikona polecenia ping Duo I C M P](./media/user-guide/netx-events/image58.png)

**Opis**

To zdarzenie reprezentuje wysyłanie polecenia ping (żądanie echa) do hosta IPv6 za pośrednictwem nxd_icmp_ping.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IPv6
- Pole informacji 3: wskaźnik do ECHA danych
- Pole informacji 4: rozmiar danych ECHA

### <a name="duo-ip-max-payload-size-find"></a>Maksymalny rozmiar ładunku w programie Duo — Znajdowanie 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**Ikona** ![ Ikona wyszukiwania Duo I P z maksymalnym rozmiarem ładunku](./media/user-guide/netx-events/image59.png)

**Opis**

To zdarzenie oblicza maksymalną liczbę ładunków, które może przenosić określony pakiet bez konieczności fragmentacji.

**Pola informacji**

- Pole informacji 1: wskaźnik gniazda
- Pole informacji 2: adres IP elementu równorzędnego
- Pole informacyjne 3: pole informacji o porcie równorzędnym 4: nieużywane

### <a name="duo-ip-raw-packet-send"></a>Wysyłanie pakietów pierwotnych adresów IP Duo 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**Ikona** ![ Ikona odrzuconego wysyłania pakietów w programie Duo I](./media/user-guide/netx-events/image60.png)

**Opis**

To zdarzenie reprezentuje wysyłanie pakietu pierwotnego adresu IP z określonego interfejsu sieciowego do podanego nxd_ip_raw_packet_send docelowego adresu IP.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu do wysłania
- Pole informacji 3: wskaźnik do adresu docelowego
- Pole informacji 4: Protokół pakietów

### <a name="duo-ipv6-default-router-add"></a>Dodawanie domyślnego routera IPv6 Duo 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**Ikona** ![ Ikona dodawania domyślnego routera Duo I P v 6](./media/user-guide/netx-events/image61.png)

**Opis**

To zdarzenie reprezentuje dodanie routera domyślnego do tabeli routingu IPv6 wystąpienia IP za pośrednictwem nxd_ipv6_default_router_add.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP.
- Pole informacji 2: docelowy adres sieciowy.
- Pole informacji 3: informacje o czasie życia.
- Pole informacji 4: nieużywane.

### <a name="duo-ipv6-default-router-delete"></a>Usuwanie domyślnego routera IPv6 w programie Duo 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**Ikona** ![ Ikona usuwania domyślnego routera Duo I v 6](./media/user-guide/netx-events/image62.png)

**Opis**

To zdarzenie reprezentuje usunięcie routera domyślnego z tabeli routingu IPv6 wystąpienia IP za pośrednictwem nxd_ipv6_default_router_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP.
- Pole informacji 2: czwarty wyraz (najmniej znaczący) domyślnego adresu IPv6 routera.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="duo-ipv6-enable"></a>Włącz protokół IPv6 w programie Duo 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**Ikona** ![ Ikona włączania Duo I v 6](./media/user-guide/netx-events/image63.png)

**Opis**

To zdarzenie reprezentuje włączenie usług IPv6 w podanym wystąpieniu IP za pośrednictwem nxd_ipv6_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-ipv6-global-address-get"></a>Pobieranie globalnego adresu IPv6 w programie Duo 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**Ikona** ![ Ikona uzyskiwania adresu globalnego Duo I P v 6](./media/user-guide/netx-events/image64.png)

**Opis**

To zdarzenie reprezentuje pobieranie globalnego (podstawowego) adresu IP z wystąpienia adresu IP znajdującego się w indeksie 1 w tabeli interfejsu wystąpienia IP za pośrednictwem nxd_ipv6_global_address_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP.
- Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu globalnego
- Pole informacji 3: długość prefiksu adresu IPv6.
- Pole informacji 4: indeks w tabeli interfejsów IP (1).

### <a name="duo-ipv6-global-address-set"></a>Globalny zestaw adresów IPv6 w programie Duo 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**Ikona** ![ Ikona zestawu adresów globalnych Duo I P v 6](./media/user-guide/netx-events/image65.png)

**Opis**

To zdarzenie reprezentuje globalny (podstawowy) adres IP wystąpienia adresu IP znajdującego się w indeksie 1 w tabeli interfejsu wystąpienia IP za pośrednictwem nxd_ipv6_global_address_set.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu globalnego
- Pole informacji 3: długość prefiksu adresu IPv6
- Pole informacji 4: indeksowanie w tabeli interfejsów IP (1)

### <a name="duo-ipv6-initiate-dad-process"></a>Duo — inicjowanie procesu DAD 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**Ikona** ![ Duo I P v 6 — ikona inicjowania procesu DAD](./media/user-guide/netx-events/image66.png)

**Opis**

To zdarzenie reprezentuje rozpoczęcie procesu wykrywania zduplikowanych adresów (DAD), gdy do wystąpienia IP jest przypisany link lokalny lub adres IP interfejsu za pośrednictwem nxd_ipv6_initiate_dad_process.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-ipv6-interface-address-get"></a>Pobieranie adresu interfejsu IPv6 w programie Duo 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**Ikona** ![ Ikona uzyskiwania adresu interfejsu Duo I P v 6](./media/user-guide/netx-events/image67.png)

**Opis**

To zdarzenie reprezentuje pobieranie adresu IP i prefiksu w określonym indeksie w tabeli adresów interfejsu wystąpienia IP za pośrednictwem nxd_ipv6_interface_address_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu IPv6 do zwrócenia
- Pole informacji 4: indeks interfejsu w tabeli interfejsu wystąpienia protokołu IP

### <a name="duo-ipv6-interface-address-set"></a>Zestaw adresów interfejsu IPv6 w programie Duo 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**Ikona** ![ Na ikonie "Duo I P v 6"](./media/user-guide/netx-events/image68.png)

**Opis**

To zdarzenie reprezentuje ustawienie adresu IP i prefiksu w określonym indeksie w tabeli adresów interfejsu wystąpienia IP. Niedozwolone w przypadku indeksu zerowego (łączny adres lokalny) za pośrednictwem nxd_ipv6_interface_address_set.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu IPv6 do zwrócenia
- Pole informacji 3: długość prefiksu
- Pole informacji 4: indeks interfejsu w tabeli interfejsu wystąpienia protokołu IP

### <a name="duo-ipv6-link-local-address-get"></a>Pobieranie adresu lokalnego linku do protokołu Duo 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**Ikona** ![ Ikona uzyskiwania adresu lokalnego linku Duo I P 6](./media/user-guide/netx-events/image69.png)

**Opis**

To zdarzenie reprezentuje pobieranie adresu lokalnego linku określonego wystąpienia IP za pośrednictwem nxd_ipv6_linklocal_address_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: czwarty wyraz (najmniej znaczący) adresu lokalnego łącza protokołu IP V6
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-ipv6-link-local-address-set"></a>Link IPv6 w programie Duo — zestaw adresów lokalnych 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**Ikona** ![ Ikona zestawu adresów lokalnych linku Duo I v 6](./media/user-guide/netx-events/image70.png)

**Opis**

To zdarzenie reprezentuje adres lokalny łącza wystąpienia IP za pośrednictwem nxd_ipv6_linklocal_address_set.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: czwarty (najmniej znaczący) wyraz adresu lokalnego linku IPv6
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-ipv6-raw-packet-send"></a>Wysyłanie pakietów RAW protokołu IPv6 w programie Duo 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**Ikona** ![ Ikona wysyłania pakietów pierwotnych Duo I v 6](./media/user-guide/netx-events/image71.png)

**Opis**

To zdarzenie reprezentuje wysyłanie pakietu pierwotnego adresu IP za pośrednictwem podstawowego interfejsu IP do miejsca docelowego podać za pośrednictwem nxd_ip_raw_packet_send.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu do wysłania
- Pole informacji 3: docelowy adres IP
- Pole informacji 4: nieużywane

### <a name="duo-tcp-socket-peer-info-get"></a>Pobieranie informacji o komunikacji równorzędnej gniazda TCP w programie Duo 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**Ikona** ![ Ikona pobierania informacji o komunikacji równorzędnej z gniazdami w programie Duo T C](./media/user-guide/netx-events/image72.png)

**Opis**

To zdarzenie wyodrębnia dane nadawcy z odebranego pakietu TCP w określonym gnieździe. Zwraca adres IP i port nadawcy.

**Pola informacji**

- Pole informacji 1: wskaźnik gniazda
- Pole informacji 2: adres IP elementu równorzędnego
- Pole informacji 3: Port równorzędny
- Pole informacji 4: dzierżawa o znacznym 32-bitowym adresie IP

### <a name="duo-tcp-socket-set-interface"></a>Interfejs zestawu gniazd TCP Duo 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**Ikona** ![ Ikona interfejsu zestawu gniazd w programie Duo T C](./media/user-guide/netx-events/image73.png)

**Opis**

To zdarzenie reprezentuje ustawienie interfejsu gniazda wychodzącego po połączeniu klienta z serwerem TCP na określonym adresie IP serwera za pośrednictwem nxd_tcp_client_socket_connect.

**Pola informacji** 

- Pole informacji 1: wskaźnik do gniazda TCP
- Pole informacji 2: identyfikator interfejsu
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-udp-socket-send"></a>Wysłane gniazdo UDP Duo 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**Ikona** ![ Ikona wysyłania z gniazdem Duo U D P](./media/user-guide/netx-events/image74.png)

**Opis**

To zdarzenie reprezentuje wysłanie pakietu UDP za pośrednictwem określonego gniazda z wejściowym adresem IP i portem za pośrednictwem nxd_udp_socket_send.

**Pola informacji** 

- Pole informacji 1: wskaźnik UDP gniazda
- Pole informacji 2: wskaźnik do pakietu UDP
- Pole informacji 3: długość pakietu
- Pole informacji 4: nieużywane


### <a name="duo-udp-socket-set-interface"></a>Interfejs zestawu gniazd UDP Duo 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**Ikona** ![ Ikona interfejsu zestawu gniazd w programie Duo U D](./media/user-guide/netx-events/image75.png)

**Opis**

To zdarzenie reprezentuje ustawienie określonego interfejsu wychodzącego gniazda UDP do interfejsu odpowiadającego IDENTYFIKATORowi interfejsu wejściowego za pośrednictwem nxd_udp_socket_set_interface.

**Pola informacji** 

- Pole informacji 1: wskaźnik do gniazda UDP
- Pole informacji 2: identyfikator interfejsu
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="duo-udp-source-extract"></a>Wyodrębnij Źródło UDP Duo 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**Ikona** ![ Ikona wyodrębnienia źródła w usłudze Duo U D](./media/user-guide/netx-events/image76.png)

**Opis**

To zdarzenie reprezentuje wyodrębnienie adresu IP i portu źródłowego odebranego pakietu (IPv4 lub IPv6). Jeśli IPv6, czwarty wyraz (najmniej znaczący) adresu IP jest zwracany przez nxd_udp_source_extract.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: wersja adresu IP
- Pole informacji 3: źródłowy adres IP (IPv4 lub IPv6)
- Pole informacji 4: Port źródłowy

### <a name="icmp-enable"></a>Włączanie protokołu ICMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikona** ![ Ikona włączenia I C M](./media/user-guide/netx-events/image77.png)

**Opis**

To zdarzenie reprezentuje włączenie protokołu ICMP za pośrednictwem nx_icmp_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP l;
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="icmp-information-get"></a>Informacje o protokole ICMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikona** ![ I C M P informacje o ikonie](./media/user-guide/netx-events/image78.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_icmp_info_get.

**Pola informacji**
- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wysłane polecenia ping
- Pole informacyjne 3: odpowiedzi ping
- Pole informacji 4: odebrane polecenia ping

### <a name="icmp-ping"></a>Polecenie ping protokołu ICMP 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**Ikona** ![ I C M P ikona ping](./media/user-guide/netx-events/image79.png)

**Opis**

To zdarzenie reprezentuje docelowy adres IP za pośrednictwem nx_icmp_ping.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: wskaźnik do danych
- Pole informacji 4: rozmiar danych

### <a name="igmp-enable"></a>Włączanie IGMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ikona** ![ Ikona włączenia I G M](./media/user-guide/netx-events/image80.png)

**Opis**

To zdarzenie reprezentuje włączenie protokołu IGMP za pośrednictwem nx_igmp_enable.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="igmp-information-get"></a>Informacje o protokole IGMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ikona** ![ Ikona uzyskiwania informacji o & G M](./media/user-guide/netx-events/image81.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_igmp_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wysłane raporty
- Pole informacji 3: Odebrane kwerendy
- Pole informacji 4: grupy dołączone

### <a name="igmp-loopback-disable"></a>Wyłączenie sprzężenia zwrotnego protokołu IGMP 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**Ikona** ![ Ikona wyłączenia sprzężenia zwrotnego I G M](./media/user-guide/netx-events/image82.png)

**Opis**

To zdarzenie reprezentuje wyłączenie sprzężenia zwrotnego protokołu IGMP za pośrednictwem nx_igmp_loopback_disable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="igmp-loopback-enable"></a>Włączanie sprzężenia zwrotnego protokołu IGMP 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**Ikona** ![ Ikona włączania sprzężenia zwrotnego M P](./media/user-guide/netx-events/image83.png)

**Opis**

To zdarzenie reprezentuje włączenie sprzężenia zwrotnego protokołu IGMP za pośrednictwem nx_igmp_loopback_enable.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="igmp-multicast-join"></a>Sprzężenie multiemisji IGMP 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**Ikona** ![ Ikona sprzężenia multiemisji I G M](./media/user-guide/netx-events/image84.png)

**Opis**

To zdarzenie reprezentuje grupę multiemisji za pośrednictwem nx_igmp_multicast_join.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP grupy
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="igmp-multicast-leave"></a>Wyjście z multiemisji IGMP 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**Ikona** ![ Ikona urlopu multiemisji I G M](./media/user-guide/netx-events/image85.png)

**Opis**

To zdarzenie oznacza opuszczenie grupy multiemisji za pośrednictwem nx_igmp_multicast_leave.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP grupy
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-address-change-notify"></a>Powiadomienie o zmianie adresu IP 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**Ikona** ![ Ikona powiadomienia o zmianie adresu](./media/user-guide/netx-events/image86.png)

**Opis**

To zdarzenie reprezentuje rejestrację dla powiadomienia o zmianie adresu IP za pośrednictwem nx_ip_address_change_notify.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik funkcji wywołania zwrotnego
- Pole informacji 3: dodatkowy wskaźnik informacji
- Pole informacji 4: nieużywane

### <a name="ip-address-get"></a>Pobieranie adresu IP 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**Ikona** ![ Ikona pobierania adresu](./media/user-guide/netx-events/image87.png)

**Opis**

To zdarzenie reprezentuje pobieranie adresu IP za pośrednictwem nx_ip_address_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: Maska sieci
- Pole informacji 4: nieużywane

### <a name="ip-address-set"></a>Zestaw adresów IP 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**Ikona** ![ Ikona zestawu adresów I P](./media/user-guide/netx-events/image88.png)

**Opis**

To zdarzenie reprezentuje ustawienie adresu IP za pośrednictwem nx_ip_address_set.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: Maska sieci
- Pole informacji 4: nieużywane

### <a name="ip-create"></a>Tworzenie adresu IP 

#### <a name="nx_ip_create"></a>nx_ip_create

**Ikona** ![ Ikona tworzenia](./media/user-guide/netx-events/image89.png)

**Opis**

To zdarzenie reprezentuje Tworzenie wystąpienia adresu IP za pośrednictwem nx_ip_create.

**Pola informacji** 
- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP
- Pole informacji 3: Maska sieci
- Pole informacji 4: domyślny wskaźnik puli pakietów

### <a name="ip-delete"></a>Usuwanie adresu IP 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**Ikona** ![ Ikona usuwania](./media/user-guide/netx-events/image90.png)

**Opis**

To zdarzenie reprezentuje usunięcie wystąpienia adresu IP za pośrednictwem nx_ip_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-driver-direct-command"></a>Polecenie sterownika IP Direct 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**Ikona** ![ Ikona poleceń I P sterownika](./media/user-guide/netx-events/image91.png)

**Opis**

To zdarzenie reprezentuje polecenie bezpośredniego sterownika we/wy za pośrednictwem nx_ip_driver_direct_command.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: Sterownik polecenie
- Pole informacji 3: wartość zwracana
- Pole informacji 4: nieużywane

### <a name="ip-forwarding-disable"></a>Wyłączanie przekazywania adresów IP 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**Ikona** ![ Ikona wyłączonego przesyłania dalej](./media/user-guide/netx-events/image92.png)

**Opis**

To zdarzenie przedstawia wyłączenie przesyłania dalej adresów IP za pośrednictwem nx_ip_forwarding_disable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-forwarding-enable"></a>Włączanie przekazywania adresów IP 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**Ikona** ![ Ikona włączania przesyłania dalej](./media/user-guide/netx-events/image93.png)

**Opis**

To zdarzenie reprezentuje włączenie przekazywania adresów IP za pośrednictwem nx_ip_forwarding_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-fragment-disable"></a>Wyłączenie fragmentu adresu IP 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**Ikona** ![ Ikona wyłączenia fragmentu](./media/user-guide/netx-events/image94.png)

**Opis**

To zdarzenie przedstawia wyłączenie fragmentacji adresów IP za pośrednictwem nx_ip_fragment_disable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-fragment-enable"></a>Włączanie fragmentu adresu IP 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**Ikona** ![ Ikona włączenia fragmentu](./media/user-guide/netx-events/image95.png)

**Opis**

To zdarzenie reprezentuje włączenie fragmentacji adresów IP za pośrednictwem nx_ip_fragment_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-gateway-address-set"></a>Zestaw adresów IP bramy 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**Ikona** ![ Ikona zestawu adresów bramy I](./media/user-guide/netx-events/image96.png)

**Opis**

To zdarzenie reprezentuje ustawienie adresu IP bramy za pośrednictwem nx_ip_gateway_address_set.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP bramy
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-information-get"></a>Pobieranie informacji o adresie IP 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**Ikona** ![ Ikona uzyskiwania informacji](./media/user-guide/netx-events/image97.png)

**Opis** To zdarzenie reprezentuje informacje o uzyskiwaniu adresu IP za pośrednictwem nx_ip_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: Wysłane bajty IP
- Pole informacji 3: Odebrane bajty IP
- Pole informacji 4: porzucone pakiety IP

### <a name="ip-interface-attach"></a>Dołączanie interfejsu IP 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**Ikona** ![ P Iterface ikona dołączania](./media/user-guide/netx-events/image98.png)

**Opis**

To zdarzenie reprezentuje pomocniczy interfejs sieciowy, który jest dołączany do wystąpienia IP za pośrednictwem nx_ip_interface_attach.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP interfejsu
- Pole informacji 3: indeksowanie w tabeli interfejsów IP
- Pole informacji 4: nieużywane

### <a name="ip-interface-info-get"></a>Pobieranie informacji o interfejsie IP 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**Ikona** ![ Ikona uzyskiwania informacji o interfejsie IP](./media/user-guide/netx-events/image99.png)

**Opis**

To zdarzenie reprezentuje informacje pobrane z określonego interfejsu sieciowego za pośrednictwem nx_ip_interface_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres IP interfejsu
- Pole informacyjne 3: adres MAC interfejsu MSB
- Pole informacji 4: adres MAC interfejsu LSB

### <a name="ip-raw-packet-disable"></a>Wyłączanie pierwotnego pakietu IP 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**Ikona** ![ Ikona wyłączania pakietów pierwotnych](./media/user-guide/netx-events/image100.png)

**Opis**

To zdarzenie reprezentuje wyłączenie komunikacji pakietów pierwotnych adresów IP za pośrednictwem nx_ip_raw_packet_disable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-raw-packet-enable"></a>Włączanie pakietów pierwotnych adresów IP 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**Ikona** ![ Ikona włączenia pakietu RAW](./media/user-guide/netx-events/image101.png)

**Opis**

To zdarzenie reprezentuje włączenie komunikacji pakietów pierwotnych adresów IP za pośrednictwem nx_ip_raw_packet_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="ip-raw-packet-receive"></a>Odbieranie pakietów pierwotnych adresów IP 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**Ikona** ![ Ikona odbierania pakietów RAW](./media/user-guide/netx-events/image102.png)

**Opis**

To zdarzenie reprezentuje pakiet Raw IP za pośrednictwem nx_ip_raw_packet_receive.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: opcja oczekiwania
- Pole informacji 4: nieużywane

### <a name="ip-raw-packet-send"></a>Wysyłanie pakietów Raw IP 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**Ikona** ![ Ikona wysyłania pakietów RAW](./media/user-guide/netx-events/image103.png)

**Opis**

To zdarzenie reprezentuje wysyłanie pakietów pierwotnych adresów IP za pośrednictwem nx_ip_raw_packet_send.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: docelowy adres IP
- Pole informacji 4: typ usługi

### <a name="ip-static-route-add"></a>Dodawanie statycznej trasy IP 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**Ikona** ![ Ikona dodawania trasy statycznej](./media/user-guide/netx-events/image104.png)

**Opis**

To zdarzenie reprezentuje trasę statyczną dodawaną do tabeli routingu wystąpień IP za pośrednictwem nx_ip_static_route_add.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres sieciowy
- Pole informacji 3: Maska sieci
- Pole informacji 4: Następny przeskok

### <a name="ip-static-route-delete"></a>Usuwanie statycznej trasy IP 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**Ikona** ![ & P static Rute Delete Icon](./media/user-guide/netx-events/image105.png)

**Opis**

To zdarzenie reprezentuje trasę statyczną usuwaną z tabeli routingu wystąpień IP za pośrednictwem nx_ip_static_route_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: adres sieciowy
- Pole informacji 3: Maska sieci
- Pole informacji 4: nieużywane

### <a name="ip-status-check"></a>Sprawdzenie stanu adresów IP 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**Ikona** ![ Ikona sprawdzania stanu P](./media/user-guide/netx-events/image106.png)

**Opis**

To zdarzenie reprezentuje sprawdzenie stanu IP za pośrednictwem nx_ip_status_check.

Pola informacji 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: żądany stan
- Pole informacji 3: rzeczywisty stan
- Pole informacji 4: opcja oczekiwania

### <a name="ipsec-enable"></a>Włączanie protokołu IPSEC 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**Ikona** ![ Ikona włączenia I S E C](./media/user-guide/netx-events/image107.png)

**Opis**

To zdarzenie reprezentuje włączenie usług IPSec w podanym wystąpieniu IP za pośrednictwem nx_ipsec_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="packet-allocate"></a>Przydział pakietu 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**Ikona** ![ Ikona alokacji pakietów](./media/user-guide/netx-events/image108.png)

**Opis**

To zdarzenie reprezentuje przydzielenie pakietu za pośrednictwem nx_packet_allocate.

**Pola informacji**

- Pole informacji 1: wskaźnik do puli pakietów
- Pole informacji 2: wskaźnik do przydzielenia pakietu
- Pole informacji 3: typ pakietu
- Pole informacji 4: dostępne pakiety

### <a name="packet-copy"></a>Kopiowanie pakietu 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**Ikona** ![ Ikona CPY pakietu](./media/user-guide/netx-events/image109.png)

**Opis**

To zdarzenie reprezentuje kopiowanie pakietu za pośrednictwem nx_packet_copy.

**Pola informacji**

- Pole informacji 2: Nowy wskaźnik pakietu
- Pole informacji 3: wskaźnik do puli pakietów
- Pole informacji 4: opcja oczekiwania

### <a name="packet-data-append"></a>Dołączanie danych pakietu 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**Ikona** ![ Ikona dołączania danych pakietu](./media/user-guide/netx-events/image110.png)

**Opis**

To zdarzenie reprezentuje dołączenie danych do pakietu za pośrednictwem nx_packet_data_append.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: wskaźnik do danych
- Pole informacji 3: rozmiar danych
- Pole informacji 4: wskaźnik do puli pakietów

### <a name="packet-data-extract-offset"></a>Przesunięcie wyodrębniania danych pakietu 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**Ikona** ![ Ikona przesunięcia wyodrębniania danych pakietu](./media/user-guide/netx-events/image111.png)

**Opis**

To zdarzenie reprezentuje dane pakietu, które są wyodrębniane do podanego buforu z pakietu za pośrednictwem nx_udp_source_extract_offset.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: rozmiar określonego buforu
- Pole informacji 3: liczba skopiowanych bajtów
- Pole informacji 4: nieużywane

### <a name="packet-data-retrieve"></a>Pobieranie danych pakietu 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**Ikona** ![ Ikona pobierania danych pakietu](./media/user-guide/netx-events/image112.png)

**Opis**

To zdarzenie reprezentuje pobieranie danych z pakietu za pośrednictwem nx_packet_data_retrieve.

**Pola informacji** 

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: wskaźnik do początku buforu
- Pole informacji 3: liczba skopiowanych bajtów
- Pole informacji 4: nieużywane

### <a name="packet-length-get"></a>Pobieranie długości pakietu 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**Ikona** ![ Ikona pobierania długości pakietu](./media/user-guide/netx-events/image113.png)

**Opis**

To zdarzenie reprezentuje długość pakietu za pośrednictwem nx_packet_length_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: długość pakietu
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="packet-pool-create"></a>Tworzenie puli pakietów 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**Ikona** ![ Ikona tworzenia puli pakietów](./media/user-guide/netx-events/image114.png)

**Opis**

To zdarzenie reprezentuje Tworzenie puli pakietów za pośrednictwem nx_packet_pool_create.

**Pola informacji** 

- Pole informacji 1: wskaźnik do puli pakietów
- Pole informacji 2: rozmiar ładunku pakietu
- Pole informacji 3: wskaźnik do obszaru pamięci puli
- Pole informacji 4: rozmiar obszaru pamięci puli

### <a name="packet-pool-delete"></a>Usuwanie puli pakietów 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**Ikona** ![ Ikona usuwania puli pakietów](./media/user-guide/netx-events/image115.png)

**Opis**

To zdarzenie reprezentuje Usuwanie puli pakietów za pośrednictwem nx_packet_pool_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do puli pakietów
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

#### <a name="packet-pool-information-get"></a>Pobieranie informacji o puli pakietów 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**Ikona** ![ Ikona pobierania informacji o puli pakietów](./media/user-guide/netx-events/image116.png)

**Opis**

To zdarzenie reprezentuje informacje o puli pakietów za pośrednictwem nx_packet_pool_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do puli pakietów
- Pole informacji 2: całkowita liczba pakietów
- Pole informacji 3: dostępne pakiety
- Pole informacji 4: puste żądania

### <a name="packet-release"></a>Wydanie pakietów 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**Ikona** ![ Ikona wydania pakietu](./media/user-guide/netx-events/image117.png)

**Opis**

To zdarzenie reprezentuje wydanie pakietu za pośrednictwem nx_packet_release.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: stan pakietu
- Pole informacji 3: dostępne pakiety
- Pole informacji 4: nieużywane

### <a name="packet-transmit-release"></a>Wydanie transmisji pakietu 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**Ikona** ![ Ikona wydania transmisji pakietu](./media/user-guide/netx-events/image118.png)

**Opis**

To zdarzenie reprezentuje zwalnianie pakietu nadawczego za pośrednictwem nx_packet_transmit_release.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: stan pakietu
- Pole informacji 3: dostępne pakiety
- Pole informacji 4: nieużywane

### <a name="rarp-disable"></a>RARP wyłączyć 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**Ikona** ![ Ikona wyłączenia r P](./media/user-guide/netx-events/image119.png)

**Opis**

To zdarzenie przedstawia wyłączenie RARP za pośrednictwem nx_rarp_disable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="rarp-enable"></a>Włącz RARP 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**Ikona** ![ Ikona włączenia języka r P](./media/user-guide/netx-events/image120.png)

**Opis**

To zdarzenie reprezentuje włączenie RARP za pośrednictwem nx_rarp_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="rarp-information-get"></a>RARP informacje 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**Ikona** ![ Ikona uzyskiwania informacji o języku r P](./media/user-guide/netx-events/image121.png)

**Opis**

To zdarzenie reprezentuje informacje o pobieraniu RARP za pośrednictwem nx_rarp_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wysłane żądania
- Pole informacji 3: odebrane odpowiedzi
- Pole informacji 4: nieprawidłowe odpowiedzi

### <a name="system-initialize"></a>Inicjowanie systemu 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**Ikona** ![ Ikona inicjowania systemu](./media/user-guide/netx-events/image122.png)

**Opis**

To zdarzenie reprezentuje inicjalizację NetX za pośrednictwem nx_system_initialize.

**Pola informacji**

- Pole informacji 1: nieużywane
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="tcp-client-socket-bind"></a>Powiązanie gniazda klienta TCP 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**Ikona** ![ Ikona powiązania gniazda klienta T P](./media/user-guide/netx-events/image123.png)

**Opis**

To zdarzenie reprezentuje powiązanie gniazda klienta z portem za pośrednictwem nx_tcp_client_socket_bind.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: żądany port
- Pole informacji 4: opcja oczekiwania

### <a name="tcp-client-socket-connect"></a>Połączenie gniazda klienta TCP 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**Ikona** ![ Ikona połączenia z gniazdem klienta T C P](./media/user-guide/netx-events/image124.png)

**Opis**

To zdarzenie reprezentuje połączenie gniazda klienta za pośrednictwem nx_tcp_client_socket_connect.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: adres IP serwera
- Pole informacji 4: żądany port serwera

### <a name="tcp-client-socket-port-get"></a>Pobieranie portu gniazda klienta TCP 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**Ikona** ![ Ikona pobierania portu gniazda klienta T C P](./media/user-guide/netx-events/image125.png)

**Opis**

To zdarzenie reprezentuje numer portu gniazda klienta za pośrednictwem nx_tcp_client_socket_port_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: numer portu
- Pole informacji 4: nieużywane

### <a name="tcp-client-socket-unbind"></a>Niepowiązanie gniazda klienta TCP 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**Ikona** ![ Ikona usuwania powiązania gniazda klienta T C P](./media/user-guide/netx-events/image126.png)

**Opis**

To zdarzenie reprezentuje powiązanie portu skojarzonego z gniazdem za pośrednictwem nx_tcp_client_socket_unbind.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="tcp-enable"></a>Włączanie protokołu TCP 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**Ikona** ![ Ikona włączenia P C](./media/user-guide/netx-events/image127.png)

**Opis**

To zdarzenie reprezentuje włączenie protokołu TCP za pośrednictwem nx_tcp_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>Bezpłatny port TCP Znajdź bezpłatny port TCP Znajdź 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**Ikona** ![ Ikona wyszukiwania bezpłatny port T CP](./media/user-guide/netx-events/image128.png)

**Opis**

To zdarzenie reprezentuje bezpłatny port TCP za pośrednictwem nx_tcp_free_port_find.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: uruchamianie numeru portu wyszukiwania
- Pole informacji 3: numer wolnego portu
- Pole informacji 4: nieużywane

###  <a name="tcp-infomation-get"></a>Pobieranie informacji TCP 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**Ikona** ![ Ikona pobierania informacji T C P](./media/user-guide/netx-events/image129.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji TCP dla określonego wystąpienia IP za pośrednictwem nx_tcp_info_get.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: liczba wysłanych bajtów
- Pole informacji 3: liczba odebranych bajtów
- Pole informacji 4: Liczba nieprawidłowych pakietów

###  <a name="tcp-server-socket-accept"></a>Akceptowanie gniazda serwera TCP 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**Ikona** ![ Ikona akceptowania gniazda serwera T C P](./media/user-guide/netx-events/image130.png)

**Opis**

To zdarzenie reprezentuje skonfigurowanie gniazda serwera po odebraniu żądania połączenia aktywnego za pośrednictwem nx_tcp_server_socket_accept.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: opcja oczekiwania
- Pole informacji 4: stan gniazda

###  <a name="tcp-server-socket-listen"></a>Nasłuchiwanie gniazda serwera TCP 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**Ikona** ![ Ikona lsten T C P Server Socket](./media/user-guide/netx-events/image131.png)

**Opis**

To zdarzenie przedstawia rejestrowanie żądania Listen i gniazda serwera dla określonego portu TCP za pośrednictwem nx_tcp_server_socket_listen.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: numer portu TCP
- Pole informacji 3: wskaźnik do gniazda
- Pole informacji 4: Maksymalna liczba połączeń, które można umieścić w kolejce

###  <a name="tcp-server-socket-relisten"></a>Gniazdo serwera TCP, nasłuchiwanie 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**Ikona** ![ Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image132.png)

**Opis**

To zdarzenie reprezentuje inne gniazdo serwera dla istniejącego żądania nasłuchiwania na określonym porcie TCP za pośrednictwem nx_tcp_server_socket_relisten.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: numer portu TCP
- Pole informacji 3: wskaźnik do gniazda
- Pole informacji 4: stan gniazda

###  <a name="tcp-server-socket-unaccept"></a>Nieakceptowanie gniazda serwera TCP 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**Ikona** ![ Ikona nieakceptowania gniazda serwera T C P](./media/user-guide/netx-events/image133.png)

**Opis**

To zdarzenie reprezentuje usunięcie gniazda serwera ze skojarzenia z portem, który uzyskuje wcześniejsze połączenie pasywne za pośrednictwem nx_tcp_server_socket_unaccept.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: stan gniazda
- Pole informacji 4: nieużywane

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>Niesłuchane gniazdo serwera TCP gniazda serwera TCP 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**Ikona** ![ Ikona odsłuchiwania gniazda serwera T C P](./media/user-guide/netx-events/image134.png)

**Opis**

To zdarzenie reprezentuje usunięcie poprzedniego żądania nasłuchiwania dla określonego portu TCP za pośrednictwem nx_tcp_server_socket_unlisten.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: numer portu TCP
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="tcp-socket-bytes-available"></a>Dostępne bajty gniazda TCP 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**Ikona** ![ Ikona dostępnych bajtów gniazda T C](./media/user-guide/netx-events/image135.png)

**Opis**

To zdarzenie reprezentuje liczbę aktualnie dostępnych bajtów w określonym gnieździe odbioru TCP za pośrednictwem nx_tcp_socket_bytes_available.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda TCP
- Pole informacji 3: bajty odebrane w gnieździe
- Pole informacji 4: nieużywane

### <a name="tcp-socket-create"></a>Tworzenie gniazda TCP 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**Ikona** ![ Ikona tworzenia gniazda T C P](./media/user-guide/netx-events/image136.png)

**Opis**

To zdarzenie reprezentuje tworzenie gniazda TCP za pośrednictwem nx_tcp_socket_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: typ usługi
- Pole informacji 4: rozmiar okna odbierania

### <a name="tcp-socket-delete"></a>Usuwanie gniazda TCP 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**Ikona** ![ Ikona usuwania gniazda T C P](./media/user-guide/netx-events/image137.png)

**Opis**

To zdarzenie reprezentuje usunięcie gniazda za pośrednictwem nx_tcp_socket_delete.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: stan gniazda
- Pole informacji 4: nieużywane

### <a name="tcp-socket-disconnect"></a>Połączenie gniazda TCP 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**Ikona** ![ Ikona rozłączenia gniazda T C P](./media/user-guide/netx-events/image138.png)

**Opis**

To zdarzenie reprezentuje odłączenie gniazda za pośrednictwem nx_tcp_socket_disconnect.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: opcja oczekiwania
- Pole informacji 4: stan gniazda

### <a name="tcp-socket-information-get"></a>Pobieranie informacji o gnieździe TCP 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**Ikona** ![ Ikona uzyskiwania informacji o gnieździe T C P](./media/user-guide/netx-events/image139.png)

**Opis**

To zdarzenie reprezentuje informacje o gnieździe za pośrednictwem nx_tcp_socket_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: Bajty wysłane przez to gniazdo
- Pole informacji 4: bajty odebrane przez to gniazdo

### <a name="tcp-socket-mss-get"></a>Pobieranie z gniazda TCP Socket 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**Ikona** ![ T C P gniazdo M S S Uzyskaj ikonę](./media/user-guide/netx-events/image140.png)

**Opis**

To zdarzenie reprezentuje pobieranie danych o przełączeniu gniazda za pośrednictwem nx_tcp_socket_mss_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: maksymalny rozmiar segmentu (Identyfikator
- Pole informacji 4: stan gniazda

### <a name="tcp-socket-mss-peer-get"></a>Pobieranie elementu równorzędnego w gnieździe TCP Socket 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**Ikona** ![ Ikona pobierania elementów równorzędnych T C P Socket M s](./media/user-guide/netx-events/image141.png)

**Opis**

To zdarzenie reprezentuje wartość parametru "/średnika" elementu równorzędnego gniazda za pośrednictwem nx_tcp_socket_mss_peer_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: rozmiar elementu równorzędnego
- Pole informacji 4: stan gniazda

### <a name="tcp-socket-mss-set"></a>Zestaw o wartościach sieciowych TCP Socket 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**Ikona** ![ Ikona zestawu M S w gnieździe T C](./media/user-guide/netx-events/image142.png)

**Opis**

To zdarzenie reprezentuje ustawienie parametru o przełączeniu gniazda za pośrednictwem nx_tcp_socket_mss_set.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: profilowanie
- Pole informacji 4: stan gniazda

### <a name="tcp-socket-peer-info-get"></a>Pobieranie informacji o komunikacji równorzędnej gniazda TCP 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**Ikona** ![ Ikona pobierania informacji o komunikacji równorzędnej gniazda T C](./media/user-guide/netx-events/image143.png)

**Opis**

To zdarzenie reprezentuje informacje pobrane z gniazda TCP dotyczące elementu równorzędnego (np. >łączenia hosta) i portu IP za pośrednictwem nx_tcp_socket_peer_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do gniazda TCP
- Pole informacji 2: adres IP elementu równorzędnego
- Pole informacji 3: numer portu elementu równorzędnego
- Pole informacji 4: nieużywane

### <a name="tcp-socket-receive"></a>Odbieranie gniazda TCP 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**Ikona** ![ Ikona odbioru gniazda T C P](./media/user-guide/netx-events/image144.png)

**Opis**

To zdarzenie reprezentuje dane odebrane z gniazda za pośrednictwem nx_tcp_socket_receive.

**Pola informacji**

- Pole informacji 1: wskaźnik do gniazda
- Pole informacji 2: wskaźnik do odebranego pakietu
- Pole informacji 3: Odebrano długość pakietu
- Pole informacji 4: numer sekwencyjny odbioru

### <a name="tcp-socket-receive-notify"></a>Powiadomienie o odebraniu gniazda TCP 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**Ikona** ![ Ikona powiadomienia o odebraniu gniazda T C P](./media/user-guide/netx-events/image145.png)

**Opis**

To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego powiadomienia o odebraniu dla gniazda za pośrednictwem nx_tcp_socket_receive_notify.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: wskaźnik otrzymywania powiadomienia o wywołaniu zwrotnym pole 4: nieużywane

### <a name="tcp-socket-send"></a>Wysyłanie gniazda TCP 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**Ikona** ![ Ikona wysyłania gniazda T C P](./media/user-guide/netx-events/image146.png)

**Opis**

To zdarzenie reprezentuje wysyłanie danych w gnieździe za pośrednictwem nx_tcp_socket_send.

**Pola informacji**

- Pole informacji 1: wskaźnik do gniazda
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: długość pakietu
- Pole informacji 4: numer sekwencyjny transmisji

### <a name="tcp-socket-state-wait"></a>Oczekiwanie na stan gniazda TCP 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**Ikona** ![ Ikona oczekiwania stanu gniazda T C P](./media/user-guide/netx-events/image147.png)

**Opis**

To zdarzenie reprezentuje oczekiwanie, aż gniazdo wprowadzi określony stan za pośrednictwem nx_tcp_socket_state_wait.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: żądany stan gniazda
- Pole informacji 4: poprzedni stan gniazda

### <a name="tcp-socket-transmit-configure"></a>Konfigurowanie transmisji gniazda TCP 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**Ikona** ![ Ikona wysyłania gniazda sieciowego T C P](./media/user-guide/netx-events/image148.png)

**Opis**

To zdarzenie reprezentuje konfigurację opcji przesyłania dla gniazda za pośrednictwem nx_tcp_socket_transmit_configure.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: przekazywanie głębokości kolejki
- Pole informacji 4: wartość limitu czasu

### <a name="tcp-socket-window-update-notify-set"></a>Zestaw powiadomień o aktualizacji okna gniazda TCP 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**Ikona** ![ Ikona zestawu powiadomień o aktualizacji okna gniazda T C](./media/user-guide/netx-events/image149.png)

**Opis**

To zdarzenie reprezentuje gniazdo TCP odbierające powiadomienie o zwiększeniu okna odbierania hosta zdalnego za pośrednictwem nx_tcp_window_update_notify_set.

**Pola informacji** 

- Pole informacji 1: wskaźnik do gniazda TCP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="udp-enable"></a>Włączanie protokołu UDP 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**Ikona** ![ Ikona włączenia u D P](./media/user-guide/netx-events/image150.png)

**Opis**

To zdarzenie reprezentuje włączenie protokołu UDP za pośrednictwem nx_udp_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: nieużywane
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="udp-free-port-find"></a>Znajdowanie portów bezpłatnych UDP 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**Ikona** ![ Ikona Znajdź bezpłatny port U D P](./media/user-guide/netx-events/image151.png)

**Opis**

To zdarzenie reprezentuje bezpłatny port UDP za pośrednictwem nx_udp_free_port_find.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: uruchamianie portu w celu wyszukania
- Pole informacji 3: Port bezpłatny
- Pole informacji 4: nieużywane

### <a name="udp-information-get"></a>Pobieranie informacji o UDP 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**Ikona** ![ Ikona pobierania informacji u D P](./media/user-guide/netx-events/image152.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji za pośrednictwem nx_udp_info_get.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: Wysłane bajty UDP
- Pole informacji 3: Odebrane bajty UDP
- Pole informacji 4: nieprawidłowe pakiety

### <a name="udp-socket-bind"></a>Powiązanie gniazda UDP 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**Ikona** ![ Ikona powiązania z gniazdem u D P](./media/user-guide/netx-events/image153.png)

**Opis**

To zdarzenie reprezentuje połączenie gniazda UDP z portem za pośrednictwem nx_udp_socket_bind.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: numer portu
- Pole informacji 4: opcja oczekiwania

### <a name="udp-socket-bytes-available"></a>Dostępne bajty gniazda UDP 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**Ikona** ![ Ikona U-D P Sockets available](./media/user-guide/netx-events/image154.png)

**Opis**

To zdarzenie reprezentuje bieżącą liczbę bajtów odebranych w gnieździe UDP za pośrednictwem nx_udp_socket_bytes_available.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: bajty odebrane w gnieździe
- Pole informacji 4: nieużywane

### <a name="udp-socket-checksum-disable"></a>Wyłączenie sumy kontrolnej gniazda UDP 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**Ikona** ![ Ikona wyłączenia sumy kontrolnej P D w gnieździe](./media/user-guide/netx-events/image155.png)

**Opis**

To zdarzenie przedstawia wyłączenie sumy kontrolnej dla danych w gnieździe UDP za pośrednictwem nx_udp_socket_checksum_disable.

**Pola informacji** 

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="udp-socket-checksum-enable"></a>Włączono sumę kontrolną gniazda UDP 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**Ikona** ![ Ikona włączenia sumy kontrolnej w gnieździe u D P](./media/user-guide/netx-events/image156.png)

**Opis**

To zdarzenie reprezentuje włączenie przetwarzania sumy kontrolnej w gnieździe za pośrednictwem nx_udp_socket_checksum_enable.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="udp-socket-create"></a>Tworzenie gniazda UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikona** ![ Ikona tworzenia gniazda P D](./media/user-guide/netx-events/image157.png)

**Opis**

To zdarzenie reprezentuje tworzenie gniazda UDP za pośrednictwem nx_udp_socket_create.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: typ usługi
- Pole informacji 4: Maksymalna Kolejka odbierania

### <a name="udp-socket-delete-event"></a>Zdarzenie usunięcia gniazda UDP 

#### <a name="nx_udp_socket_delete-event"></a>zdarzenie nx_udp_socket_delete

**Ikona** ![ Ikona zdarzenia usuwania gniazda P D](./media/user-guide/netx-events/image158.png)

**Opis**

To zdarzenie przedstawia usuwanie gniazda UDP za pośrednictwem nx_udp_socket_delete.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="udp-socket-information-get-event"></a>Zdarzenie pobierania informacji o gnieździe UDP 

#### <a name="nx_udp_socket_info_get-event"></a>zdarzenie nx_udp_socket_info_get

**Ikona** ![ Ikona zdarzenia odczytaj informacje o gnieździe U D P](./media/user-guide/netx-events/image159.png)

**Opis**

To zdarzenie reprezentuje informacje o gnieździe UDP za pośrednictwem nx_udp_socket_info_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: Bajty wysłane przez gniazdo
- Pole informacji 4: bajty odebrane przez gniazdo

### <a name="udp-socket-interface-set"></a>Zestaw interfejsów gniazda UDP 

#### <a name="nx_udp_socket_interface_set-event"></a>zdarzenie nx_udp_socket_interface_set

**Ikona** ![ Ikona ustawienia interfejsu gniazda P D Socket](./media/user-guide/netx-events/image160.png)

**Opis**

To zdarzenie reprezentuje ustawienie interfejsu wychodzącego określonego gniazda UDP z określonym interfejsem za pośrednictwem nx_udp_socket_interface_set.

**Pola informacji**

- Pole informacji 1: wskaźnik do gniazda UDP
- Pole informacji 2: indeks odpowiadający interfejsowi gniazda
- Pole informacji 3: nieużywane
- Pole informacji 4: nieużywane

### <a name="udp-socket-port-get"></a>Pobieranie portu gniazda UDP 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**Ikona** ![ Ikona pobierania portu gniazda P D](./media/user-guide/netx-events/image161.png)

**Opis**

To zdarzenie reprezentuje pobieranie portu UDP, z którym powiązana jest określone gniazdo UDP za pośrednictwem nx_udp_socket_port_get.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda UDP
- Pole informacji 3: numer portu
- Pole informacji 4: nieużywane

### <a name="udp-socket-receive"></a>Odbieranie gniazda UDP 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**Ikona** ![ Ikona odbioru w gnieździe U D P](./media/user-guide/netx-events/image162.png)

**Opis**

To zdarzenie reprezentuje dane odebrane w określonym gnieździe UDP za pośrednictwem nx_udp_socket_receive.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda UDP
- Pole informacji 3: wskaźnik do odebranego pakietu
- Pole informacji 4: Odebrano rozmiar pakietu

### <a name="udp-socket-receive-notify"></a>Powiadomienie o odebraniu gniazda UDP 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**Ikona** ![ Ikona powiadomienia o odebraniu gniazda P ](./media/user-guide/netx-events/image163.png) D 

To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego powiadomienia o odebraniu za pośrednictwem nx_udp_socket_receive_notify.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacyjne 3: wskaźnik otrzymywania informacji o funkcji powiadamiania 4: nieużywane

### <a name="udp-socket-send"></a>Wysyłanie gniazda UDP 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**Ikona** ![ Ikona wysyłania w gnieździe u D P](./media/user-guide/netx-events/image164.png)

**Opis**

To zdarzenie reprezentuje wysyłanie danych za pośrednictwem gniazda UDP za pośrednictwem nx_udp_socket_send.

**Pola informacji**

- Pole informacji 1: wskaźnik do gniazda
- Pole informacji 2: wskaźnik do pakietu
- Pole informacji 3: długość pakietu
- Pole informacji 4: docelowy adres IP

### <a name="udp-socket-unbind"></a>Niepowiązanie gniazda UDP 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**Ikona** ![ Ikona nieusuwania powiązania U gniazda P D](./media/user-guide/netx-events/image165.png)

**Opis**

To zdarzenie reprezentuje powiązanie portu UDP z gniazdem za pośrednictwem nx_udp_socket_unbind.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP
- Pole informacji 2: wskaźnik do gniazda
- Pole informacji 3: numer portu
- Pole informacji 4: nieużywane

### <a name="udp-source-extract"></a>Wyodrębnij Źródło UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ikona** ![ Ikona wyodrębnienia źródła U D P](./media/user-guide/netx-events/image166.png)

**Opis**

To zdarzenie reprezentuje adres IP i numer portu odebranego pakietu UDP za pośrednictwem nx_udp_source_extract.

**Pola informacji**

- Pole informacji 1: wskaźnik do pakietu
- Pole informacji 2: adres IP nadawcy
- Pole informacji 3: numer portu nadawcy
- Pole informacji 4: nieużywane