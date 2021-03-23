---
title: Podręcznik użytkownika usługi Azure RTO TraceX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO TraceX, narzędzia do analizy systemu opartego na systemie Microsoft Windows firmy Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823773"
---
# <a name="about-this-guide"></a><span data-ttu-id="c62bb-103">O tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="c62bb-103">About this guide</span></span>

<span data-ttu-id="c62bb-104">Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO TraceX, narzędzia do analizy systemu opartego na systemie Microsoft Windows dla Microsoft Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="c62bb-104">This guide contains comprehensive information about Azure RTOS TraceX, the Microsoft Windows-based system analysis tool for Microsoft Azure RTOS.</span></span>

<span data-ttu-id="c62bb-105">Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym przy użyciu usługi Azure RTO ThreadX Real-Time system operacyjny (RTO) i składniki dodatków.</span><span class="sxs-lookup"><span data-stu-id="c62bb-105">It is intended for the embedded real-time software developer using Azure RTOS ThreadX Real-Time Operating System (RTOS) and add-on components.</span></span> <span data-ttu-id="c62bb-106">Deweloper powinien znać Standard platformy Azure RTO ThreadX Azure RTO FileX oraz koncepcje platformy Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-106">The developer should be familiar with standard Azure RTOS ThreadX Azure RTOS FileX, and Azure RTOS NetX concepts.</span></span>

## <a name="organization"></a><span data-ttu-id="c62bb-107">Organizacja</span><span class="sxs-lookup"><span data-stu-id="c62bb-107">Organization</span></span>

- <span data-ttu-id="c62bb-108">[Rozdział 1](chapter1.md) — zawiera podstawowe Omówienie usługi Azure RTO TraceX i opisuje jej relacje z programowaniem w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="c62bb-108">[Chapter 1](chapter1.md) - contains an basic overview of Azure RTOS TraceX and describes its relationship to real-time development.</span></span>
- <span data-ttu-id="c62bb-109">[Rozdział 2](chapter2.md) — zawiera podstawowe kroki umożliwiające zainstalowanie i użycie usługi Azure RTO TraceX w celu przeanalizowania aplikacji od razu.</span><span class="sxs-lookup"><span data-stu-id="c62bb-109">[Chapter 2](chapter2.md) - gives the basic steps to install and use Azure RTOS TraceX to analyze your application right out of the box.</span></span>
- <span data-ttu-id="c62bb-110">[Rozdział 3](chapter3.md) — opis głównych funkcji usługi Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-110">[Chapter 3](chapter3.md) - describes the main features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="c62bb-111">[Rozdział 4](chapter4.md) — Szczegóły funkcji analizy wydajności usługi Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-111">[Chapter 4](chapter4.md) - details performance analysis features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="c62bb-112">[Rozdział 5](chapter5.md) — opis sposobu konfigurowania usługi Azure RTO ThreadX, platformy Azure RTO FileX i platformy Azure RTO NetX w celu wygenerowania bufora śledzenia, który można wyświetlić w usłudze Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-112">[Chapter 5](chapter5.md) - describes how to set up Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX in order to generate a trace buffer that is viewable by Azure RTOS TraceX.</span></span>
- <span data-ttu-id="c62bb-113">[Rozdział 6](chapter6.md) — szczegółowe omówienie zdarzeń usługi Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-113">[Chapter 6](chapter6.md) - describes Azure RTOS TraceX events in detail.</span></span>
- <span data-ttu-id="c62bb-114">[Rozdział 7](chapter7.md) — szczegółowe omówienie zdarzeń usługi Azure RTO FileX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-114">[Chapter 7](chapter7.md) - describes Azure RTOS FileX events in detail.</span></span>
- <span data-ttu-id="c62bb-115">[Rozdział 8](chapter8.md) — szczegółowe omówienie zdarzeń usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-115">[Chapter 8](chapter8.md) - describes Azure RTOS NetX events in detail.</span></span>
- <span data-ttu-id="c62bb-116">[Rozdział 9](chapter9.md) — szczegółowe omówienie zdarzeń usługi Azure RTO USBX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-116">[Chapter 9](chapter9.md) - describes Azure RTOS USBX events in detail.</span></span>
- <span data-ttu-id="c62bb-117">[Rozdział 10](chapter10.md) — omówienie tworzenia niestandardowych zdarzeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c62bb-117">[Chapter 10](chapter10.md) - describes creating custom user events in detail.</span></span>
- <span data-ttu-id="c62bb-118">[Rozdział 11](chapter11.md) — opisuje szczegóły wewnętrznego buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c62bb-118">[Chapter 11](chapter11.md) - describes the internal trace buffer in detail.</span></span>
- <span data-ttu-id="c62bb-119">[Dodatek A](appendix-a.md) — Azure RTO ThreadX plik specyficzny dla portu ze źródłem sygnatury czasowej do zbierania zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c62bb-119">[Appendix A](appendix-a.md) - Azure RTOS ThreadX port-specific file with its time-stamp source for gathering trace events.</span></span>
- <span data-ttu-id="c62bb-120">[Dodatek B](appendix-b.md) -Azure rto ThreadX *tx_trace. h* , który zawiera szczegółowe informacje dotyczące implementacji buforu śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c62bb-120">[Appendix B](appendix-b.md) - Azure RTOS ThreadX *tx_trace.h* file that shows implementation details regarding the event trace buffer.</span></span>
- <span data-ttu-id="c62bb-121">[Dodatek C](appendix-c.md) — zawiera podsumowanie narzędzi wiersza polecenia do konwertowania różnych formatów plików na odpowiednie pliki binarne usługi Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="c62bb-121">[Appendix C](appendix-c.md) - Summarizes command line utilities for converting various file formats into proper Azure RTOS TraceX binary files.</span></span>
- <span data-ttu-id="c62bb-122">[Dodatek D](appendix-d.md) -przykłady zatopienia plików śledzenia z różnych narzędzi programistycznych.</span><span class="sxs-lookup"><span data-stu-id="c62bb-122">[Appendix D](appendix-d.md) - Examples of dumping trace files from various development tools.</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="c62bb-123">Konwencje przewodnika</span><span class="sxs-lookup"><span data-stu-id="c62bb-123">Guide Conventions</span></span>

<span data-ttu-id="c62bb-124">*Kursywa* — oznacza tytuły książek, wyróżnia ważne słowa i określa zmienne.</span><span class="sxs-lookup"><span data-stu-id="c62bb-124">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="c62bb-125">**Pogrubiona** — kroje liter oznacza nazwy plików, słowa kluczowe i bardziej podkreśla ważne słowa i zmienne.</span><span class="sxs-lookup"><span data-stu-id="c62bb-125">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="c62bb-126">Wskazuje informacje o notatce.</span><span class="sxs-lookup"><span data-stu-id="c62bb-126">Indicates information of note.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="c62bb-127">Centrum pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="c62bb-127">Customer Support Center</span></span>

<span data-ttu-id="c62bb-128">Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków.</span><span class="sxs-lookup"><span data-stu-id="c62bb-128">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="c62bb-129">Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="c62bb-129">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="c62bb-130">Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="c62bb-130">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="c62bb-131">Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.</span><span class="sxs-lookup"><span data-stu-id="c62bb-131">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="c62bb-132">Zawartość ciągu *_tx_version_id* można znaleźć w pliku *tx_port. h* dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="c62bb-132">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="c62bb-133">Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c62bb-133">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="c62bb-134">Zawartość w pamięci RAM *_tx_build_options* zmiennej ulong.</span><span class="sxs-lookup"><span data-stu-id="c62bb-134">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="c62bb-135">Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="c62bb-135">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
