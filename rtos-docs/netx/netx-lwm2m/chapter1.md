---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX LWM2M
description: Protokół Azure RTO NetX LWM2M zawiera implementację klienta programu Lightweight Machine for Machine Protocol Standard.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c29af430975266eed684bd1de38d9e5d7e2586a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822614"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX LWM2M

Protokół Azure RTO NetX LWM2M zawiera implementację klienta programu Lightweight Machine for Machine Protocol Standard.

## <a name="netx-lwm2m-requirements"></a>Wymagania dotyczące NetX LWM2M

Aby zapewnić prawidłowe działanie, Biblioteka wykonawcza NetX LWM2M wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Pakiet LWM2M NetX nie ma żadnych dalszych wymagań.

## <a name="netx-lwm2m-rfcs"></a>NetX LWM2M — specyfikacje RFC

NetX LWM2M jest zgodny z identyfikatorem OMA-TS-LightweightM2M-V1_0 -20170208-A i poniższymi specyfikacjami RFC związanymi z ograniczonym protokołem aplikacji (CoAP):

- **RFC 7252**: protokół ograniczonych aplikacji (CoAP)

- **RFC 7641**: obserwowanie zasobów w protokole ograniczonych aplikacji (CoAP)

- **RFC 6690**: format łącza z ograniczeniami (CoRE) RESTful