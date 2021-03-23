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
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a><span data-ttu-id="ab753-103">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo mDNS/DNS-SD</span><span class="sxs-lookup"><span data-stu-id="ab753-103">Chapter 1 - Introduction to Azure RTOS NetX Duo mDNS/DNS-SD</span></span>

<span data-ttu-id="ab753-104">Usługa mDNS i system DNS-SD to protokoły zaprojektowane w celu rozszerzenia tradycyjnej usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="ab753-104">The mDNS and DNS-SD are protocols designed to augment the traditional DNS service.</span></span> <span data-ttu-id="ab753-105">Usługa mDNS udostępnia nazwy hosta i wyszukiwania usług do węzłów w sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="ab753-105">mDNS provides host name and service lookup to the nodes on the local network.</span></span> <span data-ttu-id="ab753-106">Każdy węzeł korzysta z protokołu IPv4 lub IPv6 kanału multiemisji do ogłaszania usług, które oferuje do swoich sąsiadów, reaguje na zapytania od jego sąsiadów i wysyła zapytania dotyczące zachowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ab753-106">Each node uses IPv4 or IPv6 multicast channel to announce services it offers to its neighbors, responds to queries from its neighbors, and sends queries on behave of its applications.</span></span> <span data-ttu-id="ab753-107">Zgodnie z projektem usługa mDNS działa w środowisku rozproszonym, dzięki czemu eliminuje scentralizowaną ochronę.</span><span class="sxs-lookup"><span data-stu-id="ab753-107">By design, mDNS operates in a distributed environment, thus eliminates a centralized serve.</span></span>

<span data-ttu-id="ab753-108">Usługa DNS-SD jest oparta na usłudze mDNS.</span><span class="sxs-lookup"><span data-stu-id="ab753-108">DNS-SD is built on top of mDNS.</span></span> <span data-ttu-id="ab753-109">Usługa DNS-SD umożliwia węzłom ogłaszanie usług udostępnianych w sieci lokalnej lub odnajdywania usług oferowanych przez inne węzły w sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="ab753-109">DNS-SD allows nodes to announce services they provide to the local network or to discover services offered by other nodes on the local network.</span></span> <span data-ttu-id="ab753-110">W całym dokumencie termin *mDNS* odnosi się do usług, które obejmują specyfikację MDNS i specyfikację DNS-SD.</span><span class="sxs-lookup"><span data-stu-id="ab753-110">Throughout the document, the term *mDNS* refers to the services that cover both the mDNS specification and the DNS-SD specification.</span></span>

## <a name="mdns-standard"></a><span data-ttu-id="ab753-111">Standard mDNS</span><span class="sxs-lookup"><span data-stu-id="ab753-111">mDNS Standard</span></span>

<span data-ttu-id="ab753-112">Implementacja usługi mDNS/SD NetX Duo jest zgodna z następującymi specyfikacjami RFC:</span><span class="sxs-lookup"><span data-stu-id="ab753-112">NetX Duo mDNS/DNS-SD implementation conforms to the following RFCs:</span></span>

- <span data-ttu-id="ab753-113">RFC 6762: Specyfikacja mDNS</span><span class="sxs-lookup"><span data-stu-id="ab753-113">RFC 6762: mDNS Specification</span></span>
- <span data-ttu-id="ab753-114">RFC 6763: Specyfikacja DNS-SD</span><span class="sxs-lookup"><span data-stu-id="ab753-114">RFC 6763: DNS-SD Specification</span></span>