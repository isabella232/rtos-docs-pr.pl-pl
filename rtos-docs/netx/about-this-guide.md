---
title: Podręcznik użytkownika usługi Azure RTO NetX — informacje
description: Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO NetX, stosie sieci o wysokiej wydajności firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8e1c23892c4360ddc8783b04ae8f23e371899f1d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822824"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a><span data-ttu-id="80872-103">Podręcznik użytkownika usługi Azure RTO NetX — informacje</span><span class="sxs-lookup"><span data-stu-id="80872-103">About The Azure RTOS NetX User Guide</span></span>

<span data-ttu-id="80872-104">Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO NetX, stosie sieci o wysokiej wydajności firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="80872-104">This guide contains comprehensive information about Azure RTOS NetX, the Microsoft high-performance network stack.</span></span>

<span data-ttu-id="80872-105">Jest ona przeznaczona dla wbudowanych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe pojęcia dotyczące sieci, Azure RTO ThreadX i języka programowania C.</span><span class="sxs-lookup"><span data-stu-id="80872-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="80872-106">Organizacja</span><span class="sxs-lookup"><span data-stu-id="80872-106">Organization</span></span>

<span data-ttu-id="80872-107">[Rozdział 1](chapter1.md) — wprowadzenie do usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="80872-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX</span></span>

<span data-ttu-id="80872-108">[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO NetX z aplikacją ThreadX.</span><span class="sxs-lookup"><span data-stu-id="80872-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX with your ThreadX application.</span></span>

<span data-ttu-id="80872-109">[Rozdział 3](chapter3.md) — zawiera przegląd funkcjonalny systemu Azure RTO NetX i podstawowe informacje o standardach sieci TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="80872-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX system and basic information about the TCP/IP networking standards.</span></span>

<span data-ttu-id="80872-110">[Rozdział 4](chapter4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="80872-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX.</span></span>

<span data-ttu-id="80872-111">[Rozdział 5](chapter5.md) — opis sterowników sieciowych dla usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="80872-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX.</span></span>

<span data-ttu-id="80872-112">[Dodatek A](appendix-a.md) — Azure RTO NetX Services</span><span class="sxs-lookup"><span data-stu-id="80872-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Services</span></span>

<span data-ttu-id="80872-113">[Dodatek B](appendix-b.md) — stałe usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="80872-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Constants</span></span>

<span data-ttu-id="80872-114">[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="80872-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="80872-115">[Dodatek D](appendix-d.md) — interfejs API usługi BSD-Compatible Socket</span><span class="sxs-lookup"><span data-stu-id="80872-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="80872-116">[Dodatek E](appendix-e.md) -ASCII — wykres</span><span class="sxs-lookup"><span data-stu-id="80872-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="azure-rtos-netx-data-types"></a><span data-ttu-id="80872-117">Azure RTO — typy danych NetX</span><span class="sxs-lookup"><span data-stu-id="80872-117">Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="80872-118">Oprócz niestandardowych typów danych struktury formantów NetX usługi Azure RTO, istnieje kilka specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="80872-118">In addition to the custom Azure RTOS NetX control structure data types, there are several special data types that are used in Azure RTOS NetX service call interfaces.</span></span> <span data-ttu-id="80872-119">Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C.</span><span class="sxs-lookup"><span data-stu-id="80872-119">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="80872-120">Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C.</span><span class="sxs-lookup"><span data-stu-id="80872-120">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="80872-121">Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć w pliku ***tx_port. h*** zawartym w dystrybucji ThreadX.</span><span class="sxs-lookup"><span data-stu-id="80872-121">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="80872-122">Poniżej znajduje się lista typów danych wywołań usługi Azure RTO NetX i skojarzonych z nimi znaczenia:</span><span class="sxs-lookup"><span data-stu-id="80872-122">The following is a list of Azure RTOS NetX service call data types and their associated meanings:</span></span>

| <!-- -->    | <!-- -->    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="80872-123">**UINT**</span><span class="sxs-lookup"><span data-stu-id="80872-123">**UINT**</span></span>  | <span data-ttu-id="80872-124">Podstawowa niepodpisana liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="80872-124">Basic unsigned integer.</span></span> <span data-ttu-id="80872-125">Ten typ musi obsługiwać 32-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="80872-125">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="80872-126">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="80872-126">**ULONG**</span></span> | <span data-ttu-id="80872-127">Typ Long unsigned.</span><span class="sxs-lookup"><span data-stu-id="80872-127">Unsigned long type.</span></span> <span data-ttu-id="80872-128">Ten typ musi obsługiwać 32-bitowe dane niepodpisane.</span><span class="sxs-lookup"><span data-stu-id="80872-128">This type must support 32-bit unsigned data.</span></span>                                                                      |
| <span data-ttu-id="80872-129">**POZYCJĘ**</span><span class="sxs-lookup"><span data-stu-id="80872-129">**VOID**</span></span>  | <span data-ttu-id="80872-130">Prawie zawsze jest równoważne z typem void kompilatora.</span><span class="sxs-lookup"><span data-stu-id="80872-130">Almost always equivalent to the compiler's void type.</span></span>                                                                                 |
| <span data-ttu-id="80872-131">**DELIKATN**</span><span class="sxs-lookup"><span data-stu-id="80872-131">**CHAR**</span></span>  | <span data-ttu-id="80872-132">Najczęściej jest to standardowy 8-bitowy typ znaku.</span><span class="sxs-lookup"><span data-stu-id="80872-132">Most often a standard 8-bit character type.</span></span>                                                                                           |

<span data-ttu-id="80872-133">Dodatkowe typy danych są używane w źródle NetX usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="80872-133">Additional data types are used within the Azure RTOS NetX source.</span></span> <span data-ttu-id="80872-134">Znajdują się one w plikach \***tx_port. h** _ lub _ \*_nx_port. h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="80872-134">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="80872-135">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="80872-135">Customer Support Center</span></span>

<span data-ttu-id="80872-136">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="80872-136">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="80872-137">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="80872-137">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="80872-138">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="80872-138">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="80872-139">Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO NetX, który poprzedza problem.</span><span class="sxs-lookup"><span data-stu-id="80872-139">A detailed description of any changes to the application and/or Azure RTOS NetX that preceded the problem.</span></span>

3. <span data-ttu-id="80872-140">Zawartość **_tx_version_id** i **_nx_version_id** ciągów znalezionych w **_tx_port. h_*_ i _*_nx_port. h_** plików dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="80872-140">The contents of the **_tx_version_id** and **_nx_version_id** strings found in the **_tx_port.h_*_ and _*_nx_port.h_** files of your distribution.</span></span> <span data-ttu-id="80872-141">Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="80872-141">These strings will provide us valuable information regarding your run-time environment.</span></span>

4. <span data-ttu-id="80872-142">Zawartość w pamięci RAM następujących zmiennych **ULONG** :</span><span class="sxs-lookup"><span data-stu-id="80872-142">The contents in RAM of the following **ULONG** variables:</span></span>

    <span data-ttu-id="80872-143">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="80872-143">**_tx_build_options**</span></span>

    <span data-ttu-id="80872-144">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="80872-144">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="80872-145">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="80872-145">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="80872-146">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="80872-146">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="80872-147">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="80872-147">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="80872-148">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="80872-148">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="80872-149">Te zmienne zawierają informacje o sposobie kompilowania bibliotek RTO ThreadX i Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="80872-149">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX libraries were built.</span></span>

5. <span data-ttu-id="80872-150">Bufor śledzenia przechwycony natychmiast po wykryciu problemu.</span><span class="sxs-lookup"><span data-stu-id="80872-150">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="80872-151">Jest to realizowane przez utworzenie bibliotek Azure RTO ThreadX i Azure RTO NetX przy użyciu **TX_ENABLE_EVENT_TRACE** i wywołanie **tx_trace_enable** z informacjami o buforze śledzenia.</span><span class="sxs-lookup"><span data-stu-id="80872-151">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX libraries with **TX_ENABLE_EVENT_TRACE** and calling **tx_trace_enable** with the trace buffer information.</span></span> <span data-ttu-id="80872-152">Aby uzyskać szczegółowe informacje, zobacz Podręcznik użytkownika usługi Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="80872-152">Refer to the Azure RTOS TraceX User Guide for details.</span></span>
