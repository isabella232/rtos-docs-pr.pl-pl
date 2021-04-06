---
title: Rozdział 1 — wprowadzenie do zestawu profilów wykonywania
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO ThreadX Execution profile Kit (EPK).
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30676437535229ad5bdbca10dcc9ca009d6e74
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377653"
---
# <a name="chapter-1--introduction-to-the-execution-profile-kit"></a><span data-ttu-id="ab0c1-103">Rozdział 1 wprowadzenie do zestawu profilów wykonywania</span><span class="sxs-lookup"><span data-stu-id="ab0c1-103">Chapter 1  Introduction to the Execution Profile Kit</span></span>

<span data-ttu-id="ab0c1-104">Zestaw profilów wykonywania ThreadX (EPK) oferuje infrastrukturę aplikacji do dynamicznego śledzenia czasu wykonywania wątków, procedur usługi przerwania (procedury ISR) i bezczynnych warunków systemu.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-104">The ThreadX Execution Profile Kit (EPK) provides an infrastructure for applications to dynamically track execution time for threads, Interrupt Service Routines (ISRs), and idle system conditions.</span></span> <span data-ttu-id="ab0c1-105">Jest to szczególnie przydatne w przypadku optymalizacji i dostrajania aplikacji pod kątem maksymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-105">This is especially useful for optimization and tuning the application for maximum performance.</span></span> <span data-ttu-id="ab0c1-106">Jest to jednak również cenna pomoc w debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-106">However, it is also a valuable debug aid.</span></span>

<span data-ttu-id="ab0c1-107">EPK zależy od \" punktów zaczepienia \" wbudowanych w logikę planowania ThreadX w kodzie zestawu, który jest wywoływany przy wpisie wątku, zamknięciu wątku, wpisie ISR i wyjściu do procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-107">The EPK relies on \"hooks\" built into the ThreadX scheduling logic in assembly code that are called on thread entry, thread exit, ISR entry, and ISR exit.</span></span> <span data-ttu-id="ab0c1-108">Procedury EPK obliczają czas między takimi zdarzeniami i przechowują czas Delta w zmiennych globalnych, jak również elementy członkowskie bloku sterowania **TX_THREAD** .</span><span class="sxs-lookup"><span data-stu-id="ab0c1-108">The EPK routines calculate the time in between such events and store the delta time in global variables as well as members of the **TX_THREAD** control block.</span></span>

> [!NOTE]
> <span data-ttu-id="ab0c1-109">*Deweloper może modyfikować lub nawet zamieniać te funkcje haka na własne, aby przełączać numery PIN we/wy w celu zapewnienia widoczności sprzętowej działającej aplikacji ThreadX*.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-109">*The developer is free to modify or even replace these hook functions with their own logic to toggle I/O pins in order to provide hardware visibility to a running ThreadX application*.</span></span>

## 

## <a name="epk-requirements"></a><span data-ttu-id="ab0c1-110">Wymagania EPK</span><span class="sxs-lookup"><span data-stu-id="ab0c1-110">EPK Requirements</span></span>

<span data-ttu-id="ab0c1-111">EPK wymaga ThreadX 6,0 (lub więcej) do działania.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-111">The EPK requires ThreadX 6.0 (or above) in order to operate.</span></span> <span data-ttu-id="ab0c1-112">EPK wymaga również \" rozsądnej \" rozdzielczości, zwiększając czas sprzętowy źródła.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-112">The EPK also requires a \"reasonable\" resolution, incrementing hardware time source.</span></span> <span data-ttu-id="ab0c1-113">Najbardziej rozsądne rozwiązanie zwykle będzie coś w skali mikrosekundowych.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-113">The most reasonable resolution would typically be something on a microsecond scale.</span></span> <span data-ttu-id="ab0c1-114">Jeśli rozwiązanie jest zbyt duże, liczniki EPK będą zbyt szybko maksymalne.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-114">If the resolution is too great, the EPK counters will max out too quickly.</span></span> <span data-ttu-id="ab0c1-115">Z drugiej strony, jeśli rozwiązanie jest zbyt małe, dokładne chronometraże nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-115">Conversely, if the resolution is too small, accurate timing is not possible.</span></span> <span data-ttu-id="ab0c1-116">Źródło czasu aplikacji jest zdefiniowane w \***tx_execution_profile. h** _ przez makro _ \* TX_EXECUTION_TIME_SOURCE \* \*.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-116">The application time source is defined in ***tx_execution_profile.h** _ by the macro _*TX_EXECUTION_TIME_SOURCE\*\*.</span></span>

<span data-ttu-id="ab0c1-117">Kompilator języka C musi obsługiwać typ \" unsigned long long \" for unsigned 64-bit Total Counters.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-117">The C compiler must support the type \"unsigned long long\" for unsigned 64-bit total counters.</span></span> <span data-ttu-id="ab0c1-118">Ponadto EPK zakłada, że zmienne globalne są inicjowane przez kod uruchamiania kompilatora w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-118">Furthermore, the EPK assumes the global variables are initialized by the compiler run-time startup code.</span></span> <span data-ttu-id="ab0c1-119">Jeśli tak się nie dzieje, zmienne globalne zdefiniowane w ***tx_execution_profile. c*** muszą być zainicjowane do 0 przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-119">If this is not the case, the global variables defined in ***tx_execution_profile.c*** must be initialized to 0 by the application.</span></span>

## <a name="epk-installation"></a><span data-ttu-id="ab0c1-120">Instalacja EPK</span><span class="sxs-lookup"><span data-stu-id="ab0c1-120">EPK Installation</span></span>

<span data-ttu-id="ab0c1-121">Aby zainstalować ThreadX EPK, wykonaj poniższe kroki i ponownie skompiluj całą bibliotekę ThreadX i aplikację.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-121">To install the ThreadX EPK, follow the steps below and rebuild the entire ThreadX library and application.</span></span>

1. <span data-ttu-id="ab0c1-122">Uwzględnij pliki źródłowe EPK (***tx_execution_profile. h** _ i _*_tx_execution_profile. c_\*_) w projekcie kompilacji biblioteki ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-122">Include the EPK source files (***tx_execution_profile.h** _ and _*_tx_execution_profile.c_\*_) in your ThreadX library build project.</span></span> <span data-ttu-id="ab0c1-123">Te pliki mogą znajdować się w [repozytorium usługi Azure RTO ThreadX](<https://github.com/azure-rtos/threadx>) w folderze _ \*_Utility/Execution_Profile_\*\*).</span><span class="sxs-lookup"><span data-stu-id="ab0c1-123">These files can be in the [Azure RTOS ThreadX repo](<https://github.com/azure-rtos/threadx>) under the _ *_utility/Execution_Profile_*\* folder).</span></span>

1. <span data-ttu-id="ab0c1-124">W ***tx_port. h** _ Zdefiniuj makro _ *TX_THREAD_EXTENSION_3** w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-124">In ***tx_port.h** _, define the _ *TX_THREAD_EXTENSION_3** macro as follows.</span></span>
```
    #define TX_THREAD_EXTENSION_3 unsigned long long tx_thread_execution_time_total; \
    unsigned long tx_thread_execution_time_last_start;
```

3. <span data-ttu-id="ab0c1-125">Zdefiniuj makro **TX_EXECUTION_TIME_SOURCE** w **_tx_execution_profile. h_** , aby mapować do źródła czasu sprzętowego.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-125">Define the **TX_EXECUTION_TIME_SOURCE** macro in **_tx_execution_profile.h_** to map to your hardware time source.</span></span>

1. <span data-ttu-id="ab0c1-126">Upewnij się, że środowisko kompilacji definiuje **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** , dzięki czemu punkty zaczepienia planowania są wywoływane z kodu zestawu ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-126">Ensure that the build environment defines **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** so that the scheduling hooks are called from the ThreadX assembly code.</span></span>

1. <span data-ttu-id="ab0c1-127">Jeśli chcesz użyć 64-bitowego źródła czasu, przejrzyj plik ***tx_execution_profile. h*** , aby uzyskać instrukcje dotyczące sposobu jego wykonania.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-127">If you wish to use 64-bit time source, please review the ***tx_execution_profile.h*** file for instructions on how to accomplish this.</span></span>

1. <span data-ttu-id="ab0c1-128">Skompiluj ponownie całą bibliotekę i aplikację, tak aby wszystkie te opcje zostały prawidłowo skompilowane.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-128">Rebuild the entire library and application so that all of these options are properly compiled-in.</span></span>

<span data-ttu-id="ab0c1-129">Teraz możesz przystąpić do używania EPK z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-129">You are now ready to use EPK with your application.</span></span>

##  <a name="epk-example"></a><span data-ttu-id="ab0c1-130">Przykład EPK</span><span class="sxs-lookup"><span data-stu-id="ab0c1-130">EPK Example</span></span> 

<span data-ttu-id="ab0c1-131">Poniżej znajduje się przykład EPK używany w standardowej demonstracji ThreadX skonfigurowany przy użyciu 32-bitowego źródła czasomierza, które zwiększa 7,2 razy na mikrosekundowych.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-131">The following is an example of EPK being used on a standard ThreadX demonstration, configured with a 32-bit timer source that increments 7.2 times per microsecond.</span></span> 

<span data-ttu-id="ab0c1-132">Makro **TX_EXECUTION_TIME_SOURCE** zostało zdefiniowane w celu pobrania rejestru czasomierza zamapowanego na pamięć w 0xE0001004, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-132">The **TX_EXECUTION_TIME_SOURCE** macro is defined to pick up the memory-mapped timer register at 0xE0001004, as follows.</span></span>
```
(EXECUTION_TIME_SOURCE_TYPE) \*((ULONG \*) 0xE0001004)
```

<span data-ttu-id="ab0c1-133">Umożliwienie pokazania przebiegu przez pięć sekund daje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-133">Letting the demonstration run for five seconds yields the following results.</span></span>

![Wyniki umożliwiające uruchomienie demonstracji.](media/demo_results.png)

<span data-ttu-id="ab0c1-135">Ponieważ standardowa Demonstracja ThreadX nie ma czasu bezczynności (wątki 1 i 2 działają w sposób ciągły), EPK prawidłowo zgłasza zero jako czas bezczynności.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-135">Since the standard ThreadX demonstration has no idle time (threads 1 and 2 run continuously), the EPK correctly reports zero for idle time.</span></span> <span data-ttu-id="ab0c1-136">Łączny czas i wartości wątku ISR mogą być podzielone przez 7,2 w celu uzyskania mikrosekund dla każdej kategorii wykonania.</span><span class="sxs-lookup"><span data-stu-id="ab0c1-136">The ISR total time and thread values may be divided by 7.2 in order to derive the microseconds for each execution category.</span></span> <span data-ttu-id="ab0c1-137">EPK udostępnia również interfejsy API umożliwiające dostęp do tych informacji (zobacz [rozdział 2](chapter2.md)).</span><span class="sxs-lookup"><span data-stu-id="ab0c1-137">The EPK also provides APIs to access this information (please see please see [Chapter 2](chapter2.md)).</span></span>