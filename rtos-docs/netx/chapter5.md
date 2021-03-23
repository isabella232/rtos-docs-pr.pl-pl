---
title: Rozdział 5 — sterowniki sieciowe usługi Azure RTO NetX
description: Ten rozdział zawiera opis sterowników sieciowych dla usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 09/11/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ccc55111d785d84cdb193c387830abbc03a15e7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822758"
---
# <a name="chapter-5---netx-network-drivers"></a>Rozdział 5 — NetX sterowniki sieciowe

Ten rozdział zawiera opis sterowników sieciowych dla usługi NetX. Przedstawione informacje ułatwiają deweloperom pisanie sterowników sieciowych specyficznych dla aplikacji dla usługi Azure RTO NetX.

## <a name="driver-introduction"></a>Wprowadzenie do sterownika

Struktura NX_IP zawiera wszystkie elementy do zarządzania pojedynczym wystąpieniem IP. Obejmuje to ogólne informacje o protokole TCP/IP, a także procedurę wejścia sterownika sieci fizycznej specyficzną dla aplikacji. Procedura wejścia sterownika jest definiowana podczas ***nx_ip_create*** usługi. Dodatkowe urządzenia mogą być dodawane do wystąpienia IP za pośrednictwem usługi ***nx_ip_interface_attach*** .

Komunikacja między NetX i sterownikiem sieciowym aplikacji jest realizowana za pomocą struktury żądania **NX_IP_DRIVER** . Ta struktura jest najczęściej zdefiniowana lokalnie na stosie obiektu wywołującego i dlatego jest wydawana po powrocie sterownika i wywołania funkcji. Struktura jest zdefiniowana w następujący sposób.

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

NetX wywołuje funkcję wpisu sterownika sieci na potrzeby inicjowania sterownika i wysyłania pakietów oraz dla różnych operacji kontroli i stanu, w tym inicjowania i włączania urządzenia sieciowego. NetX wydaje polecenia do sterownika sieciowego przez ustawienie ***nx_ip_driver_command** _ pola w strukturze _ *NX_IP_DRIVER**. Funkcja wprowadzania sterowników ma następujący format:

```C
VOID my_driver_entry(NX_IP_DRIVER *request);
```

## <a name="driver-requests"></a>Żądania sterowników

NetX tworzy żądanie sterownika przy użyciu określonego polecenia i wywołuje funkcję wejścia sterownika, aby wykonać polecenie. Ponieważ każdy sterownik sieciowy ma funkcję pojedynczego wpisu, NetX wykonuje wszystkie żądania za pomocą struktury danych żądania sterownika. ***Nx_ip_driver_command*** członek struktury danych żądania sterownika (**NX_IP_DRIVER**) definiuje żądanie. Informacje o stanie są raportowane z powrotem do obiektu wywołującego w ***nx_ip_driver_status*** członkowskich. Jeśli to pole jest **NX_SUCCESS**, żądanie sterownika zostało zakończone pomyślnie.

NetX serializować cały dostęp do sterownika. W związku z tym sterownik nie musi obsługiwać wielu wątków asynchronicznie wywołujących funkcję entry. Należy pamiętać, że funkcja sterownika urządzenia jest wykonywana z zablokowanym elementem mutex IP. W związku z tym wewnętrzna funkcja sterownika urządzenia nie jest blokowana.

Zazwyczaj sterownik urządzenia obsługuje również przerwania. W związku z tym wszystkie funkcje sterownika muszą być bezpieczne dla przerwań.

### <a name="driver-initialization"></a>Inicjowanie sterownika

Chociaż rzeczywiste przetwarzanie inicjacji sterownika jest specyficzne dla aplikacji, zwykle składa się ona ze struktury danych i fizycznej inicjalizacji sprzętowej. Informacje wymagane od NetX do inicjacji sterownika to maksymalna jednostka transmisji (MTU) IP, czyli liczba bajtów dostępnych dla ładunku warstwy IP, w tym nagłówek IP, a jeśli interfejs fizyczny wymaga mapowania logicznego do fizycznego. Wymagania dotyczące sterownika

Aby skonfigurować jednostkę MTU interfejsu przez ustawienie wartości w ***nx_interface_ip_mtu_size** _ w strukturze _ *NX_INTERFACE**.

Sterownik urządzenia musi również skonfigurować wartość w ***nx_ip_interface_address_mapping_needed*** w

**NX_INTERFACE** , aby informować o tym, czy mapowanie adresów interfejsu jest wymagane. Jeśli konieczne jest mapowanie adresów, sterownik jest odpowiedzialny za skonfigurowanie interfejsu z prawidłowym adresem MAC i dostarczenie adresu MAC NetX.

Gdy sterownik sieciowy odbiera NX_LINK żądanie INITIALIZE z NetX, otrzymuje wskaźnik do bloku kontroli IP w ramach bloku kontrolki żądania NX_IP_DRIVER pokazanego powyżej.

Gdy aplikacja wywoła ***nx_ip_create***, wątek pomocnika IP wysyła żądanie sterownika z zestawem polecenie, aby NX_LINK_INITIALIZE do sterownika w celu zainicjowania fizycznego interfejsu sieciowego. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania Initialize.

| NX_IP_DRIVER składową    | Znaczenie |
|------------------------|-----------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INITIALIZE |
| nx_ip_driver_ptr       | Wskaźnik na wystąpienie protokołu IP. Ta wartość powinna być zapisywana przez sterownik, aby funkcja sterownika mogła znaleźć wystąpienie adresu IP, na którym ma działać. |
| nx_ip_driver_interface | Wskaźnik do struktury interfejsu sieciowego w ramach wystąpienia adresu IP. Te informacje powinny być zapisywane przez sterownik. W przypadku pakietów odbierających sterownik używa informacji o strukturze interfejsu podczas wysyłania pakietu w górę stosu. |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może zainicjować określonego interfejsu w wystąpieniu protokołu IP, spowoduje to zwrócenie stanu błędu o wartości niezerowej.                                                                                           |


> [!IMPORTANT]
> *Większość poleceń sterowników jest wywoływanych z wątku pomocnika IP, który został utworzony dla wystąpienia IP. W związku z tym procedura sterownika powinna unikać wykonywania operacji blokowania lub wątek pomocnika IP może spowodować nieograniczone opóźnienia dla aplikacji, które korzystają z wątku IP.*

### <a name="enable-link"></a>Włącz link  

Następnie wątek pomocnika IP włącza sieć fizyczną przez ustawienie polecenia sterownika NX_LINK_ENABLE w żądaniu sterownika i wysłanie żądania do sterownika sieciowego. Dzieje się to wkrótce po zakończeniu wątku pomocnika IP. Włączenie linku może być proste, ponieważ ustawienie pola nx_interface_link_up w wystąpieniu interfejsu. Może to jednak również wymagać manipulowania sprzętem fizycznym. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania włączenia linku.

| NX_IP_DRIVER składową    | Znaczenie |
|------------------------|------------------------------------------|
| nx_ip_driver_command   | NX_LINK_ENABLE                                                                                                          |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP                                                                                                  |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu                                                                                       |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może włączyć określonego interfejsu, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |



### <a name="disable-link"></a>Wyłącz link  

To żądanie jest nawiązywane przez NetX podczas usuwania wystąpienia IP przez usługę ***nx_ip_delete** _. Lub aplikacja może wydać to polecenie, aby tymczasowo wyłączyć link w celu zaoszczędzenia mocy. Ta usługa wyłącza fizyczny interfejs sieciowy w wystąpieniu IP. Przetwarzanie w celu wyłączenia łącza może być proste, ponieważ czyści _flagę nx_interface_link_up * w wystąpieniu interfejsu. Może to jednak również wymagać manipulowania sprzętem fizycznym. Zwykle jest to operacja odwrotna operacji ***enable link**_ . Gdy łącze zostanie wyłączone, żądanie aplikacji _ Włącz operację *_link_**, aby włączyć interfejs. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania Disable link.

| NX_IP_DRIVER składową    | Znaczenie |
|------------------------|--------------------------------------|
| nx_ip_driver_command   | NX_LINK_DISABLE |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może wyłączyć określonego interfejsu w wystąpieniu protokołu IP, zwróci on stan błędu różny od zera. |


### <a name="uninitialize-link"></a>Odinicjuj łącze  

To żądanie jest nawiązywane przez NetX podczas usuwania wystąpienia IP przez usługę ***nx_ip_delete*** . To żądanie służy do odinicjowania interfejsu i zwolnienia wszelkich zasobów utworzonych podczas fazy inicjalizacji. Zwykle jest to operacja odwrotna operacji ***inicjowania linku*** . Po uninitalized interfejsu nie można użyć urządzenia, dopóki interfejs nie zostanie ponownie zainicjowany.

Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania Disable link.

| NX_IP_DRIVER składową  | Znaczenie                |
|----------------------|------------------------|
| nx_ip_driver_command | NX_LINK_UNINITIALZE    |
| nx_ip_driver_ptr     | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może wymusić inicjalizacji określonego interfejsu do wystąpienia IP, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |


### <a name="packet-send"></a>Wysyłanie pakietów  

To żądanie jest wykonywane w trakcie wewnętrznego przetwarzania wysyłania adresów IP, przetwarzania, w którym wszystkie protokoły NetX używają do przesyłania pakietów (z wyjątkiem ARP, RARP). W przypadku odebrania polecenia Wyślij pakiet *nx_packet_prepend_ptr* wskazuje na początek pakietu do wysłania, czyli początek nagłówka IP.
*nx_packet_length* wskazuje łączny rozmiar (w bajtach) przesyłanych danych. Jeśli *nx_packet_next* jest prawidłowy, wychodzący datagram IP jest przechowywany w wielu pakietach, sterownik jest wymagany do podążania za łańcuchowym pakietem i przesyłania całej ramki. Należy zauważyć, że prawidłowy obszar danych w każdym łańcuchowym pakiecie jest przechowywany między *nx_packet_prepend_ptr* i *nx_packet_append_ptr*.

Sterownik jest odpowiedzialny za konstruowanie nagłówka fizycznego. Jeśli wymagany jest adres fizyczny do mapowania adresów IP (np. Ethernet), warstwa adresów IP już rozwiązała adres MAC. Docelowy adres MAC jest przesyłany z wystąpienia IP przechowywanego w *nx_ip_driver_physical_address_msw i nx_ip_driver_physical_address_lsw.*

Po dodaniu fizycznego nagłówka, przetwarzanie wysyłane przez pakiet, następnie wywołuje funkcję wyjściową sterownika, aby przesłać pakiet.

Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania wysłania pakietu.

| NX_IP_DRIVER składową               | Znaczenie |
|-----------------------------------|---------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_PACKET_SEND |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_packet               | Wskaźnik do pakietu do wysłania |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu.             |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32-bitowe adresów fizycznych (tylko w przypadku konieczności mapowania fizycznego) |
| nx_ip_driver_physical_address_lsw | Najmniej znaczące 32-bitów adresów fizycznych (tylko w przypadku konieczności mapowania fizycznego)    |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu, spowoduje to zwrócenie stanu błędu o wartości innej niż zero.  |

### <a name="packet-broadcast"></a>Emisja pakietów  
To żądanie jest niemal identyczne z żądaniem wysyłania pakietu. Jedyną różnicą jest to, że docelowe pola adresu fizycznego są ustawiane na adres MAC emisji sieci Ethernet. Do żądania emisji pakietów są używane następujące elementy członkowskie NX_IP_DRIVER.

| NX_IP_DRIVER składową                | Znaczenie          |
|------------------------------------|--------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST |
| nx_ip_driver_ptr                   | Wskaźnik do wystąpienia adresu IP  |
| nx_ip_driver_packet                | Wskaźnik do pakietu do końca |
| nx_ip_driver_physical_address_ms w | Emisja 0x0000FFFF) |
| nx_ip_driver_physical_address_lsw  | emisji 0xFFFFFFFF) |
| nx_ip_driver_interface             | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status                | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |

### <a name="arp-send"></a>Wysyłanie protokołu ARP  

To żądanie jest również podobne do żądania wysłania pakietów IP.
Jedyną różnicą jest to, że nagłówek Ethernet określa pakiet ARP zamiast pakietu IP, a docelowe pola adresów fizycznych są ustawiane na adres MAC emisji. Do żądania wysłania ARP są używane następujące elementy członkowskie NX_IP_DRIVER.

| **NX_IP_DRIVER składową** | **Znaczenie** |
| --- | --- |
| nx_ip_driver_command | NX_LINK_ARP_SEND |
| nx_ip_driver_ptr | Wskaźnik na wystąpienie adresu IP. |
| nx_ip_driver_packet | Wskaźnik do pakietu do wysłania. |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (broadcast) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (emisja) |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu ARP, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |

*Jeśli mapowanie fizyczne nie jest potrzebne, implementacja tego żądania nie jest wymagana.*

### <a name="arp-response-send"></a>Wysyłanie odpowiedzi ARP  

To żądanie jest niemal identyczne z żądaniem wysyłania pakietów protokołu ARP. Jedyną różnicą jest to, że docelowe pola adresów fizycznych są przesyłane z wystąpienia IP. Do żądania wysłania odpowiedzi ARP są używane następujące elementy członkowskie NX_IP_DRIVER.

| NX_IP_DRIVER składową               | Znaczenie |
|-----------------------------------| ------------------------------------|
| nx_ip_driver_command              | NX_LINK_ARP_RESPONSE_SEND |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_packet               | Wskaźnik do pakietu do wysłania|
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32-bitów adresu fizycznego |
| nx_ip_driver_physical_address_lsw | Najmniej znaczące 32-bitowe adresy fizyczne                     |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu ARP, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |

> [!NOTE]
> *Jeśli mapowanie fizyczne nie jest potrzebne, implementacja tego żądania nie jest wymagana.*

### <a name="rarp-send"></a>RARP wysyłaj  

To żądanie jest niemal identyczne z żądaniem wysyłania pakietów protokołu ARP. Jedyne różnice to typ nagłówka pakietu i pola adresu fizycznego nie są wymagane, ponieważ fizyczne miejsce docelowe jest zawsze adresem emisji.

Następujące NX_IP_DRIVER elementy członkowskie są używane dla żądania wysłania RARP.

| NX_IP_DRIVER składową               | Znaczenie |
|-----------------------------------|---------------------------------|
| nx_ip_driver_command              |NX_LINK_RARP_SEND |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_packet               | Wskaźnik do pakietu do wysłania |
| nx_ip_driver_physical_address_msw | 0x0000FFFF (broadcast) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF (emisja) |
| NX_IP_DRIVER składową               | Znaczenie |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może wysłać pakietu RARP, spowoduje to zwrócenie stanu błędu o wartości innej niż zero.  |

> [!NOTE]
> *Aplikacje wymagające usługi RARP muszą implementować to polecenie.*

### <a name="multicast-group-join"></a>Przyłączanie do grupy multiemisji  

To żądanie jest nawiązywane z usługą ***nx_igmp_multicast_interface Join*** . Sterownik sieciowy przyjmuje podany adres grupy multiemisji i konfiguruje nośnik fizyczny do akceptowania pakietów przychodzących z tego adresu grupy multiemisji. Należy pamiętać, że w przypadku sterowników, które nie obsługują filtru multiemisji, logika odbierania sterowników może być w trybie ogólnym. W takim przypadku może być konieczne odfiltrowanie ramek przychodzących na podstawie docelowego adresu MAC, co zmniejsza ilość ruchu przesyłanego do wystąpienia IP. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania dołączenia do grupy multiemisji.

| NX_IP_DRIVER składową               | Znaczenie |
|-----------------------------------|-----------------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_JOIN                                                |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP                                                |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32-bitowe fizyczne adresy multiemisji                |
| nx_ip_driver_physical_address_lsw | Najmniej znaczące 32-bitowe fizyczne adresy multiemisji               |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu                                     |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może dołączyć do grupy multiemisji, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |


### <a name="multicast-group-leave"></a>Opuszczenie grupy multiemisji  

To żądanie jest wywoływane przez jawne wywołanie usługi ***nx_igmp_multicast_leave*** . Sterownik usuwa podany adres multiemisji Ethernet z listy multiemisji. Gdy host opuścił grupę multiemisji, pakiety w sieci z tym adresem multiemisji Ethernet nie są już odbierane przez to wystąpienie tego adresu IP. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania opuszczenia grupy multiemisji.

| NX_IP_DRIVER składową               | Znaczenie |
|-----------------------------------|-----------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_LEAVE |
| nx_ip_driver_ptr                  | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_physical_address_msw | Najbardziej znaczące 32 dres IP fizycznych multiemisji |
| nx_ip_driver_physical_address_lsw | Najmniej znaczące 32 bitów fizycznego adresu multiemisji |
| nx_ip_driver_interface            | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status               | Stan ukończenia. Jeśli sterownik nie może opuścić grupy multiemisji, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |


### <a name="attach-interface"></a>Dołącz interfejs  

To żądanie jest wywoływane z NetX do sterownika urządzenia, umożliwiając sterownikowi skojarzenie wystąpienia sterownika z odpowiednim wystąpieniem adresu IP i wystąpieniem interfejsu fizycznego w ramach adresu IP. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania dołączania interfejsu.

| NX_IP_DRIVER składową    | Znaczenie |
|------------------------|-------------------------------------------------|
| nx_ip_driver_command   | X_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może odłączyć określonego interfejsu do wystąpienia IP, zostanie zwrócony stan błędu różny od zera.  |


### <a name="detach-interface"></a>Odłącz interfejs  

To żądanie jest wywoływane przez NetX do sterownika urządzenia, umożliwiając sterownikowi skojarzenie wystąpienia sterownika z odpowiednim wystąpieniem IP i wystąpieniem interfejsu fizycznego w ramach adresu IP. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania dołączania interfejsu.

| NX_IP_DRIVER składową    | Znaczenie |
|------------------------|---------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu. |
| nx_ip_driver_status    | Stan ukończenia. Jeśli sterownik nie może dołączyć określonego interfejsu do wystąpienia protokołu IP, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |

### <a name="get-link-status"></a>Pobierz stan łącza  

Aplikacja może wysyłać zapytania o stan łącza interfejsu sieciowego za pomocą usługi NetX  ***nx_ip_interface_status_check*** Service dla dowolnego interfejsu na hoście. Aby uzyskać więcej informacji na temat tych usług, zobacz rozdział 4 "Opis usług NetX Services" na stronie 107.

Stan łącza jest zawarty w polu *nx_interface_link_up* w strukturze NX_INTERFACE wskazywanym przez *nx_ip_driver_interface* wskaźnik. Do żądania stanu linku są używane następujące elementy członkowskie NX_IP_DRIVER.

| NX_IP_DRIVER składową     | Znaczenie                                                                                                      |
|-------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_STATUS                                                                                           |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                       |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego w celu umieszczenia stanu.                                                              |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                            |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać określonego stanu, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |
|                         |                                                                                                              |

> [!NOTE]
> ***nx_ip_status_check** nadal dostępne do sprawdzenia stanu interfejsu podstawowego. Jednak deweloperzy aplikacji zachęca się do korzystania z usługi specyficznej dla interfejsu **nx_ip_interface_status_check.***

### <a name="get-link-speed"></a>Pobierz szybkość łącza  

To żądanie jest nawiązywane z poziomu usługi ***nx_ip_driver_direct_command*** . Sterownik przechowuje szybkość linii linku w podanym miejscu docelowym. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania szybkiej szybkości łącza.

| NX_IP_DRIVER składową     | Znaczenie |
|-------------------------|---------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_SPEED |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, aby umieścić szybkość linii |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać informacji o szybkości, spowoduje to zwrócenie stanu błędu o wartości innej niż zero.
 |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez NetX, więc jego implementacja jest opcjonalna.*

### <a name="get-duplex-type"></a>Pobierz typ dupleksu  

To żądanie jest nawiązywane z poziomu usługi ***nx_ip_driver_direct_command*** . Sterownik przechowuje typ dupleksu linku w podanym miejscu docelowym. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania typu dupleksowego.

| NX_IP_DRIVER składową     | Znaczenie |
|-------------------------|-----------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_DUPLEX_TYPE |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego w celu umieszczenia typu dupleksowego |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać informacji o dupleksie, spowoduje to zwrócenie stanu błędu o wartości niezerowej.
 |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez NetX, więc jego implementacja jest opcjonalna.*

### <a name="get-error-count"></a>Pobierz liczbę błędów  

To żądanie jest nawiązywane z poziomu usługi ***nx_ip_driver_direct_command*** . Sterownik przechowuje liczbę błędów linku w podanym miejscu docelowym. Aby zapewnić obsługę tej funkcji, Sterownik musi śledzić błędy operacji. Do żądania liczby błędów linków są używane następujące elementy członkowskie NX_IP_DRIVER.

| NX_IP_DRIVER składową     | Znaczenie                                                                                                  |
|-------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_ERROR_COUNT                                                                                  |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                   |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma zostać umieszczona liczba błędów                                                      |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                        |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby błędów, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez NetX, więc jego implementacja jest opcjonalna.*

### <a name="get-receive-packet-count"></a>Pobierz liczbę pakietów odebranych  

To żądanie jest nawiązywane z poziomu usługi ***nx_ip_driver_direct_command*** . Sterownik przechowuje liczbę pakietów odbioru linku w podanej lokalizacji docelowej. Aby zapewnić obsługę tej funkcji, Sterownik musi śledzić liczbę odebranych pakietów. Następujące NX_IP_DRIVER członkowie są używani do żądania odebrania liczby pakietów.

| NX_IP_DRIVER składową     | Znaczenie                                                                                                    |
|-------------------------|------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_RX_COUNT                                                                                       |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                     |
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma zostać umieszczona liczba pakietów odbieranych                                               |
| nx_ip_driver_interface  | Wskaźnik do fizycznego interfejsu sieciowego                                                                  |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może uzyskać liczby odbieranych, zostanie zwrócony stan błędu różny od zera. |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez NetX, więc jego implementacja jest opcjonalna.*

### <a name="get-transmit-packet-count"></a>Pobierz liczbę pakietów transmisji  

To żądanie jest nawiązywane z poziomu usługi ***nx_ip_driver_direct_command*** . Sterownik przechowuje liczbę pakietów przesyłanych przez link w podanej lokalizacji docelowej. Aby zapewnić obsługę tej funkcji, Sterownik musi śledzić każdy pakiet przesyłany w każdym interfejsie. Następujące elementy członkowskie NX_IP_DRIVER są używane dla żądania liczby pakietów przesyłania linku.

| NX_IP_DRIVER składową     | Znaczenie                                                                                                     |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_TX_COUNT                                                                                        |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                      |
| nx_ip_driver_return_ptr | Wskaźnik do lokalizacji docelowej, w której ma zostać umieszczona liczba pakietów transmisji                                               |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                           |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie jest w stanie uzyskać liczby transmisji, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |


> [!NOTE]
> *To żądanie nie jest używane wewnętrznie przez NetX, więc jego implementacja jest opcjonalna.*

### <a name="get-allocation-errors"></a>Pobierz błędy alokacji  

To żądanie jest nawiązywane z poziomu usługi ***nx_ip_driver_direct_command*** . Sterownik przechowuje liczbę błędów alokacji puli pakietów linku w podanym miejscu docelowym. Do żądania liczby błędów alokacji łącza są używane następujące elementy członkowskie NX_IP_DRIVER.

| **NX_IP_DRIVER składową** | **Znaczenie** |
| --- | ---|
| nx_ip_driver_command | NX_LINK_GET_ALLOC_ERRORS |
| nx_ip_driver_ptr | Wskaźnik do wystąpienia adresu IP |

| NX_IP_DRIVER składową     | Znaczenie                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_return_ptr | Wskaźnik do miejsca docelowego, w którym ma zostać umieszczona liczba błędów alokacji                                                 |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                              |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może pobrać błędów alokacji, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |


*To żądanie nie jest używane wewnętrznie przez NetX, więc jego implementacja jest opcjonalna.*

### <a name="driver-deferred-processing"></a>Przetwarzanie Odroczone sterownika  

To żądanie jest nawiązywane z wątku pomocnika IP w odpowiedzi na sterownik wywołujący procedurę _ ***nx_ip_driver_deferred_processing*** z procedury przesyłania lub odbierania funkcji ISR. Dzięki temu sterownik może opóźniać odbieranie i przesyłanie pakietów do wątku pomocnika IP, a tym samym zmniejszyć ilość do przetworzenia w procesie ISR. Pole *nx_interface_additional_link_info* w strukturze NX_INTERFACE wskazywane przez *nx_ip_driver_interface* może być używane przez sterownik do przechowywania informacji o odroczonym zdarzeniu przetwarzania z kontekstu wątku pomocnika IP. Następujące NX_IP_DRIVER elementy członkowskie są używane dla zdarzenia odroczonego przetwarzania.

**NX_IP_DRIVER**

| członek                 | Znaczenie                           |
|------------------------|-----------------------------------|
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING       |
| nx_ip_driver_ptr       | Wskaźnik do wystąpienia adresu IP            |
| nx_ip_driver_interface | Wskaźnik do wystąpienia interfejsu |


### <a name="user-commands"></a>Polecenia użytkownika  

To żądanie jest nawiązywane z poziomu usługi ***nx_ip_driver_direct_command*** . Sterownik przetwarza polecenia użytkownika specyficzne dla aplikacji. Następujące NX_IP_DRIVER elementy członkowskie są używane dla żądania polecenia użytkownika.

| NX_IP_DRIVER składową     | Znaczenie                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_USER_COMMAND                                                                                           |
| nx_ip_driver_ptr        | Wskaźnik do wystąpienia adresu IP                                                                                         |
| nx_ip_driver_return_ptr | Zdefiniowane przez użytkownika                                                                                                   |
| nx_ip_driver_interface  | Wskaźnik do wystąpienia interfejsu                                                                              |
| nx_ip_driver_status     | Stan ukończenia. Jeśli sterownik nie może wykonać poleceń użytkownika, spowoduje to zwrócenie stanu błędu o wartości innej niż zero. |


*To żądanie nie jest używane wewnętrznie przez NetX, więc jego implementacja jest opcjonalna.*

### <a name="unimplemented-commands"></a>Niezaimplementowane polecenia  

Polecenia niezaimplementowane przez sterownik sieciowy muszą mieć pole stanu powrotu ustawione na NX_UNHANDLED_COMMAND.

## <a name="driver-output"></a>Dane wyjściowe sterownika  

Wszystkie poprzednio wymienione żądania przesyłania pakietów wymagają funkcji wyjściowej zaimplementowanej w sterowniku. Określona logika przesyłania jest specyficzna dla sprzętu, ale zazwyczaj polega na sprawdzaniu wydajności sprzętu w celu natychmiastowego wysłania pakietu. Jeśli to możliwe, ładunek pakietu (i dodatkowe ładunki w łańcuchu pakietów) są ładowane do jednego lub większej liczby buforów transmisji sprzętowej i zostanie zainicjowana operacja wysyłania. Jeśli pakiet nie mieści się w dostępnych buforach transmisji, pakiet powinien znajdować się w kolejce i być przesyłany, gdy bufory transmisji staną się dostępne.

Zalecana Kolejka przesyłania jest pojedynczo połączoną listą ze wskaźnikami głównymi i końcowymi. Nowe pakiety są dodawane na końcu kolejki, utrzymując najstarszy pakiet na pierwszym planie. Pole *nx_packet_queue_next* jest używane jako następny link do pakietu w kolejce. Sterownik definiuje wskaźniki główne i końcowe kolejki transmisji.

*Ponieważ do tej kolejki uzyskuje się dostęp z części wątku i przerwania w sterowniku, ochrona przerywania musi zostać umieszczona wokół manipulacji kolejek.*

Większość implementacji sprzętu fizycznego generuje przerwanie podczas przesyłania pakietów.
Gdy sterownik odbiera takie przerwanie, zazwyczaj zwalnia zasoby skojarzone z pakietem, które właśnie są przesyłane. W przypadku gdy logika przesyłania odczytuje dane bezpośrednio z bufora NX_PACKET, Sterownik powinien używać usługi ***nx_packet_transmit_release*** , aby zwolnić pakiet skojarzony z zakończonym przerwaniem przesyłania zwrotnego z powrotem do dostępnej puli pakietów. Następnie sterownik analizuje kolejkę transmisji dla dodatkowych pakietów oczekujących na wysłanie. Ponieważ wiele pakietów przesyłania umieszczonych w kolejce, które pasują do buforów przesyłania sprzętowego, są dekolejkowane i ładowane do buforów. Następuje to po zainicjowaniu innej operacji wysyłania.

Gdy tylko dane w NX_PACKET zostały przeniesione do przekaźnika FIFO (lub w przypadku, gdy sterownik obsługuje operację zerocopy, dane w NX_PACKET zostały przesłane), Sterownik musi przenieść nx_packet_prepend_ptr na początek nagłówka IP przed wywołaniem ***nx_packet_transmit_release.*** Pamiętaj, aby odpowiednio dostosować pole *nx_packet_length* . Jeśli ramka IP składa się z wielu pakietów, należy zwolnić tylko nagłówek łańcucha pakietów.

## <a name="driver-input"></a>Dane wejściowe sterownika  

Po odebraniu otrzymanego przerwania pakietów sterownik sieciowy pobiera pakiet z buforów odbioru fizycznego sprzętowego i tworzy prawidłowy pakiet NetX. Kompilowanie prawidłowego pakietu NetX obejmuje skonfigurowanie odpowiedniej długości pola i łączenie wielu pakietów, jeśli rozmiar pakietu przychodzącego jest większy niż pojedynczy ładunek pakietu. Po poprawnym skompilowaniu prepend_ptr jest przenoszona po utworzeniu nagłówka warstwy fizycznej, a pakiet odbioru jest wysyłany do NetX.

NetX zakłada, że nagłówki IP i ARP są wyrównane na granicy ULONG. W związku z tym należy upewnić się, że to wyrównanie jest stosowane w sterowniku NetX. W środowiskach Ethernet w tym celu należy uruchomić nagłówek Ethernet dwa bajty od początku pakietu. Gdy *nx_packet_prepend_ptr* jest przenoszona poza nagłówek Ethernet, bazowy adres IP lub nagłówek ARP jest wyrównany do 4byte.

W programie NetX dostępne są kilka funkcji odbioru pakietów. Jeśli odebrany pakiet jest pakietem ARP, wywoływana jest _* **nx_arp_packet_deferred_receive**_ . Jeśli otrzymany pakiet jest pakietem RARP, wywoływana jest wartość _ _*_nx_rarp_packet_deferred_receive_*_ . Istnieje kilka opcji obsługi przychodzących pakietów IP. W celu uzyskania najszybszej obsługi pakietów IP jest wywoływana _*_nx_ip_packet_receive_*_ . Takie podejście ma najmniejszy koszt, ale wymaga więcej przetwarzania w ramach procedury obsługi przerwania odbierania usługi (ISR) sterownika. W przypadku minimalnej liczby procesów ISR należy wywołać *_nx_ip_packet_deferred_receive_**.

Po poprawnym skompilowaniu nowego pakietu odbioru fizyczne Bufory odbioru sprzętu są skonfigurowane w celu uzyskania większej ilości danych. Może to wymagać przydzielenia pakietów NetX i umieszczenia adresu ładunku w buforze odbioru sprzętowego lub po prostu w przypadku zmiany ustawienia w buforze odbioru sprzętowego. Aby zminimalizować możliwości przepełnienia, ważne jest, aby Bufory odbioru sprzętu były dostępne bufory najszybciej, jak to możliwe po odebraniu pakietu.

*Początkowe Bufory odbioru są skonfigurowane podczas inicjowania sterownika.*

### <a name="deferred-receive-packet-handling"></a>Odroczona obsługa odbieranych pakietów  

Sterownik może opóźnić odbieranie przetwarzania pakietów do wątku pomocnika IP NetX. W przypadku niektórych aplikacji może być konieczne zminimalizowanie przetwarzania w trybie ISR oraz pakietów porzuconych. Aby można było użyć odroczonego obsługi pakietów, biblioteka NetX musi najpierw becompiled z funkcją ***NX_DRIVER_DEFERRED_PROCESSING** _. Spowoduje to dodanie odroczonej logiki pakietów do wątku pomocnika IP NetX. Następnie w przypadku odebrania pakietu danych sterownik musi wywołać __nx_ip_packet_deferred_receive ():*

```C
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```

Odroczona funkcja Receive umieszcza pakiet odbierający reprezentowany przez *packet_ptr* na FIFO (lista połączona) i powiadamia wątek pomocnika IP. Po wykonaniu tego pomocnika IP powtarza wywołania funkcji obsługi odroczonej, aby przetwarzać każdy odroczony pakiet. Przetwarzanie odroczonego programu obsługi zazwyczaj obejmuje usunięcie nagłówka warstwy fizycznej pakietu (zazwyczaj Ethernet) i wysłanie go do jednej z tych funkcji odbierania NetX:  

***_nx_ip_packet_deferred_receive***  
***_nx_arp_packet_deferred_receive***  
***_nx_rarp_packet_deferred_receive*** 


## <a name="example-ram-ethernet-network-driver"></a>Przykład sterownika sieci Ethernet w pamięci RAM  

System demonstracyjny NetX jest dostarczany z małym sterownikiem sieciowym opartym na pamięci RAM, zdefiniowanym w pliku ***nx_ram_network_driver. c.***
Ten sterownik zakłada, że wystąpienia protokołu IP są wszystkie w tej samej sieci i po prostu przypisuje wirtualne adresy sprzętowe (adresy MAC) do każdego wystąpienia urządzenia w miarę ich tworzenia. Ten plik zawiera dobry przykład podstawowej struktury NetX fizycznych urządzeń sieciowych. Użytkownicy mogą opracowywać własne sterowniki sieciowe przy użyciu platformy sterowników przedstawionej w tym przykładzie.

Funkcja wejścia sterownika sieciowego jest ***_nx_ram_network_driver, _,** która jest przenoszona do wywołania tworzenia wystąpienia IP. Funkcje wprowadzania dla dodatkowych interfejsów sieciowych mogą być przesyłane do usługi _*_nx_ip_interface_attach_*_ . Po uruchomieniu wystąpienia adresu IP funkcja wprowadzania sterowników jest wywoływana w celu zainicjowania i włączenia urządzenia (zobacz przypadek _ *NX_LINK_INITIALIZE** i **NX_LINK_ENABLE**). Po wydaniu polecenia **NX_LINK_ENABLE** urządzenie powinno być gotowe do przesyłania i odbierania pakietów. 

Wystąpienie IP przesyła pakiety sieciowe za pomocą jednego z następujących poleceń:

| ***NX_LINK_PACKET_SEND***    | Pakiet IP jest przesyłany,                             |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_ARP_SEND***       | Trwa przesyłanie żądania ARP lub pakietu odpowiedzi ARP,    |
| ***NX_LINK_ARP_RARP_SEND*** | Trwa przesyłanie żądania odwrotnego protokołu ARP lub pakietu odpowiedzi. |

W przypadku przetwarzania tych poleceń sterownik sieciowy musi dołączać odpowiedni nagłówek ramki Ethernet, a następnie wysyłać go do podstawowego sprzętu do transmisji. W trakcie procesu transmisji sterownik sieciowy ma wyłączną własność obszaru bufora pakietu. W związku z tym po przesłaniu danych (lub po skopiowaniu danych do wewnętrznego buforu transferu sterownika) Sterownik sieciowy jest odpowiedzialny za zwolnienie buforu pakietów przez przeniesienie wskaźnika dołączania poza nagłówek Ethernet do nagłówka IP (i odpowiednio dostosować długość pakietu), a następnie przez wywołanie usługi ***nx_packet_transmit_release*** , aby zwolnić pakiet. Nie można zwolnić pakietu, gdy transmisja danych spowoduje przeciek pakietów.

Sterownik urządzenia sieciowego jest również odpowiedzialny za obsługę przychodzących pakietów danych. W przykładzie sterownika pamięci RAM otrzymany pakiet jest przetwarzany przez funkcję ***_nx_ram_network_driver_receive***.

Gdy urządzenie otrzyma ramkę Ethernet, sterownik jest odpowiedzialny za przechowywanie danych w

Struktura NX_PACKET. Należy pamiętać, że NetX zakłada, że nagłówek IP zaczyna się od 4-bajtowego wyrównanego adresu. Ze względu na to, że Długość nagłówka Ethernet wynosi 14 bajtów, Sterownik musi przechowywać początek nagłówka Ethernet w adresie wyrównanym 2-bajtowym w celu zagwarantowania, że nagłówek IP zaczyna się od 4-bajtowego wyrównanego adresu.