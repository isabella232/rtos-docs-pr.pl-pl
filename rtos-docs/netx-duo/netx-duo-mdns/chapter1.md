---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo mDNS/DNS-SD
description: Azure RTO NetX Duo mDNS/DNS-SD rozszerza tradycyjną usługę DNS.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821829"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo mDNS/DNS-SD

Usługa mDNS i system DNS-SD to protokoły zaprojektowane w celu rozszerzenia tradycyjnej usługi DNS. Usługa mDNS udostępnia nazwy hosta i wyszukiwania usług do węzłów w sieci lokalnej. Każdy węzeł korzysta z protokołu IPv4 lub IPv6 kanału multiemisji do ogłaszania usług, które oferuje do swoich sąsiadów, reaguje na zapytania od jego sąsiadów i wysyła zapytania dotyczące zachowania aplikacji. Zgodnie z projektem usługa mDNS działa w środowisku rozproszonym, dzięki czemu eliminuje scentralizowaną ochronę.

Usługa DNS-SD jest oparta na usłudze mDNS. Usługa DNS-SD umożliwia węzłom ogłaszanie usług udostępnianych w sieci lokalnej lub odnajdywania usług oferowanych przez inne węzły w sieci lokalnej. W całym dokumencie termin *mDNS* odnosi się do usług, które obejmują specyfikację MDNS i specyfikację DNS-SD.

## <a name="mdns-standard"></a>Standard mDNS

Implementacja usługi mDNS/SD NetX Duo jest zgodna z następującymi specyfikacjami RFC:

- RFC 6762: Specyfikacja mDNS
- RFC 6763: Specyfikacja DNS-SD