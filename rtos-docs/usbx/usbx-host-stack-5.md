---
title: Rozdział 5 — interfejs API klas hostów USBX
description: Dowiedz się więcej o interfejsie API klas hostów USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824523"
---
# <a name="chapter-5---usbx-host-classes-api"></a><span data-ttu-id="3cf28-103">Rozdział 5 — interfejs API klas hostów USBX</span><span class="sxs-lookup"><span data-stu-id="3cf28-103">Chapter 5 - USBX Host Classes API</span></span>

<span data-ttu-id="3cf28-104">W tym rozdziale opisano wszystkie uwidocznione interfejsy API klas hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="3cf28-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="3cf28-105">Poniższe interfejsy API dla każdej klasy są szczegółowo opisane.</span><span class="sxs-lookup"><span data-stu-id="3cf28-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="3cf28-106">Klasa HID</span><span class="sxs-lookup"><span data-stu-id="3cf28-106">HID class</span></span>
- <span data-ttu-id="3cf28-107">Przechwytywanie zmian — Klasa ACM</span><span class="sxs-lookup"><span data-stu-id="3cf28-107">CDC-ACM class</span></span>
- <span data-ttu-id="3cf28-108">Reprzechwytywania — Klasa ECM</span><span class="sxs-lookup"><span data-stu-id="3cf28-108">CDC-ECM class</span></span>
- <span data-ttu-id="3cf28-109">Klasa magazynu</span><span class="sxs-lookup"><span data-stu-id="3cf28-109">Storage class</span></span>

## <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="3cf28-110">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="3cf28-110">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="3cf28-111">Zarejestruj klienta HID w klasie HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-111">Register a HID client to the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-112">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-112">Prototype</span></span>

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="3cf28-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-113">Description</span></span>

<span data-ttu-id="3cf28-114">Ta funkcja służy do rejestrowania klienta HID w klasie HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-114">This function is used to register a HID client to the HID class.</span></span> <span data-ttu-id="3cf28-115">Przed zażądaniem danych z tego urządzenia Klasa HID musi znaleźć dopasowanie między urządzeniem HID a klientem HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-115">The HID class needs to find a match between a HID device and HID client before requesting data from this device.</span></span>

> [!NOTE]
> <span data-ttu-id="3cf28-116">Ciąg C hid_client_name musi być zakończony zerem i długością (bez samego terminatora NULL) nie może być większy niż **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="3cf28-116">The C string of hid_client_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-117">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-117">Parameters</span></span>

- <span data-ttu-id="3cf28-118">**hid_client_name** Wskaźnik na nazwę klienta HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-118">**hid_client_name** Pointer to the HID client name.</span></span>
- <span data-ttu-id="3cf28-119">**hid_client_handler** Wskaźnik do programu obsługi klienta HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-119">**hid_client_handler** Pointer to the HID client handler.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-120">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-120">Return Values</span></span>

- <span data-ttu-id="3cf28-121">**UX_SUCCESS** (0x00) transfer danych został ukończony</span><span class="sxs-lookup"><span data-stu-id="3cf28-121">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="3cf28-122">Alokacja pamięci dla **UX_MEMORY_INSUFFICIENT** (0x12) dla klienta nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="3cf28-122">**UX_MEMORY_INSUFFICIENT** (0x12) Memory allocation for client failed.</span></span>
- <span data-ttu-id="3cf28-123">**UX_MEMORY_ARRAY_FULL** (0x1A) jest już zarejestrowana Maksymalna liczba klientów.</span><span class="sxs-lookup"><span data-stu-id="3cf28-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Max clients already registered.</span></span>
- <span data-ttu-id="3cf28-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0X58) Ta klasa już istnieje</span><span class="sxs-lookup"><span data-stu-id="3cf28-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) This class already exists</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-125">Example</span></span>

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a><span data-ttu-id="3cf28-126">ux_host_class_hid_report_callback_register</span><span class="sxs-lookup"><span data-stu-id="3cf28-126">ux_host_class_hid_report_callback_register</span></span>

<span data-ttu-id="3cf28-127">Zarejestruj wywołanie zwrotne z klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-127">Register a callback from the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-128">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-128">Prototype</span></span>

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a><span data-ttu-id="3cf28-129">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-129">Description</span></span>

<span data-ttu-id="3cf28-130">Ta funkcja służy do rejestrowania wywołania zwrotnego z klasy HID do klienta HID po odebraniu raportu.</span><span class="sxs-lookup"><span data-stu-id="3cf28-130">This function is used to register a callback from the HID class to the HID client when a report is received.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-131">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-131">Parameters</span></span>

- <span data-ttu-id="3cf28-132">**HID** Wskaźnik do wystąpienia klasy HID</span><span class="sxs-lookup"><span data-stu-id="3cf28-132">**hid** Pointer to the HID class instance</span></span>
- <span data-ttu-id="3cf28-133">**call_back** Wskaźnik do struktury call_back</span><span class="sxs-lookup"><span data-stu-id="3cf28-133">**call_back** Pointer to the call_back structure</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-134">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="3cf28-134">Return values</span></span>

- <span data-ttu-id="3cf28-135">**UX_SUCCESS** (0x00) transfer danych został ukończony</span><span class="sxs-lookup"><span data-stu-id="3cf28-135">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="3cf28-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b) nieprawidłowe wystąpienie HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Invalid HID instance.</span></span>
- <span data-ttu-id="3cf28-137">Wystąpił błąd **UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) podczas rejestracji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3cf28-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Error in the report callback registration.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-138">Example</span></span>

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a><span data-ttu-id="3cf28-139">ux_host_class_hid_periodic_report_start</span><span class="sxs-lookup"><span data-stu-id="3cf28-139">ux_host_class_hid_periodic_report_start</span></span>

<span data-ttu-id="3cf28-140">Uruchom okresowy punkt końcowy dla wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-140">Start the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-141">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-141">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="3cf28-142">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-142">Description</span></span>

<span data-ttu-id="3cf28-143">Ta funkcja służy do uruchamiania okresowego (przerwania) punktu końcowego dla wystąpienia klasy HID, która jest powiązana z tym klientem HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-143">This function is used to start the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="3cf28-144">Klasa HID nie może uruchomić okresowego punktu końcowego, dopóki klient HID nie zostanie aktywowany i w związku z tym zostanie pozostawiony do klienta HID, aby uruchomić ten punkt końcowy w celu otrzymywania raportów.</span><span class="sxs-lookup"><span data-stu-id="3cf28-144">The HID class cannot start the periodic endpoint until the HID client is activated and therefore it is left to the HID client to start this endpoint to receive reports.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3cf28-145">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="3cf28-145">Input Parameter</span></span>

- <span data-ttu-id="3cf28-146">**HID** Wskaźnik do wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-146">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-147">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-147">Return Values</span></span>

- <span data-ttu-id="3cf28-148">Raportowanie okresowe **UX_SUCCESS** (0x00) zostało pomyślnie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="3cf28-148">**UX_SUCCESS** (0x00) Periodic reporting successfully started.</span></span>
- <span data-ttu-id="3cf28-149">Błąd **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7a) w raporcie okresowym.</span><span class="sxs-lookup"><span data-stu-id="3cf28-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="3cf28-150">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3cf28-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-151">Example</span></span>

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a><span data-ttu-id="3cf28-152">ux_host_class_hid_periodic_report_stop</span><span class="sxs-lookup"><span data-stu-id="3cf28-152">ux_host_class_hid_periodic_report_stop</span></span>

<span data-ttu-id="3cf28-153">Zatrzymaj okresowy punkt końcowy dla wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-153">Stop the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-154">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-154">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="3cf28-155">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-155">Description</span></span>

<span data-ttu-id="3cf28-156">Ta funkcja służy do zatrzymania okresowego (przerwania) punktu końcowego dla wystąpienia klasy HID, która jest powiązana z tym klientem HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-156">This function is used to stop the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="3cf28-157">Klasa HID nie może zatrzymać okresowego punktu końcowego, dopóki klient HID nie zostanie zdezaktywowany, wszystkie jego zasoby zostaną zwolnione i w związku z tym zostanie pozostawiony klientowi HID, aby zatrzymać ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="3cf28-157">The HID class cannot stop the periodic endpoint until the HID client is deactivated, all its resources freed and therefore it is left to the HID client to stop this endpoint.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3cf28-158">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="3cf28-158">Input Parameter</span></span>

- <span data-ttu-id="3cf28-159">**HID** Wskaźnik do wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-159">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-160">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-160">Return Values</span></span>

- <span data-ttu-id="3cf28-161">Raportowanie okresowe **UX_SUCCESS** (0x00) zostało pomyślnie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="3cf28-161">**UX_SUCCESS** (0x00) Periodic reporting successfully stopped.</span></span>
- <span data-ttu-id="3cf28-162">Błąd **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7a) w raporcie okresowym.</span><span class="sxs-lookup"><span data-stu-id="3cf28-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="3cf28-163">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje</span><span class="sxs-lookup"><span data-stu-id="3cf28-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-164">Example</span></span>

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="3cf28-165">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="3cf28-165">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="3cf28-166">Pobierz Raport z wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-166">Get a report from a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-167">Prototype</span></span>

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="3cf28-168">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-168">Description</span></span>

<span data-ttu-id="3cf28-169">Ta funkcja służy do otrzymywania raportu bezpośrednio z urządzenia bez polegania na okresowym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="3cf28-169">This function is used to receive a report directly from the device without relying on the periodic endpoint.</span></span> <span data-ttu-id="3cf28-170">Ten raport pochodzi z punktu końcowego kontroli, ale jego przetwarzanie jest takie samo, jak gdyby było ono wykonywane w okresowym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="3cf28-170">This report is coming from the control endpoint but its treatment is the same as though it were coming on the periodic endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-171">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-171">Parameters</span></span>

- <span data-ttu-id="3cf28-172">**HID** Wskaźnik do wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-172">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="3cf28-173">**client_report** Wskaźnik do raportu klienta HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-173">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-174">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-174">Return Values</span></span>

- <span data-ttu-id="3cf28-175">**UX_SUCCESS** (0x00) raport został pomyślnie odebrany.</span><span class="sxs-lookup"><span data-stu-id="3cf28-175">**UX_SUCCESS** (0x00) The report was successfully received.</span></span>
- <span data-ttu-id="3cf28-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) raport klienta był nieprawidłowy lub wystąpił błąd podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="3cf28-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="3cf28-177">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3cf28-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="3cf28-178">**UX_BUFFER_OVERFLOW** (0x5D) podany bufor nie jest wystarczająco duży, aby pomieścić nieskompresowany raport.</span><span class="sxs-lookup"><span data-stu-id="3cf28-178">**UX_BUFFER_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-179">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-179">Example</span></span>

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="3cf28-180">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="3cf28-180">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="3cf28-181">Wyślij raport</span><span class="sxs-lookup"><span data-stu-id="3cf28-181">Send a report</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-182">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-182">Prototype</span></span>

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="3cf28-183">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-183">Description</span></span>

<span data-ttu-id="3cf28-184">Ta funkcja służy do wysyłania raportu bezpośrednio do urządzenia.</span><span class="sxs-lookup"><span data-stu-id="3cf28-184">This function is used to send a report directly to the device.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-185">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-185">Parameters</span></span>

- <span data-ttu-id="3cf28-186">**HID** Wskaźnik do wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-186">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="3cf28-187">**client_report** Wskaźnik do raportu klienta HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-187">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-188">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-188">Return Values</span></span>

- <span data-ttu-id="3cf28-189">**UX_SUCCESS** (0x00) raport został pomyślnie wysłany.</span><span class="sxs-lookup"><span data-stu-id="3cf28-189">**UX_SUCCESS** (0x00) The report was successfully sent.</span></span>
- <span data-ttu-id="3cf28-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) raport klienta był nieprawidłowy lub wystąpił błąd podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="3cf28-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="3cf28-191">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3cf28-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="3cf28-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5D) podany bufor nie jest wystarczająco duży, aby pomieścić nieskompresowany raport.</span><span class="sxs-lookup"><span data-stu-id="3cf28-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-193">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-193">Example</span></span>

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a><span data-ttu-id="3cf28-194">ux_host_class_hid_mouse_buttons_get</span><span class="sxs-lookup"><span data-stu-id="3cf28-194">ux_host_class_hid_mouse_buttons_get</span></span>

<span data-ttu-id="3cf28-195">Pobierz przyciski myszy.</span><span class="sxs-lookup"><span data-stu-id="3cf28-195">Get mouse buttons.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-196">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-196">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a><span data-ttu-id="3cf28-197">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-197">Description</span></span>

<span data-ttu-id="3cf28-198">Ta funkcja służy do pobierania przycisków myszy</span><span class="sxs-lookup"><span data-stu-id="3cf28-198">This function is used to get the mouse buttons</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-199">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-199">Parameters</span></span>

- <span data-ttu-id="3cf28-200">**mouse_instance** Wskaźnik do wystąpienia myszy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-200">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="3cf28-201">**mouse_buttons** Wskaźnik na przyciski powrotu.</span><span class="sxs-lookup"><span data-stu-id="3cf28-201">**mouse_buttons** Pointer to the return buttons.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-202">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-202">Return Values</span></span>

- <span data-ttu-id="3cf28-203">Pomyślnie pobrano przycisk myszy **UX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="3cf28-203">**UX_SUCCESS** (0x00) Mouse button successfully retrieved.</span></span>
- <span data-ttu-id="3cf28-204">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3cf28-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-205">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-205">Example</span></span>

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a><span data-ttu-id="3cf28-206">ux_host_class_hid_mouse_position_get</span><span class="sxs-lookup"><span data-stu-id="3cf28-206">ux_host_class_hid_mouse_position_get</span></span>

<span data-ttu-id="3cf28-207">Pobierz pozycję myszy.</span><span class="sxs-lookup"><span data-stu-id="3cf28-207">Get mouse position.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-208">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-208">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a><span data-ttu-id="3cf28-209">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-209">Description</span></span>

<span data-ttu-id="3cf28-210">Ta funkcja służy do pobierania położenia myszy w współrzędnej x & y.</span><span class="sxs-lookup"><span data-stu-id="3cf28-210">This function is used to get the mouse position in x & y coordinates.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-211">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-211">Parameters</span></span>

- <span data-ttu-id="3cf28-212">**mouse_instance** Wskaźnik do wystąpienia myszy HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-212">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="3cf28-213">**mouse_x_position** Wskaźnik na współrzędną x.</span><span class="sxs-lookup"><span data-stu-id="3cf28-213">**mouse_x_position** Pointer to the x coordinate.</span></span>
- <span data-ttu-id="3cf28-214">**mouse_y_position** Wskaźnik na współrzędną y.</span><span class="sxs-lookup"><span data-stu-id="3cf28-214">**mouse_y_position** Pointer to the y coordinate.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-215">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-215">Return Values</span></span>

- <span data-ttu-id="3cf28-216">Pomyślnie pobrano współrzędne dotyczące **UX_SUCCESS** (0X00) X &amp; Y.</span><span class="sxs-lookup"><span data-stu-id="3cf28-216">**UX_SUCCESS** (0x00) X &amp; Y coordinates successfully retrieved.</span></span>
- <span data-ttu-id="3cf28-217">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3cf28-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-218">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-218">Example</span></span>

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a><span data-ttu-id="3cf28-219">ux_host_class_hid_keyboard_key_get</span><span class="sxs-lookup"><span data-stu-id="3cf28-219">ux_host_class_hid_keyboard_key_get</span></span>

<span data-ttu-id="3cf28-220">Pobierz klucz i stan klawiatury.</span><span class="sxs-lookup"><span data-stu-id="3cf28-220">Get keyboard key and state.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-221">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-221">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a><span data-ttu-id="3cf28-222">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-222">Description</span></span>

<span data-ttu-id="3cf28-223">Ta funkcja służy do uzyskiwania klucza i stanu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="3cf28-223">This function is used to get the keyboard key and state.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-224">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-224">Parameters</span></span>

- <span data-ttu-id="3cf28-225">**keyboard_instance** Wskaźnik do wystąpienia klawiatury HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-225">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="3cf28-226">**keyboard_key** Wskaźnik do kontenera kluczy klawiatury.</span><span class="sxs-lookup"><span data-stu-id="3cf28-226">**keyboard_key** Pointer to keyboard key container.</span></span>
- <span data-ttu-id="3cf28-227">**keyboard_state** Wskaźnik do kontenera stanu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="3cf28-227">**keyboard_state** Pointer to the keyboard state container.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-228">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-228">Return Values</span></span>

- <span data-ttu-id="3cf28-229">Pomyślnie pobrano klucz **UX_SUCCESS** (0x00) i stan.</span><span class="sxs-lookup"><span data-stu-id="3cf28-229">**UX_SUCCESS** (0x00) Key and state successfully retrieved.</span></span>
- <span data-ttu-id="3cf28-230">Brak wartości **UX_ERROR** (0xFF) do zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="3cf28-230">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="3cf28-231">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3cf28-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="3cf28-232">Stan klawiatury może mieć następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="3cf28-232">The keyboard state can have the following values.</span></span>

- <span data-ttu-id="3cf28-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span><span class="sxs-lookup"><span data-stu-id="3cf28-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span></span>
- <span data-ttu-id="3cf28-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span><span class="sxs-lookup"><span data-stu-id="3cf28-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span></span>
- <span data-ttu-id="3cf28-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="3cf28-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span></span>
- <span data-ttu-id="3cf28-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span><span class="sxs-lookup"><span data-stu-id="3cf28-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span></span>
- <span data-ttu-id="3cf28-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span><span class="sxs-lookup"><span data-stu-id="3cf28-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span></span>
- <span data-ttu-id="3cf28-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span><span class="sxs-lookup"><span data-stu-id="3cf28-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span></span>
- <span data-ttu-id="3cf28-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span><span class="sxs-lookup"><span data-stu-id="3cf28-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span></span>
- <span data-ttu-id="3cf28-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span><span class="sxs-lookup"><span data-stu-id="3cf28-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span></span>
- <span data-ttu-id="3cf28-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span><span class="sxs-lookup"><span data-stu-id="3cf28-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span></span>
- <span data-ttu-id="3cf28-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span><span class="sxs-lookup"><span data-stu-id="3cf28-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span></span>
- <span data-ttu-id="3cf28-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span><span class="sxs-lookup"><span data-stu-id="3cf28-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span></span>
- <span data-ttu-id="3cf28-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span><span class="sxs-lookup"><span data-stu-id="3cf28-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span></span>
- <span data-ttu-id="3cf28-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span><span class="sxs-lookup"><span data-stu-id="3cf28-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span></span>
- <span data-ttu-id="3cf28-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span><span class="sxs-lookup"><span data-stu-id="3cf28-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span></span>
- <span data-ttu-id="3cf28-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span><span class="sxs-lookup"><span data-stu-id="3cf28-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span></span>
- <span data-ttu-id="3cf28-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span><span class="sxs-lookup"><span data-stu-id="3cf28-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span></span>
- <span data-ttu-id="3cf28-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span><span class="sxs-lookup"><span data-stu-id="3cf28-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-250">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-250">Example</span></span>

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a><span data-ttu-id="3cf28-251">ux_host_class_hid_keyboard_ioctl</span><span class="sxs-lookup"><span data-stu-id="3cf28-251">ux_host_class_hid_keyboard_ioctl</span></span>

<span data-ttu-id="3cf28-252">Wykonaj funkcję IOCTL na klawiaturze HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-252">Perform an IOCTL function to the HID keyboard.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-253">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-253">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="3cf28-254">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-254">Description</span></span>

<span data-ttu-id="3cf28-255">Ta funkcja wykonuje określoną funkcję IOCTL na klawiaturze HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-255">This function performs a specific ioctl function to the HID keyboard.</span></span> <span data-ttu-id="3cf28-256">Wywołanie jest blokowane i zwraca tylko wtedy, gdy występuje błąd lub po zakończeniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cf28-256">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-257">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-257">Parameters</span></span>

- <span data-ttu-id="3cf28-258">**keyboard_instance** Wskaźnik do wystąpienia klawiatury HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-258">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="3cf28-259">**ioctl_function** funkcję IOCTL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="3cf28-259">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="3cf28-260">W poniższej tabeli znajduje się jedna z dozwolonych funkcji IOCTL.</span><span class="sxs-lookup"><span data-stu-id="3cf28-260">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="3cf28-261">**parametr** Wskaźnik na parametr specyficzny dla elementu IOCTL.</span><span class="sxs-lookup"><span data-stu-id="3cf28-261">**parameter** Pointer to a parameter specific to the ioctl.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-262">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-262">Return Values</span></span>

- <span data-ttu-id="3cf28-263">**UX_SUCCESS** (0x00) funkcja IOCTL została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3cf28-263">**UX_SUCCESS** (0x00) The ioctl function completed successfully.</span></span>
- <span data-ttu-id="3cf28-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) nieznana funkcja IOCTL</span><span class="sxs-lookup"><span data-stu-id="3cf28-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="3cf28-265">Funkcje IOCTL</span><span class="sxs-lookup"><span data-stu-id="3cf28-265">IOCTL functions</span></span>

- <span data-ttu-id="3cf28-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="3cf28-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span></span>
- <span data-ttu-id="3cf28-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span><span class="sxs-lookup"><span data-stu-id="3cf28-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span></span>
- <span data-ttu-id="3cf28-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span><span class="sxs-lookup"><span data-stu-id="3cf28-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span></span>

### <a name="example--change-keyboard-layout"></a><span data-ttu-id="3cf28-269">Przykład — Zmień układ klawiatury</span><span class="sxs-lookup"><span data-stu-id="3cf28-269">Example – change keyboard layout</span></span>

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a><span data-ttu-id="3cf28-270">Przykład — wyłączenie dekodowania klucza klawiatury</span><span class="sxs-lookup"><span data-stu-id="3cf28-270">Example – disable keyboard key decode</span></span>

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a><span data-ttu-id="3cf28-271">ux_host_class_hid_remote_control_usage_get</span><span class="sxs-lookup"><span data-stu-id="3cf28-271">ux_host_class_hid_remote_control_usage_get</span></span>

<span data-ttu-id="3cf28-272">Pobierz Użycie zdalnego sterowania</span><span class="sxs-lookup"><span data-stu-id="3cf28-272">Get remote control usage</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-273">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-273">Prototype</span></span>

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a><span data-ttu-id="3cf28-274">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-274">Description</span></span>

<span data-ttu-id="3cf28-275">Ta funkcja służy do uzyskiwania użycia zdalnego sterowania.</span><span class="sxs-lookup"><span data-stu-id="3cf28-275">This function is used to get the remote control usages.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-276">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-276">Parameters</span></span>

- <span data-ttu-id="3cf28-277">**remote_control_instance** Wskaźnik do wystąpienia zdalnego sterowania HID.</span><span class="sxs-lookup"><span data-stu-id="3cf28-277">**remote_control_instance** Pointer to the HID remote control instance.</span></span>
- <span data-ttu-id="3cf28-278">**użycie** Wskaźnik do użycia.</span><span class="sxs-lookup"><span data-stu-id="3cf28-278">**usage** Pointer to the usage.</span></span>
- <span data-ttu-id="3cf28-279">**wartość** Wskaźnik na wartość użycia.</span><span class="sxs-lookup"><span data-stu-id="3cf28-279">**value** Pointer to the value for the usage.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-280">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-280">Return Values</span></span>

- <span data-ttu-id="3cf28-281">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="3cf28-281">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="3cf28-282">Brak wartości **UX_ERROR** (0xFF) do zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="3cf28-282">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="3cf28-283">Wystąpienie klasy HID **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3cf28-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="3cf28-284">Lista wszystkich możliwych użycia jest zbyt długa, aby można ją było dopasować do tego podręcznika użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3cf28-284">The list of all possible usages is too long to fit in this user guide.</span></span> <span data-ttu-id="3cf28-285">Aby uzyskać pełny opis, ux_host_class_hid. h ma cały zestaw możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="3cf28-285">For a full description, the ux_host_class_hid.h has the entire set of possible values.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-286">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-286">Example</span></span>

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="3cf28-287">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="3cf28-287">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="3cf28-288">Odczytaj z interfejsu cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-288">Read from the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-289">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="3cf28-290">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-290">Description</span></span>

<span data-ttu-id="3cf28-291">Ta funkcja odczytuje z interfejsu cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-291">This function reads from the cdc_acm interface.</span></span> <span data-ttu-id="3cf28-292">Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.</span><span class="sxs-lookup"><span data-stu-id="3cf28-292">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-293">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-293">Parameters</span></span>

- <span data-ttu-id="3cf28-294">**cdc_acm** Wskaźnik do wystąpienia klasy cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-294">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="3cf28-295">**data_pointer** Wskaźnik na adres buforu ładunku danych.</span><span class="sxs-lookup"><span data-stu-id="3cf28-295">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="3cf28-296">**requested_length** Długość do odebrania.</span><span class="sxs-lookup"><span data-stu-id="3cf28-296">**requested_length** Length to be received.</span></span>
- <span data-ttu-id="3cf28-297">**actual_length** Rzeczywista długość odebrana.</span><span class="sxs-lookup"><span data-stu-id="3cf28-297">**actual_length** Length actually received.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-298">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-298">Return Values</span></span>

- <span data-ttu-id="3cf28-299">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="3cf28-299">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="3cf28-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) wystąpienie cdc_acm jest nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="3cf28-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="3cf28-301">Limit czasu transferu **UX_TRANSFER_TIMEOUT** (0x5c), odczytywanie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="3cf28-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-302">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-302">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a><span data-ttu-id="3cf28-303">ux_host_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="3cf28-303">ux_host_class_cdc_acm_write</span></span>

<span data-ttu-id="3cf28-304">Zapisz w interfejsie cdc_acm</span><span class="sxs-lookup"><span data-stu-id="3cf28-304">Write to the cdc_acm interface</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-305">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-305">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="3cf28-306">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-306">Description</span></span>

<span data-ttu-id="3cf28-307">Ta funkcja zapisuje w interfejsie cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-307">This function writes to the cdc_acm interface.</span></span> <span data-ttu-id="3cf28-308">Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.</span><span class="sxs-lookup"><span data-stu-id="3cf28-308">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-309">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-309">Parameters</span></span>

- <span data-ttu-id="3cf28-310">**cdc_acm** Wskaźnik do wystąpienia klasy cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-310">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="3cf28-311">**data_pointer** Wskaźnik na adres buforu ładunku danych.</span><span class="sxs-lookup"><span data-stu-id="3cf28-311">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="3cf28-312">**requested_length** Długość do wysłania.</span><span class="sxs-lookup"><span data-stu-id="3cf28-312">**requested_length** Length to be sent.</span></span>
- <span data-ttu-id="3cf28-313">**actual_length** Rzeczywista długość wysłana.</span><span class="sxs-lookup"><span data-stu-id="3cf28-313">**actual_length** Length actually sent.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cf28-314">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="3cf28-314">Return Values</span></span>

- <span data-ttu-id="3cf28-315">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="3cf28-315">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="3cf28-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) wystąpienie cdc_acm jest nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="3cf28-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="3cf28-317">Limit czasu transferu **UX_TRANSFER_TIMEOUT** (0x5c), zapisywanie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="3cf28-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="3cf28-318">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf28-318">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a><span data-ttu-id="3cf28-319">ux_host_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="3cf28-319">ux_host_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="3cf28-320">Wykonaj funkcję IOCTL w interfejsie cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-320">Perform an IOCTL function to the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-321">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-321">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="3cf28-322">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-322">Description</span></span>

<span data-ttu-id="3cf28-323">Ta funkcja wykonuje konkretną funkcję IOCTL do interfejsu cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-323">This function performs a specific ioctl function to the cdc_acm interface.</span></span> <span data-ttu-id="3cf28-324">Wywołanie jest blokowane i zwraca tylko wtedy, gdy występuje błąd lub po zakończeniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cf28-324">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-325">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-325">Parameters</span></span>

- <span data-ttu-id="3cf28-326">**cdc_acm** Wskaźnik do wystąpienia klasy cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-326">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="3cf28-327">**ioctl_function** funkcję IOCTL do wykonania.</span><span class="sxs-lookup"><span data-stu-id="3cf28-327">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="3cf28-328">W poniższej tabeli znajduje się jedna z dozwolonych funkcji IOCTL.</span><span class="sxs-lookup"><span data-stu-id="3cf28-328">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="3cf28-329">**parametr** Wskaźnik do parametru specyficznego dla elementu IOCTL</span><span class="sxs-lookup"><span data-stu-id="3cf28-329">**parameter** Pointer to a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="3cf28-330">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3cf28-330">Return Value</span></span>

- <span data-ttu-id="3cf28-331">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="3cf28-331">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="3cf28-332">**UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="3cf28-332">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory.</span></span>
- <span data-ttu-id="3cf28-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — wystąpienie metody przechwytywania jest w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="3cf28-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM instance is in an invalid state.</span></span>
- <span data-ttu-id="3cf28-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) nieznana funkcja IOCTL.</span><span class="sxs-lookup"><span data-stu-id="3cf28-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="3cf28-335">Funkcje IOCTL:</span><span class="sxs-lookup"><span data-stu-id="3cf28-335">IOCTL functions:</span></span>

- <span data-ttu-id="3cf28-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="3cf28-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="3cf28-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="3cf28-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="3cf28-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="3cf28-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="3cf28-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="3cf28-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="3cf28-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="3cf28-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="3cf28-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="3cf28-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="3cf28-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="3cf28-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="3cf28-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="3cf28-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="3cf28-344">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="3cf28-344">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="3cf28-345">Rozpoczyna odbieranie danych z urządzenia w tle.</span><span class="sxs-lookup"><span data-stu-id="3cf28-345">Begins background reception of data from the device.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-346">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-346">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="3cf28-347">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-347">Description</span></span>

<span data-ttu-id="3cf28-348">Ta funkcja powoduje, że USBX stale odczytywać dane z urządzenia w tle.</span><span class="sxs-lookup"><span data-stu-id="3cf28-348">This function causes USBX to continuously read data from the device in the background.</span></span> <span data-ttu-id="3cf28-349">Po zakończeniu każdej transakcji wywołania zwrotne określone w **cdc_acm_reception** są wywoływane, aby aplikacja mogła wykonać dalsze przetwarzanie danych transakcji.</span><span class="sxs-lookup"><span data-stu-id="3cf28-349">Upon completion of each transaction, the callback specified in **cdc_acm_reception** is invoked so the application may perform further processing of the transaction's data.</span></span>

> [!NOTE]
> <span data-ttu-id="3cf28-350">nie można użyć **ux_host_class_cdc_acm_read** , gdy odbieranie w tle jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="3cf28-350">**ux_host_class_cdc_acm_read** must not be used while background reception is in use.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-351">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-351">Parameters</span></span>

- <span data-ttu-id="3cf28-352">**cdc_acm** Wskaźnik do wystąpienia klasy cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-352">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="3cf28-353">**cdc_acm_reception** Wskaźnik do parametru, który zawiera wartości definiujące zachowanie odbioru w tle.</span><span class="sxs-lookup"><span data-stu-id="3cf28-353">**cdc_acm_reception** Pointer to parameter that contains values defining behavior of background reception.</span></span> <span data-ttu-id="3cf28-354">Układ tego parametru jest następujący:</span><span class="sxs-lookup"><span data-stu-id="3cf28-354">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="3cf28-355">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3cf28-355">Return Value</span></span>

- <span data-ttu-id="3cf28-356">Odbieranie w tle **UX_SUCCESS** (0x00) zostało pomyślnie rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="3cf28-356">**UX_SUCCESS** (0x00) Background reception successfully started.</span></span>
- <span data-ttu-id="3cf28-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0X5b) złe wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="3cf28-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="3cf28-358">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="3cf28-358">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="3cf28-359">Wyłącza odbieranie pakietów w tle.</span><span class="sxs-lookup"><span data-stu-id="3cf28-359">Stops background reception of packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="3cf28-360">Prototype</span><span class="sxs-lookup"><span data-stu-id="3cf28-360">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="3cf28-361">Opis</span><span class="sxs-lookup"><span data-stu-id="3cf28-361">Description</span></span>

<span data-ttu-id="3cf28-362">Ta funkcja powoduje, że program USBX ma zatrzymywać odbieranie w tle wcześniej uruchomione przez **ux_host_class_cdc_acm_reception_start**.</span><span class="sxs-lookup"><span data-stu-id="3cf28-362">This function causes USBX to stop background reception previously started by **ux_host_class_cdc_acm_reception_start**.</span></span>

### <a name="parameters"></a><span data-ttu-id="3cf28-363">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf28-363">Parameters</span></span>

- <span data-ttu-id="3cf28-364">**cdc_acm** Wskaźnik do wystąpienia klasy cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="3cf28-364">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="3cf28-365">**cdc_acm_reception** Wskaźnik na ten sam parametr, który został użyty do rozpoczęcia odbierania w tle.</span><span class="sxs-lookup"><span data-stu-id="3cf28-365">**cdc_acm_reception** Pointer to the same parameter that was used to start background reception.</span></span> <span data-ttu-id="3cf28-366">Układ tego parametru jest następujący:</span><span class="sxs-lookup"><span data-stu-id="3cf28-366">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="3cf28-367">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3cf28-367">Return Value</span></span>

- <span data-ttu-id="3cf28-368">Odbieranie w tle **UX_SUCCESS** (0x00) zostało pomyślnie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="3cf28-368">**UX_SUCCESS** (0x00) Background reception successfully stopped.</span></span>
- <span data-ttu-id="3cf28-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0X5b) złe wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="3cf28-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
