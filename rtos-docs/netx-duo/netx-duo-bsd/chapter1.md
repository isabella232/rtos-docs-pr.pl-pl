---
title: Rozdział 1 — wprowadzenie do Azure RTOS NetX Duo BSD
description: Otoka compagcy interfejsu API gniazd BSD obsługuje niektóre z podstawowych wywołań interfejsu API gniazd BSD, z pewnymi ograniczeniami i wykorzystuje Azure RTOS podstawowych NetX Duo poniżej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: caf8d5374204bc553ac903f4720d3db402d9a10da5c26caa0fa67c4b5d340049
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790500"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>Rozdział 1 — wprowadzenie do Azure RTOS NetX Duo BSD

Otoka compagcy interfejsu API gniazd BSD obsługuje niektóre z podstawowych wywołań interfejsu API gniazd BSD, z pewnymi ograniczeniami i wykorzystuje Azure RTOS podstawowych NetX Duo poniżej.

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>Źródło otoki interfejsu API gniazd BSD

Kod źródłowy otoki został zaprojektowany dla uproszczenia i składa się z dwóch plików: *nxd_bsd.h* *i nxd_bsd.c.* Plik *nxd_bsd.h* definiuje wszystkie niezbędne stałe i prototypy otoki interfejsu API gniazd BSD, natomiast plik *nxd_bsd.c* zawiera rzeczywisty kod źródłowy zgodności interfejsu API gniazd BSD. Te pliki źródłowe otoki są wspólne dla wszystkich pakietów obsługi netX Duo.

Pakiet składa się z:

- **nxd_bsd.c:** Kod źródłowy otoki
- **nxd_bsd.h:** Główny plik nagłówkowy

Przykładowe programy demonstracyjne:

- **bsd_demo_udp.c:** pokaz *z dwoma równorzędami UDP (tylko protokół IPv4)*
- **bsd_demo_tcp.c:** pokaz *z jednym serwerem TCP i klientem*
- **bsd_demo_raw.c:** pokaz *z dwoma nieprzetworzonych elementów równorzędnych*