---
title: Rozdział 5 — interfejsy API Menedżera modułów
author: philmea
description: Ten artykuł zawiera podsumowanie interfejsów API Menedżera modułów dostępnych dla rezydentnej części aplikacji.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821390"
---
# <a name="chapter-5---module-manager-apis"></a><span data-ttu-id="a087d-103">Rozdział 5 — interfejsy API Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="a087d-103">Chapter 5 - Module Manager APIs</span></span>

## <a name="summary-of-module-manager-apis"></a><span data-ttu-id="a087d-104">Podsumowanie interfejsów API Menedżera modułów</span><span class="sxs-lookup"><span data-stu-id="a087d-104">Summary of Module Manager APIs</span></span>

<span data-ttu-id="a087d-105">Istnieje kilka dodatkowych interfejsów API, które są dostępne dla rezydentnej części aplikacji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a087d-105">There are several additional APIs available to the resident portion of the application, as follows.</span></span>

- <span data-ttu-id="a087d-106">\***txm_module_manager_external_memory_enable** _ _Enable dostępu do modułu do udostępnionej przestrzeni pamięci \*</span><span class="sxs-lookup"><span data-stu-id="a087d-106">***txm_module_manager_external_memory_enable** _ - _Enable module access to a shared memory space*</span></span>
- <span data-ttu-id="a087d-107">\***txm_module_manager_file_load** _-_Load moduł z pliku za pośrednictwem FileX \*</span><span class="sxs-lookup"><span data-stu-id="a087d-107">***txm_module_manager_file_load** _ - _Load module from file via FileX*</span></span>
- <span data-ttu-id="a087d-108">\***txm_module_manager_in_place_load** _-_Load dane modułu, wykonaj w miejscu \*</span><span class="sxs-lookup"><span data-stu-id="a087d-108">***txm_module_manager_in_place_load** _ - _Load module data, execute in place*</span></span>
- <span data-ttu-id="a087d-109">\***txm_module_manager_initialize** _-_Initialize Menedżera modułów \*</span><span class="sxs-lookup"><span data-stu-id="a087d-109">***txm_module_manager_initialize** _ - _Initialize the module manager*</span></span>
- <span data-ttu-id="a087d-110">\***txm_module_manager_mm_initialize** _-_Initialize sprzęt zarządzania pamięcią \*</span><span class="sxs-lookup"><span data-stu-id="a087d-110">***txm_module_manager_mm_initialize** _ - _Initialize the memory management hardware*</span></span>
- <span data-ttu-id="a087d-111">\***txm_module_manager_maximum_module_priority_set** _-_Set maksymalny priorytet wątku dozwolony w module \*</span><span class="sxs-lookup"><span data-stu-id="a087d-111">***txm_module_manager_maximum_module_priority_set** _ - _Set the maximum thread priority allowed in a module*</span></span>
- <span data-ttu-id="a087d-112">\***txm_module_manager_memory_fault_notify** _-_Register wywołanie zwrotne aplikacji dotyczące błędu pamięci \*</span><span class="sxs-lookup"><span data-stu-id="a087d-112">***txm_module_manager_memory_fault_notify** _ - _Register an application callback on memory fault*</span></span>
- <span data-ttu-id="a087d-113">\***txm_module_manager_memory_load** _-_Load module z pamięci \*</span><span class="sxs-lookup"><span data-stu-id="a087d-113">***txm_module_manager_memory_load** _ - _Load the module from memory*</span></span>
- <span data-ttu-id="a087d-114">\***txm_module_manager_object_pool_create** _-_Create pulę obiektów dla modułów \*</span><span class="sxs-lookup"><span data-stu-id="a087d-114">***txm_module_manager_object_pool_create** _ - _Create an object pool for modules*</span></span>
- <span data-ttu-id="a087d-115">\***txm_module_manager_properties_get** _-_Get właściwości modułu \*</span><span class="sxs-lookup"><span data-stu-id="a087d-115">***txm_module_manager_properties_get** _ - _Get module properties*</span></span>
- <span data-ttu-id="a087d-116">\***txm_module_manager_start** _-_Start wykonywanie określonego modułu \*</span><span class="sxs-lookup"><span data-stu-id="a087d-116">***txm_module_manager_start** _ - _Start execution of the specified module*</span></span>
- <span data-ttu-id="a087d-117">\***txm_module_manager_stop** _-_Stop wykonywanie określonego modułu \*</span><span class="sxs-lookup"><span data-stu-id="a087d-117">***txm_module_manager_stop** _ - _Stop execution of the specified module*</span></span>
- <span data-ttu-id="a087d-118">\***txm_module_manager_unload** _-_Unload module \*</span><span class="sxs-lookup"><span data-stu-id="a087d-118">***txm_module_manager_unload** _ - _Unload the module*</span></span>

---

## <a name="txm_module_manager_external_memory_enable"></a><span data-ttu-id="a087d-119">txm_module_manager_external_memory_enable</span><span class="sxs-lookup"><span data-stu-id="a087d-119">txm_module_manager_external_memory_enable</span></span>

<span data-ttu-id="a087d-120">Włącz moduł, aby uzyskać dostęp do udostępnionej przestrzeni pamięci.</span><span class="sxs-lookup"><span data-stu-id="a087d-120">Enable module to access a shared memory space.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-121">Prototype</span></span>

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a><span data-ttu-id="a087d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-122">Description</span></span>

<span data-ttu-id="a087d-123">Ta usługa tworzy wpis w tabeli sprzętowej zarządzania pamięcią dla regionu pamięci współdzielonej, do którego moduł może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="a087d-123">This service creates an entry in the memory management hardware table for a shared memory region that the module can access.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-124">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-124">Input parameters</span></span>

- <span data-ttu-id="a087d-125">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-125">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="a087d-126">**start_address** Adres początkowy obszaru pamięci udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="a087d-126">**start_address** Starting address of shared memory region.</span></span>
- <span data-ttu-id="a087d-127">**Długość** Długość regionu pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="a087d-127">**length** Length of shared memory region.</span></span>
- <span data-ttu-id="a087d-128">**atrybuty** Atrybuty regionu pamięci (pamięć podręczna, Odczyt, zapis itp.).</span><span class="sxs-lookup"><span data-stu-id="a087d-128">**attributes** Attributes of memory region (cache, read, write, etc.).</span></span> <span data-ttu-id="a087d-129">Atrybuty są specyficzne dla portu; Zobacz [dodatek](appendix.md) dla formatu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a087d-129">Attributes are port-specific; see [appendix](appendix.md) for attributes format.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-130">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-130">Return values</span></span>

- <span data-ttu-id="a087d-131">Pomyślnie utworzono wpis pamięci **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-131">**TX_SUCCESS** (0x00) Memory entry created successfully.</span></span>
- <span data-ttu-id="a087d-132">Menedżer **TX_NOT_AVAILABLE** (0x1D) nie został zainicjowany lub funkcja jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="a087d-132">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized or feature not available.</span></span>
- <span data-ttu-id="a087d-133">**TX_PTR_ERROR** (0X03) nieprawidłowe wystąpienie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-133">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="a087d-134">Moduł **TX_START_ERROR** (0x10) nie jest w stanie załadowania.</span><span class="sxs-lookup"><span data-stu-id="a087d-134">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>
- <span data-ttu-id="a087d-135">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie adresu początkowego.</span><span class="sxs-lookup"><span data-stu-id="a087d-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid start address alignment.</span></span>
- <span data-ttu-id="a087d-136">Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).</span><span class="sxs-lookup"><span data-stu-id="a087d-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-137">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-137">Allowed from</span></span>

<span data-ttu-id="a087d-138">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-138">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-139">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a><span data-ttu-id="a087d-140">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="a087d-140">txm_module_manager_file_load</span></span>

<span data-ttu-id="a087d-141">Załaduj moduł z pliku za pośrednictwem FileX.</span><span class="sxs-lookup"><span data-stu-id="a087d-141">Load module from file via FileX.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-142">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-142">Prototype</span></span>

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a><span data-ttu-id="a087d-143">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-143">Description</span></span>

<span data-ttu-id="a087d-144">Ta usługa ładuje obraz binarny modułu zawartego w określonym pliku do obszaru pamięci modułu i przygotowuje go do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a087d-144">This service loads the binary image of the module contained in the specified file into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="a087d-145">Przyjęto, że dostarczony nośnik jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="a087d-145">It is assumed that the supplied media is already opened.</span></span>

> [!NOTE]
> <span data-ttu-id="a087d-146">System FileX jest używany do ładowania pliku.</span><span class="sxs-lookup"><span data-stu-id="a087d-146">The FileX system is utilized to load the file.</span></span> <span data-ttu-id="a087d-147">Aby można było włączyć dostęp do FileX, moduł, biblioteka modułów, Menedżer modułów i Biblioteka ThreadX (ze źródłami Menedżera modułów) muszą zostać skompilowane przy użyciu **FX_FILEX_PRESENT** zdefiniowanych w projektach.</span><span class="sxs-lookup"><span data-stu-id="a087d-147">In order to enable FileX access, the module, module library, Module Manager and the ThreadX library (with the Module Manager sources) must be built with **FX_FILEX_PRESENT** defined in the projects.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-148">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-148">Input parameters</span></span>

- <span data-ttu-id="a087d-149">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-149">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="a087d-150">**module_name** Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-150">**module_name** Name of the module.</span></span>
- <span data-ttu-id="a087d-151">**media_ptr** Wskaźnik do już otwartego nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="a087d-151">**media_ptr** Pointer to already opened FileX media.</span></span>
- <span data-ttu-id="a087d-152">**file_name** Nazwa pliku binarnego modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-152">**file_name** Name of module's binary file.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-153">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-153">Return values</span></span>

- <span data-ttu-id="a087d-154">Załadowanie modułu zakończyło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-154">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="a087d-155">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-155">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="a087d-156">Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).</span><span class="sxs-lookup"><span data-stu-id="a087d-156">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="a087d-157">**TX_NO_MEMORY** (0x10) za mało pamięci do załadowania modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-157">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="a087d-158">**TX_NOT_DONE** (0x20) nie jest otwarty, nie znaleziono pliku lub plik jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a087d-158">**TX_NOT_DONE** (0x20) Media not open, file not found or file is invalid.</span></span>
- <span data-ttu-id="a087d-159">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-159">**TX_PTR_ERROR** (0x03) Invalid module pointer.</span></span>
- <span data-ttu-id="a087d-160">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie.</span><span class="sxs-lookup"><span data-stu-id="a087d-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="a087d-161">Moduł **TXM_MODULE_ALREADY_LOADED** (0xF1) jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="a087d-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="a087d-162">**TXM_MODULE_INVALID** (0xF2) | Nieprawidłowa Preambuła modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-162">**TXM_MODULE_INVALID** (0xF2) | Invalid module preamble.</span></span>
- <span data-ttu-id="a087d-163">Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).</span><span class="sxs-lookup"><span data-stu-id="a087d-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-164">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-164">Allowed from</span></span>

<span data-ttu-id="a087d-165">Wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-165">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-166">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-166">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="a087d-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-167">See also</span></span>

- <span data-ttu-id="a087d-168">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="a087d-168">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="a087d-169">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="a087d-169">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="a087d-170">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="a087d-170">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_in_place_load"></a><span data-ttu-id="a087d-171">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="a087d-171">txm_module_manager_in_place_load</span></span>

<span data-ttu-id="a087d-172">Załaduj tylko dane modułu, wykonaj moduł w istniejącej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a087d-172">Load module data only, execute module in existing location.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-173">Prototype</span></span>

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="a087d-174">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-174">Description</span></span>

<span data-ttu-id="a087d-175">Ta usługa ładuje obszar danych modułu tylko do obszaru pamięci modułu i przygotowuje go do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a087d-175">This service loads the module's data area only into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="a087d-176">Wykonanie kodu modułu będzie w miejscu, czyli od przesunięcia adresu określonego przez numer preambuły modułu w podanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a087d-176">Module code execution will be in-place, that is, from the address offset specified by the module preamble at the supplied location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-177">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-177">Input parameters</span></span>

- <span data-ttu-id="a087d-178">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-178">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="a087d-179">**module_name** Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-179">**module_name** Name of the module.</span></span>
- <span data-ttu-id="a087d-180">**Lokalizacja** Wskaźnik do obszaru kodu modułu, najpierw preambuły.</span><span class="sxs-lookup"><span data-stu-id="a087d-180">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-181">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-181">Return values</span></span>

- <span data-ttu-id="a087d-182">Załadowanie modułu zakończyło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-182">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="a087d-183">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-183">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="a087d-184">Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).</span><span class="sxs-lookup"><span data-stu-id="a087d-184">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="a087d-185">**TX_NO_MEMORY** (0x10) za mało pamięci do załadowania modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-185">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="a087d-186">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik, wystąpienie modułu lub Preambuła modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-186">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="a087d-187">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie.</span><span class="sxs-lookup"><span data-stu-id="a087d-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="a087d-188">Moduł **TXM_MODULE_ALREADY_LOADED** (0xF1) jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="a087d-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="a087d-189">**TXM_MODULE_INVALID** (0XF2) Nieprawidłowa Preambuła modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-189">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="a087d-190">Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).</span><span class="sxs-lookup"><span data-stu-id="a087d-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-191">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-191">Allowed from</span></span>

<span data-ttu-id="a087d-192">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-192">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-193">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-193">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="a087d-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-194">See also</span></span>

- <span data-ttu-id="a087d-195">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="a087d-195">txm_module_manager_file_load</span></span>
- <span data-ttu-id="a087d-196">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="a087d-196">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="a087d-197">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="a087d-197">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_initialize"></a><span data-ttu-id="a087d-198">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="a087d-198">txm_module_manager_initialize</span></span>

<span data-ttu-id="a087d-199">Zainicjuj Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="a087d-199">Initialize the module manager.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-200">Prototype</span></span>

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a><span data-ttu-id="a087d-201">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-201">Description</span></span>

<span data-ttu-id="a087d-202">Ta usługa inicjuje wewnętrzne zasoby Menedżera modułów, w tym obszar pamięci używany do ładowania modułów.</span><span class="sxs-lookup"><span data-stu-id="a087d-202">This service initializes the Module Manager's internal resources, including the memory area used for loading modules.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-203">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-203">Input parameters</span></span>

- <span data-ttu-id="a087d-204">**module_memory_start** Wskaźnik na początek pamięci modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-204">**module_memory_start** Pointer to the start of module memory.</span></span>
- <span data-ttu-id="a087d-205">**module_memory_size** Rozmiar w bajtach pamięci modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-205">**module_memory_size** Size in bytes of the module memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-206">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-206">Return values</span></span>

- <span data-ttu-id="a087d-207">Pomyślnie zainicjowano **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-207">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="a087d-208">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-208">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-209">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-209">Allowed from</span></span>

<span data-ttu-id="a087d-210">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-210">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-211">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-211">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="a087d-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-212">See also</span></span>

- <span data-ttu-id="a087d-213">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="a087d-213">txm_module_manager_object_pool_create</span></span>

---

## <a name="txm_module_manager_initialize_mmu"></a><span data-ttu-id="a087d-214">txm_module_manager_initialize_mmu</span><span class="sxs-lookup"><span data-stu-id="a087d-214">txm_module_manager_initialize_mmu</span></span>

<span data-ttu-id="a087d-215">Zainicjuj sprzęt zarządzania pamięcią.</span><span class="sxs-lookup"><span data-stu-id="a087d-215">Initialize the memory management hardware.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-216">Prototype</span></span>

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a><span data-ttu-id="a087d-217">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-217">Description</span></span>

<span data-ttu-id="a087d-218">Ta usługa inicjuje pamięcią.</span><span class="sxs-lookup"><span data-stu-id="a087d-218">This service initializes the MMU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-219">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-219">Input parameters</span></span>

<span data-ttu-id="a087d-220">brak</span><span class="sxs-lookup"><span data-stu-id="a087d-220">none</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-221">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-221">Return values</span></span>

- <span data-ttu-id="a087d-222">Pomyślnie zainicjowano **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-222">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="a087d-223">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-223">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-224">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-224">Allowed from</span></span>

<span data-ttu-id="a087d-225">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-225">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-226">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-226">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a><span data-ttu-id="a087d-227">txm_module_manager_maximum_module_priority_set</span><span class="sxs-lookup"><span data-stu-id="a087d-227">txm_module_manager_maximum_module_priority_set</span></span>

<span data-ttu-id="a087d-228">Ustaw maksymalny priorytet wątku dozwolony w module.</span><span class="sxs-lookup"><span data-stu-id="a087d-228">Set the maximum thread priority allowed in a module.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-229">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-229">Prototype</span></span>

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a><span data-ttu-id="a087d-230">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-230">Description</span></span>

<span data-ttu-id="a087d-231">Ta usługa ustawia maksymalny priorytet wątku dozwolony w module.</span><span class="sxs-lookup"><span data-stu-id="a087d-231">This service sets the maximum thread priority allowed in a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-232">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-232">Input parameters</span></span>

- <span data-ttu-id="a087d-233">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-233">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="a087d-234">**priorytet** Maksymalny priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="a087d-234">**priority** Maximum thread priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-235">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-235">Return values</span></span>

- <span data-ttu-id="a087d-236">Pomyślnie zainicjowano **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-236">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="a087d-237">Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).</span><span class="sxs-lookup"><span data-stu-id="a087d-237">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="a087d-238">**TX_PTR_ERROR** (0X03) nieprawidłowe wystąpienie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-238">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="a087d-239">Moduł **TX_START_ERROR** (0x10) nie jest w stanie załadowania.</span><span class="sxs-lookup"><span data-stu-id="a087d-239">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-240">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-240">Allowed from</span></span>

<span data-ttu-id="a087d-241">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-241">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-242">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-242">Example</span></span>

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a><span data-ttu-id="a087d-243">txm_module_manager_memory_fault_notify</span><span class="sxs-lookup"><span data-stu-id="a087d-243">txm_module_manager_memory_fault_notify</span></span>

<span data-ttu-id="a087d-244">Zarejestruj wywołanie zwrotne aplikacji dla błędu pamięci.</span><span class="sxs-lookup"><span data-stu-id="a087d-244">Register an application callback on memory fault.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-245">Prototype</span></span>

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a><span data-ttu-id="a087d-246">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-246">Description</span></span>

<span data-ttu-id="a087d-247">Ta usługa rejestruje określoną funkcję wywołania zwrotnego powiadomień o błędach pamięci aplikacji za pomocą Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="a087d-247">This service registers the specified application memory fault notification callback function with the Module Manager.</span></span> <span data-ttu-id="a087d-248">Jeśli wystąpi błąd pamięci, ta funkcja jest wywoływana ze wskaźnikiem do wątku, którego to dotyczy, i wystąpieniem modułu odpowiadającemu wątkowi, którego to dotyczy.</span><span class="sxs-lookup"><span data-stu-id="a087d-248">If a memory fault occurs, this function is called with a pointer to the offending thread and the module instance corresponding to the offending thread.</span></span> <span data-ttu-id="a087d-249">Przetwarzanie przez Menedżera modułów automatycznie kończy działanie wątku, ale pozostawia wszystkie inne wątki w module bez zmian.</span><span class="sxs-lookup"><span data-stu-id="a087d-249">The Module Manager processing automatically terminates the offending thread, but leaves any other threads in the module untouched.</span></span> <span data-ttu-id="a087d-250">Do aplikacji można zdecydować, co należy zrobić z modułem skojarzonym z błędem pamięci.</span><span class="sxs-lookup"><span data-stu-id="a087d-250">It is up to the application to decide what to do with the module associated with the memory fault.</span></span>

<span data-ttu-id="a087d-251">Zapoznaj się z wewnętrzną strukturą **_txm_module_manager_memory_fault_info** , aby uzyskać szczegółowe informacje dotyczące samego błędu pamięci.</span><span class="sxs-lookup"><span data-stu-id="a087d-251">Please see the internal **_txm_module_manager_memory_fault_info** struct for specific information on the memory fault itself.</span></span>

> [!NOTE]
> <span data-ttu-id="a087d-252">Funkcja wywołania zwrotnego powiadomienia o błędzie pamięci jest wykonywana bezpośrednio z powodu wyjątku błędu pamięci, więc można wywołać tylko interfejsy API ThreadX dozwolone z procedur usługi przerwania.</span><span class="sxs-lookup"><span data-stu-id="a087d-252">The memory fault notification callback function is executed directly from the memory fault exception, so only ThreadX APIs Allowed from interrupt service routines can be called.</span></span> <span data-ttu-id="a087d-253">W związku z tym w celu zatrzymania i zwolnienia nieprawidłowego modułu wywołanie zwrotne powiadomienia aplikacji musi wysłać sygnał do zadania aplikacji, aby można było zatrzymać i zwolnić moduł.</span><span class="sxs-lookup"><span data-stu-id="a087d-253">Thus, in order to stop and unload the offending module, the application notification callback must send a signal to an application task so that the module can be stopped and unloaded.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-254">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-254">Input parameters</span></span>

- <span data-ttu-id="a087d-255">**notify_function** Wskaźnik funkcji do wywołania zwrotnego powiadomienia o błędzie pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a087d-255">**notify_function** Function pointer to the application's memory fault notification callback.</span></span> <span data-ttu-id="a087d-256">Podanie wartości NULL powoduje wyłączenie powiadomienia o błędzie pamięci.</span><span class="sxs-lookup"><span data-stu-id="a087d-256">Supplying a NULL value disables the memory fault notification.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-257">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-257">Return values</span></span>

- <span data-ttu-id="a087d-258">Rejestracja funkcji powiadomień pomyślnych **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-258">**TX_SUCCESS** (0x00) Successful notification function registration.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-259">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-259">Allowed from</span></span>

<span data-ttu-id="a087d-260">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-260">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-261">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-261">Example</span></span>

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a><span data-ttu-id="a087d-262">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="a087d-262">txm_module_manager_memory_load</span></span>

<span data-ttu-id="a087d-263">Załaduj moduł z pamięci.</span><span class="sxs-lookup"><span data-stu-id="a087d-263">Load module from memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-264">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-264">Prototype</span></span>

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="a087d-265">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-265">Description</span></span>

<span data-ttu-id="a087d-266">Ta usługa ładuje kod modułu i obszar danych do obszaru pamięci modułu skonfigurowanym przez ***txm_module_manager_initialize*** i przygotowuje go do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a087d-266">This service loads the module's code and data area into the module memory area set up by ***txm_module_manager_initialize*** and prepares it for execution.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-267">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-267">Input parameters</span></span>

- <span data-ttu-id="a087d-268">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-268">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="a087d-269">**module_name** Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-269">**module_name** Name of the module.</span></span>
- <span data-ttu-id="a087d-270">**Lokalizacja** Wskaźnik do obszaru kodu modułu, najpierw preambuły.</span><span class="sxs-lookup"><span data-stu-id="a087d-270">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-271">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-271">Return values</span></span>

- <span data-ttu-id="a087d-272">Załadowanie modułu zakończyło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-272">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="a087d-273">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-273">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="a087d-274">Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).</span><span class="sxs-lookup"><span data-stu-id="a087d-274">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="a087d-275">**TX_NO_MEMORY** (0x10) za mało pamięci do załadowania modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-275">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="a087d-276">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik, wystąpienie modułu lub Preambuła modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-276">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="a087d-277">**TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie.</span><span class="sxs-lookup"><span data-stu-id="a087d-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="a087d-278">Moduł **TXM_MODULE_ALREADY_LOADED** (0xF1) jest już załadowany.</span><span class="sxs-lookup"><span data-stu-id="a087d-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="a087d-279">**TXM_MODULE_INVALID** (0XF2) Nieprawidłowa Preambuła modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-279">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="a087d-280">Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).</span><span class="sxs-lookup"><span data-stu-id="a087d-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-281">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-281">Allowed from</span></span>

<span data-ttu-id="a087d-282">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-282">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-283">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-283">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a><span data-ttu-id="a087d-284">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-284">See also</span></span>

- <span data-ttu-id="a087d-285">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="a087d-285">txm_module_manager_file_load</span></span>
- <span data-ttu-id="a087d-286">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="a087d-286">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="a087d-287">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="a087d-287">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_object_pool_create"></a><span data-ttu-id="a087d-288">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="a087d-288">txm_module_manager_object_pool_create</span></span>

<span data-ttu-id="a087d-289">Utwórz pulę obiektów dla modułów.</span><span class="sxs-lookup"><span data-stu-id="a087d-289">Create an object pool for modules.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-290">Prototype</span></span>

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a><span data-ttu-id="a087d-291">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-291">Description</span></span>

<span data-ttu-id="a087d-292">Ta usługa tworzy pulę pamięci obiektu menedżera modułów, z której moduły mogą przydzielić obiekty ThreadX/NetX z, a tym samym zachować obiekt system z obszaru pamięci modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-292">This service creates a Module Manager object memory pool that the modules can allocate ThreadX/NetX objects from, thereby keeping the system object out of the module's memory area.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-293">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-293">Input parameters</span></span>

- <span data-ttu-id="a087d-294">**pool_memory_start** Wskaźnik na początek pamięci obiektu.</span><span class="sxs-lookup"><span data-stu-id="a087d-294">**pool_memory_start** Pointer to the start of object memory.</span></span>
- <span data-ttu-id="a087d-295">**pool_memory_size** Rozmiar w bajtach puli pamięci obiektu.</span><span class="sxs-lookup"><span data-stu-id="a087d-295">**pool_memory_size** Size in bytes of the object memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-296">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-296">Return values</span></span>

- <span data-ttu-id="a087d-297">Pomyślnie zainicjowano **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-297">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="a087d-298">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-298">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-299">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-299">Allowed from</span></span>

<span data-ttu-id="a087d-300">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-300">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-301">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-301">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="a087d-302">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-302">See also</span></span>

- <span data-ttu-id="a087d-303">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="a087d-303">txm_module_manager_initialize</span></span>

---

## <a name="txm_module_manager_properties_get"></a><span data-ttu-id="a087d-304">txm_module_manager_properties_get</span><span class="sxs-lookup"><span data-stu-id="a087d-304">txm_module_manager_properties_get</span></span>

<span data-ttu-id="a087d-305">Pobierz właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-305">Get module properties.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-306">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-306">Prototype</span></span>

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a><span data-ttu-id="a087d-307">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-307">Description</span></span>

<span data-ttu-id="a087d-308">Ta usługa zwraca właściwości (określone w preambule) modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-308">This service returns the properties (specified in the preamble) of a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-309">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-309">Input parameters</span></span>

- <span data-ttu-id="a087d-310">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-310">**module_instance** Pointer to the module instance.</span></span>
- <span data-ttu-id="a087d-311">**module_properties_ptr** Wskaźnik do miejsca docelowego dla właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-311">**module_properties_ptr** Pointer to destination for module's properties.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-312">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-312">Return values</span></span>

- <span data-ttu-id="a087d-313">Pomyślnie zainicjowano **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-313">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="a087d-314">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="a087d-314">**TX_PTR_ERROR** (0x03) Invalid pointer.</span></span>
- <span data-ttu-id="a087d-315">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-315">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-316">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-316">Allowed from</span></span>

<span data-ttu-id="a087d-317">Wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-317">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-318">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-318">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a><span data-ttu-id="a087d-319">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="a087d-319">txm_module_manager_start</span></span>

<span data-ttu-id="a087d-320">Rozpocznij wykonywanie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-320">Start execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-321">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-321">Prototype</span></span>

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="a087d-322">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-322">Description</span></span>

<span data-ttu-id="a087d-323">Ta usługa uruchamia wykonywanie określonego, już załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-323">This service starts execution of the specified, already loaded module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-324">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-324">Input parameters</span></span>

- <span data-ttu-id="a087d-325">**module_instance** Wskaźnik do poprzednio załadowanego wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-325">**module_instance** Pointer to previously loaded module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-326">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-326">Return values</span></span>

- <span data-ttu-id="a087d-327">**TX_SUCCESS** (0X00) pomyślne uruchomienie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-327">**TX_SUCCESS** (0x00) Successful module start.</span></span>
- <span data-ttu-id="a087d-328">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-328">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="a087d-329">Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).</span><span class="sxs-lookup"><span data-stu-id="a087d-329">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="a087d-330">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik lub wystąpienie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-330">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="a087d-331">Moduł **TX_START_ERROR** (0x10) jest już uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a087d-331">**TX_START_ERROR** (0x10) Module already started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-332">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-332">Allowed from</span></span>

<span data-ttu-id="a087d-333">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-333">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-334">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-334">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="a087d-335">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-335">See also</span></span>

- <span data-ttu-id="a087d-336">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="a087d-336">txm_module_manager_stop</span></span>

---

## <a name="txm_module_manager_stop"></a><span data-ttu-id="a087d-337">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="a087d-337">txm_module_manager_stop</span></span>

<span data-ttu-id="a087d-338">Zatrzymaj wykonywanie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-338">Stop execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-339">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-339">Prototype</span></span>

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="a087d-340">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-340">Description</span></span>

<span data-ttu-id="a087d-341">Ta usługa umożliwia zatrzymanie modułu, który został wcześniej załadowany i uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a087d-341">This service stops a module that was previously loaded and started.</span></span> <span data-ttu-id="a087d-342">Zatrzymywanie modułu obejmuje wykonanie opcjonalnego wątku zatrzymania modułu, zakończenie wszystkich wątków i usunięcie wszystkich zasobów skojarzonych z modułem.</span><span class="sxs-lookup"><span data-stu-id="a087d-342">Stopping a module includes executing the module's optional stop thread, terminating all threads, and deleting all resources associated with the module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-343">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-343">Input parameters</span></span>

- <span data-ttu-id="a087d-344">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-344">**module_instance** Pointer to module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-345">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-345">Return values</span></span>

- <span data-ttu-id="a087d-346">Zakończono pomyślne zatrzymywanie modułu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="a087d-346">**TX_SUCCESS** (0x00) Successful module stop.</span></span>
- <span data-ttu-id="a087d-347">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-347">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="a087d-348">Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).</span><span class="sxs-lookup"><span data-stu-id="a087d-348">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="a087d-349">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik lub wystąpienie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-349">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="a087d-350">Moduł **TX_START_ERROR** (0x10) nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a087d-350">**TX_START_ERROR** (0x10) Module not started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-351">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-351">Allowed from</span></span>

<span data-ttu-id="a087d-352">Wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-352">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-353">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-353">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="a087d-354">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-354">See also</span></span>

- <span data-ttu-id="a087d-355">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="a087d-355">txm_module_manager_start</span></span>

---

## <a name="txm_module_manager_unload"></a><span data-ttu-id="a087d-356">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="a087d-356">txm_module_manager_unload</span></span>

<span data-ttu-id="a087d-357">Zwolnij moduł.</span><span class="sxs-lookup"><span data-stu-id="a087d-357">Unload the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="a087d-358">Prototype</span><span class="sxs-lookup"><span data-stu-id="a087d-358">Prototype</span></span>

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="a087d-359">Opis</span><span class="sxs-lookup"><span data-stu-id="a087d-359">Description</span></span>

<span data-ttu-id="a087d-360">Ta usługa zwalnia poprzednio załadowany i zatrzymany moduł, zwalniając wszystkie skojarzone zasoby pamięci modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-360">This service unloads the previously loaded and stopped module, freeing all the associated module memory resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a087d-361">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a087d-361">Input parameters</span></span>

- <span data-ttu-id="a087d-362">**module_instance** Wskaźnik do wystąpienia modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-362">**module_instance** Pointer to the instance of the module.</span></span>

### <a name="return-values"></a><span data-ttu-id="a087d-363">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a087d-363">Return values</span></span>

- <span data-ttu-id="a087d-364">**TX_SUCCESS** 0x00) załadowanie modułu zakończone powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a087d-364">**TX_SUCCESS** 0x00) Successful module unload.</span></span>
- <span data-ttu-id="a087d-365">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a087d-365">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="a087d-366">Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).</span><span class="sxs-lookup"><span data-stu-id="a087d-366">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="a087d-367">**TX_NOT_DONE** (0X20) nieprawidłowy moduł lub moduł nie został zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="a087d-367">**TX_NOT_DONE** (0x20) Invalid module or module not stopped.</span></span>
- <span data-ttu-id="a087d-368">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik lub wystąpienie modułu.</span><span class="sxs-lookup"><span data-stu-id="a087d-368">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a087d-369">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a087d-369">Allowed from</span></span>

<span data-ttu-id="a087d-370">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="a087d-370">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="a087d-371">Przykład</span><span class="sxs-lookup"><span data-stu-id="a087d-371">Example</span></span>

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="a087d-372">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a087d-372">See also</span></span>

- <span data-ttu-id="a087d-373">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="a087d-373">txm_module_manager_file_load</span></span>
- <span data-ttu-id="a087d-374">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="a087d-374">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="a087d-375">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="a087d-375">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="a087d-376">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="a087d-376">txm_module_manager_stop</span></span>
