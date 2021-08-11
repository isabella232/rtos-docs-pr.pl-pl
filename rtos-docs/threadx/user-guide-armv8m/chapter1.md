---
title: Rozdział 1 — Wprowadzenie do Azure RTOS ThreadX dla ARMv8-M.
description: Ten rozdział jest punktem wyjścia do przeczytania informacji o Azure RTOS ThreadX dla ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f0d87ec562c7fcfa6af5d2240655ef526f6e0611d509fe60c745436371413d7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798252"
---
# <a name="chapter-1--overview"></a>Omówienie rozdziału 1

Architektura ARMv8-M wprowadza nowe funkcje zabezpieczeń, w tym TrustZone, które umożliwiają tagowanie pamięci jako bezpiecznej lub niezabezpieczonej. Zgodnie z wytycznymi arm, ThreadX (i aplikacja użytkownika) jest przeznaczony do uruchamiania w trybie niezabezpieczony. ThreadX (i aplikacja użytkownika) można również uruchamiać w trybie bezpiecznym. Do interfejsu z oprogramowaniem w trybie bezpiecznym niezbędne są nowe interfejsy API ThreadX. W tym dokumencie opisano te usługi ThreadX, które są specyficzne dla architektury ARMv8-M, w tym Cortex-M23, Cortex-M33, Cortex-M35P i Cortex-M55.
