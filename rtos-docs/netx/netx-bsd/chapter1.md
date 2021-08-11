---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX BSD
description: Otoka kompecyjności interfejsu API BSD Azure RTOS NetX obsługuje niektóre podstawowe wywołania interfejsu API gniazd BSD z pewnymi ograniczeniami i wykorzystuje typy pierwotne NetX poniżej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b58283a38a25ffdd438d7853999f3b6e390f280a947aa45101d8df86447bf3dd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796724"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX BSD

Otoka kompecyjna interfejsu API netX BSD Sockets obsługuje niektóre podstawowe wywołania interfejsu API gniazd BSD z pewnymi ograniczeniami i wykorzystuje typy pierwotne NetX poniżej. Ta warstwa zgodności interfejsu API gniazd BSD powinna działać tak szybko lub nieco szybciej niż typowe implementacje BSD, ponieważ ta otoka wykorzystuje wewnętrzne typy pierwotne NetX i pomija podstawowe sprawdzanie błędów NetX.

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>Źródło otoki compagcy interfejsu API gniazd BSD

Kod źródłowy otoki BSD został zaprojektowany dla uproszczenia i składa się tylko z dwóch plików, *nx_bsd.h* *i nx_bsd.c.* Plik *nx_bsd.h* definiuje wszystkie niezbędne stałe i prototypy otoki interfejsu API BSD Sockets, natomiast plik *nx_bsd.c* zawiera rzeczywisty kod źródłowy zgodności interfejsu API gniazd BSD. Te pliki źródłowe otoki BSD są wspólne dla wszystkich pakietów obsługi NetX.

Pakiet składa się z:

- **nx_bsd.c:** Kod źródłowy otoki
- **nx_bsd.h:** Główny plik nagłówkowy

Przykładowe programy demonstracyjne:

- **bsd_demo_tcp.c:** pokaz *z jednym serwerem TCP i klientem*
- **bsd_demo_udp.c:** pokaz *z dwoma klientami UDP i serwerem UDP*
