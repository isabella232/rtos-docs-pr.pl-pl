---
title: Dodatek D — interfejs API usługi Azure RTO NetX BSD-Compatible Socket
description: Dowiedz się więcej o interfejsie API usługi BSD-Compatible Socket dla protokołu IPv4.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9062e27d8f447ac8d36e7a09afee5ac14f86f8c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822801"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a>Dodatek D — interfejs API usługi Azure RTO NetX BSD-Compatible Socket

## <a name="bsd-compatible-socket-api"></a>Interfejs API usługi BSD-Compatible Socket

Interfejs API BSD-Compatible Socket obsługuje podzestaw wywołań interfejsu API usługi BSD Sockets (z pewnymi ograniczeniami) przez wykorzystanie RTO NetX podstawowych. Obsługiwane są Protokoły IPv4 i adresy sieciowe. Ta warstwa interfejsu API usługi BSD-Compatible Sockets powinna działać jako Szybka lub nieco szybsza niż typowe implementacje BSD, ponieważ ten interfejs API wykorzystuje wewnętrzne NetXe podstawowe i pomija niepotrzebne sprawdzanie błędów NetX.

Konfigurowalne opcje umożliwiają aplikacji hosta zdefiniowanie maksymalnej liczby gniazd, maksymalnego rozmiaru okna TCP i głębokości kolejki nasłuchiwania.

Ze względu na ograniczenia wydajności i architektury ten interfejs API usługi BSD-Compatible Sockets nie obsługuje wszystkich wywołań usługi BSD Sockets. Ponadto nie wszystkie opcje BSD dla usług BSD są dostępne w następujący sposób:

- Funkcja ***SELECT** _ działa tylko z _fd_set \* readfds *, inne argumenty w tym wywołaniu, np. *writefds*, *exceptfds* nie są obsługiwane.
- Argument *flag int* nie jest obsługiwany dla funkcji ***send** _, _*_recv_*_, _*_SendTo_*_ i _ *_recvfrom_**. Interfejs API gniazda BSD-Compatible obsługuje tylko ograniczony zestaw wywołań BSD Sockets.

Kod źródłowy jest przeznaczony dla uproszczenia i składa się tylko z dwóch plików, ***nx_bsd. c** _ i _*_nx_bsd. h_*_. Instalacja wymaga dodania tych dwóch plików do projektu kompilacji (nie biblioteki NetX) i utworzenia aplikacji hosta, która będzie używać wywołań usługi gniazda BSD. Plik _ *_nx_bsd. h_** musi być również dołączony do źródła aplikacji. Przykładowe pliki demonstracyjne są dołączone do dystrybucji, która jest dostępna bezpłatnie z NetX. Dalsze szczegóły są dostępne w pliku pomocy BSD-Compatible gniazda API **417** i pliki Readme dołączone do pakietu BSD-Compatible interfejsu API gniazda.

Interfejs API BSD-Compatible Sockets obsługuje następujące wywołania interfejsu API usługi BSD Sockets:

```C
*INT bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool,
    CHAR *bsd_memory_not_used);*

*INT getpeername( INT sockID, struct sockaddr *remoteAddress, INT *addressLength);*

*INT getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);*

*INT recvfrom(INT sockID, CHAR *buffer, INT buffersize,
    INT flags,struct sockaddr *fromAddr, INT *fromAddrLen);*

*INT recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);*

*INT sendto(INT sockID, CHAR *msg, INT msgLength, INT flags,
    struct sockaddr *destAddr, INT destAddrLen);*

*INT send(INT sockID, const CHAR *msg, INT msgLength, INT flags);*

 *INT accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);*

*INT listen(INT sockID, INT backlog);*

*INT bind (INT sockID, struct sockaddr *localAddress, INT addressLength);*

*INT connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);*

*INT socket( INT protocolFamily, INT type, INT protocol);*

*INT soc_close ( INT sockID);*

*INT select(INT nfds, fd_set *readfds, fd_set *writefds,
    fd_set *exceptfds, struct timeval *timeout);*

*VOID FD_SET(INT fd, fd_set *fdset);*

*VOID FD_CLR(INT fd, fd_set *fdset);*

*INT FD_ISSET(INT fd, fd_set *fdset);*

*VOID FD_ZERO(fd_set *fdset);*

```
