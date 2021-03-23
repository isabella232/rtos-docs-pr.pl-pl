---
title: Rozdział 2 — wymagania dotyczące modułów
description: Ten artykuł zawiera opis wymagań dotyczących kompilowania modułu ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32288d78ceffb74ab088a1d720dbac657f6d3ed4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821397"
---
# <a name="chapter-2---module-requirements"></a><span data-ttu-id="d71ec-103">Rozdział 2 — wymagania dotyczące modułów</span><span class="sxs-lookup"><span data-stu-id="d71ec-103">Chapter 2 - Module requirements</span></span>

<span data-ttu-id="d71ec-104">Moduł ThreadX zawiera preambułę, która definiuje podstawowe cechy modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-104">A ThreadX Module contains a preamble, which defines the basic characteristics of the module.</span></span> <span data-ttu-id="d71ec-105">Po preambule następuje obszar instrukcji modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-105">The preamble is followed by the instruction area of the module.</span></span> <span data-ttu-id="d71ec-106">Moduły mogą być wykonywane w miejscu lub mogą być ładowane do obszaru pamięci modułu przez Menedżera modułów przed wykonaniem.</span><span class="sxs-lookup"><span data-stu-id="d71ec-106">Modules may be executed in place or they may be loaded into the module memory area by the Module Manager prior to execution.</span></span> <span data-ttu-id="d71ec-107">Jedyny wymóg polega na tym, że Preambuła zawsze znajduje się na pierwszym adresie modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-107">The only requirement is that the preamble is always located at the first address of the module.</span></span> <span data-ttu-id="d71ec-108">Rysunek 2 ilustruje podstawowy układ modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-108">Figure 2 illustrates a basic module layout.</span></span>

| <span data-ttu-id="d71ec-109">Układ modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-109">Module Layout</span></span> |
|:---:|
| <span data-ttu-id="d71ec-110">\[Preambuła modułu\]</span><span class="sxs-lookup"><span data-stu-id="d71ec-110">\[module preamble\]</span></span>         |
| <span data-ttu-id="d71ec-111">\[obszar instrukcji modułu\]</span><span class="sxs-lookup"><span data-stu-id="d71ec-111">\[module instruction area\]</span></span> |
| <span data-ttu-id="d71ec-112">\[obszar pamięci RAM modułu\]</span><span class="sxs-lookup"><span data-stu-id="d71ec-112">\[module RAM area\]</span></span>         |

<span data-ttu-id="d71ec-113">**Rysunek 2** — układ modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-113">**Figure 2** - Module Layout</span></span>

> [!NOTE]
> <span data-ttu-id="d71ec-114">Moduły muszą być kompilowane przy użyciu odpowiednich kodów niezależnych od pozycji i kompilatora danych/konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="d71ec-114">Modules must be built with the appropriate position independent code and data compiler/linker options.</span></span> <span data-ttu-id="d71ec-115">Dzięki temu można wykonać moduł w dowolnym obszarze pamięci.</span><span class="sxs-lookup"><span data-stu-id="d71ec-115">This enables execution of the module in any memory area.</span></span>

<span data-ttu-id="d71ec-116">Po utworzeniu wątku modułu zostaje przypisana druga przestrzeń stosu do użycia, gdy wątek znajduje się w jądrze chronionym w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d71ec-116">When a Module thread is created, a second stack space is allocated for use when the thread is in the memory-protected kernel.</span></span> <span data-ttu-id="d71ec-117">Rozmiar obszaru stosu jądra wątku jest konfigurowalny przez użytkownika przy użyciu **TXM_MODULE_KERNEL_STACK_SIZE** w **_txm_module_port. h_*_. Pozwala to na użycie mniejszego rozmiaru stosu podczas tworzenia wątku modułu, ponieważ stos określony przez użytkownika podczas wywoływania _*_tx_thread_create_** jest używany tylko w module.</span><span class="sxs-lookup"><span data-stu-id="d71ec-117">The size of the thread's kernel stack space is user-configurable using **TXM_MODULE_KERNEL_STACK_SIZE** in **_txm_module_port.h_*_. This allows a smaller stack size to be used when creating a Module thread, as the stack specified by the user when calling _*_tx_thread_create_** is only used in the module.</span></span>

> [!NOTE]
> <span data-ttu-id="d71ec-118">Góra stosu wątków modułu zawiera strukturę informacji o wpisie wątku (**TXM_MODULE_THREAD_ENTRY_INFO**), dzięki czemu rozmiar dostępnego stosu jest zmniejszany o rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="d71ec-118">The top of a module thread stack contains the thread entry information structure (**TXM_MODULE_THREAD_ENTRY_INFO**), so the available stack size is decreased by the size of this structure.</span></span> <span data-ttu-id="d71ec-119">Podczas tworzenia wątku w module należy zwiększyć jego rozmiar stosu, co najmniej ten rozmiar tej struktury.</span><span class="sxs-lookup"><span data-stu-id="d71ec-119">When creating a thread in a module, increase its stack size by at least this the size of this structure.</span></span>

<span data-ttu-id="d71ec-120">Poniższe kroki są wymagane do utworzenia i skompilowania modułu ThreadX (każdy krok został szczegółowo opisany poniżej).</span><span class="sxs-lookup"><span data-stu-id="d71ec-120">The following steps are required for creating and building a ThreadX Module (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="d71ec-121">Wszystkie pliki C w module muszą #define **TXM_MODULE** przed dołączeniem **_txm_module. h_**.</span><span class="sxs-lookup"><span data-stu-id="d71ec-121">All C files in a module must #define **TXM_MODULE** prior to including **_txm_module.h_**.</span></span> <span data-ttu-id="d71ec-122">Można to osiągnąć w pliku źródłowym kompilowanym lub w ramach ustawień projektu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-122">This can be accomplished in the source file being compiled or as part of the project settings.</span></span> <span data-ttu-id="d71ec-123">W ten sposób ponownie mapuje wywołania interfejsu API ThreadX do wersji interfejsu API specyficznej dla modułu, która wywołuje funkcję wysyłania w Menedżerze modułu rezydentnego w celu wykonania wywołania do rzeczywistej funkcji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="d71ec-123">Doing so remaps the ThreadX API calls to the module-specific version of the API that invokes the dispatch function in the resident Module Manager to perform the call to the actual API function.</span></span>
2. <span data-ttu-id="d71ec-124">Każdy moduł musi mieć preambułę według pierwszego adresu obszaru instrukcji, który definiuje cechy i wymagania dotyczące zasobów modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-124">Each module must have a preamble at its first instruction area address which defines the characteristics and the resource needs of the module.</span></span>
3. <span data-ttu-id="d71ec-125">Każdy moduł musi połączyć preambułę na początku obszaru instrukcji modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-125">Each module must link the preamble at the beginning of the module instruction area.</span></span>
4. <span data-ttu-id="d71ec-126">Każdy moduł musi łączyć się z biblioteką modułu (***TXM. a***), która zawiera funkcje specyficzne dla modułu używane do współpracy z ThreadX.</span><span class="sxs-lookup"><span data-stu-id="d71ec-126">Each module must link against a module library (***txm.a***), which contains module-specific functions used to interact with ThreadX.</span></span>

## <a name="module-sources"></a><span data-ttu-id="d71ec-127">Źródła modułów</span><span class="sxs-lookup"><span data-stu-id="d71ec-127">Module sources</span></span>

<span data-ttu-id="d71ec-128">Moduły ThreadX mają własny zestaw plików źródłowych, które zostały zaprojektowane tak, aby były połączone i znajdować się bezpośrednio z kodem źródłowym modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-128">ThreadX Modules have their own set of source files that are designed to be linked and located directly with the module source code.</span></span> <span data-ttu-id="d71ec-129">Te pliki zapewniają mostek między oddzielnym modułem i menedżerem rezydentów modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-129">These files provide the bridge between the separate module and resident Module Manager.</span></span> <span data-ttu-id="d71ec-130">Pliki modułów są następujące.</span><span class="sxs-lookup"><span data-stu-id="d71ec-130">The Module files are as follows.</span></span>

| <span data-ttu-id="d71ec-131">Nazwa pliku</span><span class="sxs-lookup"><span data-stu-id="d71ec-131">File Name</span></span> | <span data-ttu-id="d71ec-132">Zawartość</span><span class="sxs-lookup"><span data-stu-id="d71ec-132">Contents</span></span> |
|---|---|
| <span data-ttu-id="d71ec-133">**txm_module. h**</span><span class="sxs-lookup"><span data-stu-id="d71ec-133">**txm_module.h**</span></span> | <span data-ttu-id="d71ec-134">Plik dołączany, który definiuje informacje o module.</span><span class="sxs-lookup"><span data-stu-id="d71ec-134">Include file that defines module information.</span></span> |
| <span data-ttu-id="d71ec-135">**txm_module_port. h**</span><span class="sxs-lookup"><span data-stu-id="d71ec-135">**txm_module_port.h**</span></span> | <span data-ttu-id="d71ec-136">Plik dołączany, który definiuje informacje o module specyficznym dla portów.</span><span class="sxs-lookup"><span data-stu-id="d71ec-136">Include file that defines port-specific module information.</span></span> |
| <span data-ttu-id="d71ec-137">**txm_module_user. h**</span><span class="sxs-lookup"><span data-stu-id="d71ec-137">**txm_module_user.h**</span></span> | <span data-ttu-id="d71ec-138">Definiuje i wartości, które użytkownik może dostosować.</span><span class="sxs-lookup"><span data-stu-id="d71ec-138">Defines and values the user can customize.</span></span> |
| <span data-ttu-id="d71ec-139">**txm_module_initialize. s [1] [3]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-139">**txm_module_initialize.s [1][3]**</span></span> | <span data-ttu-id="d71ec-140">Wywołuje funkcje wewnętrzne do modułu uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d71ec-140">Calls intrinsic functions to startup module.</span></span> |
| <span data-ttu-id="d71ec-141">**txm_module_preamble. \{ s/S/68\}**</span><span class="sxs-lookup"><span data-stu-id="d71ec-141">**txm_module_preamble.\{s/S/68\}**</span></span> | <span data-ttu-id="d71ec-142">Plik zestawu preambuły modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-142">Module preamble assembly file.</span></span> <span data-ttu-id="d71ec-143">Ten plik definiuje różne atrybuty specyficzne dla modułu i jest połączony z kodem aplikacji modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-143">This file defines various module-specific attributes and is linked with the module application code.</span></span> |
| <span data-ttu-id="d71ec-144">**txm_module_application_request. c [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-144">**txm_module_application_request.c [1]**</span></span> | <span data-ttu-id="d71ec-145">Funkcja żądania aplikacji modułu wysyła do kodu rezydentnego żądanie specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d71ec-145">Module application request function sends an application-specific request to the resident code.</span></span> |
| <span data-ttu-id="d71ec-146">**txm_module_callback_request_thread_entry. c &nbsp; [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-146">**txm_module_callback_request_thread_entry.c&nbsp;[1]**</span></span> | <span data-ttu-id="d71ec-147">Wątek wywołania zwrotnego modułu, który jest odpowiedzialny za przetwarzanie wywołań zwrotnych żądanych przez moduł, w tym czasomierzy i wywołania zwrotne powiadomień.</span><span class="sxs-lookup"><span data-stu-id="d71ec-147">Module callback thread that is responsible for processing callbacks requested by the module, including timers and notification callbacks.</span></span> |
| <span data-ttu-id="d71ec-148">\**txm_ *. c [1] [2]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-148">**txm_\*.c [1][2]**</span></span> | <span data-ttu-id="d71ec-149">Standardowe usługi interfejsu API ThreadX, które wywołują dyspozytora jądra.</span><span class="sxs-lookup"><span data-stu-id="d71ec-149">The standard ThreadX API services, these call the kernel dispatcher.</span></span>
| <span data-ttu-id="d71ec-150">**txm_module_object_allocate. c [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-150">**txm_module_object_allocate.c [1]**</span></span> | <span data-ttu-id="d71ec-151">Funkcja modułu służąca do przydzielania pamięci dla obiektów modułów znajdujących się w puli pamięci Menedżera.</span><span class="sxs-lookup"><span data-stu-id="d71ec-151">Module function to allocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="d71ec-152">**txm_module_object_deallocate. c [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-152">**txm_module_object_deallocate.c [1]**</span></span> | <span data-ttu-id="d71ec-153">Funkcja modułu służąca do cofania alokacji pamięci dla obiektów modułów znajdujących się w puli pamięci Menedżera.</span><span class="sxs-lookup"><span data-stu-id="d71ec-153">Module function to deallocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="d71ec-154">**txm_module_object_pointer_get. c [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-154">**txm_module_object_pointer_get.c [1]**</span></span> | <span data-ttu-id="d71ec-155">Funkcja modułu do pobierania wskaźnika do obiektu systemowego.</span><span class="sxs-lookup"><span data-stu-id="d71ec-155">Module function to retrieve a pointer to a system object.</span></span> |
| <span data-ttu-id="d71ec-156">**txm_module_object_pointer_get_extended. c [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-156">**txm_module_object_pointer_get_extended.c [1]**</span></span> | <span data-ttu-id="d71ec-157">Funkcja modułu służąca do pobierania wskaźnika do obiektu systemowego, o długości nazwy.</span><span class="sxs-lookup"><span data-stu-id="d71ec-157">Module function to retrieve a pointer to a system object, name length safety.</span></span> |
| <span data-ttu-id="d71ec-158">**txm_module_thread_shell_entry. c [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-158">**txm_module_thread_shell_entry.c [1]**</span></span> | <span data-ttu-id="d71ec-159">Funkcja wprowadzania wątku modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-159">Module thread entry function.</span></span> |
| <span data-ttu-id="d71ec-160">**txm_module_thread_system_suspend. c [1]**</span><span class="sxs-lookup"><span data-stu-id="d71ec-160">**txm_module_thread_system_suspend.c [1]**</span></span> | <span data-ttu-id="d71ec-161">Funkcja modułu służąca do wstrzymywania wątku.</span><span class="sxs-lookup"><span data-stu-id="d71ec-161">Module function to suspend a thread.</span></span> |

<span data-ttu-id="d71ec-162">**[1]** znajduje się w bibliotece **_TXM. a_**.</span><span class="sxs-lookup"><span data-stu-id="d71ec-162">**[1]** Located in library **_txm.a_**.</span></span>

<span data-ttu-id="d71ec-163">**[2]** te pliki mają taką samą nazwę jak pliki interfejsu API ThreadX, z prefiksem **txm_** , a nie prefiksem **TX_** .</span><span class="sxs-lookup"><span data-stu-id="d71ec-163">**[2]** These files have the same name as the ThreadX API files, with **txm_** prefix instead of **tx_** prefix.</span></span>

<span data-ttu-id="d71ec-164">**[3]** plik **txm_module_initialize. s** jest tylko dla portów korzystających z narzędzi ARM.</span><span class="sxs-lookup"><span data-stu-id="d71ec-164">**[3]** The **txm_module_initialize.s** file is only for ports using ARM tools.</span></span>

## <a name="module-preamble"></a><span data-ttu-id="d71ec-165">Preambuła modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-165">Module preamble</span></span>

<span data-ttu-id="d71ec-166">Preambuła modułu definiuje charakterystyki i zasoby modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-166">The Module Preamble defines characteristics and resources of the module.</span></span> <span data-ttu-id="d71ec-167">Informacje, takie jak początkowa funkcja wprowadzania wątku i początkowy obszar pamięci skojarzony z wątkiem, są zdefiniowane w preambule.</span><span class="sxs-lookup"><span data-stu-id="d71ec-167">Information such as the initial thread entry function and the initial memory area associated with the thread are defined in the preamble.</span></span> <span data-ttu-id="d71ec-168">Przykłady z preambuły specyficzne dla portów znajdują się w [dodatku](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="d71ec-168">Port-specific preamble examples are in the [appendix](appendix.md).</span></span> <span data-ttu-id="d71ec-169">Rysunek 3 przedstawia przykład preambuły modułu ThreadX dla ogólnego celu (wiersze zaczynające się od \* są wartościami zwykle modyfikowanymi przez aplikację):</span><span class="sxs-lookup"><span data-stu-id="d71ec-169">Figure 3 shows an example ThreadX module preamble for a generic target (the lines starting with \* are values typically modified by the application):</span></span>

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

<span data-ttu-id="d71ec-170">**Rysunek 3**</span><span class="sxs-lookup"><span data-stu-id="d71ec-170">**Figure 3**</span></span>

<span data-ttu-id="d71ec-171">W większości przypadków Deweloper musi definiować tylko wątek początkowy (offset 0x1C), identyfikator modułu (offset 0x10), priorytet uruchamiania/zatrzymywania wątku (offset 0x24) i początkowy/zatrzymany rozmiar stosu wątku (offset 0x28).</span><span class="sxs-lookup"><span data-stu-id="d71ec-171">In most cases, the developer only needs to define the module's starting thread (offset 0x1C), module ID (offset 0x10), start/stop thread priority (offset 0x24), and start/stop thread stack size (offset 0x28).</span></span> <span data-ttu-id="d71ec-172">Powyższa prezentacja jest skonfigurowana w taki sposób, że początkowy wątek modułu to ***demo_module_start** _, identyfikator modułu to _*_0x12345678 również_*_, a wątek początkowy ma priorytet _*_1_*_, a rozmiar stosu wynoszący _ *_2048_** b.</span><span class="sxs-lookup"><span data-stu-id="d71ec-172">The demonstration above is set up such that the starting thread of the module is ***demo_module_start** _, the module ID is _*_0x12345678_*_, and the starting thread has a priority of _*_1_*_, and a stack size of _ *_2048_** bytes.</span></span>

<span data-ttu-id="d71ec-173">Niektóre aplikacje mogą opcjonalnie definiować wątek zatrzymania, który jest wykonywany, gdy Menedżer modułów zatrzymuje moduł.</span><span class="sxs-lookup"><span data-stu-id="d71ec-173">Some applications may optionally define a stopping thread, which is executed as the Module Manager stops the module.</span></span> <span data-ttu-id="d71ec-174">Ponadto niektóre aplikacje mogą korzystać z pola właściwości modułu zdefiniowanego w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d71ec-174">In addition, some applications might utilize the Module Properties field, defined as follows.</span></span>

## <a name="module-properties-bit-map"></a><span data-ttu-id="d71ec-175">Mapa bitów właściwości modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-175">Module properties bit map</span></span>

<span data-ttu-id="d71ec-176">W poniższej tabeli przedstawiono przykład mapy bitowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d71ec-176">The table below shows an example of the properties bit map.</span></span> <span data-ttu-id="d71ec-177">Mapy bitowe właściwości specyficzne dla portów znajdują się w [dodatku](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="d71ec-177">Port-specific properties bitmaps are in the [appendix](appendix.md).</span></span>

| <span data-ttu-id="d71ec-178">Bit</span><span class="sxs-lookup"><span data-stu-id="d71ec-178">Bit</span></span> | <span data-ttu-id="d71ec-179">Wartość</span><span class="sxs-lookup"><span data-stu-id="d71ec-179">Value</span></span> | <span data-ttu-id="d71ec-180">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="d71ec-180">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="d71ec-181">0</span><span class="sxs-lookup"><span data-stu-id="d71ec-181">0</span></span> | <span data-ttu-id="d71ec-182">0</span><span class="sxs-lookup"><span data-stu-id="d71ec-182">0</span></span><br /><span data-ttu-id="d71ec-183">1</span><span class="sxs-lookup"><span data-stu-id="d71ec-183">1</span></span> | <span data-ttu-id="d71ec-184">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="d71ec-184">Privileged mode execution</span></span><br /><span data-ttu-id="d71ec-185">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="d71ec-185">User mode execution</span></span> |
| <span data-ttu-id="d71ec-186">1</span><span class="sxs-lookup"><span data-stu-id="d71ec-186">1</span></span> | <span data-ttu-id="d71ec-187">0</span><span class="sxs-lookup"><span data-stu-id="d71ec-187">0</span></span><br /><span data-ttu-id="d71ec-188">1</span><span class="sxs-lookup"><span data-stu-id="d71ec-188">1</span></span> | <span data-ttu-id="d71ec-189">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="d71ec-189">No MPU protection</span></span><br /><span data-ttu-id="d71ec-190">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="d71ec-190">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="d71ec-191">2</span><span class="sxs-lookup"><span data-stu-id="d71ec-191">2</span></span> | <span data-ttu-id="d71ec-192">0</span><span class="sxs-lookup"><span data-stu-id="d71ec-192">0</span></span><br /><span data-ttu-id="d71ec-193">1</span><span class="sxs-lookup"><span data-stu-id="d71ec-193">1</span></span> | <span data-ttu-id="d71ec-194">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="d71ec-194">Disable shared/external memory access</span></span><br /><span data-ttu-id="d71ec-195">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="d71ec-195">Enable shared/external memory access</span></span> |
| <span data-ttu-id="d71ec-196">[23-3]</span><span class="sxs-lookup"><span data-stu-id="d71ec-196">[23-3]</span></span> | <span data-ttu-id="d71ec-197">0</span><span class="sxs-lookup"><span data-stu-id="d71ec-197">0</span></span> | <span data-ttu-id="d71ec-198">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="d71ec-198">Reserved</span></span>
| <span data-ttu-id="d71ec-199">[31-24]</span><span class="sxs-lookup"><span data-stu-id="d71ec-199">[31-24]</span></span> | <br /><span data-ttu-id="d71ec-200">0x01</span><span class="sxs-lookup"><span data-stu-id="d71ec-200">0x01</span></span><br /><span data-ttu-id="d71ec-201">0x02</span><span class="sxs-lookup"><span data-stu-id="d71ec-201">0x02</span></span><br /><span data-ttu-id="d71ec-202">0x03</span><span class="sxs-lookup"><span data-stu-id="d71ec-202">0x03</span></span> | <span data-ttu-id="d71ec-203">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="d71ec-203">**Compiler ID**</span></span><br /><span data-ttu-id="d71ec-204">IAR</span><span class="sxs-lookup"><span data-stu-id="d71ec-204">IAR</span></span><br /><span data-ttu-id="d71ec-205">ARM</span><span class="sxs-lookup"><span data-stu-id="d71ec-205">ARM</span></span><br /><span data-ttu-id="d71ec-206">GNU</span><span class="sxs-lookup"><span data-stu-id="d71ec-206">GNU</span></span> |


## <a name="module-linker-control-file"></a><span data-ttu-id="d71ec-207">Plik sterowania konsolidatorem modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-207">Module linker control file</span></span>

<span data-ttu-id="d71ec-208">Podczas kompilowania modułu Preambuła modułu musi być umieszczona przed każdą inną sekcją kodu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-208">When building a module, the module preamble must be placed before any other code section.</span></span> <span data-ttu-id="d71ec-209">Moduł musi być skompilowany przy użyciu kodu niezależnego od pozycji i sekcji danych.</span><span class="sxs-lookup"><span data-stu-id="d71ec-209">A module must be built with position-independent code and data sections.</span></span> <span data-ttu-id="d71ec-210">Przykładowe pliki konsolidatora specyficzne dla portów znajdują się w [dodatku](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="d71ec-210">Port-specific example linker files are in the [appendix](appendix.md).</span></span>

## <a name="module-threadx-library"></a><span data-ttu-id="d71ec-211">Biblioteka ThreadX modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-211">Module ThreadX library</span></span>

<span data-ttu-id="d71ec-212">Każdy moduł musi być połączony z specjalną, skoncentrowaną na module biblioteką ThreadX.</span><span class="sxs-lookup"><span data-stu-id="d71ec-212">Each module must link against a special, module-centric ThreadX library.</span></span> <span data-ttu-id="d71ec-213">Ta biblioteka zapewnia dostęp do usług ThreadX Services w kodzie rezydentnym.</span><span class="sxs-lookup"><span data-stu-id="d71ec-213">This library provides access to ThreadX services in the resident code.</span></span> <span data-ttu-id="d71ec-214">Większość dostępu jest realizowana za pośrednictwem plików ***txm_ \* . c*** .</span><span class="sxs-lookup"><span data-stu-id="d71ec-214">Most of the access is accomplished via the ***txm_\*.c*** files.</span></span> <span data-ttu-id="d71ec-215">Poniżej znajduje się przykład wywołania dostępu do modułu dla funkcji API ThreadX **_tx_thread_relinquish_* _ (w _*_ \_ txm_thread_relinquish. c \* \* \* \* ).</span><span class="sxs-lookup"><span data-stu-id="d71ec-215">The following is an example of the module access call for the ThreadX API function **_tx_thread_relinquish_* _ (in _*_\_txm_thread_relinquish.c\*\*\*\*).</span></span>

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

<span data-ttu-id="d71ec-216">W tym przykładzie wskaźnik funkcji dostarczony przez Menedżera modułów jest używany do wywołania funkcji wysyłania Menedżera modułów z IDENTYFIKATORem skojarzonym z usługą ***tx_thread_relinquish*** .</span><span class="sxs-lookup"><span data-stu-id="d71ec-216">In this example, the function pointer supplied by the Module Manager is used to call the Module Manager dispatch function with the ID associated with the ***tx_thread_relinquish*** service.</span></span> <span data-ttu-id="d71ec-217">Ta usługa nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d71ec-217">This service takes no parameters.</span></span>

## <a name="module-example"></a><span data-ttu-id="d71ec-218">Przykład modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-218">Module example</span></span>

<span data-ttu-id="d71ec-219">Poniżej znajduje się przykład standardowej demonstracji ThreadX w postaci modułu.</span><span class="sxs-lookup"><span data-stu-id="d71ec-219">The following is an example of the standard ThreadX demonstration in the form of a module.</span></span> <span data-ttu-id="d71ec-220">Główne różnice między standardową prezentacją ThreadX a demonstracją modułu są.</span><span class="sxs-lookup"><span data-stu-id="d71ec-220">The main differences between the standard ThreadX demonstration and the module demonstration are.</span></span>

1. <span data-ttu-id="d71ec-221">Zastąpienie elementu ***tx_api. h** _ znakiem _ *_txm_module. h_**</span><span class="sxs-lookup"><span data-stu-id="d71ec-221">Replacement of ***tx_api.h** _ with _ *_txm_module.h_**</span></span>
2. <span data-ttu-id="d71ec-222">Dodanie **#define TXM_MODULE** przed **_txm_module. h_**</span><span class="sxs-lookup"><span data-stu-id="d71ec-222">Addition of **#define TXM_MODULE** prior to **_txm_module.h_**</span></span>
3. <span data-ttu-id="d71ec-223">Zastąpienie ***Main** _ i _ *tx_application_define** z **_demo_module_start_**</span><span class="sxs-lookup"><span data-stu-id="d71ec-223">Replacement of ***main** _ and _ *tx_application_define** with **_demo_module_start_**</span></span>
4. <span data-ttu-id="d71ec-224">Deklarowanie *wskaźników* do obiektów ThreadX, a nie samych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d71ec-224">Declaring *pointers* to ThreadX objects rather than the objects themselves.</span></span>

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

void thread_0_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}

void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}

void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 3 and thread 4. As the loop
       below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;

    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
                                        &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
       below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a><span data-ttu-id="d71ec-225">Kompilowanie modułów</span><span class="sxs-lookup"><span data-stu-id="d71ec-225">Building Modules</span></span>

<span data-ttu-id="d71ec-226">Kompilowanie modułu jest zależne od używanego łańcucha narzędzi.</span><span class="sxs-lookup"><span data-stu-id="d71ec-226">Building a module is dependent on the tool chain being used.</span></span> <span data-ttu-id="d71ec-227">Zobacz [dodatek](appendix.md) dla przykładów specyficznych dla portów.</span><span class="sxs-lookup"><span data-stu-id="d71ec-227">See [appendix](appendix.md) for port-specific examples.</span></span> <span data-ttu-id="d71ec-228">Typowe działania dotyczące wszystkich portów obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="d71ec-228">Common activities to all ports include the following.</span></span>

- <span data-ttu-id="d71ec-229">Kompilowanie biblioteki modułów</span><span class="sxs-lookup"><span data-stu-id="d71ec-229">Building a module library</span></span>
- <span data-ttu-id="d71ec-230">Kompilowanie aplikacji modułu</span><span class="sxs-lookup"><span data-stu-id="d71ec-230">Building the module application</span></span>

<span data-ttu-id="d71ec-231">Każdy moduł musi mieć **txm_module_preamble** (konfigurację specyficzną dla modułu) i bibliotekę modułów (na przykład **_TXM. a_**).</span><span class="sxs-lookup"><span data-stu-id="d71ec-231">Each module is required to have a **txm_module_preamble** (setup specifically for the module) and the module library (for example, **_txm.a_**).</span></span>
