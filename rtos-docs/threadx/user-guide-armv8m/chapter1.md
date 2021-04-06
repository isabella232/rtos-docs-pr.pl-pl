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
# <a name="chapter-1--overview"></a>Rozdział 1 — omówienie

W architekturze ARMv8-M wprowadzono nowe funkcje zabezpieczeń, w tym TrustZone, które umożliwiają określenie, że pamięć ma być oznaczona jako bezpieczna lub niezabezpieczona. Zgodnie z zaleceniami ARM ThreadX (i aplikacja użytkownika) została zaprojektowana tak, aby była uruchamiana w trybie niezabezpieczonym. ThreadX (i aplikacja użytkownika) można również uruchomić w trybie zabezpieczonym. Aby można było interfejsować za pomocą oprogramowania w trybie zabezpieczonym, niektóre nowe interfejsy API ThreadX są konieczne. W tym dokumencie opisano te usługi ThreadX, które są specyficzne dla architektury ARMv8-M, w tym Cortex-M23, Cortex-— M33, Cortex-M35P i Cortex-M55.
