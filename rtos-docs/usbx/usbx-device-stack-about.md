---
title: Przewodnik użytkownika stosu urządzeń usługi Azure RTO USBX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO USBX, czyli oprogramowania USB Foundation o wysokiej wydajności firmy Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821331"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a><span data-ttu-id="c1239-103">Przewodnik użytkownika stosu urządzeń usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="c1239-103">Azure RTOS USBX Device Stack User Guide</span></span>

<span data-ttu-id="c1239-104">Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO USBX, czyli oprogramowaniu High Performance USB Foundation od firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c1239-104">This guide provides comprehensive information about Azure RTOS USBX, the high performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="c1239-105">Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="c1239-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="c1239-106">Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym, specyfikację USB i język programowania C.</span><span class="sxs-lookup"><span data-stu-id="c1239-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="c1239-107">Aby uzyskać informacje techniczne dotyczące technologii USB, zobacz specyfikację USB i specyfikacje klasy USB, które można pobrać w https://www.USB.org/developers</span><span class="sxs-lookup"><span data-stu-id="c1239-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at https://www.USB.org/developers</span></span>

## <a name="organization"></a><span data-ttu-id="c1239-108">Organizacja</span><span class="sxs-lookup"><span data-stu-id="c1239-108">Organization</span></span>

- <span data-ttu-id="c1239-109">[**Rozdział 1**](usbx-device-stack-1.md) — zawiera wprowadzenie do usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="c1239-109">[**Chapter 1**](usbx-device-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="c1239-110">[**Rozdział 2**](usbx-device-stack-2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO USBX z aplikacją ThreadX</span><span class="sxs-lookup"><span data-stu-id="c1239-110">[**Chapter 2**](usbx-device-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your ThreadX application</span></span>

- <span data-ttu-id="c1239-111">[**Rozdział 3**](usbx-device-stack-3.md) — Opis składników funkcjonalnych stosu urządzeń usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="c1239-111">[**Chapter 3**](usbx-device-stack-3.md) - describes the functional components of the Azure RTOS USBX device stack</span></span>

- <span data-ttu-id="c1239-112">[**Rozdział 4**](usbx-device-stack-4.md) — Opis usługi Azure RTO USBX Stack</span><span class="sxs-lookup"><span data-stu-id="c1239-112">[**Chapter 4**](usbx-device-stack-4.md) - describes the Azure RTOS USBX device stack services</span></span>

- <span data-ttu-id="c1239-113">[**Rozdział 5**](usbx-device-stack-5.md) — opis każdej klasy urządzeń usługi Azure RTO USBX, w tym interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c1239-113">[**Chapter 5**](usbx-device-stack-5.md) - describes each Azure RTOS USBX device class including their APIs</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="c1239-114">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="c1239-114">Customer Support Center</span></span>

<span data-ttu-id="c1239-115">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="c1239-115">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="c1239-116">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="c1239-116">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="c1239-117">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="c1239-117">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="c1239-118">Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.</span><span class="sxs-lookup"><span data-stu-id="c1239-118">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="c1239-119">Zawartość ciągu **_tx_version_id** można znaleźć w pliku **_tx_port. h_** dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="c1239-119">The contents of the **_tx_version_id** string found in the **_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="c1239-120">Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c1239-120">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="c1239-121">Zawartość w pamięci RAM _tx_build_options zmiennej  **ULONG** .</span><span class="sxs-lookup"><span data-stu-id="c1239-121">The contents in RAM of the *_tx_build_options* **ULONG** variable.</span></span> <span data-ttu-id="c1239-122">Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="c1239-122">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
