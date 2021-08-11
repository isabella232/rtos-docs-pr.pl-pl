---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo Telnet
description: Program Azure RTOS NetX Duo Telnet to protokół przeznaczony do przesyłania poleceń i odpowiedzi między dwoma węzłami w Internecie.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50a2c4d8726863f4e609debadd9ddf2455cfd540219a476970756d3d250ec562
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799034"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo Telnet

Program Azure RTOS NetX Duo Telnet to protokół przeznaczony do przesyłania poleceń i odpowiedzi między dwoma węzłami w Internecie. Telnet to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu. W związku z tym Telnet jest wysoce niezawodnym protokołem transferu. Telnet jest również jednym z najczęściej używanych protokołów aplikacji.

## <a name="telnet-requirements"></a>Wymagania telnetu

Aby zapewnić prawidłowe działanie, pakiet NetX Duo Telnet wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto protokół TCP musi być włączony w tym samym wystąpieniu adresu IP. Część klienta Telnet pakietu NetX Duo Telnet nie ma dodatkowych wymagań.

Część serwera Telnet pakietu NetX Duo Telnet ma jedno dodatkowe wymaganie. Wymaga ona pełnego dostępu do dobrze *znanego portu 23* protokołu TCP do obsługi wszystkich żądań Telnet klienta.

## <a name="telnet-constraints"></a>Ograniczenia Telnet 

Protokół NetX Duo Telnet implementuje standard Telnet. Jednak interpretacja i odpowiedź poleceń Telnet, wskazywana przez bajt o wartości 255, jest odpowiedzialna za aplikację. Różne polecenia Telnet i parametry poleceń są zdefiniowane w *plikach nxd_telnet_client.h i nxd_telnet_server.h.*

## <a name="telnet-communication"></a>Komunikacja Telnet

Jak wspomniano wcześniej, serwer Telnet używa dobrze znanego portu *TCP 23 do* pola Żądania klienta. Klienci Telnet mogą używać dowolnego dostępnego portu TCP.

## <a name="telnet-authentication"></a>Uwierzytelnianie Telnet

Uwierzytelnianie Telnet jest odpowiedzialne za funkcję wywołania zwrotnego serwera Telnet aplikacji. Wywołanie zwrotne "nowego połączenia" serwera Telnet aplikacji zwykle monituje klienta o nazwę i/lub hasło. Klient będzie wtedy odpowiedzialny za podanie informacji. Serwer będzie następnie przetwarzał informacje w wywołaniu zwrotym "odbierania danych". W tym miejscu kod serwera aplikacji musi uwierzytelnić informacje i zdecydować, czy są one prawidłowe.

## <a name="telnet-new-connection-callback"></a>Wywołanie zwrotne nowego połączenia Telnet

Serwer NetX Duo Telnet wywołuje funkcję wywołania zwrotnego określoną przez aplikację za każdym razem, gdy zostanie odebrane nowe żądanie klienta Telnet. Aplikacja określa funkcję wywołania zwrotnego podczas tworzenia serwera Telnet za ***pośrednictwem nx_telnet_server_create*** funkcji. Typowe akcje wywołania zwrotnego "nowego połączenia" obejmują wysłanie baneru lub monitu do klienta. Może to obejmować monit o informacje logowania.

### <a name="prototype"></a>Prototype

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do wywołującego serwera Telnet.
- **logical_connection:** wewnętrzne połączenie logiczne serwera Telnet. Może to być używane przez aplikację jako indeks buforów i/lub struktur danych specyficznych dla każdego połączenia klienta. Jej wartość waha się od 0 do NX_TELNET_MAX_CLIENTS-1.

## <a name="telnet-receive-data-callback"></a>Wywołanie zwrotne odbierania danych Telnet

Serwer NetX Duo Telnet wywołuje funkcję wywołania zwrotnego określoną przez aplikację za każdym razem, gdy odbierane są nowe dane klienta Telnet. Aplikacja określa funkcję wywołania zwrotnego podczas tworzenia serwera Telnet za ***pośrednictwem nx_telnet_server_create*** funkcji. Typowe akcje wywołania zwrotnego "nowego połączenia" obejmują przekazywanie danych z powrotem i/lub analizowanie danych i dostarczanie danych w wyniku interpretacji polecenia od klienta.

Należy pamiętać, że ta procedura wywołania zwrotnego musi również zwolnić dostarczony pakiet.

### <a name="prototype"></a>Prototype

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do wywołującego serwera Telnet.
- **logical_connection:** wewnętrzne połączenie logiczne serwera Telnet. Może to być używane przez aplikację jako indeks buforów i/lub struktur danych specyficznych dla każdego połączenia klienta. Jej wartość waha się od 0 do NX_TELNET_MAX_CLIENTS-1.
- **packet_ptr:** wskaźnik do pakietu zawierającego dane z klienta.

## <a name="telnet-end-connection-callback"></a>Wywołanie zwrotne połączenia końcowego Telnet

Serwer NetX Duo Telnet wywołuje funkcję wywołania zwrotnego określoną przez aplikację za każdym razem, gdy klient Telnet zakończy połączenie. Aplikacja określa funkcję wywołania zwrotnego podczas tworzenia serwera Telnet za ***pośrednictwem nx_telnet_server_create*** funkcji. Typowe akcje wywołania zwrotnego "połączenia końcowego" obejmują czyszczenie wszystkich struktur danych specyficznych dla klienta skojarzonych z połączeniem logicznym.

### <a name="prototype"></a>Prototype
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik do wywołującego serwera Telnet.
- **logical_connection** Wewnętrzne połączenie logiczne dla serwera Telnet. Może to być używane przez aplikację jako indeks buforów i/lub struktur danych specyficznych dla każdego połączenia klienta. Jej wartość waha się od 0 do NX_TELNET_MAX_CLIENTS-1.

## <a name="telnet-option-negotiation"></a>Negocjacja opcji Telnet

Serwer NetX Duo Telnet obsługuje ograniczony zestaw opcji Telnet, Echo i Suppress Go Ahead.

Aby włączyć tę funkcję, NX_TELNET_SERVER_OPTION_DISABLE nie można zdefiniować. Domyślnie nie jest zdefiniowana. Serwer Telnet tworzy pulę pakietów w usłudze *nx_telnet_server_create,* z której przydziela pakiety do wysyłania żądań opcji telnet do klienta programu . Zobacz "Opcje konfiguracji", aby uzyskać informacje na temat ustawiania ładunku pakietów (NX_TELNET_SERVER_PACKET_PAYLOAD) i rozmiaru puli pakietów (NX_TELNET_SERVER_PACKET_POOL_SIZE) dla tej puli pakietów. Spowoduje to usunięcie tej puli pakietów po *nx_telnet_server_delete* wywoływania usługi.

Po nawiązaniu połączenia z klientem Telnet program wyśle ten zestaw opcji telnet do klienta, jeśli nie odebrał żądań opcji od klienta:

- spowoduje echo
- nie powtarzaj
- will sga

Po otrzymaniu danych Telnet z klienta serwer Telnet sprawdza, czy pierwszy bajt jest kodem "IAC". Jeśli tak, będzie przetwarzać wszystkie opcje w pakiecie klienta. Opcje, których nie ma na powyższej liście, są ignorowane.

Domyślnie serwer Telnet tworzy własną wewnętrzną pulę pakietów, jeśli NX_TELNET_SERVER_OPTION_DISABLE nie jest zdefiniowany i musi przesyłać polecenia opcji Telnet. Pula pakietów serwera Telnet jest definiowana przez NX_TELNET_SERVER_PACKET_PAYLOAD i NX_TELNET_SERVER_PACKET_POOLSIZE. Jeśli jednak NX_TELNET_SERVER_USER_CREATE_PACKET_POOL, aplikacja musi utworzyć pulę pakietów serwera Telnet i ustawić ją jako pulę pakietów serwera Telnet, wywołując *_nx_telnet_server_packet_pool_set*. Aby uzyskać więcej informacji na temat tej funkcji, zobacz Rozdział 3 "Opis usług Telnet".

W przeciwieństwie do serwera NetX Duo Telnet wątek zadania Klienta Telnet NetX Duo nie wysyła automatycznie opcji odebranych z serwera Telnet ani nie odpowiada na nie. Musi to być zrobione przez aplikację kliencką Telnet.

## <a name="telnet-multi-thread-support"></a>Obsługa wielu wątków Telnet

Usługi klienta NetX Duo Telnet mogą być wywoływane z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta Telnet powinny być wykonywane kolejno z tego samego wątku.

## <a name="telnet-rfcs"></a>Telnet RFC

NetX Duo Telnet jest zgodny ze standardem RFC854 i powiązanymi RFC.
