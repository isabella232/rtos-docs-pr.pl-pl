---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX BSD
description: Otoka interfejsu API usługi Azure RTO NetX BSD Sockets obsługuje niektóre z podstawowych wywołań interfejsu API protokołu BSD Sockets z pewnymi ograniczeniami i używa elementów podstawowych NetX poniżej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821511"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a><span data-ttu-id="73855-103">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX BSD</span><span class="sxs-lookup"><span data-stu-id="73855-103">Chapter 1 - Introduction to Azure RTOS NetX BSD</span></span>

<span data-ttu-id="73855-104">Otoka zgodności NetX BSD Sockets API obsługuje niektóre z podstawowych wywołań interfejsu API usługi BSD Sockets z pewnymi ograniczeniami i wykorzystuje elementy podstawowe NetX poniżej.</span><span class="sxs-lookup"><span data-stu-id="73855-104">The NetX BSD Sockets API Compliancy Wrapper supports some of the basic BSD Sockets API calls with some limitations and utilizes NetX primitives underneath.</span></span> <span data-ttu-id="73855-105">Ta warstwa zgodności interfejsu API BSD Sockets powinna działać jako Szybka lub nieco szybsza niż typowe implementacje BSD, ponieważ ta otoka korzysta z wewnętrznych NetX podstawowych i pomija sprawdzanie podstawowych błędów NetX.</span><span class="sxs-lookup"><span data-stu-id="73855-105">This BSD Sockets API compatibility layer should perform as fast or slightly faster than typical BSD implementations, since this Wrapper utilizes internal NetX primitives and bypasses basic NetX error checking.</span></span>

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a><span data-ttu-id="73855-106">Źródło otoki zgodności interfejsu API usługi BSD Sockets</span><span class="sxs-lookup"><span data-stu-id="73855-106">BSD Sockets API Compliancy Wrapper Source</span></span>

<span data-ttu-id="73855-107">Kod źródłowy otoki BSD został zaprojektowany dla uproszczenia i składa się tylko z dwóch plików, *nx_bsd. h* i *nx_bsd. c*.</span><span class="sxs-lookup"><span data-stu-id="73855-107">The BSD Wrapper source code is designed for simplicity and is comprised of only two files, *nx_bsd.h* and *nx_bsd.c*.</span></span> <span data-ttu-id="73855-108">Plik *nx_bsd. h* definiuje wszystkie niezbędne stałe OTOKI interfejsu API usługi BSD Sockets oraz prototypy podprocedur, podczas gdy *nx_bsd. c* zawiera rzeczywisty kod źródłowy zgodności interfejsu API usługi BSD Sockets.</span><span class="sxs-lookup"><span data-stu-id="73855-108">The *nx_bsd.h* file defines all the necessary BSD Sockets API Wrapper constants and subroutine prototypes, while *nx_bsd.c* contains the actual BSD Sockets API compatibility source code.</span></span> <span data-ttu-id="73855-109">Te pliki źródłowe otoki BSD są wspólne dla wszystkich pakietów pomocy technicznej NetX.</span><span class="sxs-lookup"><span data-stu-id="73855-109">These BSD Wrapper source files are common to all NetX support packages.</span></span>

<span data-ttu-id="73855-110">Pakiet składa się z:</span><span class="sxs-lookup"><span data-stu-id="73855-110">The package consists of:</span></span>

- <span data-ttu-id="73855-111">**nx_bsd. c**: kod źródłowy otoki</span><span class="sxs-lookup"><span data-stu-id="73855-111">**nx_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="73855-112">**nx_bsd. h**: główny plik nagłówkowy</span><span class="sxs-lookup"><span data-stu-id="73855-112">**nx_bsd.h**: Main header file</span></span>

<span data-ttu-id="73855-113">Przykładowe programy demonstracyjne:</span><span class="sxs-lookup"><span data-stu-id="73855-113">Sample demo programs:</span></span>

- <span data-ttu-id="73855-114">**bsd_demo_tcp. c**: *Demonstracja przy użyciu jednego serwera i klienta TCP*</span><span class="sxs-lookup"><span data-stu-id="73855-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="73855-115">**bsd_demo_udp. c**: *Demonstracja dwóch klientów UDP i serwera UDP*</span><span class="sxs-lookup"><span data-stu-id="73855-115">**bsd_demo_udp.c**: *Demo with two UDP clients and a UDP server*</span></span>
