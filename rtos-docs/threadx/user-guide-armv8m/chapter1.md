---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO ThreadX dla ARMv8-M.
description: Ten rozdział jest punktem początkowym do czytania dodatku Azure RTO ThreadX dla ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 486466f41e64adb9e32ebbd21a22629221ffa9c1
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377594"
---
# <a name="chapter-1--overview"></a><span data-ttu-id="6d879-103">Rozdział 1 — omówienie</span><span class="sxs-lookup"><span data-stu-id="6d879-103">Chapter 1  Overview</span></span>

<span data-ttu-id="6d879-104">W architekturze ARMv8-M wprowadzono nowe funkcje zabezpieczeń, w tym TrustZone, które umożliwiają określenie, że pamięć ma być oznaczona jako bezpieczna lub niezabezpieczona.</span><span class="sxs-lookup"><span data-stu-id="6d879-104">The ARMv8-M architecture introduces new security features, including TrustZone, which allows memory to be tagged as secure or non-secure.</span></span> <span data-ttu-id="6d879-105">Zgodnie z zaleceniami ARM ThreadX (i aplikacja użytkownika) została zaprojektowana tak, aby była uruchamiana w trybie niezabezpieczonym.</span><span class="sxs-lookup"><span data-stu-id="6d879-105">Following ARM's guidelines, ThreadX (and the user application) is designed to be run in non-secure mode.</span></span> <span data-ttu-id="6d879-106">ThreadX (i aplikacja użytkownika) można również uruchomić w trybie zabezpieczonym.</span><span class="sxs-lookup"><span data-stu-id="6d879-106">ThreadX (and the user application) can also be run in secure mode.</span></span> <span data-ttu-id="6d879-107">Aby można było interfejsować za pomocą oprogramowania w trybie zabezpieczonym, niektóre nowe interfejsy API ThreadX są konieczne.</span><span class="sxs-lookup"><span data-stu-id="6d879-107">In order to interface with secure mode software, some new ThreadX APIs are necessary.</span></span> <span data-ttu-id="6d879-108">W tym dokumencie opisano te usługi ThreadX, które są specyficzne dla architektury ARMv8-M, w tym Cortex-M23, Cortex-— M33, Cortex-M35P i Cortex-M55.</span><span class="sxs-lookup"><span data-stu-id="6d879-108">This document describes these ThreadX services that are specific to the ARMv8-M architecture, including the Cortex-M23, Cortex-M33, Cortex-M35P, and Cortex-M55.</span></span>
