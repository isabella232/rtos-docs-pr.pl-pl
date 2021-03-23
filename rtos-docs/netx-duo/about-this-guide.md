---
title: Informacje o podręczniku użytkownika platformy Azure RTO NetX Duo
description: Ten przewodnik zawiera wyczerpujące informacje o platformie Azure RTO NetX Duo, czyli podwójnym stosie sieci IPv4/IPv6 o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822141"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a><span data-ttu-id="eaad7-103">Informacje o podręczniku użytkownika platformy Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-103">About The Azure RTOS NetX Duo User Guide</span></span>

<span data-ttu-id="eaad7-104">Ten przewodnik zawiera wyczerpujące informacje o platformie Azure RTO NetX Duo, czyli podwójnym stosie sieci IPv4/IPv6 o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="eaad7-104">This guide contains comprehensive information about Azure RTOS NetX Duo, the Microsoft high-performance IPv4/IPv6 dual network stack.</span></span> 

<span data-ttu-id="eaad7-105">Jest ona przeznaczona dla wbudowanych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe pojęcia dotyczące sieci, Azure RTO ThreadX i języka programowania C.</span><span class="sxs-lookup"><span data-stu-id="eaad7-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="eaad7-106">Organizacja</span><span class="sxs-lookup"><span data-stu-id="eaad7-106">Organization</span></span>

<span data-ttu-id="eaad7-107">[Rozdział 1](chapter1.md) — wprowadzenie do usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX Duo</span></span>

<span data-ttu-id="eaad7-108">[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalacji i używania platformy Azure RTO NetX Duo z aplikacją ThreadX</span><span class="sxs-lookup"><span data-stu-id="eaad7-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX Duo with your ThreadX application</span></span>

<span data-ttu-id="eaad7-109">[Rozdział 3](chapter3.md) — zawiera przegląd funkcjonalny systemu Azure RTO NetX Duo oraz podstawowe informacje na temat standardów sieci TCP/IP</span><span class="sxs-lookup"><span data-stu-id="eaad7-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX Duo system and basic information about the TCP/IP networking standards</span></span>

<span data-ttu-id="eaad7-110">[Rozdział 4](chapter4.md) — szczegóły interfejsu aplikacji na platformie Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX Duo</span></span>

<span data-ttu-id="eaad7-111">[Rozdział 5](chapter5.md) — opis sterowników sieciowych dla usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX Duo</span></span>

<span data-ttu-id="eaad7-112">[Dodatek A](appendix-a.md) — usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Duo Services</span></span>

<span data-ttu-id="eaad7-113">[Dodatek B](appendix-b.md) — stałe platformy Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Duo Constants</span></span>

<span data-ttu-id="eaad7-114">[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="eaad7-115">[Dodatek D](appendix-d.md) — interfejs API usługi BSD-Compatible Socket</span><span class="sxs-lookup"><span data-stu-id="eaad7-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="eaad7-116">[Dodatek E](appendix-e.md) -ASCII — wykres</span><span class="sxs-lookup"><span data-stu-id="eaad7-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="eaad7-117">Konwencje przewodnika</span><span class="sxs-lookup"><span data-stu-id="eaad7-117">Guide Conventions</span></span>

<span data-ttu-id="eaad7-118">Kursywa — oznacza tytuły książek, wyróżnia ważne słowa i określa zmienne.</span><span class="sxs-lookup"><span data-stu-id="eaad7-118">Italics - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="eaad7-119">**Pogrubiona** — kroje liter oznacza nazwy plików, słowa kluczowe i bardziej podkreśla ważne słowa i zmienne.</span><span class="sxs-lookup"><span data-stu-id="eaad7-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eaad7-120">Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.</span><span class="sxs-lookup"><span data-stu-id="eaad7-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>
 
> [!WARNING]
> <span data-ttu-id="eaad7-121">Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni unikać, ponieważ mogą spowodować błędy krytyczne.</span><span class="sxs-lookup"><span data-stu-id="eaad7-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-netx-duo-data-types"></a><span data-ttu-id="eaad7-122">Typy danych usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="eaad7-122">Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="eaad7-123">Oprócz niestandardowych typów danych struktury kontroli usługi Azure RTO NetX Duo istnieje kilka specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="eaad7-123">In addition to the custom Azure RTOS NetX Duo control structure data types, there are several special data types that are used in Azure RTOS NetX Duo service call interfaces.</span></span> <span data-ttu-id="eaad7-124">Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C.</span><span class="sxs-lookup"><span data-stu-id="eaad7-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="eaad7-125">Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C.</span><span class="sxs-lookup"><span data-stu-id="eaad7-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="eaad7-126">Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć w pliku ***tx_port. h*** zawartym w dystrybucji ThreadX.</span><span class="sxs-lookup"><span data-stu-id="eaad7-126">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="eaad7-127">Poniżej znajduje się lista typów danych wywołań usługi Azure RTO NetX Duo i skojarzonych z nimi znaczenia:</span><span class="sxs-lookup"><span data-stu-id="eaad7-127">The following is a list of Azure RTOS NetX Duo service call data types and their associated meanings:</span></span>

<span data-ttu-id="eaad7-128">**Uint**: podstawowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="eaad7-128">**UINT**: Basic unsigned integer.</span></span> <span data-ttu-id="eaad7-129">Ten typ musi obsługiwać 32-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="eaad7-129">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span>  
<span data-ttu-id="eaad7-130">**ULONG**: typ Long unsigned.</span><span class="sxs-lookup"><span data-stu-id="eaad7-130">**ULONG**: Unsigned long type.</span></span> <span data-ttu-id="eaad7-131">Ten typ musi obsługiwać 32-bitowe dane niepodpisane.</span><span class="sxs-lookup"><span data-stu-id="eaad7-131">This type must support 32-bit unsigned  data.</span></span>
<span data-ttu-id="eaad7-132">**Void**: prawie zawsze odpowiada typowi void kompilatora.</span><span class="sxs-lookup"><span data-stu-id="eaad7-132">**VOID**: Almost always equivalent to the compiler's void type.</span></span>  
<span data-ttu-id="eaad7-133">**Char**: najczęściej jest to standardowy 8-bitowy typ znaku.</span><span class="sxs-lookup"><span data-stu-id="eaad7-133">**CHAR**: Most often a standard 8-bit character type.</span></span>  

<span data-ttu-id="eaad7-134">Dodatkowe typy danych są używane w źródle Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="eaad7-134">Additional data types are used within the Azure RTOS NetX Duo source.</span></span> <span data-ttu-id="eaad7-135">Znajdują się one w plikach \***tx_port. h** _ lub _ \*_nx_port. h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="eaad7-135">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="eaad7-136">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="eaad7-136">Customer Support Center</span></span>

<span data-ttu-id="eaad7-137">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="eaad7-137">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="eaad7-138">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="eaad7-138">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="eaad7-139">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="eaad7-139">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="eaad7-140">Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO NetX Duo, który poprzedza problem.</span><span class="sxs-lookup"><span data-stu-id="eaad7-140">A detailed description of any changes to the application and/or Azure RTOS NetX Duo that preceded the problem.</span></span>
3. <span data-ttu-id="eaad7-141">Zawartość _tx_version_id i _nx_version_id ciągów znalezionych w plikach tx_port. h i nx_port. h dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="eaad7-141">The contents of the _tx_version_id and _nx_version_id strings found in the tx_port.h and nx_port.h files of your distribution.</span></span> <span data-ttu-id="eaad7-142">Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="eaad7-142">These strings will provide us valuable information regarding your run- time environment.</span></span>
4. <span data-ttu-id="eaad7-143">Zawartość w pamięci RAM następujących zmiennych ULONG:</span><span class="sxs-lookup"><span data-stu-id="eaad7-143">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="eaad7-144">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="eaad7-144">**_tx_build_options**</span></span>

    <span data-ttu-id="eaad7-145">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="eaad7-145">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="eaad7-146">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="eaad7-146">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="eaad7-147">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="eaad7-147">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="eaad7-148">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="eaad7-148">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="eaad7-149">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="eaad7-149">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="eaad7-150">Te zmienne będą zawierać informacje o sposobie kompilowania bibliotek Azure RTO ThreadX i Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="eaad7-150">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX Duo libraries were built.</span></span>

5. <span data-ttu-id="eaad7-151">Bufor śledzenia przechwycony natychmiast po wykryciu problemu.</span><span class="sxs-lookup"><span data-stu-id="eaad7-151">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="eaad7-152">Jest to realizowane przez utworzenie bibliotek Azure RTO ThreadX i Azure RTO NetX Duo przy użyciu TX_ENABLE_EVENT_TRACE i wywołanie tx_trace_enable z informacjami o buforze śledzenia.</span><span class="sxs-lookup"><span data-stu-id="eaad7-152">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX Duo libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>
