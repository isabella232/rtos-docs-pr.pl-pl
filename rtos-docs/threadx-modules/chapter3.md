---
title: Rozdział 3 — wymagania dotyczące programu module Manager
description: Ten artykuł zawiera opis czynności wymaganych do utworzenia Menedżera modułu ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822500"
---
# <a name="chapter-3---module-manager-requirements"></a><span data-ttu-id="e35e1-103">Rozdział 3 — wymagania dotyczące programu module Manager</span><span class="sxs-lookup"><span data-stu-id="e35e1-103">Chapter 3 - Module Manager requirements</span></span>

<span data-ttu-id="e35e1-104">Program ThreadX module Manager znajduje się w rezydentnej części aplikacji wraz z RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-104">The ThreadX Module Manager resides in the resident portion of the application along with the ThreadX RTOS.</span></span> <span data-ttu-id="e35e1-105">Jest on odpowiedzialny za uruchamianie modułu, a także pole i wysyłanie żądań wszystkich modułów dla usług interfejsu API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-105">It is responsible for starting the module as well as fielding and dispatching all module requests for ThreadX API services.</span></span>

> [!NOTE]
> <span data-ttu-id="e35e1-106">Pliki źródłowe **Menedżera** modułów ThreadX (C i Assembly) należy dodać do projektu biblioteki ThreadX "**TX**".</span><span class="sxs-lookup"><span data-stu-id="e35e1-106">The ThreadX Module **Manager** source files (C and assembly) should be added to the ThreadX library project "**tx**".</span></span>

<span data-ttu-id="e35e1-107">Poniższe kroki są wymagane do utworzenia Menedżera modułu ThreadX (każdy krok został szczegółowo opisany poniżej).</span><span class="sxs-lookup"><span data-stu-id="e35e1-107">The following steps are required for building the ThreadX Module Manager (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="e35e1-108">Aby uwzględnić informacje o module, należy rozszerzyć blok sterowania **TX_THREAD** .</span><span class="sxs-lookup"><span data-stu-id="e35e1-108">The **TX_THREAD** control block must be extended to include module information.</span></span> <span data-ttu-id="e35e1-109">Najprostszym sposobem na to jest zamienienie definicji **TX_THREAD_EXTENSION_2** w **pliku _tx_port. h_\*_ z TX_THREAD_EXTENSION_2 _**\* znalezionym w **_txm_module_port. h_**.</span><span class="sxs-lookup"><span data-stu-id="e35e1-109">The easiest way to accomplish this is to replace the definition of **TX_THREAD_EXTENSION_2** in the **_tx_port.h_*_ file with the _\* TX_THREAD_EXTENSION_2*\* found in **_txm_module_port.h_**.</span></span> <span data-ttu-id="e35e1-110">Zobacz [dodatek](appendix.md) dotyczący rozszerzeń specyficznych dla portów.</span><span class="sxs-lookup"><span data-stu-id="e35e1-110">See [appendix](appendix.md) for port-specific extensions.</span></span>

<span data-ttu-id="e35e1-111">Przykładowe rozszerzenie:</span><span class="sxs-lookup"><span data-stu-id="e35e1-111">Example extension:</span></span>

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   <span data-ttu-id="e35e1-112">Następujące rozszerzenia muszą być zdefiniowane w ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="e35e1-112">The following extensions must be defined in ***tx_port.h***.</span></span>

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. <span data-ttu-id="e35e1-113">Dodaj wszystkie ***txm_module_manager_ \**** C i pliki zestawu **_do projektu biblioteki_** ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-113">Add all the ***txm_module_manager_\**** C and assembly files to the ThreadX library project **_tx_**.</span></span>
3. <span data-ttu-id="e35e1-114">Kompiluj ponownie wszystkie biblioteki i projekty wykonywalne.</span><span class="sxs-lookup"><span data-stu-id="e35e1-114">Rebuild all libraries and executable projects.</span></span> <span data-ttu-id="e35e1-115">Jeśli NetX Duo jest wymagana, wszystkie kody modułów i modułów w języku C powinny być skompilowane przy użyciu zdefiniowanych **TXM_MODULE_ENABLE_NETX_DUO** .</span><span class="sxs-lookup"><span data-stu-id="e35e1-115">If NetX Duo is required, all Module and Module Manager C code should be built with **TXM_MODULE_ENABLE_NETX_DUO** defined.</span></span>

## <a name="module-manager-sources"></a><span data-ttu-id="e35e1-116">Źródła Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-116">Module Manager sources</span></span>

<span data-ttu-id="e35e1-117">Menedżer modułu ThreadX ma zestaw plików źródłowych, które zostały zaprojektowane tak, aby można je było łączyć i znajdować bezpośrednio w kodzie rezydentnym ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-117">The ThreadX Module Manager has a set of source files that are designed to be linked and located directly with the resident ThreadX code.</span></span> <span data-ttu-id="e35e1-118">Te pliki umożliwiają uruchamianie modułu i kolejnych żądań interfejsu API ThreadX z modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-118">These files provide the ability to launch a module and field subsequent ThreadX API requests from the module.</span></span> <span data-ttu-id="e35e1-119">Pliki menedżera modułów są następujące.</span><span class="sxs-lookup"><span data-stu-id="e35e1-119">The module manager files are as follows.</span></span>

| <span data-ttu-id="e35e1-120">**Nazwa pliku**</span><span class="sxs-lookup"><span data-stu-id="e35e1-120">**File Name**</span></span> |  <span data-ttu-id="e35e1-121">**Zawartość**</span><span class="sxs-lookup"><span data-stu-id="e35e1-121">**Contents**</span></span> |
|-------------- | ------------- |
| <span data-ttu-id="e35e1-122">***txm_module. h***</span><span class="sxs-lookup"><span data-stu-id="e35e1-122">***txm_module.h***</span></span> | <span data-ttu-id="e35e1-123">Plik dołączany, który definiuje informacje o module (również zawarte w kodzie źródłowym modułu).</span><span class="sxs-lookup"><span data-stu-id="e35e1-123">Include file that defines module information (also included in the module source code).</span></span> |
| <span data-ttu-id="e35e1-124">***txm_module_manager_dispatch. h***</span><span class="sxs-lookup"><span data-stu-id="e35e1-124">***txm_module_manager_dispatch.h***</span></span> | <span data-ttu-id="e35e1-125">Plik dołączany, który definiuje funkcje pomocnika wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e35e1-125">Include file that defines dispatch helper functions.</span></span>|
| <span data-ttu-id="e35e1-126">***txm_module_manager_util. h***</span><span class="sxs-lookup"><span data-stu-id="e35e1-126">***txm_module_manager_util.h***</span></span> | <span data-ttu-id="e35e1-127">Plik dołączany, który definiuje wewnętrzne makra pomocnika narzędzi & funkcje.</span><span class="sxs-lookup"><span data-stu-id="e35e1-127">Include file that defines internal utility helper macros & functions.</span></span> |
| <span data-ttu-id="e35e1-128">***txm_module_port. h***</span><span class="sxs-lookup"><span data-stu-id="e35e1-128">***txm_module_port.h***</span></span> | <span data-ttu-id="e35e1-129">Plik dołączany, który definiuje informacje o module specyficznym dla portów (również zawarte w kodzie źródłowym modułu).</span><span class="sxs-lookup"><span data-stu-id="e35e1-129">Include file that defines port-specific module information (also included in the module source code).</span></span> |
| <span data-ttu-id="e35e1-130">\***tx_initialize_low_level. \[ s, S, 68 \]** _</span><span class="sxs-lookup"><span data-stu-id="e35e1-130">\***tx_initialize_low_level.\[s,S,68\]** _</span></span> | <span data-ttu-id="e35e1-131">Zamienia istniejący plik biblioteki ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-131">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="e35e1-132">Zaktualizowano tabelę wektorów i dodatkowe programy obsługi wektorów dla wyjątków Menedżera modułów i pamięci.</span><span class="sxs-lookup"><span data-stu-id="e35e1-132">Updated vector table and additional vector handlers for module manager and memory exceptions.</span></span> <span data-ttu-id="e35e1-133">Plik _This jest tylko w Cortex-nr/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="e35e1-133">_This file is only in Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span></span>|
| <span data-ttu-id="e35e1-134">\***tx_thread_context_restore. s** _</span><span class="sxs-lookup"><span data-stu-id="e35e1-134">\***tx_thread_context_restore.s** _</span></span> | <span data-ttu-id="e35e1-135">Zamienia istniejący plik biblioteki ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-135">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="e35e1-136">Przywróć kontekst wątku po przetworzeniu przerwań.</span><span class="sxs-lookup"><span data-stu-id="e35e1-136">Restore thread context after interrupt processing.</span></span> <span data-ttu-id="e35e1-137">Plik _This jest tylko w Cortex-Cortex/ARM, Cortex-R4/ARM,-R4/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="e35e1-137">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="e35e1-138">***tx_thread_schedule. \[ s, S, 68\]***</span><span class="sxs-lookup"><span data-stu-id="e35e1-138">***tx_thread_schedule.\[s,S,68\]***</span></span> | <span data-ttu-id="e35e1-139">Zamienia istniejący plik biblioteki ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-139">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="e35e1-140">Rozszerzony kod harmonogramu, w tym przypadku jest używany do aktualizacji rejestrów zarządzania pamięcią.</span><span class="sxs-lookup"><span data-stu-id="e35e1-140">Extended scheduler code, which in this case is used to update memory management registers.</span></span> |
| <span data-ttu-id="e35e1-141">\***tx_thread_stack_build. s** _</span><span class="sxs-lookup"><span data-stu-id="e35e1-141">\***tx_thread_stack_build.s** _</span></span> | <span data-ttu-id="e35e1-142">Zamienia istniejący plik biblioteki ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-142">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="e35e1-143">Kompiluje ramkę stosu wątku.</span><span class="sxs-lookup"><span data-stu-id="e35e1-143">Builds the stack frame of a thread.</span></span> <span data-ttu-id="e35e1-144">Plik _This jest tylko w Cortex-Cortex/ARM, Cortex-R4/ARM,-R4/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="e35e1-144">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="e35e1-145">***txm_module_manager_thread_stack_build. \[ s, S, 68\]***</span><span class="sxs-lookup"><span data-stu-id="e35e1-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span></span> | <span data-ttu-id="e35e1-146">Kompiluje wszystkie początkowe stosy modułów, w tym Instalatora dla dostępu do danych na pozycji.</span><span class="sxs-lookup"><span data-stu-id="e35e1-146">Builds all module initial stacks, includes setup for position-independent data access.</span></span> |
| <span data-ttu-id="e35e1-147">\***txm_module_manager_user_mode_entry. \[ s, S \]** _</span><span class="sxs-lookup"><span data-stu-id="e35e1-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span></span> | <span data-ttu-id="e35e1-148">Umożliwia modułowi wprowadzanie trybu jądra.</span><span class="sxs-lookup"><span data-stu-id="e35e1-148">Allows the module to enter kernel mode.</span></span> <span data-ttu-id="e35e1-149">Plik _This jest tylko w Cortex-Cortex/ARM, Cortex-R4/ARM,-R4/IAR. \*</span><span class="sxs-lookup"><span data-stu-id="e35e1-149">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="e35e1-150">***txm_module_manager_alignment_adjust. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-150">***txm_module_manager_alignment_adjust.c***</span></span> | <span data-ttu-id="e35e1-151">Obsługuje wymagania dotyczące wyrównania charakterystyczne dla portów.</span><span class="sxs-lookup"><span data-stu-id="e35e1-151">Handles port-specific alignment requirements.</span></span>|
| <span data-ttu-id="e35e1-152">***txm_module_manager_application_request. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-152">***txm_module_manager_application_request.c***</span></span> | <span data-ttu-id="e35e1-153">Obsługuje żądania specyficzne dla aplikacji w kodzie rezydentnym.</span><span class="sxs-lookup"><span data-stu-id="e35e1-153">Handles the application-specific requests to the resident code.</span></span> |
| <span data-ttu-id="e35e1-154">***txm_module_manager_callback_request. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-154">***txm_module_manager_callback_request.c***</span></span> | <span data-ttu-id="e35e1-155">Wysyła żądanie wywołania zwrotnego do modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-155">Sends a callback request to a module.</span></span> |
| <span data-ttu-id="e35e1-156">***txm_module_manager_event_flags_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-156">***txm_module_manager_event_flags_notify_trampoline.c***</span></span> | <span data-ttu-id="e35e1-157">Przetwarza flagi zdarzeń ustawia wywołanie powiadomienia z ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-157">Processes the event flags set notification call from ThreadX.</span></span> |
| <span data-ttu-id="e35e1-158">***txm_module_manager_external_memory_enable. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-158">***txm_module_manager_external_memory_enable.c***</span></span> | <span data-ttu-id="e35e1-159">Tworzy wpis w tabeli zarządzania pamięcią dla współdzielonego miejsca w pamięci, do którego moduł może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="e35e1-159">Creates an entry in the memory management table for a shared memory space the module can access.</span></span> |
| <span data-ttu-id="e35e1-160">***txm_module_manager_file_load. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-160">***txm_module_manager_file_load.c***</span></span> | <span data-ttu-id="e35e1-161">Przydziela i ładuje plik modułu binarnego do obszaru pamięci modułu i przygotowuje go do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e35e1-161">Allocates and loads a binary module file into the module memory area and prepares it for execution.</span></span> |
| <span data-ttu-id="e35e1-162">***txm_module_manager_in_place_load. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-162">***txm_module_manager_in_place_load.c***</span></span> | <span data-ttu-id="e35e1-163">Przydziela obszar danych modułu i przygotowuje się do wykonania modułu z podanego adresu kodu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-163">Allocates the module data area and prepares for module execution from the supplied code address.</span></span> |
| <span data-ttu-id="e35e1-164">***txm_module_manager_initialize. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-164">***txm_module_manager_initialize.c***</span></span> | <span data-ttu-id="e35e1-165">Inicjuje menedżera modułów, w tym specyfikację obszaru pamięci modułu dostępną do ładowania i uruchamiania modułów.</span><span class="sxs-lookup"><span data-stu-id="e35e1-165">Initializes the Module Manager, including specification of the module memory area available for loading and running modules.</span></span> |
| <span data-ttu-id="e35e1-166">\***txm_module_manager_initialize_mmu. c** _</span><span class="sxs-lookup"><span data-stu-id="e35e1-166">\***txm_module_manager_initialize_mmu.c** _</span></span> | <span data-ttu-id="e35e1-167">Zainicjuj pamięcią.</span><span class="sxs-lookup"><span data-stu-id="e35e1-167">Initialize MMU.</span></span> <span data-ttu-id="e35e1-168">Użytkownicy mogą edytować ten plik według mapy pamięci.</span><span class="sxs-lookup"><span data-stu-id="e35e1-168">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="e35e1-169">Plik _This jest tylko w Cortex-nr/ARM \*</span><span class="sxs-lookup"><span data-stu-id="e35e1-169">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="e35e1-170">\***txm_module_manager_mm_initialize. c** _</span><span class="sxs-lookup"><span data-stu-id="e35e1-170">\***txm_module_manager_mm_initialize.c** _</span></span> | <span data-ttu-id="e35e1-171">Zainicjuj MPU/pamięcią.</span><span class="sxs-lookup"><span data-stu-id="e35e1-171">Initialize MPU/MMU.</span></span> <span data-ttu-id="e35e1-172">Użytkownicy mogą edytować ten plik według mapy pamięci.</span><span class="sxs-lookup"><span data-stu-id="e35e1-172">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="e35e1-173">Plik _This jest tylko w Cortex-nr/ARM \*</span><span class="sxs-lookup"><span data-stu-id="e35e1-173">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="e35e1-174">***txm_module_manager_kernel_dispatch. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-174">***txm_module_manager_kernel_dispatch.c***</span></span> | <span data-ttu-id="e35e1-175">Obsługuje żądania interfejsu API modułu na podstawie identyfikatora żądania.</span><span class="sxs-lookup"><span data-stu-id="e35e1-175">Handles the module API requests, based on the request ID.</span></span> |
| <span data-ttu-id="e35e1-176">***txm_module_manager_maximum_module_priority_set. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-176">***txm_module_manager_maximum_module_priority_set.c***</span></span> | <span data-ttu-id="e35e1-177">Ustawia maksymalny priorytet wątku dozwolony w module.</span><span class="sxs-lookup"><span data-stu-id="e35e1-177">Sets the maximum thread priority allowed in a module.</span></span> |
| <span data-ttu-id="e35e1-178">***txm_module_manager_memory_fault_handler. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-178">***txm_module_manager_memory_fault_handler.c***</span></span> | <span data-ttu-id="e35e1-179">Obsługuje błędy pamięci wykryte w module wykonywanym.</span><span class="sxs-lookup"><span data-stu-id="e35e1-179">Handles memory faults detected in an executing module.</span></span> |
| <span data-ttu-id="e35e1-180">***txm_module_manager_memory_fault_notify. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-180">***txm_module_manager_memory_fault_notify.c***</span></span> | <span data-ttu-id="e35e1-181">Rejestruje wywołanie zwrotne powiadomień aplikacji przy każdym wystąpieniu błędu pamięci.</span><span class="sxs-lookup"><span data-stu-id="e35e1-181">Registers an application notification callback whenever a memory fault occurs.</span></span> |
| <span data-ttu-id="e35e1-182">***txm_module_manager_memory_load. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-182">***txm_module_manager_memory_load.c***</span></span> | <span data-ttu-id="e35e1-183">Przydziela i ładuje kod i dane modułu oraz przygotowuje moduł do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e35e1-183">Allocates and loads a module's code and data and prepares the module for execution.</span></span> |
| <span data-ttu-id="e35e1-184">***txm_module_manager_mm_register_setup. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-184">***txm_module_manager_mm_register_setup.c***</span></span> | <span data-ttu-id="e35e1-185">Konfiguruje rejestry MPU/pamięcią dla modułu w zależności od tego, gdzie jest ładowany kod i dane.</span><span class="sxs-lookup"><span data-stu-id="e35e1-185">Sets up MPU/MMU registers for the module based on where the code and data are loaded.</span></span> |
| <span data-ttu-id="e35e1-186">***txm_module_manager_object_allocate. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-186">***txm_module_manager_object_allocate.c***</span></span> | <span data-ttu-id="e35e1-187">Przydziela pamięć dla obiektu modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-187">Allocates memory for a module object.</span></span> |
| <span data-ttu-id="e35e1-188">***txm_module_manager_object_deallocate. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-188">***txm_module_manager_object_deallocate.c***</span></span> | <span data-ttu-id="e35e1-189">Cofa alokację pamięci dla obiektu modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-189">Deallocates memory for a module object.</span></span> |
| <span data-ttu-id="e35e1-190">***txm_module_manager_object_pointer_get. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-190">***txm_module_manager_object_pointer_get.c***</span></span> | <span data-ttu-id="e35e1-191">Wyszukuje podany typ obiektu i nazwę, a jeśli zostanie znaleziona, zwraca wskaźnik obiektu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-191">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> |
| <span data-ttu-id="e35e1-192">***txm_module_manager_object_pointer_get_extended. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-192">***txm_module_manager_object_pointer_get_extended.c***</span></span> | <span data-ttu-id="e35e1-193">Wyszukuje podany typ obiektu i nazwę, a jeśli zostanie znaleziona, zwraca wskaźnik obiektu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-193">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> <span data-ttu-id="e35e1-194">Długość nazwy określona dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="e35e1-194">Name length specified for safety.</span></span> |
| <span data-ttu-id="e35e1-195">***txm_module_manager_object_pool_create. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-195">***txm_module_manager_object_pool_create.c***</span></span>  | <span data-ttu-id="e35e1-196">Tworzy pulę obiektów poza obszarem danych modułu, z którego mogą być przydzielane aplikacje modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-196">Creates a pool of objects outside the module's data area that module applications can allocate from.</span></span> |
| <span data-ttu-id="e35e1-197">***txm_module_manager_properties_get. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-197">***txm_module_manager_properties_get.c***</span></span> | <span data-ttu-id="e35e1-198">Pobiera właściwości określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-198">Gets the properties of the specified module.</span></span> |
| <span data-ttu-id="e35e1-199">***txm_module_manager_queue_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-199">***txm_module_manager_queue_notify_trampoline.c***</span></span> | <span data-ttu-id="e35e1-200">Przetwarza wywołanie powiadomienia kolejki z ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-200">Processes the queue notification call from ThreadX.</span></span> |
| <span data-ttu-id="e35e1-201">***txm_module_manager_semaphore_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-201">***txm_module_manager_semaphore_notify_trampoline.c***</span></span> | <span data-ttu-id="e35e1-202">Przetwarza wywołanie powiadomienia o wprowadzeniu semafora z ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-202">Processes the semaphore put notification call from ThreadX.</span></span>|
| <span data-ttu-id="e35e1-203">***txm_module_manager_start. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-203">***txm_module_manager_start.c***</span></span> | <span data-ttu-id="e35e1-204">Uruchamia wykonywanie modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-204">Starts execution of a module.</span></span> |
| <span data-ttu-id="e35e1-205">***txm_module_manager_stop. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-205">***txm_module_manager_stop.c***</span></span> | <span data-ttu-id="e35e1-206">Powoduje zatrzymanie wykonywania modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-206">Stops execution of a module.</span></span> |
| <span data-ttu-id="e35e1-207">***txm_module_manager_thread_create. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-207">***txm_module_manager_thread_create.c***</span></span> | <span data-ttu-id="e35e1-208">Tworzy wszystkie wątki modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-208">Creates all module threads.</span></span> |
| <span data-ttu-id="e35e1-209">***txm_module_manager_thread_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-209">***txm_module_manager_thread_notify_trampoline.c***</span></span> | <span data-ttu-id="e35e1-210">Przetwarza wywołanie powiadomienia o wejściu/wyjściu wątku z ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-210">Processes the thread entry/exit notification call from ThreadX.</span></span> |
| <span data-ttu-id="e35e1-211">***txm_module_manager_thread_reset. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-211">***txm_module_manager_thread_reset.c***</span></span> | <span data-ttu-id="e35e1-212">Zresetuj wątek modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-212">Reset a module thread.</span></span> |
| <span data-ttu-id="e35e1-213">***txm_module_manager_timer_notify_trampoline. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-213">***txm_module_manager_timer_notify_trampoline.c***</span></span> | <span data-ttu-id="e35e1-214">Przetwarza wygaśnięcia czasomierza z ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-214">Processes timer expirations from ThreadX.</span></span> |
| <span data-ttu-id="e35e1-215">***txm_module_manager_unload. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-215">***txm_module_manager_unload.c***</span></span> | <span data-ttu-id="e35e1-216">Zwalnia moduł z obszaru pamięci modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-216">Unloads the module from the module memory area.</span></span> |
| <span data-ttu-id="e35e1-217">***txm_module_manager_util. c***</span><span class="sxs-lookup"><span data-stu-id="e35e1-217">***txm_module_manager_util.c***</span></span> | <span data-ttu-id="e35e1-218">Wewnętrzne funkcje pomocnika dla Menedżera.</span><span class="sxs-lookup"><span data-stu-id="e35e1-218">Internal helper functions for manager.</span></span> |

## <a name="module-manager-initialization"></a><span data-ttu-id="e35e1-219">Inicjowanie Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-219">Module Manager initialization</span></span>

<span data-ttu-id="e35e1-220">Rezydentna część aplikacji jest odpowiedzialna za wywoływanie funkcji inicjowania Menedżera modułów ***txm_module_manager_initialize***.</span><span class="sxs-lookup"><span data-stu-id="e35e1-220">The resident portion of the application is responsible for calling the Module Manager initialization function ***txm_module_manager_initialize***.</span></span> <span data-ttu-id="e35e1-221">Ta funkcja konfiguruje wewnętrzne struktury do ładowania i wyładowywania modułów, w tym konfigurowania obszaru pamięci używanego do przydzielania pamięci modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-221">This function sets up the internal structures for loading and unloading modules, including setting up the memory area used for allocating module memory.</span></span>

## <a name="module-manager-loading"></a><span data-ttu-id="e35e1-222">Ładowanie Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-222">Module Manager loading</span></span>

<span data-ttu-id="e35e1-223">Menedżer modułów może dynamicznie ładować moduły do pamięci modułu z plików modułów binarnych lub z sekcji kodu modułu, która znajduje się już w obszarze rezydentów.</span><span class="sxs-lookup"><span data-stu-id="e35e1-223">The Module Manager can load modules dynamically into the module memory from binary module files or from a module code section that is already present in the resident code area.</span></span> <span data-ttu-id="e35e1-224">Ponadto Menedżer modułów może wykonać kod w miejscu, to znaczy, że tylko dane modułu są przydzieleni do pamięci modułu, a wykonywanie kodu jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="e35e1-224">In addition, the module manager can execute code in place, that is, only the module data is allocated in the module memory and the code execution is done in place.</span></span> <span data-ttu-id="e35e1-225">Dostępne są następujące funkcje interfejsu API ładowania programu module Manager.</span><span class="sxs-lookup"><span data-stu-id="e35e1-225">The following Module Manager load API functions are available.</span></span>

* <span data-ttu-id="e35e1-226">***txm_module_manager_file_load***</span><span class="sxs-lookup"><span data-stu-id="e35e1-226">***txm_module_manager_file_load***</span></span>

* <span data-ttu-id="e35e1-227">***txm_module_manager_in_place_load***</span><span class="sxs-lookup"><span data-stu-id="e35e1-227">***txm_module_manager_in_place_load***</span></span>

* <span data-ttu-id="e35e1-228">***txm_module_manager_memory_load***</span><span class="sxs-lookup"><span data-stu-id="e35e1-228">***txm_module_manager_memory_load***</span></span>

<span data-ttu-id="e35e1-229">Wersja chroniona pamięci Menedżera modułów gwarantuje również, że moduł jest ładowany z odpowiednim wyrównaniem, a rejestry zarządzania pamięcią są poprawnie skonfigurowane dla każdego modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-229">The memory protected version of the Module Manager also makes sure that the module is loaded with the proper alignment and the memory management registers are set up properly for each module.</span></span> <span data-ttu-id="e35e1-230">Gdy ochrona pamięci jest włączona za pomocą opcji preambuły modułu, dostęp do pamięci modułu jest ograniczony do kodu modułu i obszarów danych.</span><span class="sxs-lookup"><span data-stu-id="e35e1-230">When memory protection is enabled via the module preamble options, module memory access is restricted to the module code and data areas.</span></span>

## <a name="module-manager-starting"></a><span data-ttu-id="e35e1-231">Uruchamianie Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-231">Module Manager starting</span></span>

<span data-ttu-id="e35e1-232">Menedżer modułów inicjuje wykonywanie poprzednio załadowanego modułu za pomocą funkcji ***txm_module_manager_start*** API.</span><span class="sxs-lookup"><span data-stu-id="e35e1-232">The Module Manager initiates execution of a previously-loaded module via the ***txm_module_manager_start*** API function.</span></span> <span data-ttu-id="e35e1-233">Aby zainicjować wykonywanie modułu, ta funkcja tworzy wątek, który przechodzi do modułu w lokalizacji początkowej określonej w preambule modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-233">To initiate module execution, this function creates a thread that enters the module at the starting location specified in the module preamble.</span></span> <span data-ttu-id="e35e1-234">Priorytet i rozmiar stosu tego wątku jest również określony w preambule modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-234">The priority and stack size of this thread is also specified in the module preamble.</span></span>

## <a name="module-manager-stopping"></a><span data-ttu-id="e35e1-235">Zatrzymywanie Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-235">Module Manager stopping</span></span>

<span data-ttu-id="e35e1-236">Menedżer modułów kończy wykonywanie wcześniej załadowanych i wykonywanych modułów za pośrednictwem funkcji ***txm_module_manager_stop*** .</span><span class="sxs-lookup"><span data-stu-id="e35e1-236">The Module Manager terminates execution of a previously-loaded and executing module via the ***txm_module_manager_stop*** function.</span></span> <span data-ttu-id="e35e1-237">Ta funkcja interfejsu API najpierw kończy działanie i usuwa początkowy wątek początkowy.</span><span class="sxs-lookup"><span data-stu-id="e35e1-237">This API function first terminates and deletes the initial starting thread.</span></span> <span data-ttu-id="e35e1-238">Jeśli Preambuła modułu określa wątek zatrzymania, ten wątek jest tworzony i wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e35e1-238">If the module preamble specifies a stop thread, this thread is created and executed.</span></span> <span data-ttu-id="e35e1-239">Menedżer modułu czeka przez ustalony czas na ukończenie wątku zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="e35e1-239">The Module Manager waits for a fixed period of time for the stop thread to complete.</span></span> <span data-ttu-id="e35e1-240">Po zakończeniu wszystkie zasoby systemowe utworzone przez moduł zostaną usunięte, a moduł zostanie umieszczony w stanie uśpienia, z którego może zostać ponownie uruchomiony lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="e35e1-240">Once complete, all system resources created by the module are deleted and the module is placed in a dormant state, from which it can be either restarted or unloaded.</span></span>

## <a name="module-manager-unloading"></a><span data-ttu-id="e35e1-241">Zwalnianie Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-241">Module Manager unloading</span></span>

<span data-ttu-id="e35e1-242">Menedżer modułów zwalnia poprzednio załadowany moduł, ale nie wykonuje go za pośrednictwem funkcji ***txm_module_manager_unload*** .</span><span class="sxs-lookup"><span data-stu-id="e35e1-242">The Module Manager unloads a previously-loaded but not executing module via the ***txm_module_manager_unload*** function.</span></span> <span data-ttu-id="e35e1-243">Ten interfejs API zwalnia całą pamięć skojarzoną z modułem, zwalniając ją do użycia z innym modułem w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e35e1-243">This API releases all memory associated with the module, freeing it for use with another module in the future.</span></span>

## <a name="module-manager-requests"></a><span data-ttu-id="e35e1-244">Żądania Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-244">Module Manager requests</span></span>

<span data-ttu-id="e35e1-245">Żądania wykonywane przez moduły do Menedżera modułów są wykonywane za pośrednictwem makr w ***txm_module. h*** , które mapują wszystkie wywołania ThreadX w celu wywołania funkcji wysyłania Menedżera modułów za pośrednictwem wskaźnika funkcji dostarczonego do modułu przez Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="e35e1-245">Requests made by modules to the Module Manager are done via macros in ***txm_module.h*** that map all ThreadX calls to call the Module Manager dispatch function via a function pointer supplied to the module by the Module Manager.</span></span>

<span data-ttu-id="e35e1-246">Dodatkowe usługi specyficzne dla aplikacji wykonywane za pośrednictwem modułu wywołującego ***txm_module_application_request*** są obsługiwane przez ten sam mechanizm makro, który jest używany przez interfejs API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-246">Additional application-specific services made via the module calling ***txm_module_application_request*** are handled by the same macro mechanism used for the ThreadX API.</span></span> <span data-ttu-id="e35e1-247">Domyślnie ta funkcja obsługi w Menedżerze modułów jest pusta i zaprojektowana w taki sposób, że aplikacja dodaje kod niezbędny do przetwarzania żądań specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e35e1-247">By default, this handling function in the Module Manager is empty and designed such that the application adds the necessary code to process the application-specific requests.</span></span>

<span data-ttu-id="e35e1-248">Jeśli żądanie nie zostanie zaimplementowane przez Menedżera modułów, Menedżer modułów zwróci wartość **TX_NOT_AVAILABLE** stan błędu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-248">If the request is not implemented by the Module Manager, a value of **TX_NOT_AVAILABLE** error status is returned by the Module Manager.</span></span> <span data-ttu-id="e35e1-249">Ten kod błędu jest również zwracany, jeśli moduł żąda operacji, która znajduje się poza zakresem dostępu modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-249">This error code is also returned if the module requests an operation that is outside the scope of the module's access.</span></span> <span data-ttu-id="e35e1-250">Na przykład moduł nie może utworzyć czasomierza z blokiem sterowania czasomierzem lub adresem wywołania zwrotnego poza obszarem kodu modułu.</span><span class="sxs-lookup"><span data-stu-id="e35e1-250">For example, a module is not allowed to create a timer with the timer control block or callback address outside of the module's code area.</span></span>

## <a name="module-manager-example"></a><span data-ttu-id="e35e1-251">Przykład Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-251">Module Manager example</span></span>

<span data-ttu-id="e35e1-252">Poniżej znajduje się przykładowy kod Menedżera modułów, który uruchamia przykładowy moduł zdefiniowany wcześniej w rozdziale 2.</span><span class="sxs-lookup"><span data-stu-id="e35e1-252">The following is an example of Module Manager code that launches the example module previously defined in Chapter 2.</span></span> <span data-ttu-id="e35e1-253">Zakłada się, że moduł jest już załadowany, najprawdopodobniej przez debuger, pod adresem ROM 0x00800000.</span><span class="sxs-lookup"><span data-stu-id="e35e1-253">It is assumed that the module is already loaded, presumably by the debugger, at ROM address 0x00800000.</span></span>

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a><span data-ttu-id="e35e1-254">Kompilowanie Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="e35e1-254">Module Manager building</span></span>

<span data-ttu-id="e35e1-255">Pliki źródłowe ***txm_module_manager_ \**** należy dodać do biblioteki ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e35e1-255">The ***txm_module_manager_\**** source files must be added to the ThreadX library.</span></span>

<span data-ttu-id="e35e1-256">Aplikacja ThreadX module Manager jest efektywnie taka sama jak standardowa aplikacja ThreadX, która jest co najmniej jednym plikami aplikacji połączonym razem z biblioteką ThreadX ***TX. a***.</span><span class="sxs-lookup"><span data-stu-id="e35e1-256">A ThreadX Module Manager application is effectively the same as a standard ThreadX application, which is one or more application files linked together with the ThreadX library ***tx.a***.</span></span> <span data-ttu-id="e35e1-257">Kompilowanie aplikacji Menedżera modułów jest zależne od używanego łańcucha narzędzi.</span><span class="sxs-lookup"><span data-stu-id="e35e1-257">Building a module manager application is dependent on the tool chain being used.</span></span> <span data-ttu-id="e35e1-258">Zobacz [dodatek](appendix.md) dla przykładów specyficznych dla portów.</span><span class="sxs-lookup"><span data-stu-id="e35e1-258">See [appendix](appendix.md) for port-specific examples.</span></span>
