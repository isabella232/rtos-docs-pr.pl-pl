---
title: Podręcznik użytkownika usługi Azure RTO NetX — informacje
description: Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO NetX, stosie sieci o wysokiej wydajności firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 01077e3315e87b918cdfd47423d8e0c1b6bbdbbd
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550273"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a><span data-ttu-id="50e77-103">Podręcznik użytkownika usługi Azure RTO NetX — informacje</span><span class="sxs-lookup"><span data-stu-id="50e77-103">About The Azure RTOS NetX User Guide</span></span>

<span data-ttu-id="50e77-104">Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO NetX, stosie sieci o wysokiej wydajności firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="50e77-104">This guide contains comprehensive information about Azure RTOS NetX, the Microsoft high-performance network stack.</span></span>

<span data-ttu-id="50e77-105">Jest ona przeznaczona dla wbudowanych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe pojęcia dotyczące sieci, Azure RTO ThreadX i języka programowania C.</span><span class="sxs-lookup"><span data-stu-id="50e77-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="50e77-106">Organizacja</span><span class="sxs-lookup"><span data-stu-id="50e77-106">Organization</span></span>

<span data-ttu-id="50e77-107">[Rozdział 1](chapter1.md) — wprowadzenie do usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="50e77-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX</span></span>

<span data-ttu-id="50e77-108">[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO NetX z aplikacją ThreadX.</span><span class="sxs-lookup"><span data-stu-id="50e77-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX with your ThreadX application.</span></span>

<span data-ttu-id="50e77-109">[Rozdział 3](chapter3.md) — zawiera przegląd funkcjonalny systemu Azure RTO NetX i podstawowe informacje o standardach sieci TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="50e77-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX system and basic information about the TCP/IP networking standards.</span></span>

<span data-ttu-id="50e77-110">[Rozdział 4](chapter4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="50e77-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX.</span></span>

<span data-ttu-id="50e77-111">[Rozdział 5](chapter5.md) — opis sterowników sieciowych dla usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="50e77-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX.</span></span>

<span data-ttu-id="50e77-112">[Dodatek A](appendix-a.md) — Azure RTO NetX Services</span><span class="sxs-lookup"><span data-stu-id="50e77-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Services</span></span>

<span data-ttu-id="50e77-113">[Dodatek B](appendix-b.md) — stałe usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="50e77-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Constants</span></span>

<span data-ttu-id="50e77-114">[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="50e77-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="50e77-115">[Dodatek D](appendix-d.md) — interfejs API usługi BSD-Compatible Socket</span><span class="sxs-lookup"><span data-stu-id="50e77-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="50e77-116">[Dodatek E](appendix-e.md) -ASCII — wykres</span><span class="sxs-lookup"><span data-stu-id="50e77-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="azure-rtos-netx-data-types"></a><span data-ttu-id="50e77-117">Azure RTO — typy danych NetX</span><span class="sxs-lookup"><span data-stu-id="50e77-117">Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="50e77-118">Oprócz niestandardowych typów danych struktury formantów NetX usługi Azure RTO, istnieje kilka specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="50e77-118">In addition to the custom Azure RTOS NetX control structure data types, there are several special data types that are used in Azure RTOS NetX service call interfaces.</span></span> <span data-ttu-id="50e77-119">Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C.</span><span class="sxs-lookup"><span data-stu-id="50e77-119">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="50e77-120">Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C.</span><span class="sxs-lookup"><span data-stu-id="50e77-120">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="50e77-121">Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć w pliku ***tx_port. h*** zawartym w dystrybucji ThreadX.</span><span class="sxs-lookup"><span data-stu-id="50e77-121">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="50e77-122">Poniżej znajduje się lista typów danych wywołań usługi Azure RTO NetX i skojarzonych z nimi znaczenia:</span><span class="sxs-lookup"><span data-stu-id="50e77-122">The following is a list of Azure RTOS NetX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="50e77-123">Typy danych</span><span class="sxs-lookup"><span data-stu-id="50e77-123">Data Types</span></span> | <span data-ttu-id="50e77-124">Opis</span><span class="sxs-lookup"><span data-stu-id="50e77-124">Description</span></span>  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="50e77-125">**UINT**</span><span class="sxs-lookup"><span data-stu-id="50e77-125">**UINT**</span></span>  | <span data-ttu-id="50e77-126">Podstawowa niepodpisana liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="50e77-126">Basic unsigned integer.</span></span> <span data-ttu-id="50e77-127">Ten typ musi obsługiwać 32-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="50e77-127">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="50e77-128">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="50e77-128">**ULONG**</span></span> | <span data-ttu-id="50e77-129">Typ Long unsigned.</span><span class="sxs-lookup"><span data-stu-id="50e77-129">Unsigned long type.</span></span> <span data-ttu-id="50e77-130">Ten typ musi obsługiwać 32-bitowe dane niepodpisane.</span><span class="sxs-lookup"><span data-stu-id="50e77-130">This type must support 32-bit unsigned data.</span></span>                                                                      |
| <span data-ttu-id="50e77-131">**POZYCJĘ**</span><span class="sxs-lookup"><span data-stu-id="50e77-131">**VOID**</span></span>  | <span data-ttu-id="50e77-132">Prawie zawsze jest równoważne z typem void kompilatora.</span><span class="sxs-lookup"><span data-stu-id="50e77-132">Almost always equivalent to the compiler's void type.</span></span>                                                                                 |
| <span data-ttu-id="50e77-133">**DELIKATN**</span><span class="sxs-lookup"><span data-stu-id="50e77-133">**CHAR**</span></span>  | <span data-ttu-id="50e77-134">Najczęściej jest to standardowy 8-bitowy typ znaku.</span><span class="sxs-lookup"><span data-stu-id="50e77-134">Most often a standard 8-bit character type.</span></span>                                                                                           |

<span data-ttu-id="50e77-135">Dodatkowe typy danych są używane w źródle NetX usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="50e77-135">Additional data types are used within the Azure RTOS NetX source.</span></span> <span data-ttu-id="50e77-136">Znajdują się one w plikach \***tx_port. h** _ lub _ \*_nx_port. h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="50e77-136">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="50e77-137">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="50e77-137">Customer Support Center</span></span>

<span data-ttu-id="50e77-138">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="50e77-138">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="50e77-139">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="50e77-139">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="50e77-140">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="50e77-140">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="50e77-141">Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO NetX, który poprzedza problem.</span><span class="sxs-lookup"><span data-stu-id="50e77-141">A detailed description of any changes to the application and/or Azure RTOS NetX that preceded the problem.</span></span>

3. <span data-ttu-id="50e77-142">Zawartość **_tx_version_id** i **_nx_version_id** ciągów znalezionych w **_tx_port. h_*_ i _*_nx_port. h_** plików dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="50e77-142">The contents of the **_tx_version_id** and **_nx_version_id** strings found in the **_tx_port.h_*_ and _*_nx_port.h_** files of your distribution.</span></span> <span data-ttu-id="50e77-143">Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="50e77-143">These strings will provide us valuable information regarding your run-time environment.</span></span>

4. <span data-ttu-id="50e77-144">Zawartość w pamięci RAM następujących zmiennych **ULONG** :</span><span class="sxs-lookup"><span data-stu-id="50e77-144">The contents in RAM of the following **ULONG** variables:</span></span>

    <span data-ttu-id="50e77-145">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="50e77-145">**_tx_build_options**</span></span>

    <span data-ttu-id="50e77-146">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="50e77-146">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="50e77-147">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="50e77-147">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="50e77-148">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="50e77-148">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="50e77-149">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="50e77-149">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="50e77-150">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="50e77-150">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="50e77-151">Te zmienne zawierają informacje o sposobie kompilowania bibliotek RTO ThreadX i Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="50e77-151">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX libraries were built.</span></span>

5. <span data-ttu-id="50e77-152">Bufor śledzenia przechwycony natychmiast po wykryciu problemu.</span><span class="sxs-lookup"><span data-stu-id="50e77-152">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="50e77-153">Jest to realizowane przez utworzenie bibliotek Azure RTO ThreadX i Azure RTO NetX przy użyciu **TX_ENABLE_EVENT_TRACE** i wywołanie **tx_trace_enable** z informacjami o buforze śledzenia.</span><span class="sxs-lookup"><span data-stu-id="50e77-153">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX libraries with **TX_ENABLE_EVENT_TRACE** and calling **tx_trace_enable** with the trace buffer information.</span></span> <span data-ttu-id="50e77-154">Aby uzyskać szczegółowe informacje, zobacz Podręcznik użytkownika usługi Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="50e77-154">Refer to the Azure RTOS TraceX User Guide for details.</span></span>
