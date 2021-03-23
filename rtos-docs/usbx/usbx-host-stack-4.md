---
title: Rozdział 4 — Opis usług hosta USBX
description: Dowiedz się więcej na temat usług hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824360"
---
# <a name="chapter-4---description-of-usbx-host-services"></a><span data-ttu-id="fa306-103">Rozdział 4 — Opis usług hosta USBX</span><span class="sxs-lookup"><span data-stu-id="fa306-103">Chapter 4 - Description of USBX Host Services</span></span>

## <a name="ux_host_stack_initialize"></a><span data-ttu-id="fa306-104">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="fa306-104">ux_host_stack_initialize</span></span>

<span data-ttu-id="fa306-105">Zainicjuj USBX dla operacji hosta.</span><span class="sxs-lookup"><span data-stu-id="fa306-105">Initialize USBX for host operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-106">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-106">Prototype</span></span>

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a><span data-ttu-id="fa306-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-107">Description</span></span>

<span data-ttu-id="fa306-108">Ta funkcja spowoduje zainicjowanie stosu hosta USB.</span><span class="sxs-lookup"><span data-stu-id="fa306-108">This function will initialize the USB host stack.</span></span> <span data-ttu-id="fa306-109">Dostarczony obszar pamięci zostanie skonfigurowany do użytku wewnętrznego USBX.</span><span class="sxs-lookup"><span data-stu-id="fa306-109">The supplied memory area will be setup for USBX internal use.</span></span> <span data-ttu-id="fa306-110">Jeśli zostanie zwrócona UX_SUCCESS, USBX jest gotowa do rejestracji kontrolerów hosta i klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-110">If UX_SUCCESS is returned, USBX is ready for host controller and class registration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="fa306-111">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="fa306-111">Input Parameter</span></span>

- <span data-ttu-id="fa306-112">**system_change_function** Wskaźnik do opcjonalnej procedury wywołania zwrotnego w celu powiadomienia aplikacji o zmianach urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fa306-112">**system_change_function** Pointer to optional callback routine for notifying application of device changes.</span></span>

### <a name="return-value"></a><span data-ttu-id="fa306-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa306-113">Return Value</span></span>

- <span data-ttu-id="fa306-114">Pomyślnie zainicjowano **UX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="fa306-114">**UX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="fa306-115">**UX_MEMORY_INSUFFICIENT** (0x12) alokacja pamięci nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="fa306-115">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-116">Example</span></span>

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="fa306-117">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="fa306-117">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="fa306-118">Przerwij wszystkie transakcje dołączone do żądania transferu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fa306-118">Abort all transactions attached to a transfer request for an endpoint.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-119">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-119">Prototype</span></span>

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="fa306-120">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-120">Description</span></span>

<span data-ttu-id="fa306-121">Ta funkcja spowoduje anulowanie wszystkich transakcji aktywnych lub oczekujących na określone żądanie transferu dołączone do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fa306-121">This function will cancel all transactions active or pending for a specific transfer request attached to an endpoint.</span></span> <span data-ttu-id="fa306-122">Żądanie transferu ma załączoną funkcję wywołania zwrotnego, funkcja wywołania zwrotnego zostanie wywołana ze stanem UX_TRANSACTION_ABORTED.</span><span class="sxs-lookup"><span data-stu-id="fa306-122">It the transfer request has a callback function attached, the callback function will be called with the UX_TRANSACTION_ABORTED status.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="fa306-123">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="fa306-123">Input Parameter</span></span>

- <span data-ttu-id="fa306-124">**punkt końcowy** Wskaźnik do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fa306-124">**endpoint** Pointer to an endpoint.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-125">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-125">Return Values</span></span>

- <span data-ttu-id="fa306-126">**UX_SUCCESS** (0X00) nie ma błędów.</span><span class="sxs-lookup"><span data-stu-id="fa306-126">**UX_SUCCESS** (0x00) No errors.</span></span>
- <span data-ttu-id="fa306-127">Dojście punktu końcowego **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) jest nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="fa306-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint handle is not valid.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-128">Example</span></span>

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a><span data-ttu-id="fa306-129">ux_host_stack_class_get</span><span class="sxs-lookup"><span data-stu-id="fa306-129">ux_host_stack_class_get</span></span>

<span data-ttu-id="fa306-130">Pobierz wskaźnik do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-130">Get the pointer to a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-131">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-131">Prototype</span></span>

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a><span data-ttu-id="fa306-132">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-132">Description</span></span>

<span data-ttu-id="fa306-133">Ta funkcja zwraca wskaźnik do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-133">This function returns a pointer to the class container.</span></span> <span data-ttu-id="fa306-134">Klasa musi uzyskać kontener ze stosu USB, aby wyszukać wystąpienia, gdy Klasa lub aplikacja chcą otworzyć urządzenie.</span><span class="sxs-lookup"><span data-stu-id="fa306-134">A class needs to obtain its container from the USB stack to search for instances when a class or an application wants to open a device.</span></span>

> [!NOTE]
> <span data-ttu-id="fa306-135">Ciąg C class_name musi być zakończony zerem i długością (bez samego terminatora NULL) nie może być większy niż UX_MAX_CLASS_NAME_LENGTH.</span><span class="sxs-lookup"><span data-stu-id="fa306-135">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than UX_MAX_CLASS_NAME_LENGTH.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-136">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-136">Parameters</span></span>

- <span data-ttu-id="fa306-137">**class_name** Wskaźnik na nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-137">**class_name** Pointer to the class name.</span></span>
- <span data-ttu-id="fa306-138">**Klasa** Wskaźnik zaktualizowany przez wywołanie funkcji, który zawiera kontener klasy dla nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-138">**class** A pointer updated by the function call that contains the class container for the name of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-139">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-139">Return Values</span></span>

- <span data-ttu-id="fa306-140">**UX_SUCCESS** (0X00) Brak błędów, na zwrócić pole klasy jest zgłaszane ze wskaźnikiem do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-140">**UX_SUCCESS** (0x00) No errors, on return the class field is filed with the pointer to the class container.</span></span>
- <span data-ttu-id="fa306-141">Klasa **UX_HOST_CLASS_UNKNOWN** (0x59) jest nieznana przez stos.</span><span class="sxs-lookup"><span data-stu-id="fa306-141">**UX_HOST_CLASS_UNKNOWN** (0x59) Class is unknown by the stack.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-142">Example</span></span>

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a><span data-ttu-id="fa306-143">ux_host_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="fa306-143">ux_host_stack_class_register</span></span>

<span data-ttu-id="fa306-144">Zarejestruj klasę USB na stosie USB.</span><span class="sxs-lookup"><span data-stu-id="fa306-144">Register a USB class to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-145">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-145">Prototype</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="fa306-146">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-146">Description</span></span>

<span data-ttu-id="fa306-147">Ta funkcja rejestruje klasę USB na stosie USB.</span><span class="sxs-lookup"><span data-stu-id="fa306-147">This function registers a USB class to the USB stack.</span></span> <span data-ttu-id="fa306-148">Klasa musi określać punkt wejścia dla stosu USB do wysyłania poleceń, takich jak następujące.</span><span class="sxs-lookup"><span data-stu-id="fa306-148">The class must specify an entry point for the USB stack to send commands such as the following.</span></span>

- <span data-ttu-id="fa306-149">**UX_HOST_CLASS_COMMAND_QUERY**</span><span class="sxs-lookup"><span data-stu-id="fa306-149">**UX_HOST_CLASS_COMMAND_QUERY**</span></span>
- <span data-ttu-id="fa306-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span><span class="sxs-lookup"><span data-stu-id="fa306-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span></span>
- <span data-ttu-id="fa306-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span><span class="sxs-lookup"><span data-stu-id="fa306-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span></span>

> [!NOTE]
> <span data-ttu-id="fa306-152">Ciąg C *class_name* musi być zakończony zerem i długością (bez samego terminatora null) nie może być większy niż **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="fa306-152">The C string of *class_name* must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-153">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-153">Parameters</span></span>

- <span data-ttu-id="fa306-154">**class_name** Wskaźnik na nazwę klasy, prawidłowe wpisy znajdują się w pliku ux_system_initialize. c w klasie USB klasy USBX.</span><span class="sxs-lookup"><span data-stu-id="fa306-154">**class_name** Pointer to the name of the class, valid entries are found in the file ux_system_initialize.c under the USB Classes of USBX.</span></span>
- <span data-ttu-id="fa306-155">**class_entry_address** Adres funkcji wejścia klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-155">**class_entry_address** Address of the entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-156">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-156">Return Values</span></span>

- <span data-ttu-id="fa306-157">Pomyślnie zainstalowano klasę **UX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="fa306-157">**UX_SUCCESS** (0x00) Class installed successfully.</span></span>
- <span data-ttu-id="fa306-158">**UX_MEMORY_ARRAY_FULL** (0X1a) nie więcej pamięci do przechowania tej klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No more memory to store this class.</span></span>
- <span data-ttu-id="fa306-159">Klasa hosta **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) jest już zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="fa306-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host class already installed.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-160">Przykład:</span><span class="sxs-lookup"><span data-stu-id="fa306-160">Example:</span></span>

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a><span data-ttu-id="fa306-161">ux_host_stack_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="fa306-161">ux_host_stack_class_instance_create</span></span>

<span data-ttu-id="fa306-162">Utwórz nowe wystąpienie klasy dla kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-162">Create a new class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-163">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-163">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="fa306-164">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-164">Description</span></span>

<span data-ttu-id="fa306-165">Ta funkcja tworzy nowe wystąpienie klasy dla kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-165">This function creates a new class instance for a class container.</span></span> <span data-ttu-id="fa306-166">Wystąpienie klasy nie jest zawarte w kodzie klasy, aby zmniejszyć złożoność klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-166">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="fa306-167">Zamiast tego każde wystąpienie klasy jest dołączone do kontenera klas znajdującego się w głównym stosie.</span><span class="sxs-lookup"><span data-stu-id="fa306-167">Rather, each class instance is attached to the class container located in the main stack.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-168">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-168">Parameters</span></span>

- <span data-ttu-id="fa306-169">**Klasa** Wskaźnik do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-169">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="fa306-170">**class_instance** Wskaźnik do wystąpienia klasy, które ma zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="fa306-170">**class_instance** Pointer to the class instance to be created.</span></span>

### <a name="return-value"></a><span data-ttu-id="fa306-171">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa306-171">Return Value</span></span>

- <span data-ttu-id="fa306-172">**UX_SUCCESS** (0x00) wystąpienie klasy zostało dołączone do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-172">**UX_SUCCESS** (0x00) The class instance was attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-173">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-173">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a><span data-ttu-id="fa306-174">ux_host_stack_class_instance_destroy</span><span class="sxs-lookup"><span data-stu-id="fa306-174">ux_host_stack_class_instance_destroy</span></span>

<span data-ttu-id="fa306-175">Zniszcz wystąpienie klasy dla kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-175">Destroy a class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-176">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-176">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="fa306-177">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-177">Description</span></span>

<span data-ttu-id="fa306-178">Ta funkcja niszczy wystąpienie klasy dla kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-178">This function destroys a class instance for a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-179">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-179">Parameters</span></span>

- <span data-ttu-id="fa306-180">**Klasa** Wskaźnik do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-180">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="fa306-181">**class_instance** Wskaźnik do wystąpienia, które ma zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="fa306-181">**class_instance** Pointer to the instance to destroy.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-182">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-182">Return Values</span></span>

- <span data-ttu-id="fa306-183">**UX_SUCCESS** (0x00) wystąpienie klasy zostało zniszczone.</span><span class="sxs-lookup"><span data-stu-id="fa306-183">**UX_SUCCESS** (0x00) The class instance was destroyed.</span></span>
- <span data-ttu-id="fa306-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) wystąpienie klasy nie jest dołączone do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The class instance is not attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-185">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-185">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a><span data-ttu-id="fa306-186">ux_host_stack_class_instance_get</span><span class="sxs-lookup"><span data-stu-id="fa306-186">ux_host_stack_class_instance_get</span></span>

<span data-ttu-id="fa306-187">Pobierz wskaźnik wystąpienia klasy dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-187">Get a class instance pointer for a specific class.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-188">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a><span data-ttu-id="fa306-189">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-189">Description</span></span>

<span data-ttu-id="fa306-190">Ta funkcja zwraca wskaźnik wystąpienia klasy dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-190">This function returns a class instance pointer for a specific class.</span></span> <span data-ttu-id="fa306-191">Wystąpienie klasy nie jest zawarte w kodzie klasy, aby zmniejszyć złożoność klasy.</span><span class="sxs-lookup"><span data-stu-id="fa306-191">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="fa306-192">Zamiast tego każde wystąpienie klasy jest dołączone do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-192">Rather, each class instance is attached to the class container.</span></span> <span data-ttu-id="fa306-193">Ta funkcja służy do wyszukiwania wystąpień klas w kontenerze klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-193">This function is used to search for class instances within a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-194">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-194">Parameters</span></span>

- <span data-ttu-id="fa306-195">**Klasa** Wskaźnik do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-195">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="fa306-196">**class_index** Indeks, który ma być używany przez wywołanie funkcji na liście dołączonych klas do kontenera.</span><span class="sxs-lookup"><span data-stu-id="fa306-196">**class_index** An index to be used by the function call within the list of attached classes to the container.</span></span>
- <span data-ttu-id="fa306-197">**class_instance** Wskaźnik do wystąpienia, które ma zostać zwrócone przez wywołanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="fa306-197">**class_instance** Pointer to the instance to be returned by the function call.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-198">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-198">Return Values</span></span>

- <span data-ttu-id="fa306-199">**UX_SUCCESS** (0x00) wystąpienie klasy zostało znalezione.</span><span class="sxs-lookup"><span data-stu-id="fa306-199">**UX_SUCCESS** (0x00) The class instance was found.</span></span>

- <span data-ttu-id="fa306-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie ma więcej wystąpień klasy dołączonych do kontenera klas.</span><span class="sxs-lookup"><span data-stu-id="fa306-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) There are no more class instances attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-201">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="fa306-202">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="fa306-202">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="fa306-203">Pobierz wskaźnik do kontenera konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fa306-203">Get a pointer to a configuration container.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-204">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-204">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="fa306-205">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-205">Description</span></span>

<span data-ttu-id="fa306-206">Ta funkcja zwraca kontener konfiguracji oparty na dojściem urządzenia i indeksie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fa306-206">This function returns a configuration container based on a device handle and a configuration index.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-207">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-207">Parameters</span></span>

- <span data-ttu-id="fa306-208">**urządzenie** Wskaźnik do kontenera urządzenia, do którego należy żądana konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="fa306-208">**device** Pointer to the device container that owns the configuration requested.</span></span>
- <span data-ttu-id="fa306-209">**configuration_index** Indeks konfiguracji do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="fa306-209">**configuration_index** Index of the configuration to be searched.</span></span>
- <span data-ttu-id="fa306-210">**Konfiguracja** Adres wskaźnika do zwrócenia kontenera konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fa306-210">**configuration** Address of the pointer to the configuration container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-211">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-211">Return Values</span></span>

- <span data-ttu-id="fa306-212">**UX_SUCCESS** (0x00) konfiguracja została znaleziona.</span><span class="sxs-lookup"><span data-stu-id="fa306-212">**UX_SUCCESS** (0x00) The configuration was found.</span></span>
- <span data-ttu-id="fa306-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) kontener urządzeń nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa306-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) The device container does not exist.</span></span>
- <span data-ttu-id="fa306-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie istnieje uchwyt konfiguracyjny dla tego indeksu.</span><span class="sxs-lookup"><span data-stu-id="fa306-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle for the index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-215">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-215">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="fa306-216">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="fa306-216">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="fa306-217">Wybierz konkretną konfigurację urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fa306-217">Select a specific configuration for a device.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-218">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-218">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="fa306-219">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-219">Description</span></span>

<span data-ttu-id="fa306-220">Ta funkcja wybiera określoną konfigurację dla urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fa306-220">This function selects a specific configuration for a device.</span></span> <span data-ttu-id="fa306-221">Gdy ta konfiguracja jest ustawiona na urządzenie, domyślnie na urządzeniu jest uaktywniany każdy interfejs urządzenia i jego skojarzone ustawienia alternatywne 0.</span><span class="sxs-lookup"><span data-stu-id="fa306-221">When this configuration is set to the device, by default, each device interface and its associated alternate setting 0 is activated on the device.</span></span> <span data-ttu-id="fa306-222">Jeśli Klasa urządzenia/interfejsu chce zmienić ustawienie określonego interfejsu, musi wydać **ux_host_stack_interface_setting_select** wywołanie usługi.</span><span class="sxs-lookup"><span data-stu-id="fa306-222">If the device/interface class wishes to change the setting of a particular interface, it needs to issue a **ux_host_stack_interface_setting_select** service call.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-223">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-223">Parameters</span></span>

- <span data-ttu-id="fa306-224">**Konfiguracja** Wskaźnik do kontenera konfiguracji, który ma być włączony dla tego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fa306-224">**configuration** Pointer to the configuration container that is to be enabled for this device.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-225">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-225">Return Values</span></span>

- <span data-ttu-id="fa306-226">**UX_SUCCESS** (0x00) wybór konfiguracji zakończył się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fa306-226">**UX_SUCCESS** (0x00) The configuration selection was successful.</span></span>
- <span data-ttu-id="fa306-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) dojście konfiguracji nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa306-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle does not exist.</span></span>
- <span data-ttu-id="fa306-228">Na magistrali dla tej konfiguracji **UX_OVER_CURRENT_CONDITION** (0x43) znajduje się nad bieżącym stanem.</span><span class="sxs-lookup"><span data-stu-id="fa306-228">**UX_OVER_CURRENT_CONDITION** (0x43) An over current condition exists on the bus for this configuration.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-229">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-229">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a><span data-ttu-id="fa306-230">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="fa306-230">ux_host_stack_device_get</span></span>

<span data-ttu-id="fa306-231">Pobierz wskaźnik do kontenera urządzeń.</span><span class="sxs-lookup"><span data-stu-id="fa306-231">Get a pointer to a device container.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-232">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-232">Prototype</span></span>

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a><span data-ttu-id="fa306-233">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-233">Description</span></span>

<span data-ttu-id="fa306-234">Ta funkcja zwraca kontener urządzenia na podstawie jego indeksu.</span><span class="sxs-lookup"><span data-stu-id="fa306-234">This function returns a device container based on its index.</span></span> <span data-ttu-id="fa306-235">Indeks urządzenia zaczyna się od 0.</span><span class="sxs-lookup"><span data-stu-id="fa306-235">The device index starts with 0.</span></span> <span data-ttu-id="fa306-236">Należy zauważyć, że indeks jest ULONG, ponieważ może istnieć kilka kontrolerów, a indeks bajtów może być niewystarczający.</span><span class="sxs-lookup"><span data-stu-id="fa306-236">Note that the index is a ULONG because we could have several controllers and a byte index might not be enough.</span></span> <span data-ttu-id="fa306-237">Nie należy mylić indeksu urządzenia z adresem urządzenia, który jest specyficzny dla magistrali.</span><span class="sxs-lookup"><span data-stu-id="fa306-237">The device index should not be confused with the device address that is bus specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-238">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-238">Parameters</span></span>

- <span data-ttu-id="fa306-239">**device_index** Indeks urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fa306-239">**device_index** Index of the device.</span></span>
- <span data-ttu-id="fa306-240">**urządzenie** Adres wskaźnika dla kontenera urządzenia do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="fa306-240">**device** Address of the pointer for the device container to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-241">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-241">Return Values</span></span>

- <span data-ttu-id="fa306-242">**UX_SUCCESS** (0x00) kontener urządzenia istnieje i jest zwracany</span><span class="sxs-lookup"><span data-stu-id="fa306-242">**UX_SUCCESS** (0x00) The device container exists and is returned</span></span>
- <span data-ttu-id="fa306-243">Nieznane urządzenie **UX_DEVICE_HANDLE_UNKNOWN** (0x50)</span><span class="sxs-lookup"><span data-stu-id="fa306-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Device unknown</span></span>

### <a name="example"></a><span data-ttu-id="fa306-244">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-244">Example</span></span>

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a><span data-ttu-id="fa306-245">ux_host_stack_interface_endpoint_get</span><span class="sxs-lookup"><span data-stu-id="fa306-245">ux_host_stack_interface_endpoint_get</span></span>

<span data-ttu-id="fa306-246">Pobieranie kontenera punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="fa306-246">Get an endpoint container.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-247">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-247">Prototype</span></span>

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="fa306-248">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-248">Description</span></span>

<span data-ttu-id="fa306-249">Ta funkcja zwraca kontener punktów końcowych na podstawie uchwytu interfejsu i indeksu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fa306-249">This function returns an endpoint container based on the interface handle and an endpoint index.</span></span> <span data-ttu-id="fa306-250">Przyjęto założenie, że zostało wybrane alternatywne ustawienie interfejsu lub domyślne ustawienie jest używane przed przeszukiwaniem punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="fa306-250">It is assumed that the alternate setting for the interface has been selected or the default setting is being used prior to the endpoint(s) being searched.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-251">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-251">Parameters</span></span>

- <span data-ttu-id="fa306-252">**interfejs** Wskaźnik do kontenera interfejsu zawierającego żądany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="fa306-252">**interface** Pointer to the interface container that contains the endpoint requested.</span></span>
- <span data-ttu-id="fa306-253">**endpoint_index** Indeks punktu końcowego w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="fa306-253">**endpoint_index** Index of the endpoint in this interface.</span></span>
- <span data-ttu-id="fa306-254">**punkt końcowy** Adres kontenera punktu końcowego, który ma zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="fa306-254">**endpoint** Address of the endpoint container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-255">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-255">Return Values</span></span>

- <span data-ttu-id="fa306-256">**UX_SUCCESS** (0x00) kontener punktu końcowego istnieje i jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="fa306-256">**UX_SUCCESS** (0x00) The endpoint container exists and is returned.</span></span>
- <span data-ttu-id="fa306-257">Określony interfejs **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa306-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interface specified does not exist.</span></span>
- <span data-ttu-id="fa306-258">Indeks punktu końcowego **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa306-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-259">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-259">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="fa306-260">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="fa306-260">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="fa306-261">Zarejestruj kontroler USB na stosie USB.</span><span class="sxs-lookup"><span data-stu-id="fa306-261">Register a USB controller to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-262">Prototype</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a><span data-ttu-id="fa306-263">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-263">Description</span></span>

<span data-ttu-id="fa306-264">Ta funkcja rejestruje kontroler USB na stosie USB.</span><span class="sxs-lookup"><span data-stu-id="fa306-264">This function registers a USB controller to the USB stack.</span></span> <span data-ttu-id="fa306-265">Polega to głównie na przydzieleniu pamięci używanej przez ten kontroler i przekazaniem polecenia inicjującego do kontrolera.</span><span class="sxs-lookup"><span data-stu-id="fa306-265">It mainly allocates the memory used by this controller and passes the initialization command to the controller.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-266">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-266">Parameters</span></span>

- <span data-ttu-id="fa306-267">**hcd_name** Nazwa kontrolera hosta</span><span class="sxs-lookup"><span data-stu-id="fa306-267">**hcd_name** Name of the host controller</span></span>
- <span data-ttu-id="fa306-268">**hcd_function** Funkcja w kontrolerze hosta odpowiedzialna za inicjalizację.</span><span class="sxs-lookup"><span data-stu-id="fa306-268">**hcd_function** The function in the host controller responsible for the initialization.</span></span>
- <span data-ttu-id="fa306-269">**hcd_param1** Zasób we/wy lub pamięć używany przez HCD.</span><span class="sxs-lookup"><span data-stu-id="fa306-269">**hcd_param1** The IO or memory resource used by the hcd.</span></span>
- <span data-ttu-id="fa306-270">**hcd_param2** PRZERWAnie używane przez kontroler hosta.</span><span class="sxs-lookup"><span data-stu-id="fa306-270">**hcd_param2** The IRQ used by the host controller.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-271">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-271">Return Values</span></span>

- <span data-ttu-id="fa306-272">**UX_SUCCESS** (0x00) kontroler został prawidłowo zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="fa306-272">**UX_SUCCESS** (0x00) The controller was initialized properly.</span></span>
- <span data-ttu-id="fa306-273">**UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci dla tego kontrolera.</span><span class="sxs-lookup"><span data-stu-id="fa306-273">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory for this controller.</span></span>
- <span data-ttu-id="fa306-274">**UX_PORT_RESET_FAILED** (0x31) resetowanie kontrolera nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="fa306-274">**UX_PORT_RESET_FAILED** (0x31) The reset of the controller failed.</span></span>
- <span data-ttu-id="fa306-275">**UX_CONTROLLER_INIT_FAILED** (0x32) nie można poprawnie zainicjować kontrolera.</span><span class="sxs-lookup"><span data-stu-id="fa306-275">**UX_CONTROLLER_INIT_FAILED** (0x32) The controller failed to initialize properly.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-276">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-276">Example</span></span>

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a><span data-ttu-id="fa306-277">ux_host_stack_configuration_interface_get</span><span class="sxs-lookup"><span data-stu-id="fa306-277">ux_host_stack_configuration_interface_get</span></span>

<span data-ttu-id="fa306-278">Pobierz wskaźnik kontenera interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fa306-278">Get an interface container pointer.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-279">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-279">Prototype</span></span>

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a><span data-ttu-id="fa306-280">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-280">Description</span></span>

<span data-ttu-id="fa306-281">Ta funkcja zwraca kontener interfejsu na podstawie dojścia do konfiguracji, indeksu interfejsu i alternatywnego indeksu ustawienia.</span><span class="sxs-lookup"><span data-stu-id="fa306-281">This function returns an interface container based on a configuration handle, an interface index, and an alternate setting index.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-282">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-282">Parameters</span></span>

- <span data-ttu-id="fa306-283">**Konfiguracja** Wskaźnik do kontenera konfiguracji, który jest właścicielem interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fa306-283">**configuration** Pointer to the configuration container that owns the interface.</span></span>
- <span data-ttu-id="fa306-284">**interface_index** Indeks interfejsu do przeszukania.</span><span class="sxs-lookup"><span data-stu-id="fa306-284">**interface_index** Interface index to be searched.</span></span>
- <span data-ttu-id="fa306-285">**alternate_setting_index** Alternatywne ustawienie w interfejsie do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="fa306-285">**alternate_setting_index** Alternate setting within the interface to search.</span></span>
- <span data-ttu-id="fa306-286">**interfejs** Adres wskaźnika kontenera interfejsu, który ma zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="fa306-286">**interface** Address of the interface container pointer to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-287">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-287">Return Values</span></span>

- <span data-ttu-id="fa306-288">**UX_SUCCESS** (0x00) kontener interfejsu dla indeksu interfejsu oraz ustawienia alternatywnego zostały znalezione i zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fa306-288">**UX_SUCCESS** (0x00) The interface container for the interface index and the alternate setting was found and returned.</span></span>
- <span data-ttu-id="fa306-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Konfiguracja nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa306-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration does not exist.</span></span>
- <span data-ttu-id="fa306-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) interfejs nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa306-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-291">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-291">Example</span></span>

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="fa306-292">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="fa306-292">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="fa306-293">Wybierz alternatywne ustawienie dla interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fa306-293">Select an alternate setting for an interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-294">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-294">Prototype</span></span>

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a><span data-ttu-id="fa306-295">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-295">Description</span></span>

<span data-ttu-id="fa306-296">Ta funkcja wybiera określone ustawienie alternatywne dla danego interfejsu należącego do wybranej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fa306-296">This function selects a specific alternate setting for a given interface belonging to the selected configuration.</span></span> <span data-ttu-id="fa306-297">Ta funkcja jest używana do zmiany ustawienia domyślnego alternatywnego na nowe ustawienie lub w celu powrotu do domyślnego ustawienia alternatywnego.</span><span class="sxs-lookup"><span data-stu-id="fa306-297">This function is used to change from the default alternate setting to a new setting or to go back to the default alternate setting.</span></span> <span data-ttu-id="fa306-298">W przypadku wybrania nowego ustawienia alternatywnego parametry poprzedniego punktu końcowego są nieprawidłowe i należy je ponownie załadować.</span><span class="sxs-lookup"><span data-stu-id="fa306-298">When a new alternate setting is selected, the previous endpoint characteristics are invalid and should be reloaded.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="fa306-299">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="fa306-299">Input Parameter</span></span>

- <span data-ttu-id="fa306-300">**interfejs** Wskaźnik do kontenera interfejsu, którego alternatywnym ustawieniem jest wybranie.</span><span class="sxs-lookup"><span data-stu-id="fa306-300">**interface** Pointer to the interface container whose alternate setting is to be selected.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-301">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-301">Return Values</span></span>

- <span data-ttu-id="fa306-302">**UX_SUCCESS** (0x00) ustawienie alternatywne dla tego interfejsu zostało pomyślnie wybrane.</span><span class="sxs-lookup"><span data-stu-id="fa306-302">**UX_SUCCESS** (0x00) The alternate setting for this interface has been successfully selected.</span></span>
- <span data-ttu-id="fa306-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) interfejs nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa306-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-304">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-304">Example</span></span>

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a><span data-ttu-id="fa306-305">ux_host_stack_transfer_request_abort</span><span class="sxs-lookup"><span data-stu-id="fa306-305">ux_host_stack_transfer_request_abort</span></span>

<span data-ttu-id="fa306-306">Przerywanie oczekującego żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="fa306-306">Abort a pending transfer request.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-307">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-307">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="fa306-308">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-308">Description</span></span>

<span data-ttu-id="fa306-309">Ta funkcja przerywa oczekujące żądanie transferu, które zostało wcześniej przesłane.</span><span class="sxs-lookup"><span data-stu-id="fa306-309">This function aborts a pending transfer request that has been previously submitted.</span></span> <span data-ttu-id="fa306-310">Ta funkcja tylko Anuluje określone żądanie transferu.</span><span class="sxs-lookup"><span data-stu-id="fa306-310">This function only cancels a specific transfer request.</span></span> <span data-ttu-id="fa306-311">Wywołanie z powrotem do funkcji będzie miało stan UX_TRANSFER REQUEST_STATUS_ABORT.</span><span class="sxs-lookup"><span data-stu-id="fa306-311">The call back to the function will have the UX_TRANSFER REQUEST_STATUS_ABORT status.</span></span>

### <a name="parameters"></a><span data-ttu-id="fa306-312">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa306-312">Parameters</span></span>

- <span data-ttu-id="fa306-313">**żądanie transferu** Wskaźnik do żądania przeniesienia, które ma zostać przerwane.</span><span class="sxs-lookup"><span data-stu-id="fa306-313">**transfer request** Pointer to the transfer request to be aborted.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-314">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-314">Return Values</span></span>

- <span data-ttu-id="fa306-315">**UX_SUCCESS** (0x00) anulowano transfer USB dla tego żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="fa306-315">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was canceled.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-316">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa306-316">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="fa306-317">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="fa306-317">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="fa306-318">Zażądaj transferu USB.</span><span class="sxs-lookup"><span data-stu-id="fa306-318">Request a USB transfer.</span></span>

### <a name="prototype"></a><span data-ttu-id="fa306-319">Prototype</span><span class="sxs-lookup"><span data-stu-id="fa306-319">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="fa306-320">Opis</span><span class="sxs-lookup"><span data-stu-id="fa306-320">Description</span></span>

<span data-ttu-id="fa306-321">Ta funkcja wykonuje transakcję USB.</span><span class="sxs-lookup"><span data-stu-id="fa306-321">This function performs a USB transaction.</span></span> <span data-ttu-id="fa306-322">Po wprowadzeniu żądanie transferu zapewnia potok punktu końcowego wybrany dla tej transakcji i parametry skojarzone z transferem (ładunek danych, Długość transakcji).</span><span class="sxs-lookup"><span data-stu-id="fa306-322">On entry the transfer request gives the endpoint pipe selected for this transaction and the parameters associated with the transfer (data payload, length of transaction).</span></span> <span data-ttu-id="fa306-323">W przypadku potoku kontroli transakcja jest zablokowana i zwróci się tylko wtedy, gdy trzy fazy transferu kontroli zostały zakończone lub wystąpił poprzedni błąd.</span><span class="sxs-lookup"><span data-stu-id="fa306-323">For Control pipe, the transaction is blocking and will only return when the three phases of the control transfer have been completed or if there is a previous error.</span></span> <span data-ttu-id="fa306-324">W przypadku innych potoków stos USB będzie planować transakcję na USB, ale nie czeka na jego zakończenie.</span><span class="sxs-lookup"><span data-stu-id="fa306-324">For other pipes, the USB stack will schedule the transaction on the USB but will not wait for its completion.</span></span> <span data-ttu-id="fa306-325">Każde żądanie transferu dla potoków nieblokujących musi określać procedurę obsługi procedury uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="fa306-325">Each transfer request for non-blocking pipes has to specify a completion routine handler.</span></span>

<span data-ttu-id="fa306-326">Gdy wywołanie funkcji zwraca, stan żądania przeniesienia powinien zostać zbadany, ponieważ zawiera wynik transakcji.</span><span class="sxs-lookup"><span data-stu-id="fa306-326">When the function call returns, the status of the transfer request should be examined as it contains the result of the transaction.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="fa306-327">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="fa306-327">Input Parameter</span></span>

- <span data-ttu-id="fa306-328">**transfer_request** Wskaźnik na żądanie transferu.</span><span class="sxs-lookup"><span data-stu-id="fa306-328">**transfer_request** Pointer to the transfer request.</span></span> <span data-ttu-id="fa306-329">Żądanie transferu zawiera wszystkie niezbędne informacje wymagane do przeniesienia.</span><span class="sxs-lookup"><span data-stu-id="fa306-329">The transfer request contains all the necessary information required for the transfer.</span></span>

### <a name="return-values"></a><span data-ttu-id="fa306-330">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="fa306-330">Return Values</span></span>

- <span data-ttu-id="fa306-331">**UX_SUCCESS** (0x00) transfer USB dla tego żądania transferu został zaplanowany prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="fa306-331">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was scheduled properly.</span></span> <span data-ttu-id="fa306-332">Kod stanu żądania przeniesienia należy sprawdzić po zakończeniu żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="fa306-332">The status code of the transfer request should be examined when the transfer request completes.</span></span>
- <span data-ttu-id="fa306-333">**UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci, aby przydzielić wymagane zasoby kontrolera.</span><span class="sxs-lookup"><span data-stu-id="fa306-333">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to allocate the necessary controller resources.</span></span>
- <span data-ttu-id="fa306-334">**UX_TRANSFER_NOT_READY** (0x25) urządzenie było w nieprawidłowym stanie — musi być dołączone, rozkierowane lub skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="fa306-334">**UX_TRANSFER_NOT_READY** (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>

### <a name="example"></a><span data-ttu-id="fa306-335">Przykład:</span><span class="sxs-lookup"><span data-stu-id="fa306-335">Example:</span></span>

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
