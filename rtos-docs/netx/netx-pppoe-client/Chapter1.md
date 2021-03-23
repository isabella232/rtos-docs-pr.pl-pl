---
title: Rozdział 1 — wprowadzenie do klienta usługi Azure RTO NetX PPPoE
description: Ten rozdział zawiera szczegóły modułu PPPoE usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bbf1e064bb38754bd67b279a0fd60d46d3d6d557
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822548"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a><span data-ttu-id="35272-103">Rozdział 1 — wprowadzenie do klienta usługi Azure RTO NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="35272-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Client</span></span>

<span data-ttu-id="35272-104">Protokół PPP przez sieć Ethernet (PPPoE) umożliwia hostom łączenie się z serwerem PPP za pośrednictwem sieci Ethernet zamiast tradycyjnego opartego na znakach komunikacji linii szeregowej.</span><span class="sxs-lookup"><span data-stu-id="35272-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span>  <span data-ttu-id="35272-105">Szczegółowe informacje techniczne dotyczące protokołu PPPoE zostały opisane w dokumencie RFC 2516: Metoda przesyłania PPP przez Ethernet (PPPoE).</span><span class="sxs-lookup"><span data-stu-id="35272-105">The technical details of PPPoE are described in RFC 2516:  A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="35272-106">Ten dokument koncentruje się na szczegółach dotyczących modułu PPPoE usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="35272-106">This document focuses on the details of  Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="35272-107">Aby zapewnić połączenie typu punkt-punkt za pośrednictwem sieci Ethernet, każda sesja PPP musi nauczyć się adresu Ethernet zdalnego elementu równorzędnego, a także ustanowić unikatowy identyfikator sesji.</span><span class="sxs-lookup"><span data-stu-id="35272-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="35272-108">Zgodnie ze standardem RFC 2516, PPPoE obejmuje dwa etapy: etap odnajdywania i etap sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="35272-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="35272-109">Gdy host (klient) chce uruchomić sesję PPP, musi najpierw przeprowadzić odnajdywanie, aby znaleźć serwer PPPoE.</span><span class="sxs-lookup"><span data-stu-id="35272-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="35272-110">Ten krok umożliwia również serwerowi i klientowi zidentyfikowanie adresów MAC sieci Ethernet i SESSION_ID, które będą używane w pozostałej części sesji protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="35272-110">This step also allows the server and the client to identify each other’s Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="35272-111">Ramka Ethernet jest następująca:</span><span class="sxs-lookup"><span data-stu-id="35272-111">An Ethernet frame is as follows:</span></span>

![Ramka Ethernet](media/ethernet-frame.png)

<span data-ttu-id="35272-113">Ładunek Ethernet dla protokołu PPPoE jest następujący:</span><span class="sxs-lookup"><span data-stu-id="35272-113">The Ethernet payload for PPPoE is as follows:</span></span>

![Ładunek sieci Ethernet](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="35272-115">Etap odnajdywania PPPoE</span><span class="sxs-lookup"><span data-stu-id="35272-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="35272-116">Etap odnajdywania PPPoE umożliwia klientom wybranie serwera ze wszystkich dostępnych serwerów w sieci, efektywnie w celu utworzenia sesji przed wymianą ramek PPP.</span><span class="sxs-lookup"><span data-stu-id="35272-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span>  <span data-ttu-id="35272-117">Na końcu etapu odnajdywania zarówno klient, jak i serwer zgadzają się na unikatowy identyfikator sesji, a obie strony muszą znać adres MAC elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="35272-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer’s MAC address.</span></span>

| <span data-ttu-id="35272-118">Komunikat odnajdowania</span><span class="sxs-lookup"><span data-stu-id="35272-118">Discovery Message</span></span> | <span data-ttu-id="35272-119">Kod</span><span class="sxs-lookup"><span data-stu-id="35272-119">Code</span></span> | <span data-ttu-id="35272-120">Kierunek</span><span class="sxs-lookup"><span data-stu-id="35272-120">Direction</span></span> |
| ----------------- | ---- | --------- |
| <span data-ttu-id="35272-121">Inicjowanie odnajdywania aktywnego protokołu PPPoE (PADI)</span><span class="sxs-lookup"><span data-stu-id="35272-121">PPPoE Active Discovery Initiation (PADI)</span></span> | <span data-ttu-id="35272-122">0x09</span><span class="sxs-lookup"><span data-stu-id="35272-122">0x09</span></span> | <span data-ttu-id="35272-123">Z klienta do emisji</span><span class="sxs-lookup"><span data-stu-id="35272-123">From Client to broadcast</span></span> |
| <span data-ttu-id="35272-124">Oferta aktywnego odnajdowania PPPoE (PADO)</span><span class="sxs-lookup"><span data-stu-id="35272-124">PPPoE Active Discovery Offer (PADO)</span></span> | <span data-ttu-id="35272-125">0x07</span><span class="sxs-lookup"><span data-stu-id="35272-125">0x07</span></span> | <span data-ttu-id="35272-126">Z serwera do klienta</span><span class="sxs-lookup"><span data-stu-id="35272-126">From Server to Client</span></span> |
| <span data-ttu-id="35272-127">Aktywne żądanie odnajdywania PPPoE (PADR)</span><span class="sxs-lookup"><span data-stu-id="35272-127">PPPoE Active Discovery Request (PADR)</span></span> | <span data-ttu-id="35272-128">0x19</span><span class="sxs-lookup"><span data-stu-id="35272-128">0x19</span></span> | <span data-ttu-id="35272-129">Od klienta do serwera</span><span class="sxs-lookup"><span data-stu-id="35272-129">From Client to Server</span></span> |
| <span data-ttu-id="35272-130">Sesja odnajdywania aktywnego protokołu PPPOE — potwierdzenie (KONSOLe)</span><span class="sxs-lookup"><span data-stu-id="35272-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="35272-131">0x65</span><span class="sxs-lookup"><span data-stu-id="35272-131">0x65</span></span> | <span data-ttu-id="35272-132">Z serwera do klienta</span><span class="sxs-lookup"><span data-stu-id="35272-132">From Server to Client</span></span> |
| <span data-ttu-id="35272-133">Zakończenie aktywnego odnajdowania PPPoE (PADT)</span><span class="sxs-lookup"><span data-stu-id="35272-133">PPPoE Active Discovery Terminate (PADT)</span></span> | <span data-ttu-id="35272-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="35272-134">0xa7</span></span> | <span data-ttu-id="35272-135">Można inicjować z poziomu serwera lub klienta</span><span class="sxs-lookup"><span data-stu-id="35272-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="35272-136">Wszystkie ramki sieci Ethernet odnajdowania mają ustawioną wartość 0x8863 dla pola ETHER_TYPE.</span><span class="sxs-lookup"><span data-stu-id="35272-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="35272-137">Komunikat sesji PPPoE</span><span class="sxs-lookup"><span data-stu-id="35272-137">PPPoE Session Message</span></span>

<span data-ttu-id="35272-138">Po utworzeniu sesji przez klienta i serwer ramki PPP mogą być transferowane jako komunikaty sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="35272-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span>  <span data-ttu-id="35272-139">W trakcie sesji SESSION_ID nie może ulec zmianie i musi być wartością przypisywaną przez serwer na etapie odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="35272-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="35272-140">Wszystkie ramki sieci Ethernet sesji PPPoE mają ustawione ETHER_TYPE wartość 0x8864.</span><span class="sxs-lookup"><span data-stu-id="35272-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>
