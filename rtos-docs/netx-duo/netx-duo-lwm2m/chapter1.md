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
# <a name="chapter-1--introduction-to-lwm2m-client"></a><span data-ttu-id="131cf-103">Rozdział 1 wprowadzenie do klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="131cf-103">Chapter 1  Introduction to LWM2M Client</span></span>

<span data-ttu-id="131cf-104">Protokół Azure RTO NetX Duo LWM2M Client implementuje część klienta uproszczonego komputera z protokołem Machine Protocol Standard.</span><span class="sxs-lookup"><span data-stu-id="131cf-104">The Azure RTOS NetX Duo LWM2M Client Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span> <span data-ttu-id="131cf-105">(LWM2M 1.0-20170208A)</span><span class="sxs-lookup"><span data-stu-id="131cf-105">(LWM2M 1.0-20170208A)</span></span>

## <a name="netx-lwm2m-client-requirements"></a><span data-ttu-id="131cf-106">Wymagania dotyczące klienta NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="131cf-106">NetX LWM2M Client Requirements</span></span>

<span data-ttu-id="131cf-107">Aby zapewnić prawidłowe działanie, Biblioteka wykonawcza klienta LWM2M wymaga, aby wystąpienie adresu IP NetX zostało już utworzone.</span><span class="sxs-lookup"><span data-stu-id="131cf-107">In order to function properly, the LWM2M Client run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="131cf-108">Pakiet klienta NetX LWM2M nie ma żadnych dalszych wymagań.</span><span class="sxs-lookup"><span data-stu-id="131cf-108">The NetX LWM2M Client package has no further requirements.</span></span>

## <a name="netx-lwm2m-client-rfcs"></a><span data-ttu-id="131cf-109">NetX LWM2M — specyfikacje RFC klienta</span><span class="sxs-lookup"><span data-stu-id="131cf-109">NetX LWM2M Client RFCs</span></span>

<span data-ttu-id="131cf-110">Klient LWM2M jest zgodny z identyfikatorem OMA-TS-LightweightM2M-V1 \_ 0-20170208-a i poniższymi specyfikacjami RFC związanymi z protokołem ograniczonym aplikacji (CoAP).</span><span class="sxs-lookup"><span data-stu-id="131cf-110">LWM2M Client is compliant with OMA-TS-LightweightM2M-V1\_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP).</span></span>

* <span data-ttu-id="131cf-111">RFC 7252 protokół ograniczonych aplikacji (CoAP)</span><span class="sxs-lookup"><span data-stu-id="131cf-111">RFC 7252 The Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="131cf-112">Zgodne z dokumentem RFC 7641 obserwowanie zasobów w protokole ograniczonych aplikacji (CoAP)</span><span class="sxs-lookup"><span data-stu-id="131cf-112">RFC 7641 Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="131cf-113">Format linku RESTful środowiska (rdzeń) z ograniczeniami RFC 6690</span><span class="sxs-lookup"><span data-stu-id="131cf-113">RFC 6690 Constrained RESTful Environments (CoRE) Link Format</span></span>

<span data-ttu-id="131cf-114">Aby uzyskać więcej informacji, zobacz [OMA-TS-LightweightM2M-V1 \_ 0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span><span class="sxs-lookup"><span data-stu-id="131cf-114">For more information, please see [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span></span>