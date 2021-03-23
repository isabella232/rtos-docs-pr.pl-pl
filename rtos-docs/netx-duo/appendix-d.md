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
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a><span data-ttu-id="87f1c-103">Dodatek D-Azure RTO NetX Duo BSD-Compatible interfejs API gniazda</span><span class="sxs-lookup"><span data-stu-id="87f1c-103">Appendix D - Azure RTOS NetX Duo BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="87f1c-104">Interfejs API usługi BSD-Compatible Socket</span><span class="sxs-lookup"><span data-stu-id="87f1c-104">BSD-Compatible Socket API</span></span> 
<span data-ttu-id="87f1c-105">Interfejs API usługi BSD-Compatible Socket obsługuje podzestaw wywołań interfejsu API usługi BSD Sockets (z pewnymi ograniczeniami) przez wykorzystanie podstawowych elementów NetX Duo &reg; poniżej.</span><span class="sxs-lookup"><span data-stu-id="87f1c-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing NetX Duo&reg; primitives underneath.</span></span> <span data-ttu-id="87f1c-106">Obsługiwane są zarówno protokoły IPv6, jak i IPv4 oraz adresy sieciowe.</span><span class="sxs-lookup"><span data-stu-id="87f1c-106">Both IPv6 and IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="87f1c-107">Ta warstwa interfejsu API usługi BSD-Compatible Sockets powinna działać jako Szybka lub nieco szybsza niż typowe implementacje BSD, ponieważ ten interfejs API wykorzystuje wewnętrzne elementy podstawowe NetX Duo i pomija niepotrzebne NetX sprawdzanie błędów.</span><span class="sxs-lookup"><span data-stu-id="87f1c-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX Duo primitives and bypasses unnecessary NetX error checking.</span></span>  

<span data-ttu-id="87f1c-108">Konfigurowalne opcje umożliwiają aplikacji hosta zdefiniowanie maksymalnej liczby gniazd, maksymalnego rozmiaru okna TCP i głębokości kolejki nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="87f1c-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="87f1c-109">Ze względu na ograniczenia wydajności i architektury ten interfejs API usługi BSD-Compatible Sockets nie obsługuje wszystkich wywołań usługi BSD Sockets.</span><span class="sxs-lookup"><span data-stu-id="87f1c-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="87f1c-110">Ponadto nie wszystkie opcje BSD dla usług BSD są dostępne w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="87f1c-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

  - <span data-ttu-id="87f1c-111">\***wybranie** metody _ Call działa tylko z FD_SET \_ readfds, inne argumenty w tym wywołaniu, np. writefds, exceptfds nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="87f1c-111">\***select** _ call works with only fd_set \_readfds, other arguments in this call e.g., writefds, exceptfds are not supported.</span></span>
  - <span data-ttu-id="87f1c-112">Argument "int flags" nie jest obsługiwany dla wywołań ***send** _, _*_recv_*_, _*_SendTo_\*_ i _ \*_recvfrom_\*\*.</span><span class="sxs-lookup"><span data-stu-id="87f1c-112">The "int flags" argument is not supported for ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** calls.</span></span> 
  - <span data-ttu-id="87f1c-113">Interfejs API gniazda BSD-Compatible obsługuje tylko ograniczony zestaw wywołań BSD Sockets.</span><span class="sxs-lookup"><span data-stu-id="87f1c-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="87f1c-114">Kod źródłowy jest przeznaczony dla uproszczenia i składa się tylko z dwóch plików, ***nxd_bsd. c** _ i _*_nxd_bsd. h_\*_.</span><span class="sxs-lookup"><span data-stu-id="87f1c-114">The source code is designed for simplicity and is comprised of only two files, ***nxd_bsd.c** _ and _*_nxd_bsd.h_\*_.</span></span> <span data-ttu-id="87f1c-115">Instalacja wymaga dodania tych dwóch plików do projektu kompilacji (nie biblioteki NetX) i utworzenia aplikacji hosta, która będzie używać wywołań usługi gniazda BSD.</span><span class="sxs-lookup"><span data-stu-id="87f1c-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="87f1c-116">Plik _ *_nxd_bsd. h_*\* musi być również dołączony do źródła aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87f1c-116">The _ *_nxd_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="87f1c-117">Przykładowe pliki demonstracyjne dla aplikacji opartych na protokole IPv4 i IPv6 są dołączone do dystrybucji, która jest dostępna bezpłatnie z NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="87f1c-117">Sample demo files for both IPv4 and IPv6  based applications are included with the distribution which is freely available with NetX Duo.</span></span> <span data-ttu-id="87f1c-118">Dalsze szczegółowe informacje są dostępne w plikach pomocy i Readme z pakietem interfejsu API gniazda BSDCompatible.</span><span class="sxs-lookup"><span data-stu-id="87f1c-118">Further details are available in the help and Readme files bundled with the BSDCompatible Socket API package.</span></span>

<span data-ttu-id="87f1c-119">Interfejs API BSD-Compatible Sockets obsługuje następujące wywołania interfejsu API usługi BSD Sockets:</span><span class="sxs-lookup"><span data-stu-id="87f1c-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

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