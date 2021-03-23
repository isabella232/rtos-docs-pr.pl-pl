---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo LWM2M Client
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO NetX Duo Lightweight Machine for Machine Protocol Client.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 12f13c154668b3cadfae0924e59b55631dc27424
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821859"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a>Rozdział 1 wprowadzenie do klienta LWM2M

Protokół Azure RTO NetX Duo LWM2M Client implementuje część klienta uproszczonego komputera z protokołem Machine Protocol Standard. (LWM2M 1.0-20170208A)

## <a name="netx-lwm2m-client-requirements"></a>Wymagania dotyczące klienta NetX LWM2M

Aby zapewnić prawidłowe działanie, Biblioteka wykonawcza klienta LWM2M wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Pakiet klienta NetX LWM2M nie ma żadnych dalszych wymagań.

## <a name="netx-lwm2m-client-rfcs"></a>NetX LWM2M — specyfikacje RFC klienta

Klient LWM2M jest zgodny z identyfikatorem OMA-TS-LightweightM2M-V1 \_ 0-20170208-a i poniższymi specyfikacjami RFC związanymi z protokołem ograniczonym aplikacji (CoAP).

* RFC 7252 protokół ograniczonych aplikacji (CoAP)

* Zgodne z dokumentem RFC 7641 obserwowanie zasobów w protokole ograniczonych aplikacji (CoAP)

* Format linku RESTful środowiska (rdzeń) z ograniczeniami RFC 6690

Aby uzyskać więcej informacji, zobacz [OMA-TS-LightweightM2M-V1 \_ 0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).