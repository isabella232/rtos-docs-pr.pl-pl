---
title: Rozdział 1 — wprowadzenie do stosu hosta usługi Azure RTO USBX
description: USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji. W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ee49903e764e20316438be16b47d2d9208b1363
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824450"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a><span data-ttu-id="ac761-104">Rozdział 1 — wprowadzenie do stosu hosta usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="ac761-104">Chapter 1 - Introduction to Azure RTOS USBX Host Stack</span></span>

<span data-ttu-id="ac761-105">USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac761-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="ac761-106">W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści.</span><span class="sxs-lookup"><span data-stu-id="ac761-106">This chapter introduces USBX, describing its applications and benefits.</span></span>

## <a name="usbx-features"></a><span data-ttu-id="ac761-107">Funkcje USBX</span><span class="sxs-lookup"><span data-stu-id="ac761-107">USBX features</span></span>

<span data-ttu-id="ac761-108">USBX obsługiwać trzy istniejące specyfikacje USB: 1,1, 2,0 i OTG.</span><span class="sxs-lookup"><span data-stu-id="ac761-108">USBX support the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="ac761-109">Jest ona przeznaczona do skalowalności i będzie obsługiwać proste topologie USB z tylko jednym podłączonym urządzeniem, a także złożonymi topologiami z wieloma urządzeniami i kaskadowymi centrami.</span><span class="sxs-lookup"><span data-stu-id="ac761-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="ac761-110">USBX obsługuje wszystkie typy transferu danych protokołów USB: Control, bulk, interrupt i Isochronous.</span><span class="sxs-lookup"><span data-stu-id="ac761-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="ac761-111">USBX obsługuje zarówno po stronie hosta, jak i po stronie urządzenia.</span><span class="sxs-lookup"><span data-stu-id="ac761-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="ac761-112">Każda strona składa się z trzech warstw.</span><span class="sxs-lookup"><span data-stu-id="ac761-112">Each side is comprised of three layers.</span></span>

- <span data-ttu-id="ac761-113">Warstwa kontrolera</span><span class="sxs-lookup"><span data-stu-id="ac761-113">Controller layer</span></span>
- <span data-ttu-id="ac761-114">Warstwa stosu</span><span class="sxs-lookup"><span data-stu-id="ac761-114">Stack layer</span></span>
- <span data-ttu-id="ac761-115">Warstwa klasy</span><span class="sxs-lookup"><span data-stu-id="ac761-115">Class layer</span></span>

<span data-ttu-id="ac761-116">Relacje między warstwami USB są następujące.</span><span class="sxs-lookup"><span data-stu-id="ac761-116">The relationship between the USB layers is as follows.</span></span>

![Warstwy USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="ac761-118">Najważniejsze informacje o produkcie</span><span class="sxs-lookup"><span data-stu-id="ac761-118">Product Highlights</span></span>

- <span data-ttu-id="ac761-119">Ukończ obsługę procesora ThreadX</span><span class="sxs-lookup"><span data-stu-id="ac761-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="ac761-120">Bez opłat</span><span class="sxs-lookup"><span data-stu-id="ac761-120">No royalties</span></span>
- <span data-ttu-id="ac761-121">Pełny kod źródłowy ANSI C</span><span class="sxs-lookup"><span data-stu-id="ac761-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="ac761-122">Wydajność w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="ac761-122">Real-time performance</span></span>
- <span data-ttu-id="ac761-123">Reagowanie na pomoc techniczną</span><span class="sxs-lookup"><span data-stu-id="ac761-123">Responsive technical support</span></span>
- <span data-ttu-id="ac761-124">Obsługa wielu kontrolerów hosta</span><span class="sxs-lookup"><span data-stu-id="ac761-124">Multiple host controller support</span></span>
- <span data-ttu-id="ac761-125">Obsługa wielu klas</span><span class="sxs-lookup"><span data-stu-id="ac761-125">Multiple class support</span></span>
- <span data-ttu-id="ac761-126">Wiele wystąpień klasy</span><span class="sxs-lookup"><span data-stu-id="ac761-126">Multiple class instances</span></span>
- <span data-ttu-id="ac761-127">Integracja klas z ThreadX, FileX i NetX</span><span class="sxs-lookup"><span data-stu-id="ac761-127">Integration of classes with ThreadX, FileX and NetX</span></span>
- <span data-ttu-id="ac761-128">Obsługa urządzeń USB z wieloma konfiguracjami</span><span class="sxs-lookup"><span data-stu-id="ac761-128">Support for USB devices with multiple configuration</span></span>
- <span data-ttu-id="ac761-129">Obsługa urządzeń złożonych USB</span><span class="sxs-lookup"><span data-stu-id="ac761-129">Support for USB composite devices</span></span>
- <span data-ttu-id="ac761-130">Obsługa kaskadowych centrów</span><span class="sxs-lookup"><span data-stu-id="ac761-130">Support for cascading hubs</span></span>
- <span data-ttu-id="ac761-131">Obsługa zarządzania mocą USB</span><span class="sxs-lookup"><span data-stu-id="ac761-131">Support for USB power management</span></span>
- <span data-ttu-id="ac761-132">Obsługa OTG USB</span><span class="sxs-lookup"><span data-stu-id="ac761-132">Support for USB OTG</span></span>
- <span data-ttu-id="ac761-133">Eksportuj zdarzenia śledzenia dla TraceX</span><span class="sxs-lookup"><span data-stu-id="ac761-133">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="ac761-134">Zaawansowane usługi USBX</span><span class="sxs-lookup"><span data-stu-id="ac761-134">Powerful Services of USBX</span></span>

### <a name="multiple-host-controller-support"></a><span data-ttu-id="ac761-135">Obsługa wielu kontrolerów hosta</span><span class="sxs-lookup"><span data-stu-id="ac761-135">Multiple Host Controller Support</span></span>

<span data-ttu-id="ac761-136">USBX może obsługiwać wiele kontrolerów hosta USB uruchomionych współbieżnie.</span><span class="sxs-lookup"><span data-stu-id="ac761-136">USBX can support multiple USB host controllers running concurrently.</span></span> <span data-ttu-id="ac761-137">Ta funkcja umożliwia USBXom obsługę standardu USB 2,0 przy użyciu schematu zgodności z poprzednimi wersjami skojarzonego z większością kontrolerów USB 2,0 na rynku.</span><span class="sxs-lookup"><span data-stu-id="ac761-137">This feature allows USBX to support the USB 2.0 standard using the backward compatibility scheme associated with most USB 2.0 host controllers on the market today.</span></span>

### <a name="usb-software-scheduler"></a><span data-ttu-id="ac761-138">Harmonogram oprogramowania USB</span><span class="sxs-lookup"><span data-stu-id="ac761-138">USB Software Scheduler</span></span>

<span data-ttu-id="ac761-139">USBX zawiera harmonogram oprogramowania USB, który jest wymagany do obsługi kontrolerów USB, które nie mają przetwarzania na liście sprzętowej.</span><span class="sxs-lookup"><span data-stu-id="ac761-139">USBX contains a USB software scheduler necessary to support USB controllers that do not have hardware list processing.</span></span> <span data-ttu-id="ac761-140">Harmonogram oprogramowania USBX zorganizuje transfery USB z poprawną częstotliwością usługi i priorytetem, a następnie nakazuje kontrolerowi USB wykonywanie każdego transferu.</span><span class="sxs-lookup"><span data-stu-id="ac761-140">The USBX software scheduler will organize USB transfers with the correct frequency of service and priority, and will instruct the USB controller to execute each transfer.</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="ac761-141">Pełna obsługa platformy USB</span><span class="sxs-lookup"><span data-stu-id="ac761-141">Complete USB Device Framework Support</span></span>

<span data-ttu-id="ac761-142">USBX może obsługiwać najbardziej wymagające urządzenia USB, w tym wiele konfiguracji, wiele interfejsów i wiele ustawień alternatywnych.</span><span class="sxs-lookup"><span data-stu-id="ac761-142">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="ac761-143">Łatwe w użyciu interfejsy API</span><span class="sxs-lookup"><span data-stu-id="ac761-143">Easy-To-Use APIs</span></span>

<span data-ttu-id="ac761-144">USBX zapewnia bardzo najlepszy, głęboko osadzony stos USB w sposób, który jest łatwy do zrozumienia i użycia.</span><span class="sxs-lookup"><span data-stu-id="ac761-144">USBX provides the very best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="ac761-145">Interfejs API USBX zapewnia intuicyjną i spójność usług.</span><span class="sxs-lookup"><span data-stu-id="ac761-145">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="ac761-146">Korzystając z dostarczonych interfejsów API klasy USBX, aplikacja użytkownika nie musi zrozumieć złożoności protokołów USB.</span><span class="sxs-lookup"><span data-stu-id="ac761-146">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
