---
title: Dodatek D — Azure RTOS NetX BSD-Compatible Socket API
description: Dowiedz się więcej o interfejsie API BSD-Compatible Socket dla protokołu IPv4.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bd4a35c19cd794a5135f01abe5595456d39b5306ba25ce2966c3bb1aea14ea17
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790092"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a>Dodatek D — Azure RTOS NetX BSD-Compatible Socket API

## <a name="bsd-compatible-socket-api"></a>interfejs API BSD-Compatible Socket

Interfejs API BSD-Compatible Socket obsługuje podzbiór wywołań interfejsu API gniazd BSD (z pewnymi ograniczeniami), korzystając z Azure RTOS podstawowych NetX poniżej. Obsługiwane są protokoły IPv4 i adresowanie sieciowe. Ta BSD-Compatible API gniazd powinna działać tak szybko lub nieco szybciej niż typowe implementacje BSD, ponieważ ten interfejs API wykorzystuje wewnętrzne typy pierwotne NetX i pomija niepotrzebne sprawdzanie błędów NetX.

Opcje konfigurowalne umożliwiają aplikacji hosta definiowanie maksymalnej liczby gniazd, maksymalnego rozmiaru okna protokołu TCP i głębokości kolejki nasłuchiwać.

Ze względu na ograniczenia wydajności i architektury ten interfejs API BSD-Compatible Sockets nie obsługuje wszystkich wywołań gniazd BSD. Ponadto nie wszystkie opcje BSD są dostępne dla usług BSD, w szczególności następujące:

- Funkcja ***select** _ działa tylko z _fd_set readfds*, inne argumenty w tym wywołaniu, \* np. *writefds*, *z wyjątkiemfds* nie są obsługiwane.
- Argument *int flags* nie jest obsługiwany dla funkcji ***send** _, _*_recv,_*_ _*_sendto_*_ i _ *_recvfrom_**. Interfejs API BSD-Compatible Socket obsługuje tylko ograniczony zestaw wywołań gniazd BSD.

Kod źródłowy został zaprojektowany dla uproszczenia i składa się tylko z dwóch plików, ***nx_bsd.c** _ _*_i nx_bsd.h_*_. Instalacja wymaga dodania tych dwóch plików do projektu kompilacji (nie biblioteki NetX) i utworzenia aplikacji hosta, która będzie używać wywołań usługi BSD Socket. Plik _ *_nx_bsd.h_** również musi być uwzględniony w źródle aplikacji. Przykładowe pliki demonstracyjne są dołączone do dystrybucji, która jest bezpłatnie dostępna w programie NetX. Więcej szczegółów można znaleźć w pomocy dotyczącej BSD-Compatible Socket API **417** i plików Readme dołączonych do pakietu BSD-Compatible Socket API.

Interfejs API BSD-Compatible Sockets obsługuje następujące wywołania interfejsu API gniazd BSD:

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
