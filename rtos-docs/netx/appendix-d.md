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
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a><span data-ttu-id="58fa1-103">Dodatek D — interfejs API usługi Azure RTO NetX BSD-Compatible Socket</span><span class="sxs-lookup"><span data-stu-id="58fa1-103">Appendix D - Azure RTOS NetX BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="58fa1-104">Interfejs API usługi BSD-Compatible Socket</span><span class="sxs-lookup"><span data-stu-id="58fa1-104">BSD-Compatible Socket API</span></span>

<span data-ttu-id="58fa1-105">Interfejs API BSD-Compatible Socket obsługuje podzestaw wywołań interfejsu API usługi BSD Sockets (z pewnymi ograniczeniami) przez wykorzystanie RTO NetX podstawowych.</span><span class="sxs-lookup"><span data-stu-id="58fa1-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing Azure RTOS NetX primitives underneath.</span></span> <span data-ttu-id="58fa1-106">Obsługiwane są Protokoły IPv4 i adresy sieciowe.</span><span class="sxs-lookup"><span data-stu-id="58fa1-106">IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="58fa1-107">Ta warstwa interfejsu API usługi BSD-Compatible Sockets powinna działać jako Szybka lub nieco szybsza niż typowe implementacje BSD, ponieważ ten interfejs API wykorzystuje wewnętrzne NetXe podstawowe i pomija niepotrzebne sprawdzanie błędów NetX.</span><span class="sxs-lookup"><span data-stu-id="58fa1-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX primitives and bypasses unnecessary NetX error checking.</span></span>

<span data-ttu-id="58fa1-108">Konfigurowalne opcje umożliwiają aplikacji hosta zdefiniowanie maksymalnej liczby gniazd, maksymalnego rozmiaru okna TCP i głębokości kolejki nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="58fa1-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="58fa1-109">Ze względu na ograniczenia wydajności i architektury ten interfejs API usługi BSD-Compatible Sockets nie obsługuje wszystkich wywołań usługi BSD Sockets.</span><span class="sxs-lookup"><span data-stu-id="58fa1-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="58fa1-110">Ponadto nie wszystkie opcje BSD dla usług BSD są dostępne w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="58fa1-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

- <span data-ttu-id="58fa1-111">Funkcja \***SELECT** _ działa tylko z _fd_set \* readfds \*, inne argumenty w tym wywołaniu, np. *writefds*, *exceptfds* nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="58fa1-111">The ***select** _ function works with only _fd_set \*readfds*, other arguments in this call e.g., *writefds*, *exceptfds* are not supported.</span></span>
- <span data-ttu-id="58fa1-112">Argument *flag int* nie jest obsługiwany dla funkcji ***send** _, _*_recv_*_, _*_SendTo_\*_ i _ \*_recvfrom_\*\*.</span><span class="sxs-lookup"><span data-stu-id="58fa1-112">The *int flags* argument is not supported for the ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** functions.</span></span> <span data-ttu-id="58fa1-113">Interfejs API gniazda BSD-Compatible obsługuje tylko ograniczony zestaw wywołań BSD Sockets.</span><span class="sxs-lookup"><span data-stu-id="58fa1-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="58fa1-114">Kod źródłowy jest przeznaczony dla uproszczenia i składa się tylko z dwóch plików, ***nx_bsd. c** _ i _*_nx_bsd. h_\*_.</span><span class="sxs-lookup"><span data-stu-id="58fa1-114">The source code is designed for simplicity and is comprised of only two files,***nx_bsd.c** _ and _*_nx_bsd.h_\*_.</span></span> <span data-ttu-id="58fa1-115">Instalacja wymaga dodania tych dwóch plików do projektu kompilacji (nie biblioteki NetX) i utworzenia aplikacji hosta, która będzie używać wywołań usługi gniazda BSD.</span><span class="sxs-lookup"><span data-stu-id="58fa1-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="58fa1-116">Plik _ *_nx_bsd. h_*\* musi być również dołączony do źródła aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58fa1-116">The _ *_nx_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="58fa1-117">Przykładowe pliki demonstracyjne są dołączone do dystrybucji, która jest dostępna bezpłatnie z NetX.</span><span class="sxs-lookup"><span data-stu-id="58fa1-117">Sample demo files are included with the distribution which is freely available with NetX.</span></span> <span data-ttu-id="58fa1-118">Dalsze szczegóły są dostępne w pliku pomocy BSD-Compatible gniazda API **417** i pliki Readme dołączone do pakietu BSD-Compatible interfejsu API gniazda.</span><span class="sxs-lookup"><span data-stu-id="58fa1-118">Further details are available in the help BSD-Compatible Socket API **417** and Readme files bundled with the BSD-Compatible Socket API package.</span></span>

<span data-ttu-id="58fa1-119">Interfejs API BSD-Compatible Sockets obsługuje następujące wywołania interfejsu API usługi BSD Sockets:</span><span class="sxs-lookup"><span data-stu-id="58fa1-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

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
