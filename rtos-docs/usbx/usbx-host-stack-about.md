---
title: Przewodnik użytkownika stosu hosta usługi Azure RTO USBX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO USBX, czyli oprogramowania USB Foundation o wysokiej wydajności od firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 243b12c4757ee945def8fea01c0d4114e39312ce
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823233"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a><span data-ttu-id="fe80a-103">Przewodnik użytkownika stosu hosta usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="fe80a-103">Azure RTOS USBX Host Stack User Guide</span></span>

<span data-ttu-id="fe80a-104">Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO USBX, czyli oprogramowania USB Foundation o wysokiej wydajności od firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fe80a-104">This guide provides comprehensive information about Azure RTOS USBX, the high-performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="fe80a-105">Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="fe80a-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="fe80a-106">Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym, specyfikację USB i język programowania C.</span><span class="sxs-lookup"><span data-stu-id="fe80a-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="fe80a-107">Aby uzyskać informacje techniczne dotyczące technologii USB, zobacz specyfikację USB i specyfikacje klasy USB, które można pobrać w [https://www.USB.org/developers](https://www.USB.org/developers)</span><span class="sxs-lookup"><span data-stu-id="fe80a-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at [https://www.USB.org/developers](https://www.USB.org/developers)</span></span>

## <a name="organization"></a><span data-ttu-id="fe80a-108">Organizacja</span><span class="sxs-lookup"><span data-stu-id="fe80a-108">Organization</span></span>

- <span data-ttu-id="fe80a-109">[**Rozdział 1**](usbx-host-stack-1.md) — zawiera wprowadzenie do usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="fe80a-109">[**Chapter 1**](usbx-host-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="fe80a-110">[**Rozdział 2**](usbx-host-stack-2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO USBX z aplikacją Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="fe80a-110">[**Chapter 2**](usbx-host-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your Azure RTOS ThreadX application</span></span>

- <span data-ttu-id="fe80a-111">[**Rozdział 3**](usbx-host-stack-3.md) — zawiera przegląd funkcjonalny usługi Azure RTO USBX i podstawowe informacje o USB</span><span class="sxs-lookup"><span data-stu-id="fe80a-111">[**Chapter 3**](usbx-host-stack-3.md) - provides a functional overview of Azure RTOS USBX and basic information about USB</span></span>

- <span data-ttu-id="fe80a-112">[**Rozdział 4**](usbx-host-stack-4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO USBX w trybie hosta</span><span class="sxs-lookup"><span data-stu-id="fe80a-112">[**Chapter 4**](usbx-host-stack-4.md) - details the application's interface to Azure RTOS USBX in host mode</span></span>

- <span data-ttu-id="fe80a-113">[**Rozdział 5**](usbx-host-stack-5.md) — opis interfejsów API klas hosta usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="fe80a-113">[**Chapter 5**](usbx-host-stack-5.md) - describes the APIs of the Azure RTOS USBX Host classes</span></span>

- <span data-ttu-id="fe80a-114">[**Rozdział 6**](usbx-host-stack-6.md) — opis klasy ECM usługi Azure RTO USBX — Klasa</span><span class="sxs-lookup"><span data-stu-id="fe80a-114">[**Chapter 6**](usbx-host-stack-6.md) - describes the Azure RTOS USBX CDC-ECM class</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="fe80a-115">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="fe80a-115">Customer Support Center</span></span>

<span data-ttu-id="fe80a-116">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="fe80a-116">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="fe80a-117">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="fe80a-117">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="fe80a-118">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="fe80a-118">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="fe80a-119">Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.</span><span class="sxs-lookup"><span data-stu-id="fe80a-119">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="fe80a-120">Zawartość ciągu *_tx_version_id* można znaleźć w pliku *tx_port. h* dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="fe80a-120">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="fe80a-121">Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fe80a-121">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="fe80a-122">Zawartość w pamięci RAM *_tx_build_options* zmiennej ulong.</span><span class="sxs-lookup"><span data-stu-id="fe80a-122">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="fe80a-123">Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="fe80a-123">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
