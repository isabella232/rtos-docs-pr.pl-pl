---
title: Rozdział 5 — Azure RTOS sterowników sieciowych NetX
description: Ten rozdział zawiera opis sterowników sieciowych dla Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 09/11/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0770d6beb8b2715a8e5dddf1bdf187c0cd1d5ffd74e7bea9b7ff9bdf1785d088
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801924"
---
# <a name="chapter-5---netx-network-drivers"></a>Rozdział 5 — Sterowniki sieciowe NetX

Ten rozdział zawiera opis sterowników sieciowych dla netx. Przedstawione informacje mają ułatwić deweloperom pisanie sterowników sieciowych specyficznych dla aplikacji dla Azure RTOS NetX.

## <a name="driver-introduction"></a>Wprowadzenie do sterownika

Struktura NX_IP zawiera wszystkie elementy do zarządzania pojedynczym wystąpieniem adresu IP. Obejmuje to ogólne informacje o protokole TCP/IP, a także procedurę wprowadzania sterownika sieci fizycznej specyficznej dla aplikacji. Procedura wprowadzania sterownika jest definiowana podczas ***nx_ip_create*** usługi. Dodatkowe urządzenia mogą być dodawane do wystąpienia adresu IP za pośrednictwem ***nx_ip_interface_attach*** service.

Komunikacja między netx a sterownikiem sieciowym aplikacji jest realizowane za pośrednictwem **struktury NX_IP_DRIVER** żądania. Ta struktura jest najczęściej definiowana lokalnie na stosie wywołującym i dlatego jest zwalniana po zwróceniu przez sterownik i funkcję wywołującą. Struktura jest zdefiniowana w następujący sposób.

```C
typedef struct NX_IP_DRIVER_STRUCT
{
    UINT nx_ip_driver_command;
    UINT nx_ip_driver_status;
    ULONG nx_ip_driver_physical_address_msw;
    ULONG nx_ip_driver_physical_address_lsw;
    NX_PACKET *nx_ip_driver_packet;
    ULONG *nx_ip_driver_return_ptr;
    NX_IP *nx_ip_driver_ptr;
    NX_INTERFACE *nx_ip_driver_interface;
} NX_IP_DRIVER;
```

## <a name="driver-entry"></a>Wpis sterownika

NetX wywołuje funkcję wprowadzania sterownika sieciowego do inicjowania sterowników i wysyłania pakietów oraz do różnych operacji sterowania i stanu, w tym inicjowania i włączania urządzenia sieciowego. NetX wydaje polecenia sterownikowi siecioweowi, ustawiając pole ***nx_ip_driver_command** _ w strukturze żądań _ *NX_IP_DRIVER**. Funkcja wprowadzania sterownika ma następujący format:

```C
VOID my_driver_entry(NX_IP_DRIVER *request);
```

## <a name="driver-requests"></a>Żądania sterowników

NetX tworzy żądanie sterownika za pomocą określonego polecenia i wywołuje funkcję wprowadzania sterownika w celu wykonania polecenia. Ponieważ każdy sterownik sieciowy ma jedną funkcję wpisu, NetX wykonuje wszystkie żądania za pośrednictwem struktury danych żądania sterownika. Członek ***nx_ip_driver_command*** struktury danych żądania sterownika (**NX_IP_DRIVER**) definiuje żądanie. Informacje o stanie są zgłaszane z powrotem do wywołującego w ***nx_ip_driver_status***. Jeśli to pole jest **NX_SUCCESS**, żądanie sterownika zostało ukończone pomyślnie.

NetX serializuje cały dostęp do sterownika. W związku z tym sterownik nie musi obsługiwać wielu wątków asynchronicznie wywołując funkcję entry. Należy pamiętać, że funkcja sterownika urządzenia jest wykonywana z zablokowanym obiektem mutex adresu IP. W związku z tym funkcja wewnętrzna sterownika urządzenia nie powinna blokować się.

Zazwyczaj sterownik urządzenia obsługuje również przerwania. W związku z tym wszystkie funkcje sterowników muszą być bezpieczne przed przerywaniami.

### <a name="driver-initialization"></a>Inicjowanie sterownika

Chociaż rzeczywiste przetwarzanie inicjowania sterownika jest specyficzne dla aplikacji, zwykle składa się ze struktury danych i inicjalizacji sprzętu fizycznego. Informacje wymagane z NetX do inicjowania sterownika jest maksymalna jednostka transmisji IP (MTU), która jest liczba bajtów dostępnych dla ładunku warstwy IP, w tym nagłówka IP) i czy interfejs fizyczny wymaga mapowania logicznego na fizyczny. Sterownik wymaga

w celu skonfigurowania jednostki MTU interfejsu przez ustawienie wartości w ***nx_interface_ip_mtu_size** _ w strukturze _ *NX_INTERFACE**.

Sterownik urządzenia musi również skonfigurować wartość w nx_ip_interface_address_mapping_needed ***w***

**NX_INTERFACE,** aby poinformować NetX, czy mapowanie adresów interfejsu jest wymagane. Jeśli wymagane jest mapowanie adresów, sterownik jest odpowiedzialny za skonfigurowanie interfejsu przy użyciu prawidłowego adresu MAC i dostarczenie adresu MAC do NetX.

Gdy sterownik sieciowy odbiera żądanie NX_LINK INITIALIZE z netX, otrzymuje wskaźnik do bloku sterowania ip w ramach bloku sterowania żądaniami NX_IP_DRIVER przedstawiony powyżej.

Gdy aplikacja ***wywołuje*** nx_ip_create , wątek pomocnika IP wysyła żądanie sterownika z poleceniem ustawionym na NX_LINK_INITIALIZE do sterownika w celu zainicjowania jego fizycznego interfejsu sieciowego. Następujące NX_IP_DRIVER są używane do inicjowania żądania.

| NX_IP_DRIVER członkowski    | Znaczenie |
|------------------------|-----------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INITIALIZE |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP. Ta wartość powinna zostać zapisana przez sterownik, aby funkcja sterownika znalazła wystąpienie adresu IP, na którym będzie działać. |
| nx_ip_driver_interface | Wskaźnik do struktury interfejsu sieciowego w wystąpieniu adresu IP. Te informacje powinny zostać zapisane przez sterownik. Podczas odbierania pakietów sterownik musi używać informacji o strukturze interfejsu podczas wysyłania pakietu w górę stosu. |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może zainicjować określonego interfejsu do wystąpienia adresu IP, zwróci stan błędu niezerowego.                                                                                           |


> [!IMPORTANT]
> *Większość poleceń sterownika jest wywoływana z wątku pomocnika IP, który został utworzony dla wystąpienia adresu IP. W związku z tym procedura sterownika powinna unikać wykonywania operacji blokujących lub wątek pomocnika IP może zostać zatrzymany, powodując niepowiązane opóźnienia dla aplikacji, które korzystają z wątku ip.*

### <a name="enable-link"></a>Włączanie linku  

Następnie wątek pomocnika IP włącza sieć fizyczną, ustawiając polecenie sterownika na NX_LINK_ENABLE w żądaniu sterownika i wysyłając żądanie do sterownika sieciowego. Dzieje się tak wkrótce po ukończeniu żądania inicjowania przez wątek pomocnika IP. Włączenie linku może wystarczyć do ustawienia nx_interface_link_up w wystąpieniu interfejsu. Jednak może to również obejmować manipulowanie sprzętem fizycznym. Następujące elementy NX_IP_DRIVER są używane do żądania linku włączania.

| NX_IP_DRIVER członkowski    | Znaczenie |
|------------------------|------------------------------------------|
| nx_ip_driver_command   | NX_LINK_ENABLE                                                                                                          |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP                                                                                                  |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu                                                                                       |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może włączyć określonego interfejsu, zwraca niezerowy stan błędu. |



### <a name="disable-link"></a>Wyłączanie linku  

To żądanie jest dokonywane przez firmę NetX podczas usuwania wystąpienia adresu IP przez usługę ***nx_ip_delete** _. Aplikacja może też wydać to polecenie w celu tymczasowego wyłączenia linku w celu zaoszczędzenia zasilania. Ta usługa wyłącza fizyczny interfejs sieciowy w wystąpieniu adresu IP. Przetwarzanie w celu wyłączenia linku może być tak proste, jak wyczyszczenie _flagi nx_interface_link_up* w wystąpieniu interfejsu. Jednak może to również obejmować manipulowanie sprzętem fizycznym. Zazwyczaj jest to odwrotna operacja ***Włącz łącze.**_ Po wyłączeniu linku żądanie aplikacji _ *_Włącz link_** umożliwia włączenie interfejsu. Następujące elementy NX_IP_DRIVER są używane do żądania wyłączenia linku.

| NX_IP_DRIVER członkowski    | Znaczenie |
|------------------------|--------------------------------------|
| nx_ip_driver_command   | NX_LINK_DISABLE |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może wyłączyć określonego interfejsu w wystąpieniu adresu IP, zwróci niezerowy stan błędu. |


### <a name="uninitialize-link"></a>Uninitialize Link  

To żądanie jest dokonywane przez firmę NetX podczas usuwania wystąpienia adresu IP przez ***nx_ip_delete*** usługi. To żądanie niezainicjuje interfejs i zwalnia wszystkie zasoby utworzone w fazie inicjowania. Zazwyczaj jest to odwrotna operacja ***inicjowania*** linku. Gdy interfejs jest nieunitalizowany, nie można używać urządzenia, dopóki interfejs nie zostanie ponownie zainicjowany.

Następujące elementy NX_IP_DRIVER są używane do żądania wyłączenia linku.

| NX_IP_DRIVER członkowski  | Znaczenie                |
|----------------------|------------------------|
| nx_ip_driver_command | NX_LINK_UNINITIALZE    |
| nx_ip_driver_ptr     | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie jest w stanie niezainicjować określonego interfejsu do wystąpienia adresu IP, zwróci stan błędu niezerowego. |


### <a name="packet-send"></a>Wysyłanie pakietów  

To żądanie jest dokonywane podczas wewnętrznego przetwarzania i przetwarzania wysyłania adresów IP, którego wszystkie protokoły NetX używają do przesyłania pakietów (z wyjątkiem ARP, RARP). Po otrzymaniu polecenia wysyłania  pakietów nx_packet_prepend_ptr wskazuje początek wysyłanego pakietu, który jest początek nagłówka adresu IP.
*nx_packet_length* wskazuje całkowity rozmiar (w bajtach) przesyłanych danych. Jeśli *nx_packet_next* jest prawidłowy, wychodzący datagram adresu IP jest przechowywany w wielu pakietach, sterownik musi postępować zgodnie z łańcuchowym pakietem i przesyłać całą ramkę. Należy pamiętać, że prawidłowy obszar danych w każdym pakiecie łańcuchowym jest przechowywany między *nx_packet_prepend_ptr* i *nx_packet_append_ptr*.

Sterownik jest odpowiedzialny za konstruowanie nagłówka fizycznego. Jeśli wymagane jest mapowanie adresu fizycznego na adres IP (np. Ethernet), warstwa IP rozpoznała już adres MAC. Docelowy adres MAC jest przekazywany z wystąpienia adresu IP przechowywanego w nx_ip_driver_physical_address_msw *i nx_ip_driver_physical_address_lsw.*

Po dodaniu nagłówka fizycznego przetwarzanie wysyłania pakietów wywołuje funkcję wyjściową sterownika, aby przesłać pakiet.

Następujące elementy NX_IP_DRIVER są używane do żądania wysyłania pakietów.

| NX_IP_DRIVER członkowski               | Znaczenie |
|-----------------------------------|---------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_PACKET_SEND |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_packet               | Wskaźnik do pakietu do wysłania |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu.             |
| nx_ip_driver_physical_address_msw | Większość znaczących 32-bitowych adresów fizycznych (tylko wtedy, gdy wymagane jest mapowanie fizyczne) |
| nx_ip_driver_physical_address_lsw | Najmniej znaczący 32-bitowy adres fizyczny (tylko wtedy, gdy wymagane jest mapowanie fizyczne)    |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie jest w stanie wysłać pakietu, zwróci stan błędu niezerowego.  |

### <a name="packet-broadcast"></a>Emisja pakietów  
To żądanie jest niemal identyczne z żądaniem wysyłania pakietu. Jedyna różnica polega na tym, że pola docelowego adresu fizycznego są ustawione na adres MAC emisji Ethernet. Następujące elementy NX_IP_DRIVER są używane do żądania emisji pakietów.

| NX_IP_DRIVER członkowski                | Znaczenie          |
|------------------------------------|--------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST |
| nx_ip_driver_ptr                   | Wskaźnik do wystąpienia adresu IP  |
| nx_ip_driver_packet                | Wskaźnik do pakietu do końca |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF emisji) |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF emisji) |
| nx_ip_driver_interface             | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status                | Stan ukończenia. Jeśli sterownik nie jest w stanie wysłać pakietu, zwróci stan błędu niezerowego. |

### <a name="arp-send"></a>Wysyłanie ARP  

To żądanie jest również podobne do żądania wysyłania pakietów IP.
Jedyna różnica polega na tym, że nagłówek Ethernet określa pakiet ARP zamiast pakietu IP, a pola docelowego adresu fizycznego są ustawione na adres emisji MAC. W żądaniu NX_IP_DRIVER ARP są używane następujące elementy członkowskie.

| **NX_IP_DRIVER członkowski** | **Znaczenie** |
| --- | --- |
| nx_ip_driver_command | NX_LINK_ARP_SEND |
| nx_ip_driver_ptr | Wskaźnik do wystąpienia adresu IP. |
| nx_ip_driver_packet | Wskaźnik do pakietu do wysłania. |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (emisja) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (emisja) |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu ARP, zwróci stan błędu niezerowego. |

*Jeśli mapowanie fizyczne nie jest wymagane, implementacja tego żądania nie jest wymagana.*

### <a name="arp-response-send"></a>Wysyłanie odpowiedzi ARP  

To żądanie jest niemal identyczne z żądaniem wysyłania pakietu ARP. Jedyna różnica polega na tym, że pola docelowego adresu fizycznego są przekazywane z wystąpienia adresu IP. Następujące elementy NX_IP_DRIVER są używane dla żądania wysłania odpowiedzi ARP.

| NX_IP_DRIVER członkowski               | Znaczenie |
|-----------------------------------| ------------------------------------|
| nx_ip_driver_command              | NX_LINK_ARP_RESPONSE_SEND |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_packet               | Wskaźnik do pakietu do wysłania|
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32-bity adresu fizycznego |
| nx_ip_driver_physical_address_lsw | Najmniej znaczący 32-bitowy adres fizyczny                     |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu ARP, zwróci stan błędu niezerowego. |

> [!NOTE]
> *Jeśli mapowanie fizyczne nie jest wymagane, implementacja tego żądania nie jest wymagana.*

### <a name="rarp-send"></a>Wysyłanie RARP  

To żądanie jest niemal identyczne z żądaniem wysyłania pakietu ARP. Jedynymi różnicami są typ nagłówka pakietu i pola adresu fizycznego nie są wymagane, ponieważ miejsce docelowe fizyczne jest zawsze adresem emisji.

W przypadku żądania NX_IP_DRIVER RARP są używane następujące elementy członkowskie.

| NX_IP_DRIVER członkowski               | Znaczenie |
|-----------------------------------|---------------------------------|
| nx_ip_driver_command              |NX_LINK_RARP_SEND |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_packet               | Wskaźnik do pakietu do wysłania |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (emisja) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (emisja) |
| NX_IP_DRIVER członkowski               | Znaczenie |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu RARP, zwróci stan błędu niezerowy.  |

> [!NOTE]
> *Aplikacje, które wymagają usługi RARP, muszą zaimplementować to polecenie.*

### <a name="multicast-group-join"></a>Przyłączenie do grupy multiemisji  

To żądanie jest dokonywane przy użyciu ***usługi nx_igmp_multicast_interface join.*** Sterownik sieciowy pobiera podany adres grupy multiemisji i konfiguruje nośnik fizyczny do akceptowania pakietów przychodzących z tego adresu grupy multiemisji. Należy pamiętać, że w przypadku sterowników, które nie obsługują filtru multiemisji, logika odbierania sterowników może być w trybie promiscuous. W takim przypadku sterownik może wymagać filtrowania klatek przychodzących na podstawie docelowego adresu MAC, co zmniejsza ilość ruchu przekazywanego do wystąpienia adresu IP. Następujące elementy NX_IP_DRIVER są używane w przypadku żądania dołączenia do grupy multiemisji.

| NX_IP_DRIVER członkowski               | Znaczenie |
|-----------------------------------|-----------------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_JOIN                                                |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP                                                |
| nx_ip_driver_physical_address_msw | Najbardziej znaczący 32-bitowy fizyczny adres multiemisji                |
| nx_ip_driver_physical_address_lsw | Najmniej znaczące 32-bitowe fizycznego adresu multiemisji               |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu                                     |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może dołączyć do grupy multiemisji, zwróci niezerowy stan błędu. |


### <a name="multicast-group-leave"></a>Pozostawienie grupy multiemisji  

To żądanie jest wywoływane przez jawne wywołanie ***nx_igmp_multicast_leave*** usługi. Sterownik usuwa podany adres multiemisji Ethernet z listy multiemisji. Gdy host opuści grupę multiemisji, pakiety w sieci z tym adresem multiemisji Ethernet nie będą już odbierane przez to wystąpienie adresu IP. Następujące elementy NX_IP_DRIVER są używane w przypadku żądania opuszczenia grupy multiemisji.

| NX_IP_DRIVER członkowski               | Znaczenie |
|-----------------------------------|-----------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_LEAVE |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32 bity fizycznego rozsyłania multiemisji |
| nx_ip_driver_physical_address_lsw | Najmniej znaczący 32 bity fizycznego adresu multiemisji |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może opuścić grupy multiemisji, zwróci niezerowy stan błędu. |


### <a name="attach-interface"></a>Dołączanie interfejsu  

To żądanie jest wywoływane ze sterownika NetX do sterownika urządzenia, co umożliwia sterownikowi skojarzenie wystąpienia sterownika z odpowiednim wystąpieniem adresu IP i wystąpieniem interfejsu fizycznego w obrębie adresu IP. Następujące elementy NX_IP_DRIVER są używane do żądania dołączenia interfejsu.

| NX_IP_DRIVER członkowski    | Znaczenie |
|------------------------|-------------------------------------------------|
| nx_ip_driver_command   | X_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może odłączyć określonego interfejsu od wystąpienia adresu IP, zwróci niezerowy stan błędu.  |


### <a name="detach-interface"></a>Odłączanie interfejsu  

To żądanie jest wywoływane przez netx do sterownika urządzenia, dzięki czemu sterownik może nie skojarzyć wystąpienia sterownika z odpowiednim wystąpieniem adresu IP i wystąpieniem interfejsu fizycznego w obrębie adresu IP. Następujące elementy NX_IP_DRIVER są używane do żądania dołączenia interfejsu.

| NX_IP_DRIVER członkowski    | Znaczenie |
|------------------------|---------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może dołączyć określonego interfejsu do wystąpienia adresu IP, zwróci niezerowy stan błędu. |

### <a name="get-link-status"></a>Uzyskiwanie stanu linku  

Aplikacja może zapytania o stan łącza interfejsu sieciowego przy użyciu usługi NetX  ***nx_ip_interface_status_check*** dla dowolnego interfejsu na hoście. Aby uzyskać więcej informacji na temat tych usług, zobacz rozdział 4 "Opis usług NetX" na stronie 107.

Stan łącza jest zawarty w polu *nx_interface_link_up* w strukturze NX_INTERFACE wskazywanej przez wskaźnik *nx_ip_driver_interface* danych. Następujące NX_IP_DRIVER są używane do żądania stanu łącza.

| NX_IP_DRIVER członkowski     | Znaczenie                                                                                                      |
|-------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_STATUS                                                                                           |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                       |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, aby umieścić stan.                                                              |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                            |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać określonego stanu, zwróci stan błędu niezerowego. |
|                         |                                                                                                              |

> [!NOTE]
> ***nx_ip_status_check** jest nadal dostępna do sprawdzania stanu interfejsu podstawowego. Zachęcamy jednak deweloperów aplikacji do korzystania z usług specyficznych dla **interfejsu nx_ip_interface_status_check.***

### <a name="get-link-speed"></a>Uzyskiwanie szybkości łącza  

To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje szybkość linii łącza w podanej lokalizacji docelowej. Następujące elementy NX_IP_DRIVER są używane do żądania szybkości wiersza linku.

| NX_IP_DRIVER członkowski     | Znaczenie |
|-------------------------|---------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_SPEED |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, aby umieścić szybkość linii |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać informacji o szybkości, zwróci stan błędu niezerowego.
 |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez netx, więc jego implementacja jest opcjonalna.*

### <a name="get-duplex-type"></a>Uzyskiwanie typu dwukierunkowego  

To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje dwukierunkowy typ linku w podanej lokalizacji docelowej. Następujące elementy NX_IP_DRIVER są używane do żądania typu dwukierunkowego.

| NX_IP_DRIVER członkowski     | Znaczenie |
|-------------------------|-----------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_DUPLEX_TYPE |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczany typ dwukierunkowy |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać informacji dwukierunkowych, zwróci stan błędu niezerowego.
 |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez netx, więc jego implementacja jest opcjonalna.*

### <a name="get-error-count"></a>Uzyskiwanie liczby błędów  

To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę błędów linku w podanej lokalizacji docelowej. Aby obsługiwać tę funkcję, sterownik musi śledzić błędy operacji. W żądaniu liczby NX_IP_DRIVER linku są używane następujące elementy członkowskie.

| NX_IP_DRIVER członkowski     | Znaczenie                                                                                                  |
|-------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_ERROR_COUNT                                                                                  |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                   |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba błędów                                                      |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                        |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby błędów, zwróci stan błędu niezerowego. |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez netx, więc jego implementacja jest opcjonalna.*

### <a name="get-receive-packet-count"></a>Uzyskiwanie liczby pakietów odbieranych  

To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę pakietów odbioru linku w podanej lokalizacji docelowej. Aby obsługiwać tę funkcję, sterownik musi śledzić liczbę odebranych pakietów. Następujące NX_IP_DRIVER są używane dla żądania liczby pakietów odbierania linku.

| NX_IP_DRIVER członkowski     | Znaczenie                                                                                                    |
|-------------------------|------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_RX_COUNT                                                                                       |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                     |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba pakietów odbieranych                                               |
| nx_ip_driver_interface  | Wskaźnik do fizycznego interfejsu sieciowego                                                                  |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby odbierania, zwróci stan błędu niezerowego. |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez netx, więc jego implementacja jest opcjonalna.*

### <a name="get-transmit-packet-count"></a>Uzyskiwanie liczby pakietów przesyłanych  

To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę pakietów przesyłanych linku w podanej lokalizacji docelowej. Aby obsługiwać tę funkcję, sterownik musi śledzić każdy pakiet przesyłany w każdym interfejsie. Następujące elementy NX_IP_DRIVER są używane do żądania liczby pakietów przesyłania linku.

| NX_IP_DRIVER członkowski     | Znaczenie                                                                                                     |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_TX_COUNT                                                                                        |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                      |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba pakietów przesyłanych                                               |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                           |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby transmisji, zwróci niezerowy stan błędu. |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez netx, więc jego implementacja jest opcjonalna.*

### <a name="get-allocation-errors"></a>Uzyskiwanie błędów alokacji  

To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przechowuje liczbę błędów alokacji puli pakietów łącza w podanej lokalizacji docelowej. Następujące elementy NX_IP_DRIVER są używane do żądania liczby błędów alokacji łącza.

| **NX_IP_DRIVER członkowski** | **Znaczenie** |
| --- | ---|
| nx_ip_driver_command | NX_LINK_GET_ALLOC_ERRORS |
| nx_ip_driver_ptr | Wskaźnik do wystąpienia adresu IP |

| NX_IP_DRIVER członkowski     | Znaczenie                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma być umieszczana liczba błędów alokacji                                                 |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                              |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać błędów alokacji, zwróci niezerowy stan błędu. |


*To żądanie nie jest używane wewnętrznie przez netx, więc jego implementacja jest opcjonalna.*

### <a name="driver-deferred-processing"></a>Przetwarzanie odroczone sterownika  

To żądanie jest dokonywane z wątku pomocnika IP w odpowiedzi na sterownik wywołujący _ ***nx_ip_driver_deferred_processing*** procedury z isr przesyłania lub odbierania. Dzięki temu sterownik ISR odroczyć odbieranie pakietów i przesyłanie przetwarzania do wątku pomocnika IP, a tym samym zmniejszyć ilość przetwarzania w ISR. Pole *nx_interface_additional_link_info* w strukturze NX_INTERFACE wskazywane przez  nx_ip_driver_interface może być używane przez sterownik do przechowywania informacji o zdarzeniu przetwarzania odroczonego z kontekstu wątku pomocnika IP. Następujące elementy NX_IP_DRIVER są używane dla zdarzenia przetwarzania odroczonego.

**NX_IP_DRIVER**

| członek                 | Znaczenie                           |
|------------------------|-----------------------------------|
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING       |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP            |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |


### <a name="user-commands"></a>Polecenia użytkownika  

To żądanie jest dokonywane z poziomu ***nx_ip_driver_direct_command*** usługi. Sterownik przetwarza polecenia użytkownika specyficzne dla aplikacji. Następujące NX_IP_DRIVER są używane do żądania polecenia użytkownika.

| NX_IP_DRIVER członkowski     | Znaczenie                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_USER_COMMAND                                                                                           |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                         |
| nx_ip_driver_return_ptr | Zdefiniowane przez użytkownika                                                                                                   |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                              |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może wykonać poleceń użytkownika, zwróci stan błędu niezerowy. |


*To żądanie nie jest używane wewnętrznie przez netx, więc jego implementacja jest opcjonalna.*

### <a name="unimplemented-commands"></a>Niezaimplementowane polecenia  

Polecenia niezaimplementowane przez sterownik sieciowy muszą mieć ustawione pole stanu zwracania na NX_UNHANDLED_COMMAND.

## <a name="driver-output"></a>Dane wyjściowe sterownika  

Wszystkie wymienione wcześniej żądania przesyłania pakietów wymagają funkcji wyjściowej zaimplementowanej w sterowniku. Specyficzna logika przesyłania jest specyficzna dla sprzętu, ale zazwyczaj polega na sprawdzeniu pojemności sprzętowej w celu natychmiastowego wysłania pakietu. Jeśli to możliwe, ładunek pakietu (i dodatkowe ładunki w łańcuchu pakietów) są ładowane do co najmniej jednego sprzętowego buforu przesyłania i inicjowana jest operacja przesyłania. Jeśli pakiet nie mieści się w dostępnych buforach przesyłania, należy go w kolejce i przesłać, gdy bufory transmisji staną się dostępne.

Zalecana kolejka przesyłania to lista połączona jednolicie, ze wskaźnikami zarówno głowy, jak i ogona. Nowe pakiety są dodawane na końcu kolejki, zachowując najstarszy pakiet z przodu. Pole *nx_packet_queue_next* jest używane jako następne łącze pakietu w kolejce. Sterownik definiuje wskaźniki głowy i ogona kolejki przesyłania.

*Ponieważ dostęp do tej kolejki jest uzyskiwany z części sterownika wątków i przerwań, ochrona przerwań musi być umieszczana wokół manipulacji kolejką.*

Większość implementacji sprzętu fizycznego generuje przerwanie po zakończeniu przesyłania pakietów.
Gdy sterownik otrzymuje takie przerwanie, zwykle zwalnia zasoby skojarzone z właśnie przesyłanym pakietem. Jeśli logika przesyłania odczytuje dane bezpośrednio z buforu NX_PACKET, sterownik powinien użyć usługi ***nx_packet_transmit_release*** do zwolnienia pakietu skojarzonego z kompletnym przerwaniem przesyłania z powrotem do dostępnej puli pakietów. Następnie sterownik sprawdza kolejkę przesyłania pod tematem dodatkowych pakietów oczekujących na wysłanie. Ponieważ wiele pakietów przesyłanych w kolejce, które mieszczą się w sprzętowych buforach przesyłania, jest dekodowana i ładowana do buforów. Następnie następuje zainicjowanie innej operacji wysyłania.

Gdy tylko dane w tabeli NX_PACKET zostały przeniesione do fifo (lub jeśli sterownik obsługuje operację zerocopy, dane w programie NX_PACKET zostały przesłane), sterownik musi przenieść nx_packet_prepend_ptr na początek nagłówka IP przed wywołaniem ***nx_packet_transmit_release.*** Pamiętaj, aby *odpowiednio nx_packet_length* pola. Jeśli ramka IP składa się z wielu pakietów, musi zostać zwolniona tylko część łańcucha pakietów.

## <a name="driver-input"></a>Dane wejściowe sterownika  

Po otrzymaniu odebranego przerwania pakietu sterownik sieciowy pobiera pakiet z buforów odbioru sprzętu fizycznego i tworzy prawidłowy pakiet NetX. Tworzenie prawidłowego pakietu NetX obejmuje skonfigurowanie odpowiedniego pola długości i połączenie w łańcuch wielu pakietów, jeśli rozmiar pakietu przychodzącego jest większy niż pojedynczy ładunek pakietu. Po prawidłowym s zbudowaniu prepend_ptr jest przenoszony po nagłówku warstwy fizycznej, a pakiet odbierany jest wysyłany do NetX.

NetX zakłada, że nagłówki IP i ARP są wyrównane na granicy ULONG. W związku z tym sterownik NetX musi zapewnić wyrównanie. W środowiskach Ethernet jest to wykonywane przez uruchomienie nagłówka Ethernet dwa bajty od początku pakietu. Gdy adres *nx_packet_prepend_ptr* jest przenoszony poza nagłówek Ethernet, źródłowy nagłówek adresu IP lub protokołu ARP jest wyrównany o 4 mb.

Istnieje kilka funkcji odbierania pakietów dostępnych w NetX. Jeśli odebrany pakiet jest pakietem ARP, _* **nx_arp_packet_deferred_receive**_ wywoływana. Jeśli odebrany pakiet jest pakietem RARP,_*_wywoływana jest nx_rarp_packet_deferred_receive_*_ _ . Istnieje kilka opcji obsługi przychodzących pakietów IP. W celu najszybszej obsługi pakietów IP wywoływana _*_jest nx_ip_packet_receive_*_ _ . Takie podejście ma najmniejsze obciążenie, ale wymaga większej liczby przetwarzania w obsłudze usługi przerywania odbioru (ISR) sterownika. W przypadku minimalnego przetwarzania isr *___ nx_ip_packet_deferred_receive_** jest wywoływana.

Po prawidłowym s zbudowaniu nowego pakietu odbierania bufory odbioru sprzętu fizycznego są konfigurowane w celu odbierania większej liczby danych. Może to wymagać przydzielenia pakietów NetX i umieszczenia adresu ładunku w sprzętowym buforze odbierania lub może po prostu oznaczać zmianę ustawienia w buforze odbioru sprzętu. Aby zminimalizować możliwości przepełnienia, ważne jest, aby bufory odbioru sprzętu były dostępne bufory tak szybko, jak to możliwe po otrzymaniu pakietu.

*Początkowe bufory odbierania są konfigurowane podczas inicjowania sterownika.*

### <a name="deferred-receive-packet-handling"></a>Obsługa odroczonego pakietu odbierania  

Sterownik może odroczyć odbieranie przetwarzania pakietów do wątku pomocnika IP NetX. W przypadku niektórych aplikacji może to być konieczne w celu zminimalizowania przetwarzania isr, a także porzucanych pakietów. Aby można było korzystać z obsługi pakietów odroczonych, biblioteka NetX musi najpierw zostać skompilowana przy użyciu funkcji ***NX_DRIVER_DEFERRED_PROCESSING** _ defined. Powoduje to dodanie logiki pakietów odroczonych do wątku pomocnika IP NetX. Następnie po odebraniu pakietu danych sterownik musi wywołać __nx_ip_packet_deferred_receive():*

```C
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```

Funkcja odroczonego odbierania umieszcza pakiet  odbierany reprezentowany przez packet_ptr w fifo (połączonej liście) i powiadamia wątek pomocnika IP. Po wykonaniu pomocnik IP wielokrotnie wywołuje funkcję obsługi odroczonej w celu przetwarzania każdego odroczonego pakietu. Odroczone przetwarzanie procedury obsługi zwykle obejmuje usunięcie nagłówka warstwy fizycznej pakietu (zazwyczaj Ethernet) i wysłanie go do jednej z tych funkcji odbierania NetX:  

***_nx_ip_packet_deferred_receive***  
***_nx_arp_packet_deferred_receive***  
***_nx_rarp_packet_deferred_receive*** 


## <a name="example-ram-ethernet-network-driver"></a>Przykład sterownika sieci Ethernet pamięci RAM  

Demonstracyjny system NetX jest dostarczany z małym sterownikem sieciowym opartym na pamięci RAM zdefiniowanym w pliku ***nx_ram_network_driver.c.***
Ten sterownik zakłada, że wszystkie wystąpienia adresów IP znajdują się w tej samej sieci i po prostu przypisuje wirtualne adresy sprzętowe (adresy MAC) do każdego wystąpienia urządzenia podczas ich tworzenia. Ten plik zawiera dobry przykład podstawowej struktury fizycznych sterowników sieciOwych NetX. Użytkownicy mogą opracowywać własne sterowniki sieciowe przy użyciu struktury sterowników przedstawionej w tym przykładzie.

Funkcja wprowadzania sterownika sieciowego to ***_nx_ram_network_driver,** _, która jest przekazywana do wywołania tworzenia wystąpienia adresu IP. Funkcje wejścia dla dodatkowych interfejsów sieciowych mogą być przekazywane do _*_nx_ip_interface_attach_*_ usługi. Po uruchomieniu wystąpienia adresu IP wywoływana jest funkcja wprowadzania sterownika w celu zainicjowania i włączenia urządzenia (zapoznaj się z przypadkiem _ *NX_LINK_INITIALIZE** i **NX_LINK_ENABLE**). Po **NX_LINK_ENABLE** urządzenie powinno być gotowe do przesyłania i odbierania pakietów. 

Wystąpienie adresu IP przesyła pakiety sieciowe za pomocą jednego z tych poleceń:

| ***NX_LINK_PACKET_SEND***    | Pakiet IP jest przesyłany,                             |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_ARP_SEND***       | Żądanie ARP lub pakiet odpowiedzi ARP jest przesyłany,    |
| ***NX_LINK_ARP_RARP_SEND*** | Przesyłany jest zwrotny pakiet żądania lub odpowiedzi ARP. |

Podczas przetwarzania tych poleceń sterownik sieciowy musi dołączać odpowiedni nagłówek ramki Ethernet, a następnie wysyłać go do bazowego sprzętu w celu transmisji. Podczas procesu transmisji sterownik sieciowy ma wyłączną własność obszaru buforu pakietów. W związku z tym po przesłaniu danych (lub skopiowaniu danych do wewnętrznego buforu transferu sterownika) sterownik sieciowy jest odpowiedzialny za zwolnienie buforu pakietów przez przeniesienie wstępnie otwartego wskaźnika poza nagłówek Ethernet do nagłówka IP (i odpowiednie dostosowanie długości pakietów), a następnie przez wywołanie usługi ***nx_packet_transmit_release*** w celu zwolnienia pakietu. Nie zwalnianie pakietu po transmisji danych spowoduje wyciek pakietów.

Sterownik urządzenia sieciowego jest również odpowiedzialny za obsługę przychodzących pakietów danych. W przykładzie sterownika pamięci RAM odebrany pakiet jest przetwarzany przez ***funkcję*** _nx_ram_network_driver_receive .

Gdy urządzenie odbierze ramkę Ethernet, sterownik jest odpowiedzialny za przechowywanie danych w

NX_PACKET struktury. Należy pamiętać, że netx zakłada, że nagłówek IP rozpoczyna się od adresu wyrównany 4-bajtowy. Ponieważ długość nagłówka ethernet jest 14-bajtowy, sterownik musi przechowywać początek nagłówka Ethernet na adres wyrównany 2-bajtowy, aby zagwarantować, że nagłówek IP zaczyna się od adresu wyrównane 4-bajtowego.