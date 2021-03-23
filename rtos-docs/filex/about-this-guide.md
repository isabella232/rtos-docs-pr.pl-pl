---
title: Podręcznik użytkownika usługi Azure RTO FileX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO FileX, systemu plików o wysokiej wydajności w czasie rzeczywistym firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0ebcebdd2b227ed8d9ccf8b3078b716f90f35bef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821463"
---
# <a name="about-this-filex-user-guide"></a><span data-ttu-id="98b5e-103">Informacje o tym podręczniku użytkownika FileX</span><span class="sxs-lookup"><span data-stu-id="98b5e-103">About This FileX User Guide</span></span>

<span data-ttu-id="98b5e-104">Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO FileX, systemu plików o wysokiej wydajności w czasie rzeczywistym od firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="98b5e-104">This guide contains comprehensive information about Azure RTOS FileX, the high-performance, real-time embedded file system from Microsoft.</span></span> <span data-ttu-id="98b5e-105">Aby najlepiej wykorzystać ten przewodnik, należy zapoznać się ze standardowymi funkcjami systemu operacyjnego w czasie rzeczywistym, usługami systemu plików FAT i językiem programowania C.</span><span class="sxs-lookup"><span data-stu-id="98b5e-105">To gain the most from this guide, you should be familiar with standard real-time operating system functions, FAT file system services, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="98b5e-106">Organizacja</span><span class="sxs-lookup"><span data-stu-id="98b5e-106">Organization</span></span>

<span data-ttu-id="98b5e-107">[Rozdział 1](chapter1.md) — wprowadzenie do usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="98b5e-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS FileX</span></span>

<span data-ttu-id="98b5e-108">[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO FileX z aplikacją Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="98b5e-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS FileX with your Azure RTOS ThreadX application</span></span>

<span data-ttu-id="98b5e-109">[Rozdział 3](chapter3.md) — zawiera przegląd funkcjonalny systemu Azure RTO FileX i podstawowe informacje na temat formatów systemu plików FAT</span><span class="sxs-lookup"><span data-stu-id="98b5e-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS FileX system and basic information about FAT file system formats</span></span>

<span data-ttu-id="98b5e-110">[Rozdział 4](chapter4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="98b5e-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS FileX</span></span>

<span data-ttu-id="98b5e-111">[Rozdział 5](chapter5.md) — opis dostarczonego sterownika ram usługi Azure RTO FileX i sposobu pisania własnych niestandardowych sterowników usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="98b5e-111">[Chapter 5](chapter5.md) - Describes the supplied Azure RTOS FileX RAM driver and how to write your own custom Azure RTOS FileX drivers</span></span>

<span data-ttu-id="98b5e-112">[Rozdział 6](chapter6.md) — Opis modułu odpornego na błędy usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="98b5e-112">[Chapter 6](chapter6.md) - Describes the Azure RTOS FileX Fault Tolerant Module</span></span>

<span data-ttu-id="98b5e-113">[Dodatek A](appendix-a.md) — Azure RTO FileX Services</span><span class="sxs-lookup"><span data-stu-id="98b5e-113">[Appendix A](appendix-a.md) - Azure RTOS FileX Services</span></span>

<span data-ttu-id="98b5e-114">[Dodatek B](appendix-b.md) — stałe usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="98b5e-114">[Appendix B](appendix-b.md) - Azure RTOS FileX Constants</span></span>

<span data-ttu-id="98b5e-115">[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="98b5e-115">[Appendix C](appendix-c.md) - Azure RTOS FileX Data Types</span></span>

<span data-ttu-id="98b5e-116">[Dodatek D](appendix-d.md) — wykres ASCII</span><span class="sxs-lookup"><span data-stu-id="98b5e-116">[Appendix D](appendix-d.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="98b5e-117">Konwencje przewodnika</span><span class="sxs-lookup"><span data-stu-id="98b5e-117">Guide Conventions</span></span>

<span data-ttu-id="98b5e-118">*Kursywa* — oznacza tytuły książek, wyróżnia ważne słowa i określa zmienne.</span><span class="sxs-lookup"><span data-stu-id="98b5e-118">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="98b5e-119">**Pogrubiona** — kroje liter oznacza nazwy plików, słowa kluczowe i bardziej podkreśla ważne słowa i zmienne.</span><span class="sxs-lookup"><span data-stu-id="98b5e-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="98b5e-120">Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.</span><span class="sxs-lookup"><span data-stu-id="98b5e-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98b5e-121">Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni unikać, ponieważ mogą spowodować błędy krytyczne.</span><span class="sxs-lookup"><span data-stu-id="98b5e-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="filex-data-types"></a><span data-ttu-id="98b5e-122">FileX — typy danych</span><span class="sxs-lookup"><span data-stu-id="98b5e-122">FileX Data Types</span></span>

<span data-ttu-id="98b5e-123">Oprócz niestandardowych typów danych struktury formantu FileX usługi Azure RTO istnieje szereg specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO FileX.</span><span class="sxs-lookup"><span data-stu-id="98b5e-123">In addition to the custom Azure RTOS FileX control structure data types, there is a series of special data types that are used in Azure RTOS FileX service call interfaces.</span></span> <span data-ttu-id="98b5e-124">Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C.</span><span class="sxs-lookup"><span data-stu-id="98b5e-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="98b5e-125">Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C.</span><span class="sxs-lookup"><span data-stu-id="98b5e-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="98b5e-126">Dokładna implementacja jest dziedziczona z usługi Azure RTO ThreadX i można ją znaleźć w pliku tx_port. h zawartym w dystrybucji usługi Azure RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="98b5e-126">The exact implementation is inherited from Azure RTOS ThreadX and can be found in the tx_port.h file included in the Azure RTOS ThreadX distribution.</span></span>

<span data-ttu-id="98b5e-127">Poniżej znajduje się lista typów danych wywołań usługi Azure RTO FileX i skojarzonych z nimi znaczenia.</span><span class="sxs-lookup"><span data-stu-id="98b5e-127">The following is a list of Azure RTOS FileX service call data types and their associated meanings.</span></span>
| <span data-ttu-id="98b5e-128">Typ</span><span class="sxs-lookup"><span data-stu-id="98b5e-128">Type</span></span>  | <span data-ttu-id="98b5e-129">Opis</span><span class="sxs-lookup"><span data-stu-id="98b5e-129">Description</span></span>  |
|---|---|
| <span data-ttu-id="98b5e-130">**UINT**</span><span class="sxs-lookup"><span data-stu-id="98b5e-130">**UINT**</span></span> | <span data-ttu-id="98b5e-131">Podstawowa niepodpisana liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="98b5e-131">Basic unsigned integer.</span></span> <span data-ttu-id="98b5e-132">Ten typ musi obsługiwać 8-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="98b5e-132">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="98b5e-133">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="98b5e-133">**ULONG**</span></span> | <span data-ttu-id="98b5e-134">Typ Long unsigned.</span><span class="sxs-lookup"><span data-stu-id="98b5e-134">Unsigned long type.</span></span> <span data-ttu-id="98b5e-135">Ten typ musi obsługiwać 32-bitowe dane niepodpisane.</span><span class="sxs-lookup"><span data-stu-id="98b5e-135">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="98b5e-136">**POZYCJĘ**</span><span class="sxs-lookup"><span data-stu-id="98b5e-136">**VOID**</span></span> | <span data-ttu-id="98b5e-137">Prawie zawsze jest równoważne z typem void kompilatora.</span><span class="sxs-lookup"><span data-stu-id="98b5e-137">Almost always equivalent to the compiler’s void type.</span></span> |
| <span data-ttu-id="98b5e-138">**DELIKATN**</span><span class="sxs-lookup"><span data-stu-id="98b5e-138">**CHAR**</span></span> | <span data-ttu-id="98b5e-139">Najczęściej jest to standardowy 8-bitowy typ znaku.</span><span class="sxs-lookup"><span data-stu-id="98b5e-139">Most often a standard 8-bit character type.</span></span> |
| <span data-ttu-id="98b5e-140">**ULONG64**</span><span class="sxs-lookup"><span data-stu-id="98b5e-140">**ULONG64**</span></span> | <span data-ttu-id="98b5e-141">64-bitowy typ danych Liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="98b5e-141">64-bit unsigned integer data type.</span></span> |

<span data-ttu-id="98b5e-142">W źródle FileX są używane dodatkowe typy danych.</span><span class="sxs-lookup"><span data-stu-id="98b5e-142">Additional data types are used within the FileX source.</span></span> <span data-ttu-id="98b5e-143">Znajdują się one w plikach \***tx_port. h** _ lub _ \*_fx_port. h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="98b5e-143">They are located in either the ***tx_port.h** _ or _ *_fx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="98b5e-144">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="98b5e-144">Customer Support Center</span></span>

<span data-ttu-id="98b5e-145">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="98b5e-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="98b5e-146">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="98b5e-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="98b5e-147">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="98b5e-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="98b5e-148">Szczegółowy opis wszelkich zmian w aplikacji i/lub FileX, które poprzedzają problem.</span><span class="sxs-lookup"><span data-stu-id="98b5e-148">A detailed description of any changes to the application and/or FileX that preceded the problem.</span></span>
3. <span data-ttu-id="98b5e-149">Zawartość _tx_version_id i _fx_version_id ciągów znalezionych w plikach \***tx_port. h**_ i _ *_fx_port. h_*\* dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="98b5e-149">The contents of the _tx_version_id and _fx_version_id strings found in the \***tx_port.h**_ and _ *_fx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="98b5e-150">Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="98b5e-150">These strings will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="98b5e-151">Zawartość w pamięci RAM następujących zmiennych **ULONG** .</span><span class="sxs-lookup"><span data-stu-id="98b5e-151">The contents in RAM of the following **ULONG** variables.</span></span> <span data-ttu-id="98b5e-152">Te zmienne zawierają informacje o sposobie kompilowania bibliotek ThreadX i FileX:</span><span class="sxs-lookup"><span data-stu-id="98b5e-152">These variables will give us information on how your ThreadX and FileX libraries were built:</span></span>

    <span data-ttu-id="98b5e-153">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="98b5e-153">**_tx_build_options**</span></span>

    <span data-ttu-id="98b5e-154">**_fx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="98b5e-154">**_fx_system_build_options1**</span></span>

    <span data-ttu-id="98b5e-155">**_fx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="98b5e-155">**_fx_system_build_options2**</span></span>

    <span data-ttu-id="98b5e-156">**_fx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="98b5e-156">**_fx_system_build_options3**</span></span>
