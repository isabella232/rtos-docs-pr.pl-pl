---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX BSD
description: Otoka interfejsu API usługi Azure RTO NetX BSD Sockets obsługuje niektóre z podstawowych wywołań interfejsu API protokołu BSD Sockets z pewnymi ograniczeniami i używa elementów podstawowych NetX poniżej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821511"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX BSD

Otoka zgodności NetX BSD Sockets API obsługuje niektóre z podstawowych wywołań interfejsu API usługi BSD Sockets z pewnymi ograniczeniami i wykorzystuje elementy podstawowe NetX poniżej. Ta warstwa zgodności interfejsu API BSD Sockets powinna działać jako Szybka lub nieco szybsza niż typowe implementacje BSD, ponieważ ta otoka korzysta z wewnętrznych NetX podstawowych i pomija sprawdzanie podstawowych błędów NetX.

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>Źródło otoki zgodności interfejsu API usługi BSD Sockets

Kod źródłowy otoki BSD został zaprojektowany dla uproszczenia i składa się tylko z dwóch plików, *nx_bsd. h* i *nx_bsd. c*. Plik *nx_bsd. h* definiuje wszystkie niezbędne stałe OTOKI interfejsu API usługi BSD Sockets oraz prototypy podprocedur, podczas gdy *nx_bsd. c* zawiera rzeczywisty kod źródłowy zgodności interfejsu API usługi BSD Sockets. Te pliki źródłowe otoki BSD są wspólne dla wszystkich pakietów pomocy technicznej NetX.

Pakiet składa się z:

- **nx_bsd. c**: kod źródłowy otoki
- **nx_bsd. h**: główny plik nagłówkowy

Przykładowe programy demonstracyjne:

- **bsd_demo_tcp. c**: *Demonstracja przy użyciu jednego serwera i klienta TCP*
- **bsd_demo_udp. c**: *Demonstracja dwóch klientów UDP i serwera UDP*
