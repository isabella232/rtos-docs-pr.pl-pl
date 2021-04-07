---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO USBX Stack
description: USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji. W tym rozdziale wprowadzono USBX, opisując jego zalety i aplikację.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8b1e08130d4531fd82629378761cd5b1752f0a07
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550290"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="ef5aa-104">Rozdział 1 — wprowadzenie do usługi Azure RTO USBX Stack</span><span class="sxs-lookup"><span data-stu-id="ef5aa-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="ef5aa-105">USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="ef5aa-106">W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści</span><span class="sxs-lookup"><span data-stu-id="ef5aa-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="ef5aa-107">Funkcje USBX</span><span class="sxs-lookup"><span data-stu-id="ef5aa-107">USBX features</span></span>

<span data-ttu-id="ef5aa-108">USBX obsługuje trzy istniejące specyfikacje USB: 1,1, 2,0 i OTG.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="ef5aa-109">Jest ona przeznaczona do skalowalności i będzie obsługiwać proste topologie USB z tylko jednym podłączonym urządzeniem, a także złożonymi topologiami z wieloma urządzeniami i kaskadowymi centrami.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="ef5aa-110">USBX obsługuje wszystkie typy transferu danych protokołów USB: Control, bulk, interrupt i Isochronous.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="ef5aa-111">USBX obsługuje zarówno po stronie hosta, jak i po stronie urządzenia.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="ef5aa-112">Każda strona składa się z trzech warstw.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="ef5aa-113">Warstwa kontrolera</span><span class="sxs-lookup"><span data-stu-id="ef5aa-113">Controller layer</span></span>
- <span data-ttu-id="ef5aa-114">Warstwa stosu</span><span class="sxs-lookup"><span data-stu-id="ef5aa-114">Stack layer</span></span>
- <span data-ttu-id="ef5aa-115">Warstwa klasy</span><span class="sxs-lookup"><span data-stu-id="ef5aa-115">Class layer</span></span>

<span data-ttu-id="ef5aa-116">Relacje między warstwami USB są następujące:</span><span class="sxs-lookup"><span data-stu-id="ef5aa-116">The relationship between the USB layers is as follows:</span></span>

![Warstwy USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="ef5aa-118">Najważniejsze informacje o produkcie</span><span class="sxs-lookup"><span data-stu-id="ef5aa-118">Product Highlights</span></span>

- <span data-ttu-id="ef5aa-119">Ukończ obsługę procesora ThreadX</span><span class="sxs-lookup"><span data-stu-id="ef5aa-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="ef5aa-120">Bez opłat</span><span class="sxs-lookup"><span data-stu-id="ef5aa-120">No royalties</span></span>
- <span data-ttu-id="ef5aa-121">Pełny kod źródłowy ANSI C</span><span class="sxs-lookup"><span data-stu-id="ef5aa-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="ef5aa-122">Wydajność w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="ef5aa-122">Real-time performance</span></span>
- <span data-ttu-id="ef5aa-123">Reagowanie na pomoc techniczną</span><span class="sxs-lookup"><span data-stu-id="ef5aa-123">Responsive technical support</span></span>
- <span data-ttu-id="ef5aa-124">Obsługa wielu klas</span><span class="sxs-lookup"><span data-stu-id="ef5aa-124">Multiple class support</span></span>
- <span data-ttu-id="ef5aa-125">Wiele wystąpień klasy</span><span class="sxs-lookup"><span data-stu-id="ef5aa-125">Multiple class instances</span></span>
- <span data-ttu-id="ef5aa-126">Integracja klas z ThreadX, FileX i NetX</span><span class="sxs-lookup"><span data-stu-id="ef5aa-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="ef5aa-127">Obsługa urządzeń USB z wieloma konfiguracjami</span><span class="sxs-lookup"><span data-stu-id="ef5aa-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="ef5aa-128">Obsługa urządzeń złożonych USB</span><span class="sxs-lookup"><span data-stu-id="ef5aa-128">Support for USB composite devices</span></span>
- <span data-ttu-id="ef5aa-129">Obsługa zarządzania mocą USB</span><span class="sxs-lookup"><span data-stu-id="ef5aa-129">Support for USB power management</span></span>
- <span data-ttu-id="ef5aa-130">Obsługa OTG USB</span><span class="sxs-lookup"><span data-stu-id="ef5aa-130">Support for USB OTG</span></span>
- <span data-ttu-id="ef5aa-131">Eksportuj zdarzenia śledzenia dla TraceX</span><span class="sxs-lookup"><span data-stu-id="ef5aa-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="ef5aa-132">Zaawansowane usługi USBX</span><span class="sxs-lookup"><span data-stu-id="ef5aa-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="ef5aa-133">Pełna obsługa platformy USB</span><span class="sxs-lookup"><span data-stu-id="ef5aa-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="ef5aa-134">USBX może obsługiwać najbardziej wymagające urządzenia USB, w tym wiele konfiguracji, wiele interfejsów i wiele ustawień alternatywnych.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="ef5aa-135">Łatwe w użyciu interfejsy API</span><span class="sxs-lookup"><span data-stu-id="ef5aa-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="ef5aa-136">USBX zapewnia najlepszy, głęboko osadzony stos USB w sposób, który jest łatwy do zrozumienia i użycia.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="ef5aa-137">Interfejs API USBX zapewnia intuicyjną i spójność usług.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="ef5aa-138">Korzystając z dostarczonych interfejsów API klasy USBX, aplikacja użytkownika nie musi zrozumieć złożoności protokołów USB.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
