---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO USBX Stack
description: W tym rozdziale przedstawiono stos urządzeń USBX, opisujący jego aplikacje i korzyści.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 383651bb0af42842329ad15b212e597f63a916aa
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377071"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="bcb3f-103">Rozdział 1 — wprowadzenie do usługi Azure RTO USBX Stack</span><span class="sxs-lookup"><span data-stu-id="bcb3f-103">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="bcb3f-104">USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-104">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="bcb3f-105">W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści</span><span class="sxs-lookup"><span data-stu-id="bcb3f-105">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="bcb3f-106">Funkcje USBX</span><span class="sxs-lookup"><span data-stu-id="bcb3f-106">USBX features</span></span>

<span data-ttu-id="bcb3f-107">USBX obsługuje trzy istniejące specyfikacje USB: 1,1, 2,0 i OTG.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-107">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="bcb3f-108">Jest ona przeznaczona do skalowalności i będzie obsługiwać proste topologie USB z tylko jednym podłączonym urządzeniem, a także złożonymi topologiami z wieloma urządzeniami i kaskadowymi centrami.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-108">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="bcb3f-109">USBX obsługuje wszystkie typy transferu danych protokołów USB: Control, bulk, interrupt i Isochronous.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-109">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="bcb3f-110">USBX obsługuje zarówno po stronie hosta, jak i po stronie urządzenia.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-110">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="bcb3f-111">Każda strona składa się z trzech warstw.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-111">Each side is composed of three layers.</span></span>

- <span data-ttu-id="bcb3f-112">Warstwa kontrolera</span><span class="sxs-lookup"><span data-stu-id="bcb3f-112">Controller layer</span></span>
- <span data-ttu-id="bcb3f-113">Warstwa stosu</span><span class="sxs-lookup"><span data-stu-id="bcb3f-113">Stack layer</span></span>
- <span data-ttu-id="bcb3f-114">Warstwa klasy</span><span class="sxs-lookup"><span data-stu-id="bcb3f-114">Class layer</span></span>

<span data-ttu-id="bcb3f-115">Relacje między warstwami USB są następujące:</span><span class="sxs-lookup"><span data-stu-id="bcb3f-115">The relationship between the USB layers is as follows:</span></span>

![Warstwy USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="bcb3f-117">Najważniejsze informacje o produkcie</span><span class="sxs-lookup"><span data-stu-id="bcb3f-117">Product Highlights</span></span>

- <span data-ttu-id="bcb3f-118">Ukończ obsługę procesora ThreadX</span><span class="sxs-lookup"><span data-stu-id="bcb3f-118">Complete ThreadX processor support</span></span>
- <span data-ttu-id="bcb3f-119">Bez opłat</span><span class="sxs-lookup"><span data-stu-id="bcb3f-119">No royalties</span></span>
- <span data-ttu-id="bcb3f-120">Pełny kod źródłowy ANSI C</span><span class="sxs-lookup"><span data-stu-id="bcb3f-120">Complete ANSI C source code</span></span>
- <span data-ttu-id="bcb3f-121">Wydajność w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="bcb3f-121">Real-time performance</span></span>
- <span data-ttu-id="bcb3f-122">Reagowanie na pomoc techniczną</span><span class="sxs-lookup"><span data-stu-id="bcb3f-122">Responsive technical support</span></span>
- <span data-ttu-id="bcb3f-123">Obsługa wielu klas</span><span class="sxs-lookup"><span data-stu-id="bcb3f-123">Multiple class support</span></span>
- <span data-ttu-id="bcb3f-124">Wiele wystąpień klasy</span><span class="sxs-lookup"><span data-stu-id="bcb3f-124">Multiple class instances</span></span>
- <span data-ttu-id="bcb3f-125">Integracja klas z ThreadX, FileX i NetX</span><span class="sxs-lookup"><span data-stu-id="bcb3f-125">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="bcb3f-126">Obsługa urządzeń USB z wieloma konfiguracjami</span><span class="sxs-lookup"><span data-stu-id="bcb3f-126">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="bcb3f-127">Obsługa urządzeń złożonych USB</span><span class="sxs-lookup"><span data-stu-id="bcb3f-127">Support for USB composite devices</span></span>
- <span data-ttu-id="bcb3f-128">Obsługa zarządzania mocą USB</span><span class="sxs-lookup"><span data-stu-id="bcb3f-128">Support for USB power management</span></span>
- <span data-ttu-id="bcb3f-129">Obsługa OTG USB</span><span class="sxs-lookup"><span data-stu-id="bcb3f-129">Support for USB OTG</span></span>
- <span data-ttu-id="bcb3f-130">Eksportuj zdarzenia śledzenia dla TraceX</span><span class="sxs-lookup"><span data-stu-id="bcb3f-130">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="bcb3f-131">Zaawansowane usługi USBX</span><span class="sxs-lookup"><span data-stu-id="bcb3f-131">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="bcb3f-132">Pełna obsługa platformy USB</span><span class="sxs-lookup"><span data-stu-id="bcb3f-132">Complete USB Device Framework Support</span></span>

<span data-ttu-id="bcb3f-133">USBX może obsługiwać najbardziej wymagające urządzenia USB, w tym wiele konfiguracji, wiele interfejsów i wiele ustawień alternatywnych.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-133">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="bcb3f-134">Łatwe w użyciu interfejsy API</span><span class="sxs-lookup"><span data-stu-id="bcb3f-134">Easy-To-Use APIs</span></span>

<span data-ttu-id="bcb3f-135">USBX zapewnia najlepszy, głęboko osadzony stos USB w sposób, który jest łatwy do zrozumienia i użycia.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-135">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="bcb3f-136">Interfejs API USBX zapewnia intuicyjną i spójność usług.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-136">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="bcb3f-137">Korzystając z dostarczonych interfejsów API klasy USBX, aplikacja użytkownika nie musi zrozumieć złożoności protokołów USB.</span><span class="sxs-lookup"><span data-stu-id="bcb3f-137">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
