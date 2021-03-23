---
title: Rozdział 4 — Opis usług urządzenia USBX
description: Dowiedz się więcej na temat usług urządzenia USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824042"
---
# <a name="description-of-usbx-device-services"></a><span data-ttu-id="a0361-103">Opis usług urządzenia USBX</span><span class="sxs-lookup"><span data-stu-id="a0361-103">Description of USBX Device Services</span></span>

### <a name="ux_device_stack_alternate_setting_get"></a><span data-ttu-id="a0361-104">ux_device_stack_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="a0361-104">ux_device_stack_alternate_setting_get</span></span>

<span data-ttu-id="a0361-105">Pobierz bieżące ustawienie alternatywne dla wartości interfejsu</span><span class="sxs-lookup"><span data-stu-id="a0361-105">Get current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-106">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-106">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a><span data-ttu-id="a0361-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-107">Description</span></span>

<span data-ttu-id="a0361-108">Ta funkcja jest używana przez hosta USB do uzyskiwania bieżącego alternatywnego ustawienia dla określonej wartości interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-108">This function is used by the USB host to obtain the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="a0361-109">Jest on wywoływany przez sterownik kontrolera po odebraniu żądania **GET_INTERFACE** .</span><span class="sxs-lookup"><span data-stu-id="a0361-109">It is called by the controller driver when a **GET_INTERFACE** request is received.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-110">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-110">Input Parameter</span></span>

- <span data-ttu-id="a0361-111">**Interface_value** Wartość interfejsu, dla którego jest wysyłane zapytanie do bieżącego ustawienia alternatywnego</span><span class="sxs-lookup"><span data-stu-id="a0361-111">**Interface_value** Interface value for which the current alternate setting is queried</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-112">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-112">Return Values</span></span>

- <span data-ttu-id="a0361-113">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="a0361-113">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="a0361-114">**UX_ERROR** (0Xff) Nieprawidłowa wartość interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-114">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-115">Example</span></span>

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a><span data-ttu-id="a0361-116">ux_device_stack_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="a0361-116">ux_device_stack_alternate_setting_set</span></span>

<span data-ttu-id="a0361-117">Ustaw bieżące ustawienie alternatywne dla wartości interfejsu</span><span class="sxs-lookup"><span data-stu-id="a0361-117">Set current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-118">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-118">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="a0361-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-119">Description</span></span>

<span data-ttu-id="a0361-120">Ta funkcja jest używana przez hosta USB do ustawiania bieżącego alternatywnego ustawienia dla określonej wartości interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-120">This function is used by the USB host to set the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="a0361-121">Jest on wywoływany przez sterownik kontrolera po odebraniu żądania **SET_INTERFACE** .</span><span class="sxs-lookup"><span data-stu-id="a0361-121">It is called by the controller driver when a **SET_INTERFACE** request is received.</span></span> <span data-ttu-id="a0361-122">Po zakończeniu **SET_INTERFACE** wartości ustawień alternatywnych są stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="a0361-122">When the **SET_INTERFACE** is completed, the values of the alternate settings are applied to the class.</span></span>

<span data-ttu-id="a0361-123">Stos urządzeń będzie wystawiał **UX_SLAVE_CLASS_COMMAND_CHANGE** do klasy, która jest właścicielem tego interfejsu w celu odzwierciedlenia zmiany ustawienia alternatywnego.</span><span class="sxs-lookup"><span data-stu-id="a0361-123">The device stack will issue a **UX_SLAVE_CLASS_COMMAND_CHANGE** to the class that owns this interface to reflect the change of alternate setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-124">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-124">Parameters</span></span>

- <span data-ttu-id="a0361-125">**interface_value**: wartość interfejsu, dla którego ustawiono bieżące ustawienie alternatywne.</span><span class="sxs-lookup"><span data-stu-id="a0361-125">**interface_value**: Interface value for which the current alternate setting is set.</span></span>
- <span data-ttu-id="a0361-126">**alternate_setting_value**: Nowa wartość ustawienia alternatywnego.</span><span class="sxs-lookup"><span data-stu-id="a0361-126">**alternate_setting_value**: The new alternate setting value.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-127">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-127">Return Values</span></span>

- <span data-ttu-id="a0361-128">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="a0361-128">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="a0361-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0X52) brak dołączonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) No interface attached.</span></span>
- <span data-ttu-id="a0361-130">Urządzenie **UX_FUNCTION_NOT_SUPPORTED** (0x54) nie jest skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="a0361-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Device is not configured.</span></span>
- <span data-ttu-id="a0361-131">**UX_ERROR** (0Xff) Nieprawidłowa wartość interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-131">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-132">Example</span></span>

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a><span data-ttu-id="a0361-133">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="a0361-133">ux_device_stack_class_register</span></span>

<span data-ttu-id="a0361-134">Rejestrowanie nowej klasy urządzeń USB</span><span class="sxs-lookup"><span data-stu-id="a0361-134">Register a new USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-135">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-135">Prototype</span></span>

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="a0361-136">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-136">Description</span></span>

<span data-ttu-id="a0361-137">Ta funkcja jest używana przez aplikację do zarejestrowania nowej klasy urządzenia USB.</span><span class="sxs-lookup"><span data-stu-id="a0361-137">This function is used by the application to register a new USB device class.</span></span> <span data-ttu-id="a0361-138">Ta rejestracja uruchamia kontener klasy, a nie wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="a0361-138">This registration starts a class container and not an instance of the class.</span></span> <span data-ttu-id="a0361-139">Klasa powinna mieć aktywny wątek i być dołączona do określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-139">A class should have an active thread and be attached to a specific interface.</span></span>

<span data-ttu-id="a0361-140">Niektóre klasy oczekują parametru lub listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="a0361-140">Some classes expect a parameter or parameter list.</span></span> <span data-ttu-id="a0361-141">Na przykład Klasa magazynu urządzenia powinna oczekiwać geometrii urządzenia magazynującego, które próbuje emulować.</span><span class="sxs-lookup"><span data-stu-id="a0361-141">For instance, the device storage class would expect the geometry of the storage device it is trying to emulate.</span></span> <span data-ttu-id="a0361-142">W związku z tym pole parametru jest zależne od wymaganej klasy i może być wartością lub wskaźnikiem do struktury wypełnionej wartościami klasy.</span><span class="sxs-lookup"><span data-stu-id="a0361-142">The parameter field is therefore dependent on the class requirement and can be a value or a pointer to a structure filled with the class values.</span></span>

> [!NOTE]
> <span data-ttu-id="a0361-143">Ciąg C class_name musi być zakończony zerem i długością (bez samego terminatora NULL) nie może być większy niż **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="a0361-143">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-144">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-144">Parameters</span></span>

- <span data-ttu-id="a0361-145">**class_name** Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="a0361-145">**class_name** Class Name</span></span>
- <span data-ttu-id="a0361-146">**class_entry_function** Funkcja wejścia klasy.</span><span class="sxs-lookup"><span data-stu-id="a0361-146">**class_entry_function** The entry function of the class.</span></span>
- <span data-ttu-id="a0361-147">**configuration_number** Numer konfiguracji, do której jest dołączona Ta klasa.</span><span class="sxs-lookup"><span data-stu-id="a0361-147">**configuration_number** The configuration number this class is attached to.</span></span>
- <span data-ttu-id="a0361-148">**interface_number** Numer interfejsu, do którego jest dołączona Ta klasa.</span><span class="sxs-lookup"><span data-stu-id="a0361-148">**interface_number** The interface number this class is attached to.</span></span>
- <span data-ttu-id="a0361-149">**parametr** Wskaźnik do listy parametrów specyficznych dla klasy.</span><span class="sxs-lookup"><span data-stu-id="a0361-149">**parameter** A pointer to a class specific parameter list.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-150">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-150">Return Values</span></span>

- <span data-ttu-id="a0361-151">**UX_SUCCESS** (0x00) Klasa została zarejestrowana</span><span class="sxs-lookup"><span data-stu-id="a0361-151">**UX_SUCCESS** (0x00) The class was registered</span></span>
- <span data-ttu-id="a0361-152">**UX_MEMORY_INSUFFICIENT** (0X12) nie pozostało wpisów w tabeli klas.</span><span class="sxs-lookup"><span data-stu-id="a0361-152">**UX_MEMORY_INSUFFICIENT** (0x12) No entries left in class table.</span></span>
- <span data-ttu-id="a0361-153">**UX_THREAD_ERROR** (0X16) nie może utworzyć wątku klasy.</span><span class="sxs-lookup"><span data-stu-id="a0361-153">**UX_THREAD_ERROR** (0x16) Cannot create a class thread.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-154">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a><span data-ttu-id="a0361-155">ux_device_stack_class_unregister</span><span class="sxs-lookup"><span data-stu-id="a0361-155">ux_device_stack_class_unregister</span></span>

<span data-ttu-id="a0361-156">Wyrejestrowywanie klasy urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="a0361-156">Unregister a USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-157">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-157">Prototype</span></span>

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a><span data-ttu-id="a0361-158">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-158">Description</span></span>

<span data-ttu-id="a0361-159">Ta funkcja jest używana przez aplikację do wyrejestrowywania klasy urządzenia USB.</span><span class="sxs-lookup"><span data-stu-id="a0361-159">This function is used by the application to unregister a USB device class.</span></span>

> [!NOTE]
> <span data-ttu-id="a0361-160">Ciąg C class_name musi być zakończony zerem i długością (bez samego terminatora NULL) nie może być większy niż **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="a0361-160">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-161">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-161">Parameters</span></span>

- <span data-ttu-id="a0361-162">**class_name**: Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="a0361-162">**class_name**: Class Name</span></span>
- <span data-ttu-id="a0361-163">**class_entry_function**: funkcja wejścia klasy.</span><span class="sxs-lookup"><span data-stu-id="a0361-163">**class_entry_function**: The entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-164">Return Values</span></span>

- <span data-ttu-id="a0361-165">**UX_SUCCESS** (0x00) wyrejestrowano klasę.</span><span class="sxs-lookup"><span data-stu-id="a0361-165">**UX_SUCCESS** (0x00) The class was unregistered.</span></span>
- <span data-ttu-id="a0361-166">**UX_NO_CLASS_MATCH** (0x57) Klasa nie jest zarejestrowana.</span><span class="sxs-lookup"><span data-stu-id="a0361-166">**UX_NO_CLASS_MATCH** (0x57) The class isn't registered.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-167">Example</span></span>

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a><span data-ttu-id="a0361-168">ux_device_stack_configuration_get</span><span class="sxs-lookup"><span data-stu-id="a0361-168">ux_device_stack_configuration_get</span></span>

<span data-ttu-id="a0361-169">Pobierz bieżącą konfigurację</span><span class="sxs-lookup"><span data-stu-id="a0361-169">Get the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-170">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-170">Prototype</span></span>

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a><span data-ttu-id="a0361-171">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-171">Description</span></span>

<span data-ttu-id="a0361-172">Ta funkcja jest używana przez hosta w celu uzyskania bieżącej konfiguracji uruchomionej na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="a0361-172">This function is used by the host to obtain the current configuration running in the device.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-173">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-173">Input Parameter</span></span>

<span data-ttu-id="a0361-174">Brak</span><span class="sxs-lookup"><span data-stu-id="a0361-174">None</span></span>

### <a name="return-value"></a><span data-ttu-id="a0361-175">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0361-175">Return Value</span></span>

- <span data-ttu-id="a0361-176">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="a0361-176">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-177">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="a0361-178">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="a0361-178">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="a0361-179">Ustaw bieżącą konfigurację</span><span class="sxs-lookup"><span data-stu-id="a0361-179">Set the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-180">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-180">Prototype</span></span>

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a><span data-ttu-id="a0361-181">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-181">Description</span></span>

<span data-ttu-id="a0361-182">Ta funkcja jest używana przez hosta do ustawiania bieżącej konfiguracji działającej na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="a0361-182">This function is used by the host to set the current configuration running in the device.</span></span> <span data-ttu-id="a0361-183">Po odebraniu tego polecenia stos urządzeń USB uaktywni ustawienie alternatywny 0 każdego interfejsu połączonego z tą konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="a0361-183">Upon reception of this command, the USB device stack will activate the alternate setting 0 of each interface connected to this configuration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-184">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-184">Input Parameter</span></span>

- <span data-ttu-id="a0361-185">**configuration_value** Wartość konfiguracji wybrana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="a0361-185">**configuration_value** The configuration value selected by the host.</span></span>

### <a name="return-value"></a><span data-ttu-id="a0361-186">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0361-186">Return Value</span></span>

- <span data-ttu-id="a0361-187">**UX_SUCCESS** (0x00) konfiguracja została pomyślnie ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a0361-187">**UX_SUCCESS** (0x00) The configuration was successfully set.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-188">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-188">Example</span></span>

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="a0361-189">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="a0361-189">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="a0361-190">Wyślij deskryptor do hosta</span><span class="sxs-lookup"><span data-stu-id="a0361-190">Send a descriptor to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-191">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-191">Prototype</span></span>

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="a0361-192">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-192">Description</span></span>

<span data-ttu-id="a0361-193">Ta funkcja jest używana przez stronę urządzenia do zwrócenia deskryptora do hosta.</span><span class="sxs-lookup"><span data-stu-id="a0361-193">This function is used by the device side to return a descriptor to the host.</span></span> <span data-ttu-id="a0361-194">Ten deskryptor może być deskryptorem urządzenia, deskryptorem konfiguracji lub deskryptorem ciągu.</span><span class="sxs-lookup"><span data-stu-id="a0361-194">This descriptor can be a device descriptor, a configuration descriptor or a string descriptor.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-195">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-195">Parameters</span></span>

- <span data-ttu-id="a0361-196">**descriptor_type**: typ deskryptora.</span><span class="sxs-lookup"><span data-stu-id="a0361-196">**descriptor_type**: The type of the descriptor.</span></span> <span data-ttu-id="a0361-197">Musi mieć jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="a0361-197">Must be one of the following values.</span></span>
  - <span data-ttu-id="a0361-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a0361-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a0361-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a0361-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a0361-200">**UX_STRING_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a0361-200">**UX_STRING_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a0361-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a0361-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a0361-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a0361-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span></span>
- <span data-ttu-id="a0361-203">**request_index**: indeks deskryptora.</span><span class="sxs-lookup"><span data-stu-id="a0361-203">**request_index**: The index of the descriptor.</span></span>
- <span data-ttu-id="a0361-204">**host_length**: długość wymagana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="a0361-204">**host_length**: The length required by the host.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-205">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-205">Return Values</span></span>

- <span data-ttu-id="a0361-206">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="a0361-206">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="a0361-207">**UX_ERROR** (0xFF) transfer nie został ukończony.</span><span class="sxs-lookup"><span data-stu-id="a0361-207">**UX_ERROR** (0xFF) The transfer was not completed.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-208">Example</span></span>

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="a0361-209">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="a0361-209">ux_device_stack_disconnect</span></span>

<span data-ttu-id="a0361-210">Odłącz stos urządzeń</span><span class="sxs-lookup"><span data-stu-id="a0361-210">Disconnect device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-211">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-211">Prototype</span></span>

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a><span data-ttu-id="a0361-212">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-212">Description</span></span>

<span data-ttu-id="a0361-213">Menedżer VBUS wywołuje tę funkcję w przypadku odłączenia urządzenia.</span><span class="sxs-lookup"><span data-stu-id="a0361-213">The VBUS manager calls this function when there is a device disconnection.</span></span> <span data-ttu-id="a0361-214">Stos urządzeń będzie powiadamiał wszystkie klasy zarejestrowane na tym urządzeniu i następnie zwolni wszystkie zasoby urządzenia.</span><span class="sxs-lookup"><span data-stu-id="a0361-214">The device stack will inform all classes registered to this device and will thereafter release all the device resources.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-215">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-215">Input Parameter</span></span>

<span data-ttu-id="a0361-216">Brak</span><span class="sxs-lookup"><span data-stu-id="a0361-216">None</span></span>

### <a name="return-value"></a><span data-ttu-id="a0361-217">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0361-217">Return Value</span></span>

- <span data-ttu-id="a0361-218">**UX_SUCCESS** (0x00) urządzenie zostało rozłączone.</span><span class="sxs-lookup"><span data-stu-id="a0361-218">**UX_SUCCESS** (0x00) The device was disconnected.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-219">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-219">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="a0361-220">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="a0361-220">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="a0361-221">Warunek zatrzymania punktu końcowego żądania</span><span class="sxs-lookup"><span data-stu-id="a0361-221">Request endpoint Stall condition</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-222">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-222">Prototype</span></span>

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a><span data-ttu-id="a0361-223">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-223">Description</span></span>

<span data-ttu-id="a0361-224">Ta funkcja jest wywoływana przez klasę urządzenia USB, gdy punkt końcowy powinien zwrócić warunek parkingowy do hosta.</span><span class="sxs-lookup"><span data-stu-id="a0361-224">This function is called by the USB device class when an endpoint should return a Stall condition to the host.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-225">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-225">Input Parameter</span></span>

- <span data-ttu-id="a0361-226">**punkt końcowy** Punkt końcowy, dla którego zażądano warunku parkingowego.</span><span class="sxs-lookup"><span data-stu-id="a0361-226">**endpoint** The endpoint on which the Stall condition is requested.</span></span>

### <a name="return-value"></a><span data-ttu-id="a0361-227">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0361-227">Return Value</span></span>

- <span data-ttu-id="a0361-228">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-228">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a0361-229">**UX_ERROR** (0xFF) urządzenie jest w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="a0361-229">**UX_ERROR** (0xFF) The device is in an invalid state.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-230">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-230">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="a0361-231">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="a0361-231">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="a0361-232">Wznawianie działania hosta</span><span class="sxs-lookup"><span data-stu-id="a0361-232">Wake up the host</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-233">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-233">Prototype</span></span>

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a><span data-ttu-id="a0361-234">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-234">Description</span></span>

<span data-ttu-id="a0361-235">Ta funkcja jest wywoływana, gdy urządzenie chce wznowić działanie hosta.</span><span class="sxs-lookup"><span data-stu-id="a0361-235">This function is called when the device wants to wake up the host.</span></span> <span data-ttu-id="a0361-236">To polecenie jest prawidłowe tylko wtedy, gdy urządzenie jest w trybie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="a0361-236">This command is only valid when the device is in suspend mode.</span></span> <span data-ttu-id="a0361-237">Aby określić, kiedy ma wznowić hosta USB, należy do aplikacji urządzenia.</span><span class="sxs-lookup"><span data-stu-id="a0361-237">It is up to the device application to decide when it wants to wake up the USB host.</span></span> <span data-ttu-id="a0361-238">Na przykład modem USB może wznowić Host po wykryciu sygnału PIERŚCIENIowego w linii telefonicznej.</span><span class="sxs-lookup"><span data-stu-id="a0361-238">For instance, a USB modem can wake up a host when it detects a RING signal on the telephone line.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-239">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-239">Input Parameter</span></span>

<span data-ttu-id="a0361-240">Brak</span><span class="sxs-lookup"><span data-stu-id="a0361-240">None</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-241">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="a0361-241">Return values</span></span>

- <span data-ttu-id="a0361-242">**UX_SUCCESS** (0x00) wywołanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-242">**UX_SUCCESS** (0x00) The call was successful.</span></span>
- <span data-ttu-id="a0361-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) wywołanie nie powiodło się (urządzenie prawdopodobnie nie jest w trybie zawieszenia).</span><span class="sxs-lookup"><span data-stu-id="a0361-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) The call failed (the device was probably not in the suspended mode).</span></span>

### <a name="example"></a><span data-ttu-id="a0361-244">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-244">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a><span data-ttu-id="a0361-245">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="a0361-245">ux_device_stack_initialize</span></span>

<span data-ttu-id="a0361-246">Zainicjuj stos urządzeń USB</span><span class="sxs-lookup"><span data-stu-id="a0361-246">Initialize USB device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-247">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-247">Prototype</span></span>

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a><span data-ttu-id="a0361-248">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-248">Description</span></span>

<span data-ttu-id="a0361-249">Ta funkcja jest wywoływana przez aplikację w celu zainicjowania stosu urządzeń USB.</span><span class="sxs-lookup"><span data-stu-id="a0361-249">This function is called by the application to initialize the USB device stack.</span></span> <span data-ttu-id="a0361-250">Nie inicjuje żadnych klas ani żadnych kontrolerów.</span><span class="sxs-lookup"><span data-stu-id="a0361-250">It does not initialize any classes or any controllers.</span></span> <span data-ttu-id="a0361-251">Należy to zrobić z oddzielnymi wywołaniami funkcji.</span><span class="sxs-lookup"><span data-stu-id="a0361-251">This should be done with separate function calls.</span></span> <span data-ttu-id="a0361-252">To wywołanie głównie zapewnia stos z platformą urządzenia dla funkcji USB.</span><span class="sxs-lookup"><span data-stu-id="a0361-252">This call mainly provides the stack with the device framework for the USB function.</span></span> <span data-ttu-id="a0361-253">Obsługuje zarówno wysoką, jak i pełną szybkość, z możliwością posiadania całkowicie oddzielnej struktury urządzenia dla każdej szybkości.</span><span class="sxs-lookup"><span data-stu-id="a0361-253">It supports both high and full speeds with the possibility to have completely separate device framework for each speed.</span></span> <span data-ttu-id="a0361-254">Obsługiwane są struktury ciągów i wiele języków.</span><span class="sxs-lookup"><span data-stu-id="a0361-254">String framework and multiple languages are supported.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-255">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-255">Parameters</span></span>

- <span data-ttu-id="a0361-256">**device_framework_high_speed**: wskaźnik do struktury o dużej szybkości.</span><span class="sxs-lookup"><span data-stu-id="a0361-256">**device_framework_high_speed**: Pointer to the high speed framework.</span></span>
- <span data-ttu-id="a0361-257">**device_framework_length_high_speed**: długość platformy o dużej szybkości.</span><span class="sxs-lookup"><span data-stu-id="a0361-257">**device_framework_length_high_speed**: Length of the high speed framework.</span></span>
- <span data-ttu-id="a0361-258">**device_framework_full_speed**: wskaźnik do struktury pełnej prędkości.</span><span class="sxs-lookup"><span data-stu-id="a0361-258">**device_framework_full_speed**: Pointer to the full speed framework.</span></span>
- <span data-ttu-id="a0361-259">**device_framework_length_full_speed**: długość struktury pełnej prędkości.</span><span class="sxs-lookup"><span data-stu-id="a0361-259">**device_framework_length_full_speed**: Length of the full speed framework.</span></span>
- <span data-ttu-id="a0361-260">**string_framework**: wskaźnik do struktury String.</span><span class="sxs-lookup"><span data-stu-id="a0361-260">**string_framework**: Pointer to string framework.</span></span>
- <span data-ttu-id="a0361-261">**string_framework_length**: długość struktury ciągu.</span><span class="sxs-lookup"><span data-stu-id="a0361-261">**string_framework_length**: Length of string framework.</span></span>
- <span data-ttu-id="a0361-262">**language_id_framework**: wskaźnik do struktury języka ciągu.</span><span class="sxs-lookup"><span data-stu-id="a0361-262">**language_id_framework**: Pointer to string language framework.</span></span>
- <span data-ttu-id="a0361-263">**language_id_framework_length**: długość struktury języka String.</span><span class="sxs-lookup"><span data-stu-id="a0361-263">**language_id_framework_length**: Length of the string language framework.</span></span>
- <span data-ttu-id="a0361-264">**ux_system_slave_change_function**: funkcja, która ma być wywoływana w przypadku zmiany stanu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="a0361-264">**ux_system_slave_change_function**: Function to be called when the device state changes.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-265">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-265">Return Values</span></span>

- <span data-ttu-id="a0361-266">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-266">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a0361-267">**UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci, aby zainicjować stos.</span><span class="sxs-lookup"><span data-stu-id="a0361-267">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to initialize the stack.</span></span>
- <span data-ttu-id="a0361-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) deskryptor jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a0361-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) The descriptor is invalid.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-269">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-269">Example</span></span>

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="a0361-270">Aplikacja może zażądać wywołania zwrotnego, gdy kontroler zmieni swój stan.</span><span class="sxs-lookup"><span data-stu-id="a0361-270">The application can request a call back when the controller changes its state.</span></span> <span data-ttu-id="a0361-271">Dwa główne Stany kontrolera to:</span><span class="sxs-lookup"><span data-stu-id="a0361-271">The two main states for the controller are:</span></span>

- <span data-ttu-id="a0361-272">**UX_DEVICE_SUSPENDED**</span><span class="sxs-lookup"><span data-stu-id="a0361-272">**UX_DEVICE_SUSPENDED**</span></span>
- <span data-ttu-id="a0361-273">**UX_DEVICE_RESUMED**</span><span class="sxs-lookup"><span data-stu-id="a0361-273">**UX_DEVICE_RESUMED**</span></span>

<span data-ttu-id="a0361-274">Jeśli aplikacja nie wymaga sygnałów wstrzymywania/wznawiania, może dostarczyć funkcję UX_NULL.</span><span class="sxs-lookup"><span data-stu-id="a0361-274">If the application does not need Suspend/Resume signals, it would supply a UX_NULL function.</span></span>

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="a0361-275">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="a0361-275">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="a0361-276">Usuwanie interfejsu stosu</span><span class="sxs-lookup"><span data-stu-id="a0361-276">Delete a stack interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-277">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-277">Prototype</span></span>

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="a0361-278">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-278">Description</span></span>

<span data-ttu-id="a0361-279">Ta funkcja jest wywoływana, gdy interfejs powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="a0361-279">This function is called when an interface should be removed.</span></span> <span data-ttu-id="a0361-280">Interfejs jest usuwany podczas wyodrębniania urządzenia lub po zresetowaniu magistrali lub gdy jest dostępne nowe ustawienie alternatywne.</span><span class="sxs-lookup"><span data-stu-id="a0361-280">An interface is either removed when a device is extracted, or following a bus reset, or when there is a new alternate setting.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-281">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-281">Input Parameter</span></span>

- <span data-ttu-id="a0361-282">**interfejs**: wskaźnik do interfejsu, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="a0361-282">**interface**: Pointer to the interface to remove.</span></span>

### <a name="return-value"></a><span data-ttu-id="a0361-283">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0361-283">Return Value</span></span>

- <span data-ttu-id="a0361-284">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-284">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-285">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-285">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="a0361-286">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="a0361-286">ux_device_stack_interface_get</span></span>

<span data-ttu-id="a0361-287">Pobierz bieżącą wartość interfejsu</span><span class="sxs-lookup"><span data-stu-id="a0361-287">Get the current interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-288">Prototype</span></span>

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a><span data-ttu-id="a0361-289">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-289">Description</span></span>

<span data-ttu-id="a0361-290">Ta funkcja jest wywoływana, gdy Host wysyła zapytanie do bieżącego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-290">This function is called when the host queries the current interface.</span></span> <span data-ttu-id="a0361-291">Urządzenie zwraca bieżącą wartość interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-291">The device returns the current interface value.</span></span>

> [!NOTE]
> <span data-ttu-id="a0361-292">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a0361-292">This function is deprecated.</span></span> <span data-ttu-id="a0361-293">Jest on dostępny dla starszego oprogramowania, ale zamiast tego należy użyć funkcji ***ux_device_stack_alternate_setting_get*** .</span><span class="sxs-lookup"><span data-stu-id="a0361-293">It is available for legacy software, but new software should use the ***ux_device_stack_alternate_setting_get*** function instead.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-294">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-294">Input Parameter</span></span>

- <span data-ttu-id="a0361-295">**interface_value** Wartość interfejsu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="a0361-295">**interface_value** Interface value to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-296">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-296">Return Values</span></span>

- <span data-ttu-id="a0361-297">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-297">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a0361-298">**UX_ERROR** (0Xff) nie istnieje interfejs.</span><span class="sxs-lookup"><span data-stu-id="a0361-298">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-299">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-299">Example</span></span>

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="a0361-300">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="a0361-300">ux_device_stack_interface_set</span></span>

<span data-ttu-id="a0361-301">Zmiana alternatywnego ustawienia interfejsu</span><span class="sxs-lookup"><span data-stu-id="a0361-301">Change the alternate setting of the interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-302">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-302">Prototype</span></span>

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="a0361-303">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-303">Description</span></span>

<span data-ttu-id="a0361-304">Ta funkcja jest wywoływana, gdy host żąda zmiany ustawienia alternatywnego dla interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-304">This function is called when the host requests a change of the alternate setting for the interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-305">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-305">Parameters</span></span>

- <span data-ttu-id="a0361-306">**device_framework**: adres platformy urządzenia dla tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-306">**device_framework**: Address of the device framework for this interface.</span></span>
- <span data-ttu-id="a0361-307">**device_framework_length**: długość platformy urządzeń.</span><span class="sxs-lookup"><span data-stu-id="a0361-307">**device_framework_length**: Length of the device framework.</span></span>
- <span data-ttu-id="a0361-308">**alternate_setting_value**: wartość ustawienia alternatywnego, która ma być używana przez ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="a0361-308">**alternate_setting_value**: Alternate setting value to be used by this interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-309">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-309">Return Values</span></span>

- <span data-ttu-id="a0361-310">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-310">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a0361-311">**UX_ERROR** (0Xff) nie istnieje interfejs.</span><span class="sxs-lookup"><span data-stu-id="a0361-311">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-312">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-312">Example</span></span>

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a><span data-ttu-id="a0361-313">ux_device_stack_interface_start</span><span class="sxs-lookup"><span data-stu-id="a0361-313">ux_device_stack_interface_start</span></span>

<span data-ttu-id="a0361-314">Rozpocznij wyszukiwanie klasy jako należącej do wystąpienia interfejsu</span><span class="sxs-lookup"><span data-stu-id="a0361-314">Start search for a class to own an interface instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-315">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-315">Prototype</span></span>

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="a0361-316">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-316">Description</span></span>

<span data-ttu-id="a0361-317">Ta funkcja jest wywoływana, gdy interfejs został wybrany przez hosta, a stos urządzenia musi wyszukać klasę urządzenia, aby było to wystąpienie tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-317">This function is called when an interface has been selected by the host and the device stack needs to search for a device class to own this interface instance.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a0361-318">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="a0361-318">Input Parameter</span></span>

- <span data-ttu-id="a0361-319">**interfejs**: wskaźnik do utworzonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-319">**interface**: Pointer to the interface created.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-320">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-320">Return Values</span></span>

- <span data-ttu-id="a0361-321">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-321">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a0361-322">**UX_NO_CLASS_MATCH** (0X57) nie istnieje Klasa dla tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0361-322">**UX_NO_CLASS_MATCH** (0x57) No class exists for this interface.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-323">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-323">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="a0361-324">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="a0361-324">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="a0361-325">Żądanie przeniesienia danych do hosta</span><span class="sxs-lookup"><span data-stu-id="a0361-325">Request to transfer data to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-326">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-326">Prototype</span></span>

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="a0361-327">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-327">Description</span></span>

<span data-ttu-id="a0361-328">Ta funkcja jest wywoływana, gdy Klasa lub stos chce przesłać dane do hosta.</span><span class="sxs-lookup"><span data-stu-id="a0361-328">This function is called when a class or the stack wants to transfer data to the host.</span></span> <span data-ttu-id="a0361-329">Host zawsze sonduje urządzenie, ale urządzenie może z wyprzedzeniem przygotować dane.</span><span class="sxs-lookup"><span data-stu-id="a0361-329">The host always polls the device but the device can prepare data in advance.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-330">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-330">Parameters</span></span>

- <span data-ttu-id="a0361-331">**transfer_request**: wskaźnik do żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="a0361-331">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="a0361-332">**slave_length**: długość urządzenia chce zwrócić.</span><span class="sxs-lookup"><span data-stu-id="a0361-332">**slave_length**: Length the device wants to return.</span></span>
- <span data-ttu-id="a0361-333">**host_length**: długość żądania hosta.</span><span class="sxs-lookup"><span data-stu-id="a0361-333">**host_length**: Length the host has requested.</span></span>

### <a name="return-values"></a><span data-ttu-id="a0361-334">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a0361-334">Return Values</span></span>

- <span data-ttu-id="a0361-335">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-335">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a0361-336">**UX_TRANSFER_NOT_READY** (0x25) urządzenie jest w nieprawidłowym stanie; należy ją **dołączyć**, **skonfigurować** lub **rozwiązać**.</span><span class="sxs-lookup"><span data-stu-id="a0361-336">**UX_TRANSFER_NOT_READY** (0x25) The device is in an invalid state; it must be **ATTACHED**, **CONFIGURED**, or **ADDRESSED**.</span></span>
- <span data-ttu-id="a0361-337">Błąd transportu **UX_ERROR** (0xFF).</span><span class="sxs-lookup"><span data-stu-id="a0361-337">**UX_ERROR** (0xFF) Transport error.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-338">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-338">Example</span></span>

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="a0361-339">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="a0361-339">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="a0361-340">Anulowanie żądania przeniesienia</span><span class="sxs-lookup"><span data-stu-id="a0361-340">Cancel a transfer request</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-341">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-341">Prototype</span></span>

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a><span data-ttu-id="a0361-342">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-342">Description</span></span>

<span data-ttu-id="a0361-343">Ta funkcja jest wywoływana, gdy aplikacja musi anulować żądanie transferu lub kiedy stos musi przerwać żądanie transferu skojarzone z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="a0361-343">This function is called when an application needs to cancel a transfer request or when the stack needs to abort a transfer request associated with an endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-344">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-344">Parameters</span></span>

- <span data-ttu-id="a0361-345">**transfer_request**: wskaźnik do żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="a0361-345">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="a0361-346">**completion_code**: kod błędu do zwrócenia do klasy oczekującej na ukończenie tego żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="a0361-346">**completion_code**: Error code to be returned to the class waiting for this transfer request to complete.</span></span>

### <a name="return-value"></a><span data-ttu-id="a0361-347">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0361-347">Return Value</span></span>

- <span data-ttu-id="a0361-348">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-348">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="a0361-349">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0361-349">Example</span></span>

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a><span data-ttu-id="a0361-350">ux_device_stack_uninitialize</span><span class="sxs-lookup"><span data-stu-id="a0361-350">ux_device_stack_uninitialize</span></span>

<span data-ttu-id="a0361-351">Stos Unitialize</span><span class="sxs-lookup"><span data-stu-id="a0361-351">Unitialize stack</span></span>

### <a name="prototype"></a><span data-ttu-id="a0361-352">Prototype</span><span class="sxs-lookup"><span data-stu-id="a0361-352">Prototype</span></span>

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a><span data-ttu-id="a0361-353">Opis</span><span class="sxs-lookup"><span data-stu-id="a0361-353">Description</span></span>

<span data-ttu-id="a0361-354">Ta funkcja jest wywoływana, gdy aplikacja wymaga unitialize stosu urządzeń USBX — wszystkie zasoby stosu urządzeń są zwolnione.</span><span class="sxs-lookup"><span data-stu-id="a0361-354">This function is called when an application needs to unitialize the USBX device stack – all device stack resources are freed.</span></span> <span data-ttu-id="a0361-355">Ta nazwa powinna być wywoływana po wyrejestrowaniu wszystkich klas za pośrednictwem ux_device_stack_class_unregister.</span><span class="sxs-lookup"><span data-stu-id="a0361-355">This should be called after all classes have been unregistered via ux_device_stack_class_unregister.</span></span>

### <a name="parameters"></a><span data-ttu-id="a0361-356">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0361-356">Parameters</span></span>

<span data-ttu-id="a0361-357">Brak</span><span class="sxs-lookup"><span data-stu-id="a0361-357">None</span></span>

### <a name="return-value"></a><span data-ttu-id="a0361-358">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0361-358">Return Value</span></span>

<span data-ttu-id="a0361-359">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a0361-359">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
