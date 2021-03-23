---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo BSD
description: Otoka interfejsu API zgodności gniazda BSD obsługuje niektóre podstawowe wywołania interfejsu API usługi BSD Socket, z pewnymi ograniczeniami i korzysta z podstawowych podstaw platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822063"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo BSD

Otoka interfejsu API zgodności gniazda BSD obsługuje niektóre podstawowe wywołania interfejsu API usługi BSD Socket, z pewnymi ograniczeniami i korzysta z podstawowych podstaw platformy Azure RTO NetX Duo.

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>Źródło otoki zgodności interfejsu API usługi BSD Socket

Kod źródłowy otoki został zaprojektowany dla uproszczenia i składa się z dwóch plików, czyli *nxd_bsd. h* i *nxd_bsd. c*. Plik *nxd_bsd. h* definiuje wszystkie niezbędne stałe OTOKI interfejsu API usługi BSD Socket oraz prototypy podprocedur, podczas gdy *nxd_bsd. c* zawiera rzeczywisty kod źródłowy zgodności interfejsu API usługi BSD Socket. Te pliki źródłowe otoki są wspólne dla wszystkich pakietów obsługi NetX Duo.

Pakiet składa się z:

- **nxd_bsd. c**: kod źródłowy otoki
- **nxd_bsd. h**: główny plik nagłówkowy

Przykładowe programy demonstracyjne:

- **bsd_demo_udp. c**: *Demonstracja z dwoma elementami równorzędnymi UDP (tylko IPv4)*
- **bsd_demo_tcp. c**: *Demonstracja przy użyciu jednego serwera i klienta TCP*
- **bsd_demo_raw. c**: *Demonstracja z dwoma nieprzetworzonymi elementami równorzędnymi*