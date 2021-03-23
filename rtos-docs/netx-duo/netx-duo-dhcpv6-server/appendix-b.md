---
title: Dodatek B — kody stanu serwera DHCPv6 usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich kodów stanu serwera DHCPv6 NetX Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821961"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a><span data-ttu-id="b3487-103">Dodatek B — kody stanu serwera DHCPv6 usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b3487-103">Appendix B - Azure RTOS NetX Duo DHCPv6 server status codes</span></span>

| <span data-ttu-id="b3487-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b3487-104">Name</span></span>              | <span data-ttu-id="b3487-105">Kod</span><span class="sxs-lookup"><span data-stu-id="b3487-105">Code</span></span>            | <span data-ttu-id="b3487-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b3487-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="b3487-107">Powodzenie</span><span class="sxs-lookup"><span data-stu-id="b3487-107">Success</span></span> | <span data-ttu-id="b3487-108">0</span><span class="sxs-lookup"><span data-stu-id="b3487-108">0</span></span> | <span data-ttu-id="b3487-109">Powodzenie</span><span class="sxs-lookup"><span data-stu-id="b3487-109">Success</span></span> |
| <span data-ttu-id="b3487-110">Nieokreślony błąd</span><span class="sxs-lookup"><span data-stu-id="b3487-110">Unspecified Failure</span></span> | <span data-ttu-id="b3487-111">1</span><span class="sxs-lookup"><span data-stu-id="b3487-111">1</span></span> | <span data-ttu-id="b3487-112">Niepowodzenie, przyczyna nieokreślona; Ten kod stanu jest ustawiany przez serwer w celu wskazania ogólnego błędu podczas udzielania żądania klienta niezgodnego z innymi kodami</span><span class="sxs-lookup"><span data-stu-id="b3487-112">Failure, reason unspecified; this status code is set by the Server to indicate a general failure in granting the Client request not matching the other codes</span></span> |
| <span data-ttu-id="b3487-113">Brak dostępnego adresu</span><span class="sxs-lookup"><span data-stu-id="b3487-113">NoAddress Available</span></span> | <span data-ttu-id="b3487-114">2</span><span class="sxs-lookup"><span data-stu-id="b3487-114">2</span></span> | <span data-ttu-id="b3487-115">Serwer nie ma żadnych adresów dostępnych do przypisania do klienta</span><span class="sxs-lookup"><span data-stu-id="b3487-115">Server has no addresses available to assign to the Client</span></span> |
| <span data-ttu-id="b3487-116">NoBinding</span><span class="sxs-lookup"><span data-stu-id="b3487-116">NoBinding</span></span> | <span data-ttu-id="b3487-117">3</span><span class="sxs-lookup"><span data-stu-id="b3487-117">3</span></span> | <span data-ttu-id="b3487-118">Adres IA klienta (Binding) nie jest dostępny, np. żądany adres IP nie jest dostępny dla serwera do dzierżawy lub przypisany innemu klientowi.</span><span class="sxs-lookup"><span data-stu-id="b3487-118">Client IA address (binding) is not available e.g. the requested IP address is not available for the Server to lease or assigned to another Client.</span></span> |
| <span data-ttu-id="b3487-119">NotOnLink</span><span class="sxs-lookup"><span data-stu-id="b3487-119">NotOnLink</span></span> | <span data-ttu-id="b3487-120">4</span><span class="sxs-lookup"><span data-stu-id="b3487-120">4</span></span> | <span data-ttu-id="b3487-121">Prefiks adresu wskazuje, że adres IP nie jest adresem linku</span><span class="sxs-lookup"><span data-stu-id="b3487-121">The prefix for the address indicates the IP address is not an on link address</span></span> |
| <span data-ttu-id="b3487-122">UseMulticast</span><span class="sxs-lookup"><span data-stu-id="b3487-122">UseMulticast</span></span> | <span data-ttu-id="b3487-123">5</span><span class="sxs-lookup"><span data-stu-id="b3487-123">5</span></span> | <span data-ttu-id="b3487-124">Wysyłany przez serwer w odpowiedzi na odebranie komunikatu klienta przy użyciu adresu emisji pojedynczej serwera zamiast adresu multiemisji *All_DHCP_Relay_Agents_and_Servers*</span><span class="sxs-lookup"><span data-stu-id="b3487-124">Sent by a Server in response to receiving a Client message using the Server’s unicast address instead of the *All_DHCP_Relay_Agents_and_Servers* multicast address</span></span> |