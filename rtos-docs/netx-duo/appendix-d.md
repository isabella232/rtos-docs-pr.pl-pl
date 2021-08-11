---
title: Dodatek D — Azure RTOS NetX Duo BSD-Compatible Socket API
description: Dowiedz się więcej o interfejsie API BSD-Compatible Socket dla protokołu IPv4 i IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd43c3efa18dd76f6eb996c84091024f48ad65aa5839958066161080dc02127e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789752"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>Dodatek D — Azure RTOS NetX Duo BSD-Compatible Socket API

## <a name="bsd-compatible-socket-api"></a>interfejs API BSD-Compatible Socket 
Interfejs API BSD-Compatible Socket obsługuje podzestaw wywołań interfejsu API gniazd BSD (z pewnymi ograniczeniami), korzystając z podstawowych elementów podstawowych NetX Duo &reg; poniżej. Obsługiwane są protokoły IPv6 i IPv4 oraz adresowanie sieciowe. Ta BSD-Compatible API gniazd powinna działać tak szybko lub nieco szybciej niż typowe implementacje BSD, ponieważ ten interfejs API wykorzystuje wewnętrzne typy pierwotne NetX Duo i pomija niepotrzebne sprawdzanie błędów NetX.  

Opcje konfigurowalne umożliwiają aplikacji hosta definiowanie maksymalnej liczby gniazd, maksymalnego rozmiaru okna protokołu TCP i głębokości kolejki nasłuchiwać.

Ze względu na ograniczenia wydajności i architektury ten interfejs API BSD-Compatible Sockets nie obsługuje wszystkich wywołań gniazd BSD. Ponadto nie wszystkie opcje BSD są dostępne dla usług BSD, w szczególności następujące:

  - ***Select** _ call działa tylko z fd_set readfds, inne argumenty w tym wywołaniu, \_ np. writefds, z wyjątkiemfds nie są obsługiwane.
  - Argument "int flags" nie jest obsługiwany w przypadku wywołań ***send** _, _*_recv,_*_ _*_sendto_*_ i _ *_recvfrom_**. 
  - Interfejs API BSD-Compatible Socket obsługuje tylko ograniczony zestaw wywołań gniazd BSD.

Kod źródłowy został zaprojektowany dla uproszczenia i składa się tylko z dwóch plików: ***nxd_bsd.c** _ _*_i nxd_bsd.h._*_ Instalacja wymaga dodania tych dwóch plików do projektu kompilacji (nie biblioteki NetX) i utworzenia aplikacji hosta, która będzie używać wywołań usługi BSD Socket. Plik _ *_nxd_bsd.h_** również musi być uwzględniony w źródle aplikacji. Przykładowe pliki demonstracyjne dla aplikacji opartych na protokole IPv4 i IPv6 są dołączone do dystrybucji, która jest dostępna bezpłatnie w netx duo. Dalsze szczegóły są dostępne w plikach pomocy i Readme dołączonych do pakietu interfejsu API BSDCompatible Socket API.

Interfejs API BSD-Compatible Sockets obsługuje następujące wywołania interfejsu API gniazd BSD:

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