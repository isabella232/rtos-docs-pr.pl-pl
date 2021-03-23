---
title: Dodatek D-Azure RTO NetX Duo BSD-Compatible interfejs API gniazda
description: Dowiedz się więcej o interfejsie API usługi BSD-Compatible Socket dla protokołów IPv4 i IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82439184d9facb6ddcc08ce81bc51182d7f34429
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822135"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>Dodatek D-Azure RTO NetX Duo BSD-Compatible interfejs API gniazda

## <a name="bsd-compatible-socket-api"></a>Interfejs API usługi BSD-Compatible Socket 
Interfejs API usługi BSD-Compatible Socket obsługuje podzestaw wywołań interfejsu API usługi BSD Sockets (z pewnymi ograniczeniami) przez wykorzystanie podstawowych elementów NetX Duo &reg; poniżej. Obsługiwane są zarówno protokoły IPv6, jak i IPv4 oraz adresy sieciowe. Ta warstwa interfejsu API usługi BSD-Compatible Sockets powinna działać jako Szybka lub nieco szybsza niż typowe implementacje BSD, ponieważ ten interfejs API wykorzystuje wewnętrzne elementy podstawowe NetX Duo i pomija niepotrzebne NetX sprawdzanie błędów.  

Konfigurowalne opcje umożliwiają aplikacji hosta zdefiniowanie maksymalnej liczby gniazd, maksymalnego rozmiaru okna TCP i głębokości kolejki nasłuchiwania.

Ze względu na ograniczenia wydajności i architektury ten interfejs API usługi BSD-Compatible Sockets nie obsługuje wszystkich wywołań usługi BSD Sockets. Ponadto nie wszystkie opcje BSD dla usług BSD są dostępne w następujący sposób:

  - ***wybranie** metody _ Call działa tylko z FD_SET \_ readfds, inne argumenty w tym wywołaniu, np. writefds, exceptfds nie są obsługiwane.
  - Argument "int flags" nie jest obsługiwany dla wywołań ***send** _, _*_recv_*_, _*_SendTo_*_ i _ *_recvfrom_**. 
  - Interfejs API gniazda BSD-Compatible obsługuje tylko ograniczony zestaw wywołań BSD Sockets.

Kod źródłowy jest przeznaczony dla uproszczenia i składa się tylko z dwóch plików, ***nxd_bsd. c** _ i _*_nxd_bsd. h_*_. Instalacja wymaga dodania tych dwóch plików do projektu kompilacji (nie biblioteki NetX) i utworzenia aplikacji hosta, która będzie używać wywołań usługi gniazda BSD. Plik _ *_nxd_bsd. h_** musi być również dołączony do źródła aplikacji. Przykładowe pliki demonstracyjne dla aplikacji opartych na protokole IPv4 i IPv6 są dołączone do dystrybucji, która jest dostępna bezpłatnie z NetX Duo. Dalsze szczegółowe informacje są dostępne w plikach pomocy i Readme z pakietem interfejsu API gniazda BSDCompatible.

Interfejs API BSD-Compatible Sockets obsługuje następujące wywołania interfejsu API usługi BSD Sockets:

```c
INT     bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool, CHAR
        *bsd_memory_not_used);
```
```c
INT     getpeername( INT sockID, struct sockaddr *remoteAddress, INT
        *addressLength);
```
```c
INT     getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);
```
```c
INT     recvfrom(INT sockID, CHAR *buffer, INT buffersize, INT flags,struct sockaddr
        *fromAddr, INT *fromAddrLen);
```
```c        
INT     recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);
```
```c
INT     sendto(INT sockID, CHAR *msg, INT msgLength, INT flags, struct sockaddr
        *destAddr, INT destAddrLen);
```
```c        
INT     send(INT sockID, const CHAR *msg, INT msgLength, INT flags);
```
```c
INT     accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);
```
```c
INT     listen(INT sockID, INT backlog);
```
```c
INT     bind (INT sockID, struct sockaddr *localAddress, INT addressLength);
```
```c
INT     connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);
```
```c
INT     socket( INT protocolFamily, INT type, INT protocol);
```
```c
INT     soc_close ( INT sockID);
```
```c
INT     select(INT nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct
        timeval *timeout);
```
```c
VOID    FD_SET(INT fd, fd_set *fdset);
```
```c
VOID    FD_CLR(INT fd, fd_set *fdset);
```
```c
INT     FD_ISSET(INT fd, fd_set *fdset);
```
```c
VOID    FD_ZERO(fd_set *fdset);
```