---
title: Informacje o podręczniku usługi Azure RTO ThreadX
description: Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO ThreadX, jądrze w czasie rzeczywistym firmy Microsoft o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822495"
---
# <a name="about-the-azure-rtos-threadx-guide"></a><span data-ttu-id="e9e9f-103">Informacje o podręczniku usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="e9e9f-103">About the Azure RTOS ThreadX Guide</span></span>

<span data-ttu-id="e9e9f-104">Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO ThreadX, jądrze w czasie rzeczywistym firmy Microsoft o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-104">This guide provides comprehensive information about Azure RTOS ThreadX, the Microsoft high-performance real-time kernel.</span></span> 

<span data-ttu-id="e9e9f-105">Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="e9e9f-106">Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym i język programowania C.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="e9e9f-107">Organizacja</span><span class="sxs-lookup"><span data-stu-id="e9e9f-107">Organization</span></span>

<span data-ttu-id="e9e9f-108">[Rozdział 1](chapter1.md) — zawiera podstawowe Omówienie usługi Azure RTO ThreadX i jej relacji z programowaniem osadzonym w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="e9e9f-108">[Chapter 1](chapter1.md) - Provides a basic overview of Azure RTOS ThreadX and its relationship to real-time embedded development</span></span>

<span data-ttu-id="e9e9f-109">[Rozdział 2](chapter2.md) — zawiera podstawowe kroki umożliwiające zainstalowanie i użycie usługi Azure RTO ThreadX w aplikacji bezpośrednio *z poziomu pola*</span><span class="sxs-lookup"><span data-stu-id="e9e9f-109">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS ThreadX in your application right *out of the box*</span></span>

<span data-ttu-id="e9e9f-110">[Rozdział 3](chapter3.md) — szczegółowe omówienie działania funkcjonalnego platformy Azure RTO ThreadX, jądra o wysokiej wydajności w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="e9e9f-110">[Chapter 3](chapter3.md) - Describes in detail the functional operation of Azure RTOS ThreadX, the high performance real-time kernel</span></span>

<span data-ttu-id="e9e9f-111">[Rozdział 4](chapter4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="e9e9f-111">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS ThreadX</span></span>

<span data-ttu-id="e9e9f-112">[Rozdział 5](chapter5.md) . informacje na temat pisania sterowników we/wy dla aplikacji ThreadX usługi Azure RTO</span><span class="sxs-lookup"><span data-stu-id="e9e9f-112">[Chapter 5](chapter5.md) - Describes writing I/O drivers for Azure RTOS ThreadX applications</span></span>

<span data-ttu-id="e9e9f-113">[Rozdział 6](chapter6.md) — opis aplikacji demonstracyjnej, która jest dostarczana z każdym pakietem obsługi procesora usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="e9e9f-113">[Chapter 6](chapter6.md) - Describes the demonstration application that is supplied with every Azure RTOS ThreadX processor support package</span></span>

<span data-ttu-id="e9e9f-114">[Dodatek A](appendix-a.md) — interfejs API usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="e9e9f-114">[Appendix A](appendix-a.md) - Azure RTOS ThreadX API</span></span>

<span data-ttu-id="e9e9f-115">[Dodatek B](appendix-b.md) — stałe usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="e9e9f-115">[Appendix B](appendix-b.md) - Azure RTOS ThreadX constants</span></span>

<span data-ttu-id="e9e9f-116">[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="e9e9f-116">[Appendix C](appendix-c.md) - Azure RTOS ThreadX data types</span></span>

<span data-ttu-id="e9e9f-117">[Dodatek D](appendix-d.md) — wykres ASCII</span><span class="sxs-lookup"><span data-stu-id="e9e9f-117">[Appendix D](appendix-d.md) - ASCII chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="e9e9f-118">Konwencje przewodnika</span><span class="sxs-lookup"><span data-stu-id="e9e9f-118">Guide Conventions</span></span>

<span data-ttu-id="e9e9f-119">*Kursywa* — oznacza tytuły książek, podkreśla ważne słowa i wskazuje parametry.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-119">*Italics* - typeface denotes book titles, emphasizes important words, and indicates parameters.</span></span>

<span data-ttu-id="e9e9f-120">**Pogrubiona** — kroje liter oznacza słowa kluczowe, stałe, nazwy typów, elementy interfejsu użytkownika, nazwy zmiennych i dalsze akcenty ważnych wyrazów.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-120">**Boldface** - typeface denotes key words, constants, type names, user interface elements, variable names, and further emphasizes important words.</span></span>

<span data-ttu-id="e9e9f-121">***Kursywa i pogrubiona*** — oznacza nazwy plików i nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-121">***Italics and Boldface*** - typeface denotes file names and function names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9e9f-122">Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-122">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="e9e9f-123">Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni zachować ostrożność, ponieważ mogą spowodować błędy krytyczne.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-123">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-threadx-data-types"></a><span data-ttu-id="e9e9f-124">Azure RTO — typy danych ThreadX</span><span class="sxs-lookup"><span data-stu-id="e9e9f-124">Azure RTOS ThreadX Data Types</span></span>

<span data-ttu-id="e9e9f-125">Oprócz niestandardowych typów danych struktury formantu ThreadX usługi Azure RTO istnieje szereg specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-125">In addition to the custom Azure RTOS ThreadX control structure data types, there are a series of special data types that are used in Azure RTOS ThreadX service call interfaces.</span></span> <span data-ttu-id="e9e9f-126">Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-126">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="e9e9f-127">Jest to konieczne w celu zapewnienia przenośności między różnymi kompilatorami języka C.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-127">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="e9e9f-128">Dokładną implementację można znaleźć w pliku ***tx_port. h*** dołączonym do źródła.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-128">The exact implementation can be found in the ***tx_port.h*** file included with the source.</span></span>

<span data-ttu-id="e9e9f-129">Poniżej znajduje się lista typów danych wywołań usługi Azure RTO ThreadX i skojarzonych z nimi znaczenia:</span><span class="sxs-lookup"><span data-stu-id="e9e9f-129">The following is a list of Azure RTOS ThreadX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="e9e9f-130">Typ danych</span><span class="sxs-lookup"><span data-stu-id="e9e9f-130">Data type</span></span>  | <span data-ttu-id="e9e9f-131">Opis</span><span class="sxs-lookup"><span data-stu-id="e9e9f-131">Description</span></span> |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="e9e9f-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="e9e9f-132">**UINT**</span></span> | <span data-ttu-id="e9e9f-133">Podstawowa niepodpisana liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-133">Basic unsigned integer.</span></span> <span data-ttu-id="e9e9f-134">Ten typ musi obsługiwać 8-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-134">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="e9e9f-135">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="e9e9f-135">**ULONG**</span></span> | <span data-ttu-id="e9e9f-136">Typ Long unsigned.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-136">Unsigned long type.</span></span> <span data-ttu-id="e9e9f-137">Ten typ musi obsługiwać 32-bitowe dane niepodpisane.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-137">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="e9e9f-138">**POZYCJĘ**</span><span class="sxs-lookup"><span data-stu-id="e9e9f-138">**VOID**</span></span> | <span data-ttu-id="e9e9f-139">Prawie zawsze jest równoważne z typem void kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-139">Almost always equivalent to the compiler's void type.</span></span> |
| <span data-ttu-id="e9e9f-140">**DELIKATN**</span><span class="sxs-lookup"><span data-stu-id="e9e9f-140">**CHAR**</span></span> | <span data-ttu-id="e9e9f-141">Najczęściej jest to standardowy 8-bitowy typ znaku.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-141">Most often a standard 8-bit character type.</span></span> |
|  |  |

<span data-ttu-id="e9e9f-142">Dodatkowe typy danych są używane w źródle ThreadX usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-142">Additional data types are used within the Azure RTOS ThreadX source.</span></span> <span data-ttu-id="e9e9f-143">Znajdują się one również w pliku ***tx_port. h*** .</span><span class="sxs-lookup"><span data-stu-id="e9e9f-143">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="e9e9f-144">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="e9e9f-144">Customer Support Center</span></span>

<span data-ttu-id="e9e9f-145">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="e9e9f-146">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="e9e9f-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="e9e9f-147">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="e9e9f-148">Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-148">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="e9e9f-149">Zawartość ciągu *_tx_version_id* można znaleźć w pliku *tx_port. h* dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-149">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="e9e9f-150">Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-150">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="e9e9f-151">Zawartość w pamięci RAM _tx_build_options zmiennej  **ULONG** .</span><span class="sxs-lookup"><span data-stu-id="e9e9f-151">The contents in RAM of the **_tx_build_options** **ULONG** variable.</span></span> <span data-ttu-id="e9e9f-152">Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="e9e9f-152">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
