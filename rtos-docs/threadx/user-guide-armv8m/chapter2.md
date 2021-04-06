---
title: Rozdział 2 — Instalowanie obsługi ThreadX dla ARMv8-M
description: W tym rozdziale wyjaśniono, jak zainstalować i używać kodu źródłowego ThreadX dla architektury ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377593"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a><span data-ttu-id="e4254-103">Rozdział 2 Instalowanie obsługi ThreadX dla ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="e4254-103">Chapter 2  Installing ThreadX support for ARMv8-M</span></span>

<span data-ttu-id="e4254-104">Istnieją dodatkowe pliki kodu źródłowego ThreadX do obsługi architektury ARMv8-M.</span><span class="sxs-lookup"><span data-stu-id="e4254-104">There are additional ThreadX source code files to support the ARMv8-M architecture.</span></span>

<span data-ttu-id="e4254-105">Jeśli ThreadX ma być uruchamiany w trybie zabezpieczonym, te dodatkowe pliki i interfejsy API nie są konieczne.</span><span class="sxs-lookup"><span data-stu-id="e4254-105">If ThreadX is to be run in secure mode, these additional files and APIs are not needed.</span></span> <span data-ttu-id="e4254-106">Aby uruchomić ThreadX w trybie zabezpieczonym, zdefiniuj symbol **TX_SECURE_EXECUTION** w górnej części **_tx_port. h_*_ lub w wierszu polecenia lub w ustawieniach projektu. Upewnij\* się, że TX_SECURE_EXECUTION*\* jest zdefiniowany dla wszystkich plików c i Assembly.</span><span class="sxs-lookup"><span data-stu-id="e4254-106">To run ThreadX in secure mode, define the symbol **TX_SECURE_EXECUTION** at the top of **_tx_port.h_*_ or on the command line or project settings. Ensure _\* TX_SECURE_EXECUTION*\* is defined for all c and assembly files.</span></span> <span data-ttu-id="e4254-107">ThreadX i aplikacja użytkownika zostanie wykonana w trybie zabezpieczonym.</span><span class="sxs-lookup"><span data-stu-id="e4254-107">ThreadX and the user application will execute in secure mode.</span></span>

<span data-ttu-id="e4254-108">Aby uruchomić program ThreadX i aplikację użytkownika w trybie niezabezpieczonym i obsłużyć niezabezpieczone funkcje zabezpieczeń, należy wykonać następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="e4254-108">To run ThreadX and the user application in non-secure mode and support non-secure callable secure functions, please do the following.</span></span>

<span data-ttu-id="e4254-109">Plik ***tx_thread_secure_stack. c*** należy dodać do bezpiecznej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4254-109">The file ***tx_thread_secure_stack.c*** must be added to the secure application.</span></span>

<span data-ttu-id="e4254-110">Do biblioteki ThreadX należy dodać następujące pliki.</span><span class="sxs-lookup"><span data-stu-id="e4254-110">The following files must be added to the ThreadX library.</span></span>

- <span data-ttu-id="e4254-111">***tx_secure_interface. h***</span><span class="sxs-lookup"><span data-stu-id="e4254-111">***tx_secure_interface.h***</span></span>
- <span data-ttu-id="e4254-112">***txe_thread_secure_stack_allocate. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-112">***txe_thread_secure_stack_allocate.c***</span></span>
- <span data-ttu-id="e4254-113">***txe_thread_secure_stack_free. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-113">***txe_thread_secure_stack_free.c***</span></span>
- <span data-ttu-id="e4254-114">***tx_thread_secure_stack_allocate. s***</span><span class="sxs-lookup"><span data-stu-id="e4254-114">***tx_thread_secure_stack_allocate.s***</span></span>
- <span data-ttu-id="e4254-115">***tx_thread_secure_stack_free. s***</span><span class="sxs-lookup"><span data-stu-id="e4254-115">***tx_thread_secure_stack_free.s***</span></span>

<span data-ttu-id="e4254-116">Poniższe dwa pliki zastępują pliki ogólne w bibliotece ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e4254-116">The following two files replace the generic files in the ThreadX library.</span></span>

- <span data-ttu-id="e4254-117">***tx_thread_stack_error_handler. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-117">***tx_thread_stack_error_handler.c***</span></span>
- <span data-ttu-id="e4254-118">***tx_thread_stack_error_notify. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-118">***tx_thread_stack_error_notify.c***</span></span>

## <a name="additional-threadx-sources-for-armv8-m"></a><span data-ttu-id="e4254-119">Dodatkowe źródła ThreadX dla ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="e4254-119">Additional ThreadX Sources for ARMv8-M</span></span>

<span data-ttu-id="e4254-120">Dodatkowe pliki ThreadX dla architektury ARMv8-M TrustZone zostały opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="e4254-120">The additional ThreadX files for the ARMv8-M TrustZone architecture are described below.</span></span>

  | <span data-ttu-id="e4254-121">**Nazwa pliku**</span><span class="sxs-lookup"><span data-stu-id="e4254-121">**File Name**</span></span>                            | <span data-ttu-id="e4254-122">**Zawartość**</span><span class="sxs-lookup"><span data-stu-id="e4254-122">**Contents**</span></span>                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | <span data-ttu-id="e4254-123">***tx_secure_interface. h***</span><span class="sxs-lookup"><span data-stu-id="e4254-123">***tx_secure_interface.h***</span></span>              | <span data-ttu-id="e4254-124">Plik dołączany, który definiuje funkcje, które nie są bezpiecznie wywoływane ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e4254-124">Include file that defines the ThreadX non-secure callable functions.</span></span> |
  | <span data-ttu-id="e4254-125">***txe_thread_secure_stack_allocate. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-125">***txe_thread_secure_stack_allocate.c***</span></span> |  <span data-ttu-id="e4254-126">Sprawdzanie błędów pliku dla interfejsu API alokacji bezpiecznego stosu.</span><span class="sxs-lookup"><span data-stu-id="e4254-126">Error-checking file for the secure stack allocate API.</span></span> |
  | <span data-ttu-id="e4254-127">***txe_thread_secure_stack_free. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-127">***txe_thread_secure_stack_free.c***</span></span>     |  <span data-ttu-id="e4254-128">Sprawdzanie błędów pliku dla bezpłatnego interfejsu API bezpiecznego stosu.</span><span class="sxs-lookup"><span data-stu-id="e4254-128">Error-checking file for the secure stack free API.</span></span> |
  | <span data-ttu-id="e4254-129">***tx_thread_secure_stack_allocate. s***</span><span class="sxs-lookup"><span data-stu-id="e4254-129">***tx_thread_secure_stack_allocate.s***</span></span>  |  <span data-ttu-id="e4254-130">Niezabezpieczona Veneer dla usługi alokacji bezpiecznego stosu.</span><span class="sxs-lookup"><span data-stu-id="e4254-130">Non-secure veneer for the secure stack allocate service.</span></span> |
  | <span data-ttu-id="e4254-131">***tx_thread_secure_stack_free. s***</span><span class="sxs-lookup"><span data-stu-id="e4254-131">***tx_thread_secure_stack_free.s***</span></span>      |  <span data-ttu-id="e4254-132">Niezabezpieczona Veneer dla bezpłatnej usługi bezpiecznego stosu.</span><span class="sxs-lookup"><span data-stu-id="e4254-132">Non-secure veneer for the secure stack free service.</span></span> |
  | <span data-ttu-id="e4254-133">***tx_thread_stack_error_handler. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-133">***tx_thread_stack_error_handler.c***</span></span>    |  <span data-ttu-id="e4254-134">Procedura obsługi błędów stosu wątków.</span><span class="sxs-lookup"><span data-stu-id="e4254-134">Handler for thread stack errors.</span></span> |
  | <span data-ttu-id="e4254-135">***tx_thread_stack_error_notify. c***</span><span class="sxs-lookup"><span data-stu-id="e4254-135">***tx_thread_stack_error_notify.c***</span></span>     |  <span data-ttu-id="e4254-136">Zarejestruj wywołanie zwrotne powiadomienia, aby obsłużyć błędy stosu wątków.</span><span class="sxs-lookup"><span data-stu-id="e4254-136">Register notification callback for handling thread stack errors.</span></span> |
