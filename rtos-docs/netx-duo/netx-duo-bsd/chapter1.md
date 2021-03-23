---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo BSD
description: Otoka interfejsu API zgodności gniazda BSD obsługuje niektóre podstawowe wywołania interfejsu API usługi BSD Socket, z pewnymi ograniczeniami i korzysta z podstawowych podstaw platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822063"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="e008b-103">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="e008b-103">Chapter 1 - Introduction to Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="e008b-104">Otoka interfejsu API zgodności gniazda BSD obsługuje niektóre podstawowe wywołania interfejsu API usługi BSD Socket, z pewnymi ograniczeniami i korzysta z podstawowych podstaw platformy Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="e008b-104">The BSD Socket API Compliancy Wrapper supports some of the basic BSD Socket API calls, with some limitations and utilizes Azure RTOS NetX Duo primitives underneath.</span></span>

## <a name="bsd-socket-api-compliancy-wrapper-source"></a><span data-ttu-id="e008b-105">Źródło otoki zgodności interfejsu API usługi BSD Socket</span><span class="sxs-lookup"><span data-stu-id="e008b-105">BSD Socket API Compliancy Wrapper Source</span></span>

<span data-ttu-id="e008b-106">Kod źródłowy otoki został zaprojektowany dla uproszczenia i składa się z dwóch plików, czyli *nxd_bsd. h* i *nxd_bsd. c*.</span><span class="sxs-lookup"><span data-stu-id="e008b-106">The Wrapper source code is designed for simplicity and is comprised of two files, namely *nxd_bsd.h* and *nxd_bsd.c*.</span></span> <span data-ttu-id="e008b-107">Plik *nxd_bsd. h* definiuje wszystkie niezbędne stałe OTOKI interfejsu API usługi BSD Socket oraz prototypy podprocedur, podczas gdy *nxd_bsd. c* zawiera rzeczywisty kod źródłowy zgodności interfejsu API usługi BSD Socket.</span><span class="sxs-lookup"><span data-stu-id="e008b-107">The *nxd_bsd.h* file defines all the necessary BSD Socket API wrapper constants and subroutine prototypes, while *nxd_bsd.c* contains the actual BSD Socket API compatibility source code.</span></span> <span data-ttu-id="e008b-108">Te pliki źródłowe otoki są wspólne dla wszystkich pakietów obsługi NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="e008b-108">These Wrapper source files are common to all NetX Duo support packages.</span></span>

<span data-ttu-id="e008b-109">Pakiet składa się z:</span><span class="sxs-lookup"><span data-stu-id="e008b-109">The package consists of:</span></span>

- <span data-ttu-id="e008b-110">**nxd_bsd. c**: kod źródłowy otoki</span><span class="sxs-lookup"><span data-stu-id="e008b-110">**nxd_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="e008b-111">**nxd_bsd. h**: główny plik nagłówkowy</span><span class="sxs-lookup"><span data-stu-id="e008b-111">**nxd_bsd.h**: Main header file</span></span>

<span data-ttu-id="e008b-112">Przykładowe programy demonstracyjne:</span><span class="sxs-lookup"><span data-stu-id="e008b-112">Sample demo programs:</span></span>

- <span data-ttu-id="e008b-113">**bsd_demo_udp. c**: *Demonstracja z dwoma elementami równorzędnymi UDP (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="e008b-113">**bsd_demo_udp.c**: *Demo with two UDP peers (IPv4 only)*</span></span>
- <span data-ttu-id="e008b-114">**bsd_demo_tcp. c**: *Demonstracja przy użyciu jednego serwera i klienta TCP*</span><span class="sxs-lookup"><span data-stu-id="e008b-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="e008b-115">**bsd_demo_raw. c**: *Demonstracja z dwoma nieprzetworzonymi elementami równorzędnymi*</span><span class="sxs-lookup"><span data-stu-id="e008b-115">**bsd_demo_raw.c**: *Demo with two RAW peers*</span></span>