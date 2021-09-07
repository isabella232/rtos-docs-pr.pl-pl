---
title: Rozdział 5 — Azure RTOS sieciowe NetX Duo
description: Ten rozdział zawiera opis sterowników sieciowych dla Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30e14ce1865e2fbce4a6e00cff787c859b32be
ms.sourcegitcommit: 20a136b06a25e31bbde718b4d12a03ddd8db9051
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2021
ms.locfileid: "123552419"
---
# <a name="chapter-5---azure-rtos-netx-duo-network-drivers"></a>Rozdział 5 — Azure RTOS sieciowe NetX Duo

Ten rozdział zawiera opis sterowników sieciowych dla Azure RTOS NetX Duo. Przedstawione informacje mają ułatwić deweloperom pisanie sterowników sieciowych specyficznych dla aplikacji dla oprogramowania NetX Duo.

## <a name="driver-introduction"></a>Wprowadzenie do sterowników

Struktura NX_IP zawiera wszystkie elementy do zarządzania pojedynczym wystąpieniem adresu IP. Obejmuje to ogólne informacje o protokole TCP/IP, a także procedurę wprowadzania sterownika sieci fizycznej specyficznej dla aplikacji. Procedura wprowadzania sterownika jest definiowana podczas ***nx_ip_create** _ usługi. Dodatkowe urządzenia można dodać do wystąpienia adresu IP za pośrednictwem usługi _ *_nx_ip_interface_attach_**.

Komunikacja między aplikacją NetX Duo a sterownikiem sieciowym aplikacji jest NX_IP_DRIVER **struktury** żądań. Ta struktura jest najczęściej definiowana lokalnie na stosie wywołującym i dlatego jest zwalniana po zwróceniu sterownika i funkcji wywołującej. Struktura jest zdefiniowana w następujący sposób.

```c
typedef struct NX_IP_DRIVER_STRUCT
{
      UINT           nx_ip_driver_command;
      UINT           nx_ip_driver_status;
      ULONG          nx_ip_driver_physical_address_msw;
      ULONG          nx_ip_driver_physical_address_lsw;
      NX_PACKET      *nx_ip_driver_packet;
      ULONG          *nx_ip_driver_return_ptr;
      NX_IP          *nx_ip_driver_ptr;
      NX_INTERFACE   *nx_ip_driver_interface;01
} NX_IP_DRIVER;
```
## <a name="driver-entry"></a>Wpis sterownika 

NetX Duo wywołuje funkcję wprowadzania sterownika sieciowego w celu inicjowania sterowników oraz wysyłania pakietów oraz różnych operacji sterowania i stanu, w tym inicjowania i włączania urządzenia sieciowego. NetX Duo wydaje polecenia sterownikowi siecioweowi, ustawiając ***nx_ip_driver_command** _ w strukturze żądań _ *NX_IP_DRIVER**. Funkcja wprowadzania sterownika ma następujący format:

```c
VOID my_driver_entry(NX_IP_DRIVER *request);
```
## <a name="driver-requests"></a>Żądania sterowników

NetX Duo tworzy żądanie sterownika za pomocą określonego polecenia i wywołuje funkcję wprowadzania sterownika w celu wykonania polecenia. Ponieważ każdy sterownik sieciowy ma jedną funkcję wprowadzania, netX Duo wykonuje wszystkie żądania za pośrednictwem struktury danych żądania sterownika. ***nx_ip_driver_command** _ struktury danych żądania sterownika (_*NX_IP_DRIVER**) definiuje żądanie. Informacje o stanie są zgłaszane z powrotem do wywołującego w członkowskim **_nx_ip_driver_status_*_. Jeśli to pole ma wartość _*NX_SUCCESS**, żądanie sterownika zostało ukończone pomyślnie.

NetX Duo serializuje cały dostęp do sterownika. W związku z tym sterownik nie musi obsługiwać wielu wątków asynchronicznie wywołując funkcję entry. Należy pamiętać, że funkcja sterownika urządzenia jest wykonywana z zablokowanym obiektem mutex adresu IP. W związku z tym funkcja wewnętrzna sterownika urządzenia nie powinna blokować się.

Zazwyczaj sterownik urządzenia obsługuje również przerwania. W związku z tym wszystkie funkcje sterowników muszą być bezpieczne przed przerywaniami.

### <a name="driver-initialization"></a>Inicjowanie sterownika   
Mimo że rzeczywiste przetwarzanie inicjowania sterownika jest specyficzne dla aplikacji, zwykle składa się ono ze struktury danych i inicjalizacji sprzętu fizycznego. Informacje wymagane przez netX Duo do inicjowania sterowników to maksymalna jednostka transmisji IP (MTU), która jest liczbą bajtów dostępnych dla ładunku warstwy IP, w tym nagłówkiem IPv4 lub IPv6, oraz informacjami o tym, czy interfejs fizyczny wymaga mapowania logicznego na fizyczny. Sterownik konfiguruje wartość jednostki MTU interfejsu przez wywołanie ***nx_ip_interface_mtu_set***.

Sterownik urządzenia musi wywołać wywołanie ***nx_ip_interface_address_mapping_configure _, aby** poinformować netX Duo, czy mapowanie adresów interfejsu jest wymagane. Jeśli wymagane jest mapowanie adresów, sterownik jest odpowiedzialny za konfigurowanie interfejsu przy użyciu prawidłowego adresu MAC i dostarczanie adresu MAC do NetX za pośrednictwem __*_ nx_ip_interface_physical_address_set **.

Gdy sterownik sieciowy odbiera żądanie NX_LINK INITIALIZE z netX Duo, otrzymuje wskaźnik do bloku sterowania ip w ramach bloku sterowania żądaniami NX_IP_DRIVER pokazanym powyżej.

Gdy aplikacja wywołuje ***nx_ip_create***, wątek pomocnika IP wysyła żądanie sterownika z poleceniem ustawionym na NX_LINK_INITIALIZE do sterownika w celu zainicjowania jego fizycznego interfejsu sieciowego. Następujące NX_IP_DRIVER są używane do inicjowania żądania.

| NX_IP_DRIVER &nbsp; członkowski | Znaczenie    |
| ------------------------- | ----------------------------- |
| nx_ip_driver_command   | NX_LINK_INITIALIZE    |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP. Ta wartość powinna zostać zapisana przez sterownik, aby funkcja sterownika znalazła wystąpienie adresu IP, na którym będzie działać.    |
| nx_ip_driver_interface | Wskaźnik do struktury interfejsu sieciowego w wystąpieniu adresu IP. Te informacje powinny zostać zapisane przez sterownik. Podczas odbierania pakietów sterownik musi używać informacji o strukturze interfejsu podczas wysyłania pakietu do stosu. Indeks interfejsu (indeks urządzenia) można uzyskać, odczytując dane nx_interface_index wewnątrz tej struktury danych. |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może zainicjować określonego interfejsu do wystąpienia adresu IP, zwróci stan błędu niezerowego. |


> [!NOTE]  
> *Sterownik jest w rzeczywistości wywoływany z wątku pomocnika IP, który został utworzony dla wystąpienia adresu IP. W związku z tym procedura* sterownika powinna unikać wykonywania operacji blokujących lub wątek pomocnika IP może zostać zatrzymany, powodując niepowiązane opóźnienia dla aplikacji, które korzystają z wątku ip .

### <a name="enable-link"></a>Włącz link   
Następnie wątek pomocnika IP włącza sieć fizyczną, ustawiając polecenie sterownika na NX_LINK_ENABLE w żądaniu sterownika i wysyłając żądanie do sterownika sieciowego. Dzieje się tak wkrótce po ukończeniu żądania inicjowania przez wątek pomocnika IP. Włączenie linku może być tak proste, jak ustawienie *nx_interface_link_up* w wystąpieniu interfejsu. Może jednak również obejmować manipulowanie sprzętem fizycznym. Następujące elementy NX_IP_DRIVER są używane do żądania linku włączania.

| NX_IP_DRIVER &nbsp; członkowski       | Znaczenie                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_ENABLE   |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP  |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może włączyć określonego interfejsu, zwróci stan błędu niezerowego. |

### <a name="disable-link"></a>Wyłącz link   
To żądanie jest dokonywane przez firmę NetX Duo podczas usuwania wystąpienia adresu IP przez usługę ***nx_ip_delete** _. Aplikacja może też wydać to polecenie w celu tymczasowego wyłączenia linku w celu zaoszczędzenia zasilania. Ta usługa wyłącza fizyczny interfejs sieciowy w wystąpieniu adresu IP. Przetwarzanie w celu wyłączenia linku może być tak proste, jak wyczyszczenie _flagi nx_interface_link_up* w wystąpieniu interfejsu. Może jednak również obejmować manipulowanie sprzętem fizycznym. Zazwyczaj jest to odwrotna operacja * Włącz **łącze.**_ Po wyłączeniu linku żądanie aplikacji _ *_Włącz link_** umożliwia włączenie interfejsu.

Następujące elementy NX_IP_DRIVER są używane do żądania wyłączenia linku.

| NX_IP_DRIVER &nbsp; członkowski     | Znaczenie                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_DISABLE    |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP   |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu   |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może wyłączyć określonego interfejsu w wystąpieniu adresu IP, zwróci stan błędu niezerowy. |

### <a name="uninitialize-link"></a>Uninitialize Link   
To żądanie jest dokonywane przez firmę NetX Duo podczas usuwania wystąpienia adresu IP przez usługę ***nx_ip_delete** _. To żądanie niezainicjuje interfejs i zwalnia wszystkie zasoby utworzone w fazie inicjowania. Zazwyczaj jest to odwrotna operacja operacji _ *_Initialize Link_**. Po nieocenione interfejsu nie można używać urządzenia, dopóki interfejs nie zostanie zainicjowany ponownie.

Następujące elementy NX_IP_DRIVER są używane do żądania wyłączenia linku.

| NX_IP_DRIVER &nbsp; członkowski    | Znaczenie                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_UNINITIALZE      |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP   |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie jest w stanie niezainicjować określonego interfejsu do wystąpienia adresu IP, zwróci stan błędu niezerowy. |

### <a name="packet-send"></a>Wysyłanie pakietów   
To żądanie jest dokonywane podczas wewnętrznego przetwarzania wysyłania IPv4 lub IPv6, którego wszystkie protokoły NetX Duo używają do przesyłania pakietów (z wyjątkiem ARP, RARP). Po otrzymaniu polecenia wysyłania  pakietów nx_packet_prepend_ptr wskazuje początek wysyłanego pakietu, który jest początek nagłówka IPv4 lub IPv6. *nx_packet_length* wskazuje całkowity rozmiar (w bajtach) przesyłanych danych. Jeśli *nx_packet_next* jest prawidłowy, wychodzący datagram adresu IP jest przechowywany w wielu pakietach, sterownik musi śledzić łańcuchowy pakiet i przesyłać całą ramkę. Należy pamiętać, że prawidłowy obszar danych w każdym pakiecie łańcuchowym jest przechowywany między *nx_packet_prepend_ptr* i *nx_packet_append_ptr*.

Sterownik jest odpowiedzialny za konstruowanie nagłówka fizycznego. Jeśli wymagane jest mapowanie adresu fizycznego na adres IP (np. Ethernet), warstwa IP rozpoznała już adres MAC. Docelowy adres MAC jest przekazywany z wystąpienia adresu IP przechowywanego w nx_ip_driver_physical_address_msw *i nx_ip_driver_physical_address_lsw*.

Po dodaniu nagłówka fizycznego przetwarzanie wysyłania pakietów wywołuje funkcję wyjściową sterownika, aby przesłać pakiet.

Następujące elementy NX_IP_DRIVER są używane do żądania wysyłania pakietów.

| NX_IP_DRIVER &nbsp; członkowski              | Znaczenie                               |
| -----------------------------------| --------------------------------------|
| nx_ip_driver_command            | NX_LINK_PACKET_SEND                |
| nx_ip_driver_ptr                | Wskaźnik do wystąpienia adresu IP                |
| nx_ip_driver_packet             | Wskaźnik do pakietu do wysłania         |
| nx_ip_driver_interface          | Wskaźnik do wystąpienia interfejsu.    |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32-bitowe fizycznego adresu (tylko wtedy, gdy wymagane jest mapowanie fizyczne) |
| nx_ip_driver_physical_address_lsw | Najmniej znaczący 32-bitowy adres fizyczny (tylko wtedy, gdy wymagane jest mapowanie fizyczne) |
| nx_ip_driver_status             | Stan ukończenia. Jeśli sterownik nie jest w stanie wysłać pakietu, zwróci stan błędu niezerowego. |

### <a name="packet-broadcastipv4-packets-only"></a>Emisje pakietów (tylko pakiety IPv4)  
To żądanie jest niemal identyczne z żądaniem wysyłania pakietu. Jedyna różnica polega na tym, że pola docelowego adresu fizycznego są ustawione na adres MAC emisji Ethernet. Następujące elementy NX_IP_DRIVER są używane do żądania emisji pakietów.

| NX_IP_DRIVER &nbsp; członkowski                | Znaczenie                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST                                                                                 |
| nx_ip_driver_ptr                   | Wskaźnik do wystąpienia adresu IP                                                                                   |
| nx_ip_driver_packet                | Wskaźnik do pakietu do wysłania                                                                            |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (emisja)                                                                                   |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (emisja)                                                                                   |
| nx_ip_driver_interface             | Wskaźnik do wystąpienia interfejsu.                                                                       |
| nx_ip_driver_status                | Stan ukończenia. Jeśli sterownik nie jest w stanie wysłać pakietu, zwróci stan błędu niezerowego. |

### <a name="arp-send"></a>Wysyłanie ARP  
To żądanie jest również podobne do żądania wysyłania pakietów IP. Jedyna różnica polega na tym, że nagłówek Ethernet określa pakiet ARP zamiast pakietu IP, a pola docelowego adresu fizycznego są ustawione na adres emisji MAC. Następujące elementy NX_IP_DRIVER są używane dla żądania wysłania ARP.

| NX_IP_DRIVER &nbsp; członkowski                | Znaczenie                                                                                                      |
|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_ARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Wskaźnik do wystąpienia adresu IP                                                                                       |
| nx_ip_driver_packet                | Wskaźnik do pakietu do wysłania                                                                                |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (emisja)                                                                                       |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (emisja)                                                                                       |
| nx_ip_driver_interface             | Wskaźnik do wystąpienia interfejsu.                                                                           |
| nx_ip_driver_status                | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu ARP, zwróci stan błędu niezerowego. |

> [!IMPORTANT]  
> *Jeśli mapowanie fizyczne nie jest wymagane, implementacja tego żądania nie jest wymagana.*

Mimo że protokół ARP został zastąpiony protokołem odnajdywania sąsiadów i protokołem odnajdywania routerów w protokole IPv6, sterowniki sieciowe Ethernet muszą być nadal zgodne z routerami i równorzędne *IPv4. W związku z tym sterowniki muszą nadal obsługiwać pakiety ARP.*

### <a name="arp-response-send"></a>Wysyłanie odpowiedzi ARP  
To żądanie jest niemal identyczne z żądaniem wysyłania pakietu ARP. Jedyna różnica polega na tym, że pola docelowego adresu fizycznego są przekazywane z wystąpienia adresu IP. Następujące elementy NX_IP_DRIVER są używane do żądania wysłania odpowiedzi ARP.

| NX_IP_DRIVER &nbsp; członkowski                  | Znaczenie                                  |
| -------------------------------------- | -----------------------------------------|
| nx_ip_driver_command                | NX_LINK_ARP_RESPONSE_SEND            |
| nx_ip_driver_ptr                    | Wskaźnik do wystąpienia adresu IP   |
| nx_ip_driver_packet                 | Wskaźnik do pakietu do wysłania          |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32-bitowe fizycznego adresu |
| nx_ip_driver_physical_address_lsw | Najmniej znaczący 32-bitowy adres fizyczny |
| nx_ip_driver_interface              | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status                 | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu ARP, zwróci stan błędu niezerowego. |

> [!IMPORTANT]  
> *Jeśli mapowanie fizyczne nie jest wymagane, implementacja tego żądania nie jest wymagana.*

### <a name="rarp-send"></a>Wysyłanie RARP   
To żądanie jest niemal identyczne z żądaniem wysyłania pakietu ARP. Jedynymi różnicami są typ nagłówka pakietu i pola adresu fizycznego nie są wymagane, ponieważ miejsce docelowe fizyczne jest zawsze adresem emisji.

W przypadku żądania NX_IP_DRIVER RARP są używane następujące elementy członkowskie.

| NX_IP_DRIVER &nbsp; członkowski                | Znaczenie                                                                                                       |
|------------------------------------|---------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_RARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Wskaźnik do wystąpienia adresu IP                                                                                        |
| nx_ip_driver_packet                | Wskaźnik do pakietu do wysłania                                                                                 |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (emisja)                                                                                        |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (emisja)                                                                                        |
| nx_ip_driver_interface             | Wskaźnik do wystąpienia interfejsu.                                                                            |
| nx_ip_driver_status                | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu RARP, zwróci stan błędu niezerowy. |

> [!IMPORTANT]  
> *Aplikacje, które wymagają usługi RARP, muszą zaimplementować to polecenie*.

### <a name="multicast-group-join"></a>Przyłączenie do grupy multiemisji   
To żądanie jest dokonywane przy użyciu usługi ***nx_igmp_multicast_interface join** _ i _*_nx_ipv4_multicast_interface_join_*_ w protokole IPv4, usługi _ *_nxd_ipv6_multicast_interface_join_** w protokole IPv6 i różnych operacji wymaganych przez protokół IPv6. Sterownik sieciowy pobiera podany adres grupy multiemisji i konfiguruje nośnik fizyczny do akceptowania pakietów przychodzących z tego adresu grupy multiemisji. Należy pamiętać, że w przypadku sterowników, które nie obsługują filtru multiemisji, logika odbierania sterowników może być w trybie promiscuous. W takim przypadku sterownik może wymagać filtrowania klatek przychodzących na podstawie docelowego adresu MAC, co zmniejsza ilość ruchu przekazywanego do wystąpienia adresu IP. Następujące elementy NX_IP_DRIVER są używane dla żądania dołączenia do grupy multiemisji.

| NX_IP_DRIVER &nbsp; członkowski                  | Znaczenie                                 |
| -------------------------------------- | --------------------------------------- |
| nx_ip_driver_command                | NX_LINK_MULTICAST_JOIN               |
| nx_ip_driver_ptr                    | Wskaźnik do wystąpienia adresu IP  |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32-bitowe fizycznego adresu multiemisji |
| nx_ip_driver_physical_address_lsw | Najmniej znaczące 32-bitowe fizycznego adresu multiemisji |
| nx_ip_driver_interface              | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status                 | Stan ukończenia. Jeśli sterownik nie może dołączyć do grupy multiemisji, zwraca niezerowy stan błędu. |

> [!NOTE]  
> *Aplikacje IPv6 wymagają zaimplementowania multiemisji w sterowniku dla protokołów opartych na protokole ICMPv6, takich jak konfiguracja adresu. Jednak w przypadku aplikacji protokołu IPv4 implementacja tego* żądania nie jest konieczna, jeśli możliwości multiemisji nie są wymagane.

> [!IMPORTANT]  
> *Jeśli protokół IPv6 nie jest włączony, a* funkcje multiemisji nie są wymagane przez protokół IPv4, implementacja tego żądania nie jest wymagana.

### <a name="multicast-group-leave"></a>Pozostawienie grupy multiemisji  
To żądanie jest wywoływane przez jawne wywołanie usług ***nx_igmp_multicast_interface_leave** _ lub _*_nx_ipv4_multicast_interface_leave_*_ w protokole IPv4, _ *_nxd_ipv6_multicast_interface_leave_** usługi w protokole IPv6 lub przez różne wewnętrzne operacje NetX Duo wymagane dla protokołu IPv6. Sterownik usuwa podany adres multiemisji Ethernet z listy multiemisji. Gdy host opuści grupę multiemisji, pakiety w sieci z tym adresem multiemisji Ethernet nie będą już odbierane przez to wystąpienie adresu IP. Następujące elementy NX_IP_DRIVER są używane w przypadku żądania opuszczenia grupy multiemisji.

| NX_IP_DRIVER &nbsp; członkowski              | Znaczenie                              |
| -----------------------------------| -------------------------------------|
| nx_ip_driver_command            | NX_LINK_MULTICAST_LEAVE           |
| nx_ip_driver_ptr                | Wskaźnik do wystąpienia adresu IP   |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32 bity fizycznego adresu multiemisji |
| nx_ip_driver_physical_address_lsw | Najmniej znaczący 32 bity fizycznego adresu multiemisji |
| nx_ip_driver_interface              | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status                 | Stan ukończenia. Jeśli sterownik nie może opuścić grupy multiemisji, zwróci niezerowy stan błędu. |

> [!IMPORTANT]  
> *Jeśli funkcje multiemisji nie są wymagane przez protokół IPv4 lub IPv6, implementacja tego żądania nie jest wymagana.*

### <a name="attach-interface"></a>Dołączanie interfejsu  
To żądanie jest wywoływane ze sterownika NetX Duo do sterownika urządzenia, dzięki czemu sterownik może skojarzyć wystąpienie sterownika z odpowiednim wystąpieniem adresu IP i wystąpieniem interfejsu fizycznego w obrębie adresu IP. Następujące elementy NX_IP_DRIVER są używane do żądania dołączania interfejsu.

| NX_IP_DRIVER &nbsp; członkowski    | Znaczenie                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP   |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu.|
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może odłączyć określonego interfejsu od wystąpienia adresu IP, zwróci niezerowy stan błędu. |

### <a name="detach-interface"></a>Odłączanie interfejsu    
To żądanie jest wywoływane przez firmę NetX Duo ze sterownikiem urządzenia, dzięki czemu sterownik może skojarzyć wystąpienie sterownika z odpowiednim wystąpieniem adresu IP i wystąpieniem interfejsu fizycznego w obrębie adresu IP. Następujące elementy NX_IP_DRIVER są używane do żądania dołączania interfejsu.

| NX_IP_DRIVER &nbsp; członkowski    | Znaczenie                                                                                                                                    |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH                                                                                                                   |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP                                                                                                                     |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu.                                                                                                         |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może dołączyć określonego interfejsu do wystąpienia adresu IP, zwróci niezerowy stan błędu. |

### <a name="get-link-status"></a>Uzyskiwanie stanu linku    
Aplikacja może odpytać o stan łącza interfejsu sieciowego przy użyciu usługi NetX Duo ***nx_ip_interface_status_check*** dla dowolnego interfejsu na hoście. Aby uzyskać więcej informacji na temat tych usług, zobacz rozdział 4 "Description of NetX Duo Services" (Opis usług NetX Duo) na stronie 149.

Stan łącza znajduje się w polu *nx_interface_link_up* w strukturze NX_INTERFACE wskazywanej przez *nx_ip_driver_interface* wskaźnik. Następujące elementy NX_IP_DRIVER są używane do żądania stanu łącza.

| NX_IP_DRIVER &nbsp; członkowski       | Znaczenie                  |
| --------------------------- | -------------------------|
| nx_ip_driver_command     | NX_LINK_GET_STATUS    |
| nx_ip_driver_ptr         | Wskaźnik do wystąpienia adresu IP   |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczany stan. |
| nx_ip_driver_interface   | Wskaźnik do wystąpienia interfejsu   |
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może uzyskać określonego stanu, zwraca niezerowy stan błędu. |

> [!NOTE]  
> ***nx_ip_status_check** _ jest nadal dostępna do sprawdzania stanu interfejsu podstawowego. Zachęcamy jednak deweloperów aplikacji do korzystania z usługi specyficznej dla interfejsu: _ *_nx_ip_interface_status_check._**

### <a name="get-link-speed"></a>Uzyskiwanie szybkości łącza  
To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje szybkość linii łącza w podanej lokalizacji docelowej. Następujące elementy NX_IP_DRIVER są używane do żądania szybkości łącza.

| NX_IP_DRIVER &nbsp; członkowski   | Znaczenie                   |
| ------------------------| ------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_SPEED          |
| nx_ip_driver_ptr         | Wskaźnik do wystąpienia adresu IP                                                                                         |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana szybkość linii                                                             |
| nx_ip_driver_interface   | Wskaźnik do wystąpienia interfejsu                                                                              |
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może uzyskać informacji o szybkości, zwróci niezerowy stan błędu. |

> [!IMPORTANT]  
> *To żądanie nie jest używane wewnętrznie przez netX Duo, więc jego implementacja jest opcjonalna.*

### <a name="get-duplex-type"></a>Uzyskiwanie typu dwukierunkowego   
To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje dwukierunkowy typ linku w podanej lokalizacji docelowej. Następujące elementy NX_IP_DRIVER są używane do żądania typu dwukierunkowego.

| NX_IP_DRIVER &nbsp; członkowski   | Znaczenie                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_DUPLEX_TYPE                                                                                    |
| nx_ip_driver_ptr         | Wskaźnik do wystąpienia adresu IP                                                                                         |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczany typ dwukierunkowy                                                            |
| nx_ip_driver_interface   | Wskaźnik do wystąpienia interfejsu                                                                              |
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może uzyskać informacji dwukierunkowych, zwróci stan błędu niezerowego. |

> [!IMPORTANT]  
> *To żądanie nie jest używane wewnętrznie przez netX Duo, więc jego implementacja jest opcjonalna.*

### <a name="get-error-count"></a>Uzyskiwanie liczby błędów   
To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę błędów łącza w podanej lokalizacji docelowej. Aby obsługiwać tę funkcję, sterownik musi śledzić błędy operacji. Następujące elementy NX_IP_DRIVER są używane do żądania liczby błędów linków.

| NX_IP_DRIVER &nbsp; członkowski   | Znaczenie                   |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_ERROR_COUNT   |
| nx_ip_driver_ptr         | Wskaźnik do wystąpienia adresu IP   |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba błędów |
| nx_ip_driver_interface   | Wskaźnik do wystąpienia interfejsu|
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby błędów, zwróci on niezerowy stan błędu. |

> [!IMPORTANT]
> *To żądanie nie jest używane wewnętrznie przez netX Duo, więc jego implementacja jest opcjonalna.*

### <a name="get-receive-packet-count"></a>Uzyskiwanie liczby pakietów odbierania    
To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę pakietów odbioru łącza w podanej lokalizacji docelowej. Aby obsługiwać tę funkcję, sterownik musi śledzić liczbę odebranych pakietów. Następujące elementy NX_IP_DRIVER są używane dla żądania liczby pakietów odbierania linku.

| NX_IP_DRIVER &nbsp; członkowski       | Znaczenie                        |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_RX_COUNT      |
| nx_ip_driver_ptr         | Wskaźnik do wystąpienia adresu IP  |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba pakietów odbioru   |
| nx_ip_driver_interface   | Wskaźnik do fizycznego interfejsu sieciowego  |
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby odbierania, zwróci niezerowy stan błędu. |

> [!IMPORTANT]  
> *To żądanie nie jest używane wewnętrznie przez netX Duo, więc jego implementacja jest opcjonalna.*

### <a name="get-transmit-packet-count"></a>Uzyskiwanie liczby pakietów przesyłanych   
To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę pakietów przesyłanych łącza w podanej lokalizacji docelowej. Aby obsługiwać tę funkcję, sterownik musi śledzić każdy pakiet przesyłany w każdym interfejsie. Następujące elementy NX_IP_DRIVER są używane w przypadku żądania liczby pakietów przesyłanych linkami.

| NX_IP_DRIVER &nbsp; członkowski   | Znaczenie                   |
| ----------------------- | ------------------------- |
| nx_ip_driver_command | NX_LINK_GET_TX_COUNT  |
| nx_ip_driver_ptr     | Wskaźnik do wystąpienia adresu IP    |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba pakietów przesyłanych  |
| nx_ip_driver_interface   | Wskaźnik do wystąpienia interfejsu   |
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby transmisji, zwróci stan błędu niezerowy. |

> [!IMPORTANT]  
> *To żądanie nie jest używane wewnętrznie przez netX Duo, więc jego implementacja jest opcjonalna.*

### <a name="get-allocation-errors"></a>Uzyskiwanie błędów alokacji   
To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę błędów alokacji puli pakietów łącza w podanej lokalizacji docelowej. Następujące elementy NX_IP_DRIVER są używane do żądania liczby błędów alokacji łącza.

| NX_IP_DRIVER &nbsp; członkowski       | Znaczenie                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_ALLOC_ERRORS  |
| nx_ip_driver_ptr         | Wskaźnik do wystąpienia adresu IP     |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba błędów alokacji  |
| nx_ip_driver_interface   | Wskaźnik do wystąpienia interfejsu  |
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może uzyskać błędów alokacji, zwróci niezerowy stan błędu. |

> [!IMPORTANT]  
> *To żądanie nie jest używane wewnętrznie przez netX Duo, więc jego implementacja jest opcjonalna.*

### <a name="driver-deferred-processing"></a>Przetwarzanie odroczone sterownika    
To żądanie jest wysyłana z wątku pomocnika IP _*_ w odpowiedzi na sterownik wywołujący nx_ip_driver_deferred_processing procedury z isr przesyłania lub odbierania. Dzięki temu sterownik ISR odroczyć odbieranie pakietów i przesyłanie przetwarzania do wątku pomocnika IP, a tym samym zmniejszyć ilość przetwarzania w ISR. Pole _nx_interface_additional_link_info* w strukturze NX_INTERFACE wskazywane przez nx_ip_driver_interface  może być używane przez sterownik do przechowywania informacji o zdarzeniu przetwarzania odroczonego z kontekstu wątku pomocnika IP. Następujące elementy NX_IP_DRIVER są używane dla zdarzenia przetwarzania odroczonego.

| NX_IP_DRIVER &nbsp; członkowski     | Znaczenie                           |
| ------------------------- | --------------------------------- |
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING    |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP            |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |

### <a name="set-physical-address"></a>Ustawianie adresu fizycznego  
To żądanie jest dokonywane z poziomu usługi ***nx_ip_interface_physical_address_set** _service. Ta usługa umożliwia aplikacji zmianę adresu fizycznego interfejsu w czasie uruchamiania. Po otrzymaniu tego polecenia sterownik musi ponownie skonfigurować adres sprzętowy interfejsu sieciowego na podany adres fizyczny. Ponieważ wystąpienie adresu IP ma już nowy adres, nie ma potrzeby wywołania usługi *__nx_ip_interface_address_set_** z tego polecenia.

Następujące NX_IP_DRIVER są używane do żądania polecenia użytkownika.

| NX_IP_DRIVER &nbsp; członkowski      | Znaczenie                      |
| -------------------------- | ---------------------------- |
| nx_ip_driver_command    | NX_LINK_SET_PHYSICAL_ADDRESS  |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP  |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu   |
| nx_ip_driver_physical_ad dress_msw | Najbardziej znaczące 32-bity nowego adresu fizycznego  |
| nx_ip_driver_physical_ad dress_lsw | Najmniej znaczące 32-bitowe nowe fizycznego adresu  |
| nx_ip_driver_status                  | Stan ukończenia. Jeśli sterownik nie jest w stanie ponownie skonfigurować adresu fizycznego, zwraca niezerowy stan błędu. |

### <a name="user-commands"></a>Polecenia użytkownika    
To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przetwarza polecenia użytkownika specyficzne dla aplikacji. Następujące NX_IP_DRIVER są używane do żądania polecenia użytkownika.

| NX_IP_DRIVER &nbsp; członkowski       | Znaczenie                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_USER_COMMAND       |
| nx_ip_driver_ptr         | Wskaźnik do wystąpienia adresu IP        |
| nx_ip_driver_return_ptr | Zdefiniowane przez użytkownika       |
| nx_ip_driver_interface   | Wskaźnik do wystąpienia interfejsu    |
| nx_ip_driver_status      | Stan ukończenia. Jeśli sterownik nie może wykonać poleceń użytkownika, zwróci stan błędu niezerowy. |

> [!IMPORTANT] 
> *To żądanie nie jest używane wewnętrznie przez netX Duo, więc jego implementacja jest opcjonalna.*

### <a name="unimplemented-commands"></a>Niezaimplementowane polecenia  
Polecenia niezaimplementowane przez sterownik sieciowy muszą mieć pole stanu zwracania ustawione na NX_UNHANDLED_COMMAND.

## <a name="driver-capability"></a>Możliwość sterownika

Niektóre interfejsy sieciowe oferują funkcje odciążania sumy kontrolnej. Sterowniki urządzeń mogą korzystać z przyspieszania sprzętu w celu wolnego czasu procesora CPU od wykonywania różnych obliczeń sumy kontrolnej.

W zależności od poziomu obsługi sumy kontrolnej sprzętu sterownik urządzenia musi poinformować wystąpienie adresu IP, która funkcja sprzętowa jest włączona. Dzięki temu wystąpienie adresu IP wie o funkcji sprzętowej i odciąża jak najwięcej obliczeń na sprzęcie. Sterownik powinien używać interfejsu API ***nx_ip_interface_capability_set*** do ustawienia wszystkich funkcji, które może obsłużyć interfejs fizyczny.

Można użyć następujących funkcji:

- NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_RX_CHECKSUM

W przypadku obliczeń sumy kontrolnej, które mogą być wykonywane na sprzęcie, sterownik musi poprawnie skonfigurować deskryptory sprzętu lub buforu, aby można było wygenerować i wstawić do nagłówka sumy kontrolnej dla wychodzącego pakietu przez sprzęt. Po odebraniu pakietu logika sumy kontrolnej sprzętu powinna być w stanie zweryfikować wartość sumy kontrolnej. Jeśli wartość sumy kontrolnej jest nieprawidłowa, odebrana ramka powinna zostać odrzucona.

Nawet przy możliwości wykonywania obliczeń sumy kontrolnej na sprzęcie wystąpienie adresu IP nadal utrzymuje możliwość sumy kontrolnej. W niektórych scenariuszach, na przykład datagram UDP przechodzący przez ochronę IPsec, sumy kontrolne UDP muszą zostać obliczone w oprogramowaniu przed przekazaniem ramki UDP w dół stosu. Większość funkcji sumy kontrolnej sprzętu nie obsługuje obliczeń sumy kontrolnej dla segmentu danych chronionych przez IPsec. W przypadku ramki UDP lub ICMP, która musi być podzielona na fragmenty, sumy kontrolne UDP lub ICMP muszą być obliczane w oprogramowaniu. Większość sprzętowej logiki sumy kontrolnej nie obsługuje przypadków, w których dane są podzielone na wiele ramek.

## <a name="driver-output"></a>Dane wyjściowe sterownika  

Wszystkie wymienione wcześniej żądania przesyłania pakietów wymagają funkcji wyjściowej zaimplementowanej w sterowniku. Specyficzna logika przesyłania jest specyficzna dla sprzętu, ale zwykle polega na sprawdzeniu pojemności sprzętowej w celu natychmiastowego wysłania pakietu. Jeśli to możliwe, ładunek pakietu (i dodatkowe ładunki w łańcuchu pakietów) są ładowane do co najmniej jednego sprzętowego buforu przesyłania i inicjowana jest operacja przesyłania. Jeśli pakiet nie zmieści się w dostępnych buforach przesyłania, pakiet powinien zostać w kolejce i przesłany, gdy bufory transmisji staną się dostępne.

Zalecana kolejka przesyłania to jednolicie połączona lista ze wskaźnikami zarówno head, jak i tail. Nowe pakiety są dodawane na końcu kolejki, zachowując najstarszy pakiet z przodu. Pole *nx_packet_queue_next* jest używane jako następne łącze pakietu w kolejce. Sterownik definiuje wskaźniki głowy i ogona kolejki przesyłania.

> [!CAUTION]  
> Ponieważ dostęp do tej kolejki uzyskuje się z części sterownika wątków i przerwań, ochrona przerwań musi być umieszczana wokół *manipulacji kolejkami*.

Większość implementacji sprzętu fizycznego generuje przerwanie po zakończeniu przesyłania pakietów. Gdy sterownik otrzymuje takie przerwanie, zwykle zwalnia zasoby skojarzone z właśnie przesyłanym pakietem. Jeśli logika przesyłania odczytuje dane bezpośrednio z buforu NX_PACKET, sterownik powinien użyć usługi ***nx_packet_transmit_release*** do zwolnienia pakietu skojarzonego z kompletnym przerwaniem przesyłania z powrotem do dostępnej puli pakietów. Następnie sterownik sprawdza kolejkę przesyłania pod tematem dodatkowych pakietów oczekujących na ich wysłania. Ponieważ wiele pakietów przesyłanych w kolejce, które mieszczą się w sprzętowych buforach przesyłania, jest dekodowana i ładowana do buforów. Następnie następuje zainicjowanie innej operacji wysyłania.

Gdy tylko dane w pliku NX_PACKET zostały przeniesione do fifo nagłówka fifo (lub jeśli sterownik obsługuje operację kopiowania zerowego, dane w programie NX_PACKET zostały przesłane), sterownik musi przenieść nx_packet_prepend_ptr na początek nagłówka IP *przed* wywołaniem funkcji ***nx_packet_transmit_release.** _ Pamiętaj, aby odpowiednio _nx_packet_length*. Jeśli ramka IP składa się z wielu pakietów, musi zostać zwolniona tylko część head łańcucha pakietów.

## <a name="driver-input"></a>Dane wejściowe sterownika

Po otrzymaniu odebranego przerwania pakietów sterownik sieciowy pobiera pakiet z fizycznego sprzętu odbiera bufory i tworzy prawidłowy pakiet NetX Duo. Tworzenie prawidłowego pakietu NetX Duo obejmuje skonfigurowanie odpowiedniego pola długości i połączenie wielu pakietów, jeśli rozmiar pakietu przychodzącego jest większy niż pojedynczy ładunek pakietu. Po prawidłowym s *zbudowaniu prepend_ptr* jest przenoszony po nagłówku warstwy fizycznej, a pakiet odbierany jest wysyłany do narzędzia NetX Duo.

NetX Duo zakłada, że nagłówki ADRESÓW IP (IPv4 i IPv6) i ARP są wyrównane do **granicy ULONG.** W związku z tym sterownik NetX Duo musi zapewnić takie wyrównanie. W środowiskach Ethernet odbywa się to przez uruchomienie nagłówka Ethernet dwa bajty od początku pakietu. Gdy adres *nx_packet_prepend_ptr* jest przenoszony poza nagłówek Ethernet, źródłowy adres IP (IPv4 i IPv6) lub nagłówek ARP jest wyrównany o 4 bajty.

> [!WARNING] 
> *Zapoznaj się z sekcją "Nagłówki Ethernet" poniżej,* aby uzyskać ważne różnice między nagłówkami IPv6 i IPv6 Ethernet.

W netX Duo jest dostępnych kilka funkcji odbierania pakietów. Jeśli odebrany pakiet jest pakietem ARP, _* **nx_arp_packet_deferred_receive**_ wywoływana. Jeśli odebrany pakiet jest pakietem RARP,_*_wywoływana jest nx_rarp_packet_deferred_receive_*_ _ . Istnieje kilka opcji obsługi przychodzących pakietów IP. W celu najszybszej obsługi pakietów IP wywoływana _*_jest nx_ip_packet_receive_*_ _ . Takie podejście ma najmniejsze obciążenie, ale wymaga większej liczby przetwarzania w obsłudze usługi przerywania odbierania (ISR) sterownika. W przypadku minimalnego przetwarzania isr *___ nx_ip_packet_deferred_receive_** jest wywoływana.

Po prawidłowym s zbudowaniu nowego pakietu odbierania bufory odbierania sprzętu fizycznego są konfigurowane w celu odbierania większej liczby danych. Może to wymagać przydzielenia pakietów NetX Duo i umieszczenia adresu ładunku w buforze odbierania sprzętu lub może to po prostu oznaczać zmianę ustawienia w buforze odbierania sprzętu. Aby zminimalizować możliwości przepełnienia, ważne jest, aby bufory odbierania sprzętu były dostępne bufory tak szybko, jak to możliwe po otrzymaniu pakietu.

> [!IMPORTANT] 
> *Początkowe bufory odbierania są konfigurowane podczas inicjowania sterownika*.

### <a name="deferred-receive-packet-handling"></a>Obsługa odroczonego odbierania pakietów  
Sterownik może odroczyć przetwarzanie pakietów do wątku pomocnika IP NetX Duo. W przypadku niektórych aplikacji może to być konieczne w celu zminimalizowania przetwarzania ISR, a także porzucania pakietów. 

Aby korzystać z obsługi pakietów odroczonych, należy najpierw skompilować bibliotekę NetX Duo przy użyciu funkcji ***NX_DRIVER_DEFERRED_PROCESSING** _ defined. Powoduje to dodanie logiki odroczonego pakietu do wątku pomocnika IP NetX Duo. Następnie po odebraniu pakietu danych sterownik musi wywołać __nx_ip_packet_deferred_receive():*

```c
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```
Funkcja odroczonego odbierania umieszcza pakiet  odbierany reprezentowany przez packet_ptr w fifo (połączonej liście) i powiadamia wątek pomocnika IP. Po wykonaniu pomocnik IP wielokrotnie wywołuje funkcję obsługi odroczonej w celu przetwarzania każdego odroczonego pakietu. Przetwarzanie odroczonego programu obsługi zwykle obejmuje usunięcie nagłówka warstwy fizycznej pakietu (zazwyczaj Ethernet) i wysłanie go do jednej z tych funkcji odbierania NetX Duo:

- ***_nx_ip_packet_receive***
- ***_nx_arp_packet_deferred_receive***
- ***_nx_rarp_packet_deferred_receive***

## <a name="ethernet-headers"></a>Nagłówki Ethernet 

Jedną z najważniejszych różnic między nagłówkami IPv6 i IPv4 dla sieci Ethernet jest ustawienie typu ramki. Podczas wysyłania pakietów sterownik Ethernet jest odpowiedzialny za ustawienie typu ramki Ethernet w pakietach wychodzących. W przypadku pakietów IPv6 typ ramki powinien być 0x86DD; W przypadku pakietów IPv4 typ ramki powinien być 0x0800.

Następujący segment kodu ilustruje ten proces:

```c
NX_PACKET *packet_ptr;
packet_ptr = driver_req_ptr -> nx_ip_driver_packet;
if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V4)
{

   /* Set Ethernet frame type to IPv4 /*
   ethernet_frame_ptr -> frame_type = 0x0800;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V6)
{

   /* Set Ethernet frame type to IPv6. /*
   ethernet_frame_ptr -> frame_type = 0x86DD;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else
{

   /* Unknown IP version. Free the packet we will not send. */
   nx_packet_transmit_release(packet_ptr);
}
```
Podobnie w przypadku pakietów przychodzących sterownik Ethernet powinien określać typ pakietu na podstawie typu ramki Ethernet. Należy ją zaimplementować w celu akceptowania typów ramek IPv6 (0x86DD), IPv4 (0x0800), ARP (0x0806) i RARP (0x8035).

## <a name="example-ram-ethernet-network-driver"></a>Przykład sterownika sieci Ethernet pamięci RAM

System pokazowy NetX Duo jest dostarczany z małym sterownikem sieciowym opartym na pamięci RAM zdefiniowanym w ***pliku nx_ram_network_driver.c.*** Ten sterownik zakłada, że wszystkie wystąpienia adresów IP znajdują się w tej samej sieci i po prostu przypisuje wirtualne adresy sprzętowe (adresy MAC) do każdego wystąpienia urządzenia podczas ich tworzenia. Ten plik zawiera dobry przykład podstawowej struktury fizycznych sterowników sieciowych NetX Duo. Użytkownicy mogą opracowywać własne sterowniki sieciowe przy użyciu struktury sterowników przedstawionej w tym przykładzie.

Funkcja wprowadzania sterownika sieciowego to ***_nx_ram_network_driver(),** _, która jest przekazywana do wywołania tworzenia wystąpienia adresu IP. Funkcje wejścia dla dodatkowych interfejsów sieciowych mogą być przekazywane do usługi _nx_ip_interface_attach()*. Po uruchomieniu wystąpienia adresu IP wywoływana jest funkcja wprowadzania sterownika w celu zainicjowania i włączenia urządzenia (zapoznaj się z **przypadkiem** NX_LINK_INITIALIZE i **NX_LINK_ENABLE**). Po **NX_LINK_ENABLE** urządzenie powinno być gotowe do przesyłania i odbierania pakietów. 

Wystąpienie adresu IP przesyła pakiety sieciowe za pomocą jednego z tych poleceń:

| Polecenie                         |  Opis                                                   |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_PACKET_SEND***    | Pakiet IPv4 lub IPv6 jest przesyłany.                   |
| ***NX_LINK_ARP_SEND***       | Żądanie ARP lub pakiet odpowiedzi ARP jest przesyłany,    |
| ***NX_LINK_ARP_RARP_SEND*** | Przesyłany jest zwrotny pakiet żądania lub odpowiedzi ARP. |

Podczas przetwarzania tych poleceń sterownik sieciowy musi dołączać odpowiedni nagłówek ramki Ethernet, a następnie wysyłać go do bazowego sprzętu w celu transmisji. Podczas procesu transmisji sterownik sieciowy ma wyłączną własność obszaru buforu pakietów. W związku z tym po przesłaniu danych (lub skopiowaniu danych do wewnętrznego buforu transferu sterownika) sterownik sieciowy jest odpowiedzialny za zwolnienie buforu pakietów przez przeniesienie wstępnie otwartego wskaźnika poza nagłówek Ethernet do nagłówka ip (i odpowiednie dostosowanie długości pakietów), a następnie przez wywołanie usługi ***nx_packet_transmit_release()*** w celu zwolnienia pakietu. Nie zwalnianie pakietu po transmisji danych spowoduje wyciek pakietów.

Sterownik urządzenia sieciowego jest również odpowiedzialny za obsługę przychodzących pakietów danych. W przykładzie sterownika pamięci RAM odebrany pakiet jest przetwarzany przez funkcję ***_nx_ram_network_driver_receive()***. Gdy urządzenie otrzyma ramkę Ethernet, sterownik jest odpowiedzialny za przechowywanie danych w NX_PACKET sieci. Należy pamiętać, że program NetX Duo zakłada, że nagłówek IP zaczyna się od adresu dopasowanego do 4 bajtów. Ponieważ długość nagłówka Ethernet wynosi 14bajtów, sterownik musi przechowywać początek nagłówka Sieci Ethernet na adres wyrównany 2-bajtowy, aby zagwarantować, że nagłówek IP rozpoczyna się od adresu wyrównany o 4 bajtach.

## <a name="tcpip-offload-driver-guidance"></a>Wskazówki dotyczące sterownika odciążania TCP/IP
W przypadku funkcji odciążania protokołu TCP/IP dla każdego interfejsu IP jest potrzebna funkcja sterownika. Poniżej znajduje się lista dodatkowych zadań dla sterownika sieciowego.

* Dla polecenia `NX_LINK_INITIALIZE` ,
  * Utwórz wątek sterownika do obsługi zdarzeń odciążania PROTOKOŁU TCP/IP.
* Dla polecenia `NX_LINK_INTERFACE_ATTACH` ,
  * Ustaw możliwość na interfejs sterowników. Zobacz przykładowy kod poniżej.
``` C
driver_req_ptr -> nx_ip_driver_interface -> nx_interface_capability_flag = NX_INTERFACE_CAPABILITY_TCPIP_OFFLOAD;
```
* Dla polecenia `NX_LINK_ENABLE` ,
  * Uruchom wątek sterownika.
  * Ustaw funkcję wywołania zwrotnego TCP/IP na interfejs sterownika. Zobacz przykładowy kod poniżej.
``` C
driver_req_ptr -> nx_ip_driver_interface -> nx_interface_tcpip_offload_handler = _nx_driver_tcpip_handler;
```
* Dla polecenia `NX_LINK_DISABLE` ,
  * Zatrzymaj wątek sterownika
  * Wyczyść funkcję wywołania zwrotnego TCP/IP interfejsu sterowników.
* Dla polecenia `NX_LINK_UNINITIALIZE` ,
  * Usuwanie wątku sterownika

### <a name="tcpip-offload-driver-thread"></a>Wątek sterownika odciążania TCP/IP
Celem wątku sterownika jest odbieranie przychodzących pakietów TCP lub UDP. W wątku sterownika zazwyczaj istnieje pętla while, aby sprawdzić, czy dostępny jest przychodzący pakiet TCP lub UDP albo nawiązane połączenie. Gdy dane są dostępne, przekaż pakiet TCP lub UDP do netx duo. Pomieszczenie między `nx_packet_data_start` i musi być `nx_packet_prepend_ptr` wystarczające, aby wstawić nagłówek TCP/IP. W przypadku gniazda TCP przydziel pakiet o typie `NX_TCP_PACKET` . W przypadku gniazda UDP przydziel pakiet o typie `NX_UDP_PACKET` . Wprowadź dane przychodzące z `nx_packet_append_ptr` do `nx_packet_data_end` . Dane w `nx_packet_append_ptr` programie muszą zawierać tylko ładunek TCP lub UDP. Nagłówek TCP/IP **NIE MOŻE** być wypełniony pakietem. Dostosuj długość pakietu i ustaw interfejs odbierania, a następnie `_nx_tcp_socket_driver_packet_receive` wywołaj dla pakietów TCP `_nx_udp_socket_driver_packet_receive` i UDP. Jeśli połączenie TCP zostanie zamknięty, wywołaj polecenie `_nx_tcp_socket_driver_packet_receive` z pakietem ustawionym na wartość NULL. Po nawiązaniu połączenia `_nx_tcp_socket_driver_establish` wywołaj .

### <a name="tcpip-offload-driver-handler"></a>Procedura obsługi sterowników odciążania TCP/IP
Następujące polecenia sterowników są wymagane dla interfejsów sieciowych z usługami TCP/IP. 
* W przypadku operacji `NX_TCPIP_OFFLOAD_TCP_CLIENT_SOCKET_CONNECT` :
  * W razie potrzeby przydziel zasób.
  * Powiąż z lokalnym portem TCP i połącz się z serwerem.
  * Zwracanie powodzenia po nawiązaniu połączenia. Gdy połączenie jest w toku, zwróć `NX_IN_PROGRESS` . Lub w innym przypadku zwróć błąd.
* W przypadku operacji `NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_LISTEN` :
  * Najpierw sprawdź, czy nie ma zduplikowanych danych nasłuchiwać. Może być wywoływana wiele razy na tym samym porcie. Za pierwszym razem od `nx_tcp_server_socket_listen` , a następnie `nx_tcp_server_socket_relisten` .
  * W razie potrzeby przydziel zasób.
  * Nasłuchiwać lokalnego portu TCP.
* W przypadku operacji `NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_ACCEPT` :
  * W razie potrzeby przydziel zasób.
  * Zaakceptuj połączenie.
* W przypadku operacji `NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_UNLISTEN` :
  * Znajdź nasłuchiwanie gniazda TCP na porcie lokalnym.
  * Zamknij gniazdo nasłuchiwania, jeśli zostanie znalezione.
* W przypadku operacji `NX_TCPIP_OFFLOAD_TCP_SOCKET_DISCONNECT` :
  * Zamknij połączenie odciążania PROTOKOŁU TCP/IP.
  * Unbind local TCP port (Odłącz lokalny port TCP).
  * Czyszczenie zasobów utworzonych podczas nawiązywania połączenia.
* W przypadku operacji `NX_TCPIP_OFFLOAD_TCP_SOCKET_SEND` :
  * Wysyłanie danych za pośrednictwem odciążania PROTOKOŁU TCP/IP. Przygotuj się do obsługi długości pakietów większej niż MSS lub sytuacji łańcucha pakietów.
* W przypadku operacji `NX_TCPIP_OFFLOAD_UDP_SOCKET_BIND` :
  * W razie potrzeby przydziel zasób.
  * Powiąż z lokalnym portem UDP.
* W przypadku operacji `NX_TCPIP_OFFLOAD_UDP_SOCKET_UNBIND` :
  * Unbind local UDP port (Odłącz lokalny port UDP).
  * Czyszczenie zasobów utworzonych podczas tworzenia powiązania.
* W przypadku operacji `NX_TCPIP_OFFLOAD_UDP_SOCKET_SEND` :
  * Wysyłanie danych za pośrednictwem odciążania PROTOKOŁU TCP/IP. Przygotuj się do obsługi sytuacji, w której długość pakietu jest większa niż rozmiar jednostki MTU lub łańcucha pakietów.