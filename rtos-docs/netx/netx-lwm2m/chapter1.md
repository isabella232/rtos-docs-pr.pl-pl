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
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a><span data-ttu-id="569ea-103">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="569ea-103">Chapter 1 - Introduction to Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="569ea-104">Protokół Azure RTO NetX LWM2M zawiera implementację klienta programu Lightweight Machine for Machine Protocol Standard.</span><span class="sxs-lookup"><span data-stu-id="569ea-104">The Azure RTOS NetX LWM2M Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span>

## <a name="netx-lwm2m-requirements"></a><span data-ttu-id="569ea-105">Wymagania dotyczące NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="569ea-105">NetX LWM2M Requirements</span></span>

<span data-ttu-id="569ea-106">Aby zapewnić prawidłowe działanie, Biblioteka wykonawcza NetX LWM2M wymaga, aby wystąpienie adresu IP NetX zostało już utworzone.</span><span class="sxs-lookup"><span data-stu-id="569ea-106">In order to function properly, the NetX LWM2M run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="569ea-107">Pakiet LWM2M NetX nie ma żadnych dalszych wymagań.</span><span class="sxs-lookup"><span data-stu-id="569ea-107">The NetX LWM2M package has no further requirements.</span></span>

## <a name="netx-lwm2m-rfcs"></a><span data-ttu-id="569ea-108">NetX LWM2M — specyfikacje RFC</span><span class="sxs-lookup"><span data-stu-id="569ea-108">NetX LWM2M RFCs</span></span>

<span data-ttu-id="569ea-109">NetX LWM2M jest zgodny z identyfikatorem OMA-TS-LightweightM2M-V1_0 -20170208-A i poniższymi specyfikacjami RFC związanymi z ograniczonym protokołem aplikacji (CoAP):</span><span class="sxs-lookup"><span data-stu-id="569ea-109">NetX LWM2M is compliant with OMA-TS-LightweightM2M-V1_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP):</span></span>

- <span data-ttu-id="569ea-110">**RFC 7252**: protokół ograniczonych aplikacji (CoAP)</span><span class="sxs-lookup"><span data-stu-id="569ea-110">**RFC 7252**: The Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="569ea-111">**RFC 7641**: obserwowanie zasobów w protokole ograniczonych aplikacji (CoAP)</span><span class="sxs-lookup"><span data-stu-id="569ea-111">**RFC 7641**: Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="569ea-112">**RFC 6690**: format łącza z ograniczeniami (CoRE) RESTful</span><span class="sxs-lookup"><span data-stu-id="569ea-112">**RFC 6690**: Constrained RESTful Environments (CoRE) Link Format</span></span>