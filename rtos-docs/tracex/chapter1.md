---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO TraceX
description: Azure RTO TraceX to narzędzie do analizy systemu firmy Microsoft, które wyświetla informacje o zdarzeniu systemowym zebrane przez ThreadX uruchomione w osadzonym miejscu docelowym.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823587"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a><span data-ttu-id="a1b82-103">Rozdział 1 — wprowadzenie do usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="a1b82-103">Chapter 1 - Introduction to Azure RTOS TraceX</span></span>

<span data-ttu-id="a1b82-104">Azure RTO TraceX to narzędzie do analizy systemu firmy Microsoft, które wyświetla informacje o zdarzeniu systemowym zebrane przez ThreadX uruchomione w osadzonym miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="a1b82-104">Azure RTOS TraceX is a Microsoft system analysis tool that displays system event information gathered by ThreadX running on an embedded target.</span></span> <span data-ttu-id="a1b82-105">Użytkownik jest odpowiedzialny za transfer buforu śledzenia przechowywanego w pamięci RAM w osadzonym miejscu docelowym do pliku binarnego na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="a1b82-105">The user is responsible for transferring the trace buffer stored in RAM in the embedded target to a binary file on the host computer.</span></span> <span data-ttu-id="a1b82-106">Następnie użytkownik może otworzyć ten plik za pomocą TraceX i graficznie analizować zdarzenia docelowe, diagnozować problemy z systemem i dostrajać działającą aplikację w celu zwiększenia wydajności i zarządzania zasobami.</span><span class="sxs-lookup"><span data-stu-id="a1b82-106">The user can then open this file with TraceX and graphically analyze the target events, diagnosing system problems and tuning a working application to improve performance and resource management.</span></span>

## <a name="tracex-requirements"></a><span data-ttu-id="a1b82-107">Wymagania TraceX</span><span class="sxs-lookup"><span data-stu-id="a1b82-107">TraceX Requirements</span></span>

<span data-ttu-id="a1b82-108">TraceX wymaga systemu Windows XP (lub nowszego).</span><span class="sxs-lookup"><span data-stu-id="a1b82-108">TraceX requires Windows XP (or above).</span></span> <span data-ttu-id="a1b82-109">System powinien mieć co najmniej 192 MB pamięci RAM, 2 GB dostępnego miejsca na dysku twardym oraz minimalny wyświetlacz o rozmiarze 1024x768 i 256 kolorów.</span><span class="sxs-lookup"><span data-stu-id="a1b82-109">The system should have a minimum of 192 MB of RAM, 2 GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="a1b82-110">Ponadto aplikacja musi działać w systemie ThreadX V 5.0 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="a1b82-110">In addition, the application must be running on ThreadX V5.0 or later.</span></span>

<span data-ttu-id="a1b82-111">TraceX wymaga również zainstalowania platformy Microsoft .NET, którą Instalator TraceX automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a1b82-111">TraceX also requires the Microsoft .NET framework be installed, which the TraceX installer does automatically.</span></span>

## <a name="tracex-constraints"></a><span data-ttu-id="a1b82-112">Ograniczenia TraceX</span><span class="sxs-lookup"><span data-stu-id="a1b82-112">TraceX Constraints</span></span>

<span data-ttu-id="a1b82-113">TraceX ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="a1b82-113">TraceX has the following constraints:</span></span>

- <span data-ttu-id="a1b82-114">Pliki TraceX są ograniczone do maksymalnie 32 768 zdarzeń (około 1 MB).</span><span class="sxs-lookup"><span data-stu-id="a1b82-114">TraceX files are limited to a maximum of 32,768 events (roughly 1 MB ).</span></span>
- <span data-ttu-id="a1b82-115">Źródło sygnatur czasowych musi mieć odpowiednie rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="a1b82-115">The time-stamp source must have reasonable resolution.</span></span> <span data-ttu-id="a1b82-116">Jeśli rozwiązanie jest zbyt niskie, zdarzenia będą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="a1b82-116">If the resolution is too low, the events will overlap.</span></span> <span data-ttu-id="a1b82-117">Jeśli rozwiązanie jest zbyt wysokie, istnieje potencjalne przerwy między zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="a1b82-117">If the resolution is too high, there is potential for long gaps between events.</span></span>
- <span data-ttu-id="a1b82-118">TraceX nie może dokładnie mierzyć interwałów między zdarzeniami większymi niż okres czasomierza.</span><span class="sxs-lookup"><span data-stu-id="a1b82-118">TraceX cannot accurately measure intervals between events greater than the timer period.</span></span>
