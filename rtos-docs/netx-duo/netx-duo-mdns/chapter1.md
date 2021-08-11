---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo mDNS/DNS-SD
description: Azure RTOS NetX Duo mDNS/DNS-SD rozszerza tradycyjną usługę DNS.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7cde8e81809dcc74ee5d0b09d8e7a8d2ae96850cd84250a5bf003fdd5763925a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796450"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo mDNS/DNS-SD

MDNS i DNS-SD to protokoły przeznaczone do rozszerzenia tradycyjnej usługi DNS. Usługa mDNS udostępnia nazwę hosta i wyszukiwania usług w węzłach w sieci lokalnej. Każdy węzeł używa kanału multiemisji IPv4 lub IPv6 do ogłaszania usług oferowanych sąsiadom, odpowiada na zapytania od sąsiadów i wysyła zapytania dotyczące zachowania aplikacji. Zgodnie z projektem usługa mDNS działa w środowisku rozproszonym, co eliminuje scentralizowaną obsługę.

Usługa DNS-SD jest zbudowana na podstawie nazw mDNS. System DNS-SD umożliwia węzłom ogłaszanie usług, które zapewniają w sieci lokalnej, lub odnajdywanie usług oferowanych przez inne węzły w sieci lokalnej. W całym dokumencie termin *mDNS* odnosi się do usług, które obejmują zarówno specyfikację mDNS, jak i specyfikację DNS-SD.

## <a name="mdns-standard"></a>mDNS Standard

Implementacja netX Duo mDNS/DNS-SD jest zgodna z następującymi RFC:

- RFC 6762: specyfikacja mDNS
- RFC 6763: specyfikacja DNS-SD