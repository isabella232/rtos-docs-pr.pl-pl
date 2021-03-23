---
title: Interfejs API klas hosta USBX
description: W tym rozdziale opisano wszystkie uwidocznione interfejsy API klas hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824018"
---
# <a name="chapter-2-usbx-host-classes-api"></a><span data-ttu-id="aa124-103">Rozdział 2: interfejs API klas hosta USBX</span><span class="sxs-lookup"><span data-stu-id="aa124-103">Chapter 2: USBX Host Classes API</span></span>

<span data-ttu-id="aa124-104">W tym rozdziale opisano wszystkie uwidocznione interfejsy API klas hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="aa124-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="aa124-105">Poniższe interfejsy API dla każdej klasy są szczegółowo opisane.</span><span class="sxs-lookup"><span data-stu-id="aa124-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="aa124-106">Klasa drukarki</span><span class="sxs-lookup"><span data-stu-id="aa124-106">Printer class</span></span>
- <span data-ttu-id="aa124-107">Klasa audio</span><span class="sxs-lookup"><span data-stu-id="aa124-107">Audio class</span></span>
- <span data-ttu-id="aa124-108">Klasa ASIX</span><span class="sxs-lookup"><span data-stu-id="aa124-108">Asix class</span></span>
- <span data-ttu-id="aa124-109">Pima/PTP — Klasa</span><span class="sxs-lookup"><span data-stu-id="aa124-109">Pima/PTP class</span></span>
- <span data-ttu-id="aa124-110">Klasa mnóstwo</span><span class="sxs-lookup"><span data-stu-id="aa124-110">Prolific class</span></span>
- <span data-ttu-id="aa124-111">Ogólna Klasa szeregowa</span><span class="sxs-lookup"><span data-stu-id="aa124-111">Generic Serial class</span></span>

## <a name="ux_host_class_printer_read"></a><span data-ttu-id="aa124-112">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="aa124-112">ux_host_class_printer_read</span></span>

<span data-ttu-id="aa124-113">Odczytaj z interfejsu drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-113">Read from the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-114">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-114">Prototype</span></span>

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="aa124-115">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-115">Description</span></span>

<span data-ttu-id="aa124-116">Ta funkcja odczytuje z interfejsu drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-116">This function reads from the printer interface.</span></span> <span data-ttu-id="aa124-117">Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.</span><span class="sxs-lookup"><span data-stu-id="aa124-117">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span> <span data-ttu-id="aa124-118">Odczyt jest dozwolony tylko na drukarkach dwukierunkowych.</span><span class="sxs-lookup"><span data-stu-id="aa124-118">A read is allowed only on bi-directional printers.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-119">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-119">Parameters</span></span>

- <span data-ttu-id="aa124-120">**drukarka**: wskaźnik do wystąpienia klasy drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-120">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="aa124-121">**data_pointer**: wskaźnik na adres buforu ładunku danych.</span><span class="sxs-lookup"><span data-stu-id="aa124-121">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="aa124-122">**requested_length**: długość do odebrania.</span><span class="sxs-lookup"><span data-stu-id="aa124-122">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="aa124-123">**actual_length**: długość rzeczywiście odebrana.</span><span class="sxs-lookup"><span data-stu-id="aa124-123">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-124">Return Value</span></span>

- <span data-ttu-id="aa124-125">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-125">**UX_SUCCESS**:  (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-126">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana, ponieważ drukarka nie jest dwukierunkowa.</span><span class="sxs-lookup"><span data-stu-id="aa124-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported because the printer is not bi-directional.</span></span>
- <span data-ttu-id="aa124-127">**UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, odczytywanie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="aa124-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-128">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a><span data-ttu-id="aa124-129">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="aa124-129">ux_host_class_printer_write</span></span>

<span data-ttu-id="aa124-130">Zapisz w interfejsie drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-130">Write to the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-131">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-131">Prototype</span></span>

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="aa124-132">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-132">Description</span></span>

<span data-ttu-id="aa124-133">Ta funkcja zapisuje w interfejsie drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-133">This function writes to the printer interface.</span></span> <span data-ttu-id="aa124-134">Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.</span><span class="sxs-lookup"><span data-stu-id="aa124-134">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-135">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-135">Parameters</span></span>

- <span data-ttu-id="aa124-136">**drukarka**: wskaźnik do wystąpienia klasy drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-136">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="aa124-137">**data_pointer**: wskaźnik na adres buforu ładunku danych.</span><span class="sxs-lookup"><span data-stu-id="aa124-137">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="aa124-138">**requested_length**: długość do wysłania.</span><span class="sxs-lookup"><span data-stu-id="aa124-138">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="aa124-139">**actual_length**: długość faktycznie wysłana.</span><span class="sxs-lookup"><span data-stu-id="aa124-139">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-140">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-140">Return Value</span></span>

- <span data-ttu-id="aa124-141">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-141">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-142">**UX_TRANSFER_TIMEOUT**: (0x5c) limit czasu transferu, zapisywanie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="aa124-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-143">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="aa124-144">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="aa124-144">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="aa124-145">Wykonaj resetowanie miękkie do drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-145">Perform a soft reset to the printer.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-146">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-146">Prototype</span></span>

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a><span data-ttu-id="aa124-147">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-147">Description</span></span>

<span data-ttu-id="aa124-148">Ta funkcja wykonuje funkcję resetowania miękkiego do drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-148">This function performs a soft reset to the printer.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="aa124-149">Parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa124-149">Input Parameter</span></span>

- <span data-ttu-id="aa124-150">**drukarka**: wskaźnik do wystąpienia klasy drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-150">**printer**: Pointer to the printer class instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-151">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-151">Return Value</span></span>

- <span data-ttu-id="aa124-152">**UX_SUCCESS**: (0x00) Resetowanie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="aa124-152">**UX_SUCCESS**: (0x00)The reset was completed.</span></span>
- <span data-ttu-id="aa124-153">**UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, Resetowanie nie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="aa124-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-154">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="aa124-155">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="aa124-155">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="aa124-156">Pobierz stan drukarki</span><span class="sxs-lookup"><span data-stu-id="aa124-156">Get the printer status</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-157">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-157">Prototype</span></span>

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a><span data-ttu-id="aa124-158">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-158">Description</span></span>

<span data-ttu-id="aa124-159">Ta funkcja uzyskuje stan drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-159">This function obtains the printer status.</span></span> <span data-ttu-id="aa124-160">Stan drukarki jest podobny do stanu LPT (1284 standard).</span><span class="sxs-lookup"><span data-stu-id="aa124-160">The printer status is similar to the LPT status (1284 standard).</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-161">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-161">Parameters</span></span>

- <span data-ttu-id="aa124-162">**drukarka**: wskaźnik do wystąpienia klasy drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-162">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="aa124-163">**printer_status**: adres, który ma zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="aa124-163">**printer_status**: Address of the status to be returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-164">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-164">Return Value</span></span>

- <span data-ttu-id="aa124-165">**UX_SUCCESS** (0x00): Resetowanie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="aa124-165">**UX_SUCCESS** (0x00): The reset was completed.</span></span>
- <span data-ttu-id="aa124-166">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="aa124-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="aa124-167">**UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, Resetowanie nie zostało ukończone</span><span class="sxs-lookup"><span data-stu-id="aa124-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed</span></span>

### <a name="example"></a><span data-ttu-id="aa124-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-168">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a><span data-ttu-id="aa124-169">ux_host_class_printer_device_id_get</span><span class="sxs-lookup"><span data-stu-id="aa124-169">ux_host_class_printer_device_id_get</span></span>

<span data-ttu-id="aa124-170">Pobierz identyfikator urządzenia drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-170">Get the printer device id.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-171">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-171">Prototype</span></span>

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a><span data-ttu-id="aa124-172">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-172">Description</span></span>

<span data-ttu-id="aa124-173">Ta funkcja uzyskuje ciąg identyfikatora urządzenia IEEE 1284 (łącznie z długością w pierwszych dwóch bajtach w formacie big endian).</span><span class="sxs-lookup"><span data-stu-id="aa124-173">This function obtains the printer IEEE 1284 device ID string (including length in the first two bytes in big endian format).</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-174">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-174">Parameters</span></span>

- <span data-ttu-id="aa124-175">**drukarka**: wskaźnik do wystąpienia klasy drukarki.</span><span class="sxs-lookup"><span data-stu-id="aa124-175">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="aa124-176">**descriptor_buffer**: wskaźnik do buforu, aby wypełnić ciąg identyfikatora urządzenia IEEE 1284 (łącznie z długością w ciągu pierwszych dwóch bajtów w formacie)</span><span class="sxs-lookup"><span data-stu-id="aa124-176">**descriptor_buffer**: Pointer to a buffer to fill IEEE 1284 device ID string (including length in the first two bytes in BE format)</span></span> 
- <span data-ttu-id="aa124-177">**Długość**: długość buforu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="aa124-177">**length**: Length of buffer in bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-178">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-178">Return Value</span></span>

- <span data-ttu-id="aa124-179">**UX_SUCCESS** (0x00): operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa124-179">**UX_SUCCESS** (0x00): The operation was successful.</span></span>
- <span data-ttu-id="aa124-180">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci do wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="aa124-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="aa124-181">**UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, żądanie nie zostało ukończone</span><span class="sxs-lookup"><span data-stu-id="aa124-181">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, request not completed</span></span>
- <span data-ttu-id="aa124-182">**UX_TRANSFER_NOT_READY**: (0x25) urządzenie było w nieprawidłowym stanie — musi być dołączone, rozkierowane lub skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="aa124-182">**UX_TRANSFER_NOT_READY**: (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>
- <span data-ttu-id="aa124-183">**UX_TRANSFER_STALL**: (0x21) zatrzymano transfer.</span><span class="sxs-lookup"><span data-stu-id="aa124-183">**UX_TRANSFER_STALL**: (0x21) Transfer stalled.</span></span>
- <span data-ttu-id="aa124-184">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="aa124-184">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="aa124-185">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="aa124-185">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="aa124-186">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="aa124-186">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-187">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-187">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a><span data-ttu-id="aa124-188">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="aa124-188">ux_host_class_audio_read</span></span>

<span data-ttu-id="aa124-189">Odczytaj z interfejsu audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-189">Read from the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-190">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-190">Prototype</span></span>

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="aa124-191">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-191">Description</span></span>

<span data-ttu-id="aa124-192">Ta funkcja odczytuje z interfejsu audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-192">This function reads from the audio interface.</span></span> <span data-ttu-id="aa124-193">Wywołanie nie jest blokowane.</span><span class="sxs-lookup"><span data-stu-id="aa124-193">The call is non-blocking.</span></span> <span data-ttu-id="aa124-194">Aplikacja musi upewnić się, że dla interfejsu audio streaming została wybrana opcja alternatywnego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="aa124-194">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-195">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-195">Parameters</span></span>

- <span data-ttu-id="aa124-196">**audio**: wskaźnik do wystąpienia klasy audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-196">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="aa124-197">**audio_transfer_request**: wskaźnik do struktury transferu audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-197">**audio_transfer_request**: Pointer to the audio transfer structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-198">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-198">Return Value</span></span>

- <span data-ttu-id="aa124-199">**UX_SUCCESS**: (0x00) transfer danych został ukończony</span><span class="sxs-lookup"><span data-stu-id="aa124-199">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="aa124-200">Funkcja **UX_FUNCTION_NOT_SUPPORTED**"(0x54) nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="aa124-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported</span></span>

### <a name="example"></a><span data-ttu-id="aa124-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-201">Example</span></span>

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a><span data-ttu-id="aa124-202">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="aa124-202">ux_host_class_audio_write</span></span>

<span data-ttu-id="aa124-203">Zapisz w interfejsie audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-203">Write to the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-204">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-204">Prototype</span></span>

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="aa124-205">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-205">Description</span></span>

<span data-ttu-id="aa124-206">Ta funkcja zapisuje dane w interfejsie audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-206">This function writes to the audio interface.</span></span> <span data-ttu-id="aa124-207">Wywołanie nie jest blokowane.</span><span class="sxs-lookup"><span data-stu-id="aa124-207">The call is non-blocking.</span></span> <span data-ttu-id="aa124-208">Aplikacja musi upewnić się, że dla interfejsu audio streaming została wybrana opcja alternatywnego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="aa124-208">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-209">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-209">Parameters</span></span>

- <span data-ttu-id="aa124-210">**audio**: wskaźnik do wystąpienia klasy audio</span><span class="sxs-lookup"><span data-stu-id="aa124-210">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="aa124-211">**audio_transfer_request**: wskaźnik do struktury transferu audio</span><span class="sxs-lookup"><span data-stu-id="aa124-211">**audio_transfer_request**: Pointer to the audio transfer structure</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-212">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-212">Return Value</span></span>

- <span data-ttu-id="aa124-213">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-213">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-214">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="aa124-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported.</span></span>
- <span data-ttu-id="aa124-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Nieprawidłowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="aa124-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-216">Example</span></span>

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a><span data-ttu-id="aa124-217">ux_host_class_audio_control_get</span><span class="sxs-lookup"><span data-stu-id="aa124-217">ux_host_class_audio_control_get</span></span>

<span data-ttu-id="aa124-218">Uzyskaj konkretną kontrolę z interfejsu sterowania dźwiękiem.</span><span class="sxs-lookup"><span data-stu-id="aa124-218">Get a specific control from the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-219">Prototype</span></span>

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a><span data-ttu-id="aa124-220">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-220">Description</span></span>

<span data-ttu-id="aa124-221">Ta funkcja odczytuje konkretną kontrolę z interfejsu sterowania dźwiękiem.</span><span class="sxs-lookup"><span data-stu-id="aa124-221">This function reads a specific control from the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-222">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-222">Parameters</span></span>

- <span data-ttu-id="aa124-223">**audio**: wskaźnik do wystąpienia klasy audio</span><span class="sxs-lookup"><span data-stu-id="aa124-223">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="aa124-224">**audio_control**: wskaźnik do struktury kontrolki audio</span><span class="sxs-lookup"><span data-stu-id="aa124-224">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-225">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-225">Return Value</span></span>

- <span data-ttu-id="aa124-226">**UX_SUCCESS**: (0x00) transfer danych został ukończony</span><span class="sxs-lookup"><span data-stu-id="aa124-226">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="aa124-227">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="aa124-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="aa124-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs</span><span class="sxs-lookup"><span data-stu-id="aa124-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="aa124-229">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-229">Example</span></span>

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="aa124-230">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="aa124-230">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="aa124-231">Ustaw konkretną kontrolę interfejsu sterowania dźwiękiem.</span><span class="sxs-lookup"><span data-stu-id="aa124-231">Set a specific control to the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-232">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-232">Prototype</span></span>

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

<span data-ttu-id="aa124-233">\* \* Description \* \*</span><span class="sxs-lookup"><span data-stu-id="aa124-233">\*\*Description \*\*</span></span>

<span data-ttu-id="aa124-234">Ta funkcja ustawia konkretną kontrolę interfejsu sterowania dźwiękiem.</span><span class="sxs-lookup"><span data-stu-id="aa124-234">This function sets a specific control to the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-235">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-235">Parameters</span></span>

- <span data-ttu-id="aa124-236">**audio**: wskaźnik do wystąpienia klasy audio</span><span class="sxs-lookup"><span data-stu-id="aa124-236">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="aa124-237">**audio_control**: wskaźnik do struktury kontrolki audio</span><span class="sxs-lookup"><span data-stu-id="aa124-237">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-238">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-238">Return Value</span></span>

- <span data-ttu-id="aa124-239">**UX_SUCCESS**: (0x00) transfer danych został ukończony</span><span class="sxs-lookup"><span data-stu-id="aa124-239">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="aa124-240">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="aa124-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="aa124-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs</span><span class="sxs-lookup"><span data-stu-id="aa124-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="aa124-242">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-242">Example</span></span>

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="aa124-243">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="aa124-243">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="aa124-244">Ustaw alternatywny interfejs ustawień interfejsu audio streaming.</span><span class="sxs-lookup"><span data-stu-id="aa124-244">Set an alternate setting interface of the audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-245">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="aa124-246">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-246">Description</span></span>

<span data-ttu-id="aa124-247">Ta funkcja ustawia odpowiedni interfejs ustawienia alternatywnego interfejsu audio streaming zgodnie z określoną strukturą próbkowania.</span><span class="sxs-lookup"><span data-stu-id="aa124-247">This function sets the appropriate alternate setting interface of the audio streaming interface according to a specific sampling structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-248">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-248">Parameters</span></span>

- <span data-ttu-id="aa124-249">**audio**: wskaźnik do wystąpienia klasy audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-249">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="aa124-250">**audio_sampling**: wskaźnik do struktury próbkowania audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-250">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-251">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-251">Return Value</span></span>

- <span data-ttu-id="aa124-252">**UX_SUCCESS**: (0x00) transfer danych został ukończony</span><span class="sxs-lookup"><span data-stu-id="aa124-252">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="aa124-253">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="aa124-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="aa124-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs</span><span class="sxs-lookup"><span data-stu-id="aa124-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="aa124-255">**UX_NO_ALTERNATE_SETTING**: (0X5e) brak alternatywnego ustawienia dla wartości próbkowania</span><span class="sxs-lookup"><span data-stu-id="aa124-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="aa124-256">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-256">Example</span></span>

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="aa124-257">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="aa124-257">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="aa124-258">Pobierz możliwe ustawienia próbkowania interfejsu audio streaming.</span><span class="sxs-lookup"><span data-stu-id="aa124-258">Get possible sampling settings of audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-259">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-259">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="aa124-260">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-260">Description</span></span>

<span data-ttu-id="aa124-261">Ta funkcja pobiera jedną z nich, wszystkie możliwe ustawienia próbkowania dostępne w każdym z ustawień alternatywnych interfejsu audio streaming.</span><span class="sxs-lookup"><span data-stu-id="aa124-261">This function gets, one by one, all the possible sampling settings available in each of the alternate settings of the audio streaming interface.</span></span> <span data-ttu-id="aa124-262">Przy pierwszym użyciu funkcji, należy zresetować wszystkie pola wskaźnika struktury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="aa124-262">The first time the function is used, all the fields in the calling structure pointer must be reset.</span></span> <span data-ttu-id="aa124-263">Funkcja zwróci określony zestaw wartości przesyłania strumieniowego po zwrocie, chyba że zostanie osiągnięty koniec ustawień alternatywnych.</span><span class="sxs-lookup"><span data-stu-id="aa124-263">The function will return a specific set of streaming values upon return unless the end of the alternate settings has been reached.</span></span> <span data-ttu-id="aa124-264">Gdy ta funkcja jest ponownie używana, poprzednie wartości próbkowania będą używane do znajdowania następnych wartości próbkowania.</span><span class="sxs-lookup"><span data-stu-id="aa124-264">When this function is reused, the previous sampling values will be used to find the next sampling values.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-265">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-265">Parameters</span></span>

- <span data-ttu-id="aa124-266">**audio**: wskaźnik do wystąpienia klasy audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-266">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="aa124-267">**audio_sampling**: wskaźnik do struktury próbkowania audio.</span><span class="sxs-lookup"><span data-stu-id="aa124-267">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-268">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-268">Return Value</span></span>

- <span data-ttu-id="aa124-269">**UX_SUCCESS**: (0x00) transfer danych został ukończony</span><span class="sxs-lookup"><span data-stu-id="aa124-269">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="aa124-270">**UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="aa124-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="aa124-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs</span><span class="sxs-lookup"><span data-stu-id="aa124-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="aa124-272">**UX_NO_ALTERNATE_SETTING**: (0X5e) brak alternatywnego ustawienia dla wartości próbkowania</span><span class="sxs-lookup"><span data-stu-id="aa124-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="aa124-273">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-273">Example</span></span>

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a><span data-ttu-id="aa124-274">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="aa124-274">ux_host_class_asix_read</span></span>

<span data-ttu-id="aa124-275">Odczytaj z interfejsu ASIX.</span><span class="sxs-lookup"><span data-stu-id="aa124-275">Read from the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-276">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-276">Prototype</span></span>

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="aa124-277">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-277">Description</span></span>

<span data-ttu-id="aa124-278">Ta funkcja odczytuje z interfejsu ASIX.</span><span class="sxs-lookup"><span data-stu-id="aa124-278">This function reads from the asix interface.</span></span> <span data-ttu-id="aa124-279">Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.</span><span class="sxs-lookup"><span data-stu-id="aa124-279">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-280">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-280">Parameters</span></span>

- <span data-ttu-id="aa124-281">**ASIX**: wskaźnik do wystąpienia klasy ASIX.</span><span class="sxs-lookup"><span data-stu-id="aa124-281">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="aa124-282">**data_pointer**: wskaźnik na adres buforu ładunku danych.</span><span class="sxs-lookup"><span data-stu-id="aa124-282">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="aa124-283">**requested_length**: długość do odebrania.</span><span class="sxs-lookup"><span data-stu-id="aa124-283">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="aa124-284">**actual_length**: długość rzeczywiście odebrana.</span><span class="sxs-lookup"><span data-stu-id="aa124-284">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-285">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-285">Return Value</span></span>

- <span data-ttu-id="aa124-286">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-286">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-287">**UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, odczytywanie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="aa124-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-288">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-288">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a><span data-ttu-id="aa124-289">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="aa124-289">ux_host_class_asix_write</span></span>

<span data-ttu-id="aa124-290">Zapisz w interfejsie ASIX.</span><span class="sxs-lookup"><span data-stu-id="aa124-290">Write to the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-291">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-291">Prototype</span></span>

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a><span data-ttu-id="aa124-292">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-292">Description</span></span>

<span data-ttu-id="aa124-293">Ta funkcja zapisuje w interfejsie ASIX.</span><span class="sxs-lookup"><span data-stu-id="aa124-293">This function writes to the asix interface.</span></span> <span data-ttu-id="aa124-294">Wywołanie nie blokuje się.</span><span class="sxs-lookup"><span data-stu-id="aa124-294">The call is non blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-295">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-295">Parameters</span></span>

- <span data-ttu-id="aa124-296">**ASIX**: wskaźnik do wystąpienia klasy ASIX.</span><span class="sxs-lookup"><span data-stu-id="aa124-296">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="aa124-297">**pakiet**: pakiet danych NetX</span><span class="sxs-lookup"><span data-stu-id="aa124-297">**packet**: Netx data packet</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-298">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-298">Return Value</span></span>

- <span data-ttu-id="aa124-299">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-299">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-300">**UX_ERROR**: (0xFF) nie można zażądać przeniesienia.</span><span class="sxs-lookup"><span data-stu-id="aa124-300">**UX_ERROR**: (0xFF) Transfer could not be requested.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-301">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-301">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="aa124-302">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="aa124-302">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="aa124-303">Otwórz sesję między inicjatorem a obiektem odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="aa124-303">Open a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-304">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-304">Prototype</span></span>

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="aa124-305">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-305">Description</span></span>

<span data-ttu-id="aa124-306">Ta funkcja otwiera sesję między inicjatorem PIMA a obiektem odpowiadającym PIMA.</span><span class="sxs-lookup"><span data-stu-id="aa124-306">This function opens a session between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="aa124-307">Po pomyślnym otwarciu sesji można wykonać większość poleceń PIMA.</span><span class="sxs-lookup"><span data-stu-id="aa124-307">Once a session is successfully opened, most PIMA commands can be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-308">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-308">Parameters</span></span>

- <span data-ttu-id="aa124-309">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-309">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-310">**pima_sessio**: wskaźnik do sesji Pima<</span><span class="sxs-lookup"><span data-stu-id="aa124-310">**pima_sessio**: Pointer to PIMA session<</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-311">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-311">Return Value</span></span>

- <span data-ttu-id="aa124-312">**UX_SUCCESS**: (0x00) pomyślnie otwarto sesję</span><span class="sxs-lookup"><span data-stu-id="aa124-312">**UX_SUCCESS**: (0x00) Session successfully opened</span></span>
- <span data-ttu-id="aa124-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0X201E) sesja została już otwarta</span><span class="sxs-lookup"><span data-stu-id="aa124-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session already opened</span></span>

### <a name="example"></a><span data-ttu-id="aa124-314">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-314">Example</span></span>

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="aa124-315">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="aa124-315">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="aa124-316">Zamknij sesję między inicjatorem a obiektem odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="aa124-316">Close a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-317">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-317">Prototype</span></span>

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="aa124-318">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-318">Description</span></span>

<span data-ttu-id="aa124-319">Ta funkcja zamyka sesję, która została wcześniej otwarta między inicjatorem PIMA a obiektem odpowiadającym PIMA.</span><span class="sxs-lookup"><span data-stu-id="aa124-319">This function closes a session that was previously opened between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="aa124-320">Po zamknięciu sesji większość poleceń PIMA nie można już wykonywać.</span><span class="sxs-lookup"><span data-stu-id="aa124-320">Once a session is closed, most PIMA commands can no longer be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-321">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-321">Parameters</span></span>

- <span data-ttu-id="aa124-322">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-322">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-323">**pima_session**: wskaźnik do sesji Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-323">**pima_session**: Pointer to PIMA session.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-324">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-324">Return Value</span></span>

- <span data-ttu-id="aa124-325">**UX_SUCCESS**: (0x00) sesja została zamknięta.</span><span class="sxs-lookup"><span data-stu-id="aa124-325">**UX_SUCCESS**: (0x00) The session was closed.</span></span>
- <span data-ttu-id="aa124-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).</span><span class="sxs-lookup"><span data-stu-id="aa124-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-327">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-327">Example</span></span>

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a><span data-ttu-id="aa124-328">ux_host_class_pima_storage_ids_get</span><span class="sxs-lookup"><span data-stu-id="aa124-328">ux_host_class_pima_storage_ids_get</span></span>

<span data-ttu-id="aa124-329">Uzyskaj tablicę identyfikatorów magazynu od obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-329">Obtain the storage ID array from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-330">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-330">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a><span data-ttu-id="aa124-331">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-331">Description</span></span>

<span data-ttu-id="aa124-332">Ta funkcja uzyskuje tablicę identyfikatorów magazynu od obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-332">This function obtains the storage ID array from the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-333">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-333">Parameters</span></span>

- <span data-ttu-id="aa124-334">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-334">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-335">**pima_session**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-335">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-336">**storage_ids_array**: tablica, w której zostaną zwrócone identyfikatory magazynu</span><span class="sxs-lookup"><span data-stu-id="aa124-336">**storage_ids_array**: Array where storage IDs will be returned</span></span>
- <span data-ttu-id="aa124-337">**storage_id_length**: długość tablicy magazynowej</span><span class="sxs-lookup"><span data-stu-id="aa124-337">**storage_id_length**: Length of the storage array</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-338">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-338">Return Value</span></span>

- <span data-ttu-id="aa124-339">**UX_SUCCESS**: (0x00) tablica identyfikatorów magazynu została wypełniona</span><span class="sxs-lookup"><span data-stu-id="aa124-339">**UX_SUCCESS**: (0x00) The storage ID array has been populated</span></span>
- <span data-ttu-id="aa124-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-341">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-341">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-342">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-342">Example</span></span>

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="aa124-343">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="aa124-343">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="aa124-344">Uzyskaj informacje o magazynie z obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-344">Obtain the storage information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-345">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-345">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a><span data-ttu-id="aa124-346">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-346">Description</span></span>

<span data-ttu-id="aa124-347">Ta funkcja uzyskuje informacje o magazynie dla kontenera magazynu o wartości *storage_id*.</span><span class="sxs-lookup"><span data-stu-id="aa124-347">This function obtains the storage information for a storage container of value *storage_id*.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-348">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-348">Parameters</span></span>

- <span data-ttu-id="aa124-349">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-349">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-350">**pima_session**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-350">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-351">**storage_id**: Identyfikator kontenera magazynu</span><span class="sxs-lookup"><span data-stu-id="aa124-351">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="aa124-352">**Magazyn**: wskaźnik do kontenera informacji o magazynie</span><span class="sxs-lookup"><span data-stu-id="aa124-352">**storage**: Pointer to storage information container</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-353">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-353">Return Value</span></span>

- <span data-ttu-id="aa124-354">**UX_SUCCESS**: (0x00) informacje o magazynie zostały pobrane</span><span class="sxs-lookup"><span data-stu-id="aa124-354">**UX_SUCCESS**: (0x00) The storage information was retrieved</span></span>
- <span data-ttu-id="aa124-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-356">**UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-356">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-357">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-357">Example</span></span>

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a><span data-ttu-id="aa124-358">ux_host_class_pima_num_objects_get</span><span class="sxs-lookup"><span data-stu-id="aa124-358">ux_host_class_pima_num_objects_get</span></span>

<span data-ttu-id="aa124-359">Uzyskaj liczbę obiektów w kontenerze magazynu od obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-359">Obtain the number of objects on a storage container from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-360">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-360">Prototype</span></span>

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a><span data-ttu-id="aa124-361">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-361">Description</span></span>

<span data-ttu-id="aa124-362">Ta funkcja uzyskuje liczbę obiektów przechowywanych w określonym kontenerze magazynu o wartości storage_id pasujących do określonego kodu formatu.</span><span class="sxs-lookup"><span data-stu-id="aa124-362">This function obtains the number of objects stored on a specific storage container of value storage_id matching a specific format code.</span></span> <span data-ttu-id="aa124-363">W polu jest zwracana liczba obiektów: ux_host_class_pima_session_nb_objects struktury pima_session.</span><span class="sxs-lookup"><span data-stu-id="aa124-363">The number of objects is returned in the field: ux_host_class_pima_session_nb_objects of the pima_session structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-364">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-364">Parameters</span></span>

- <span data-ttu-id="aa124-365">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-365">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-366">**pima_session**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-366">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-367">**storage_id**: Identyfikator kontenera magazynu</span><span class="sxs-lookup"><span data-stu-id="aa124-367">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="aa124-368">**object_format_code**: obiekty formatują filtr kodu.</span><span class="sxs-lookup"><span data-stu-id="aa124-368">**object_format_code**: Objects format code filter.</span></span>

<span data-ttu-id="aa124-369">Kody formatu obiektów mogą mieć jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="aa124-369">The Object Format Codes can have one of the following values.</span></span>

| <span data-ttu-id="aa124-370">Kod formatu obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-370">Object Format Code</span></span>               | <span data-ttu-id="aa124-371">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-371">Description</span></span>   |     <span data-ttu-id="aa124-372">Kod USBX</span><span class="sxs-lookup"><span data-stu-id="aa124-372">USBX code</span></span>                          |
|----------------------------------|---------------|------------------------------------------|
| <span data-ttu-id="aa124-373">0x3000</span><span class="sxs-lookup"><span data-stu-id="aa124-373">0x3000</span></span>                           | <span data-ttu-id="aa124-374">Niezdefiniowany niezdefiniowany obiekt niebędący obrazem</span><span class="sxs-lookup"><span data-stu-id="aa124-374">Undefined Undefined non-image object</span></span> | <span data-ttu-id="aa124-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span><span class="sxs-lookup"><span data-stu-id="aa124-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span></span>   |
| <span data-ttu-id="aa124-376">0x3001</span><span class="sxs-lookup"><span data-stu-id="aa124-376">0x3001</span></span>                           | <span data-ttu-id="aa124-377">Skojarzenie skojarzenia (np. folder)</span><span class="sxs-lookup"><span data-stu-id="aa124-377">Association Association (e.g. folder)</span></span> | <span data-ttu-id="aa124-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span><span class="sxs-lookup"><span data-stu-id="aa124-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span></span> |
| <span data-ttu-id="aa124-379">0x3002</span><span class="sxs-lookup"><span data-stu-id="aa124-379">0x3002</span></span>                           | <span data-ttu-id="aa124-380">Skrypt specyficzny dla modelu urządzenia</span><span class="sxs-lookup"><span data-stu-id="aa124-380">Script Device-model specific script</span></span> | <span data-ttu-id="aa124-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="aa124-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span></span>      |
| <span data-ttu-id="aa124-382">0x3003</span><span class="sxs-lookup"><span data-stu-id="aa124-382">0x3003</span></span>                           | <span data-ttu-id="aa124-383">Plik wykonywalny specyficzny dla modelu urządzenia</span><span class="sxs-lookup"><span data-stu-id="aa124-383">Executable Device model-specific binary executable</span></span> | <span data-ttu-id="aa124-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span><span class="sxs-lookup"><span data-stu-id="aa124-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span></span>  |
| <span data-ttu-id="aa124-385">0x3004</span><span class="sxs-lookup"><span data-stu-id="aa124-385">0x3004</span></span>                           | <span data-ttu-id="aa124-386">Plik tekstowy tekstu</span><span class="sxs-lookup"><span data-stu-id="aa124-386">Text Text file</span></span>  |   <span data-ttu-id="aa124-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span><span class="sxs-lookup"><span data-stu-id="aa124-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span></span>        |
| <span data-ttu-id="aa124-388">0x3005</span><span class="sxs-lookup"><span data-stu-id="aa124-388">0x3005</span></span>                           | <span data-ttu-id="aa124-389">Plik HTML HyperText Markup Language (tekst)</span><span class="sxs-lookup"><span data-stu-id="aa124-389">HTML HyperText Markup Language file (text)</span></span> | <span data-ttu-id="aa124-390">UX_HOST_CLASS_PIMA_OFC_HTML</span><span class="sxs-lookup"><span data-stu-id="aa124-390">UX_HOST_CLASS_PIMA_OFC_HTML</span></span>        |
| <span data-ttu-id="aa124-391">0x3006</span><span class="sxs-lookup"><span data-stu-id="aa124-391">0x3006</span></span>                           | <span data-ttu-id="aa124-392">Plik formatu porządkowania cyfrowych DPOF (tekst)</span><span class="sxs-lookup"><span data-stu-id="aa124-392">DPOF Digital Print Order Format file (text)</span></span> | <span data-ttu-id="aa124-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span><span class="sxs-lookup"><span data-stu-id="aa124-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span></span>        |
| <span data-ttu-id="aa124-394">0x3007</span><span class="sxs-lookup"><span data-stu-id="aa124-394">0x3007</span></span>                           | <span data-ttu-id="aa124-395">Klip audio AIFF</span><span class="sxs-lookup"><span data-stu-id="aa124-395">AIFF Audio clip</span></span>  |  <span data-ttu-id="aa124-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span><span class="sxs-lookup"><span data-stu-id="aa124-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span></span>        |
| <span data-ttu-id="aa124-397">0x3008</span><span class="sxs-lookup"><span data-stu-id="aa124-397">0x3008</span></span>                           | <span data-ttu-id="aa124-398">Klip audio WAV</span><span class="sxs-lookup"><span data-stu-id="aa124-398">WAV Audio clip</span></span>   |  <span data-ttu-id="aa124-399">UX_HOST_CLASS_PIMA_OFC_WAV</span><span class="sxs-lookup"><span data-stu-id="aa124-399">UX_HOST_CLASS_PIMA_OFC_WAV</span></span>         |
| <span data-ttu-id="aa124-400">0x3009</span><span class="sxs-lookup"><span data-stu-id="aa124-400">0x3009</span></span>                           | <span data-ttu-id="aa124-401">Klip audio MP3</span><span class="sxs-lookup"><span data-stu-id="aa124-401">MP3 Audio clip</span></span>   |  <span data-ttu-id="aa124-402">UX_HOST_CLASS_PIMA_OFC_MP3</span><span class="sxs-lookup"><span data-stu-id="aa124-402">UX_HOST_CLASS_PIMA_OFC_MP3</span></span>         |
| <span data-ttu-id="aa124-403">0x300A</span><span class="sxs-lookup"><span data-stu-id="aa124-403">0x300A</span></span>                           | <span data-ttu-id="aa124-404">Klip wideo AVI</span><span class="sxs-lookup"><span data-stu-id="aa124-404">AVI Video clip</span></span>   |  <span data-ttu-id="aa124-405">UX_HOST_CLASS_PIMA_OFC_AVI</span><span class="sxs-lookup"><span data-stu-id="aa124-405">UX_HOST_CLASS_PIMA_OFC_AVI</span></span>         |
| <span data-ttu-id="aa124-406">0x300B</span><span class="sxs-lookup"><span data-stu-id="aa124-406">0x300B</span></span>                           | <span data-ttu-id="aa124-407">Klip wideo MPEG</span><span class="sxs-lookup"><span data-stu-id="aa124-407">MPEG Video clip</span></span>  |  <span data-ttu-id="aa124-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span><span class="sxs-lookup"><span data-stu-id="aa124-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span></span>        |
| <span data-ttu-id="aa124-409">0x300C</span><span class="sxs-lookup"><span data-stu-id="aa124-409">0x300C</span></span>                           | <span data-ttu-id="aa124-410">Microsoft Advanced Streaming format (wideo)</span><span class="sxs-lookup"><span data-stu-id="aa124-410">ASF Microsoft Advanced Streaming Format (video)</span></span> | <span data-ttu-id="aa124-411">UX_HOST_CLASS_PIMA_OFC_ASF</span><span class="sxs-lookup"><span data-stu-id="aa124-411">UX_HOST_CLASS_PIMA_OFC_ASF</span></span>         |
| <span data-ttu-id="aa124-412">0x3800</span><span class="sxs-lookup"><span data-stu-id="aa124-412">0x3800</span></span>                           | <span data-ttu-id="aa124-413">Niezdefiniowany nieznany obiekt obrazu</span><span class="sxs-lookup"><span data-stu-id="aa124-413">Undefined Unknown image object</span></span> | <span data-ttu-id="aa124-414">UX_HOST_CLASS_PIMA_OFC_QT</span><span class="sxs-lookup"><span data-stu-id="aa124-414">UX_HOST_CLASS_PIMA_OFC_QT</span></span>          |
| <span data-ttu-id="aa124-415">0x3801</span><span class="sxs-lookup"><span data-stu-id="aa124-415">0x3801</span></span>                           | <span data-ttu-id="aa124-416">Format pliku EXIF/JPEG z wymianą, JEIDA Standard</span><span class="sxs-lookup"><span data-stu-id="aa124-416">EXIF/JPEG Exchangeable File Format, JEIDA standard</span></span> | <span data-ttu-id="aa124-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="aa124-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span></span>   |
| <span data-ttu-id="aa124-418">0x3802</span><span class="sxs-lookup"><span data-stu-id="aa124-418">0x3802</span></span>                           | <span data-ttu-id="aa124-419">Format pliku obrazu znacznika TIFF/EP dla fotografii elektronicznych</span><span class="sxs-lookup"><span data-stu-id="aa124-419">TIFF/EP Tag Image File Format for Electronic Photography</span></span> | <span data-ttu-id="aa124-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span><span class="sxs-lookup"><span data-stu-id="aa124-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span></span>     |
| <span data-ttu-id="aa124-421">0x3803</span><span class="sxs-lookup"><span data-stu-id="aa124-421">0x3803</span></span>                           | <span data-ttu-id="aa124-422">Format obrazu magazynu strukturalnego FlashPix</span><span class="sxs-lookup"><span data-stu-id="aa124-422">FlashPix Structured Storage Image Format</span></span> | <span data-ttu-id="aa124-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span><span class="sxs-lookup"><span data-stu-id="aa124-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span></span>    |
| <span data-ttu-id="aa124-424">0x3804</span><span class="sxs-lookup"><span data-stu-id="aa124-424">0x3804</span></span>                           | <span data-ttu-id="aa124-425">BMP plik mapy bitowej systemu Microsoft Windows</span><span class="sxs-lookup"><span data-stu-id="aa124-425">BMP Microsoft Windows Bitmap file</span></span> | <span data-ttu-id="aa124-426">UX_HOST_CLASS_PIMA_OFC_BMP</span><span class="sxs-lookup"><span data-stu-id="aa124-426">UX_HOST_CLASS_PIMA_OFC_BMP</span></span>         |
| <span data-ttu-id="aa124-427">0x3805</span><span class="sxs-lookup"><span data-stu-id="aa124-427">0x3805</span></span>                           | <span data-ttu-id="aa124-428">Format pliku obrazu aparatu CIFF firmy Canon</span><span class="sxs-lookup"><span data-stu-id="aa124-428">CIFF Canon Camera Image File Format</span></span> | <span data-ttu-id="aa124-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span><span class="sxs-lookup"><span data-stu-id="aa124-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span></span>        |
| <span data-ttu-id="aa124-430">0x3806</span><span class="sxs-lookup"><span data-stu-id="aa124-430">0x3806</span></span>                           | <span data-ttu-id="aa124-431">Niezdefiniowane zarezerwowane</span><span class="sxs-lookup"><span data-stu-id="aa124-431">Undefined Reserved</span></span> |  |
| <span data-ttu-id="aa124-432">0x3807</span><span class="sxs-lookup"><span data-stu-id="aa124-432">0x3807</span></span>                           | <span data-ttu-id="aa124-433">Graphics Interchange Format GIF</span><span class="sxs-lookup"><span data-stu-id="aa124-433">GIF Graphics Interchange Format</span></span> | <span data-ttu-id="aa124-434">UX_HOST_CLASS_PIMA_OFC_GIF</span><span class="sxs-lookup"><span data-stu-id="aa124-434">UX_HOST_CLASS_PIMA_OFC_GIF</span></span>         |
| <span data-ttu-id="aa124-435">0x3808</span><span class="sxs-lookup"><span data-stu-id="aa124-435">0x3808</span></span>                           | <span data-ttu-id="aa124-436">Format wymiany plików w formacie JFIF</span><span class="sxs-lookup"><span data-stu-id="aa124-436">JFIF JPEG File Interchange Format</span></span> | <span data-ttu-id="aa124-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span><span class="sxs-lookup"><span data-stu-id="aa124-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span></span>        |
| <span data-ttu-id="aa124-438">0x3809</span><span class="sxs-lookup"><span data-stu-id="aa124-438">0x3809</span></span>                           | <span data-ttu-id="aa124-439">PCD PhotoCD Image PAC</span><span class="sxs-lookup"><span data-stu-id="aa124-439">PCD PhotoCD Image Pac</span></span> | <span data-ttu-id="aa124-440">UX_HOST_CLASS_PIMA_OFC_PCD</span><span class="sxs-lookup"><span data-stu-id="aa124-440">UX_HOST_CLASS_PIMA_OFC_PCD</span></span>         |
| <span data-ttu-id="aa124-441">0x380A</span><span class="sxs-lookup"><span data-stu-id="aa124-441">0x380A</span></span>                           | <span data-ttu-id="aa124-442">Format obrazu PICT QUICKDRAW</span><span class="sxs-lookup"><span data-stu-id="aa124-442">PICT Quickdraw Image Format</span></span> | <span data-ttu-id="aa124-443">UX_HOST_CLASS_PIMA_OFC_PICT</span><span class="sxs-lookup"><span data-stu-id="aa124-443">UX_HOST_CLASS_PIMA_OFC_PICT</span></span>        |
| <span data-ttu-id="aa124-444">0x380B</span><span class="sxs-lookup"><span data-stu-id="aa124-444">0x380B</span></span>                           | <span data-ttu-id="aa124-445">Portable Network Graphics PNG</span><span class="sxs-lookup"><span data-stu-id="aa124-445">PNG Portable Network Graphics</span></span> | <span data-ttu-id="aa124-446">UX_HOST_CLASS_PIMA_OFC_PNG</span><span class="sxs-lookup"><span data-stu-id="aa124-446">UX_HOST_CLASS_PIMA_OFC_PNG</span></span>         |
| <span data-ttu-id="aa124-447">0x380C</span><span class="sxs-lookup"><span data-stu-id="aa124-447">0x380C</span></span>                           | <span data-ttu-id="aa124-448">Niezdefiniowane zarezerwowane</span><span class="sxs-lookup"><span data-stu-id="aa124-448">Undefined Reserved</span></span> |   |
| <span data-ttu-id="aa124-449">0x380D</span><span class="sxs-lookup"><span data-stu-id="aa124-449">0x380D</span></span>                           | <span data-ttu-id="aa124-450">Format pliku obrazu znacznika TIFF</span><span class="sxs-lookup"><span data-stu-id="aa124-450">TIFF Tag Image File Format</span></span> | <span data-ttu-id="aa124-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span><span class="sxs-lookup"><span data-stu-id="aa124-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span></span>        |
| <span data-ttu-id="aa124-452">0x380E</span><span class="sxs-lookup"><span data-stu-id="aa124-452">0x380E</span></span>                           | <span data-ttu-id="aa124-453">Format TIFF/tag obrazu dla technologii informatycznych (grafiki sztuki)</span><span class="sxs-lookup"><span data-stu-id="aa124-453">TIFF/IT Tag Image File Format for Information Technology (graphic arts)</span></span> | <span data-ttu-id="aa124-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span><span class="sxs-lookup"><span data-stu-id="aa124-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span></span>     |
| <span data-ttu-id="aa124-455">0x380F</span><span class="sxs-lookup"><span data-stu-id="aa124-455">0x380F</span></span>                           | <span data-ttu-id="aa124-456">Format pliku bazowego JP2 JPEG2000</span><span class="sxs-lookup"><span data-stu-id="aa124-456">JP2 JPEG2000 Baseline File Format</span></span> | <span data-ttu-id="aa124-457">UX_HOST_CLASS_PIMA_OFC_JP2</span><span class="sxs-lookup"><span data-stu-id="aa124-457">UX_HOST_CLASS_PIMA_OFC_JP2</span></span>         |
| <span data-ttu-id="aa124-458">0x3810</span><span class="sxs-lookup"><span data-stu-id="aa124-458">0x3810</span></span>                           | <span data-ttu-id="aa124-459">Rozszerzony format pliku JPX JPEG2000</span><span class="sxs-lookup"><span data-stu-id="aa124-459">JPX JPEG2000 Extended File Format</span></span> | <span data-ttu-id="aa124-460">UX_HOST_CLASS_PIMA_OFC_JPX</span><span class="sxs-lookup"><span data-stu-id="aa124-460">UX_HOST_CLASS_PIMA_OFC_JPX</span></span>         |
| <span data-ttu-id="aa124-461">Wszystkie inne kody z usługą MSN of 0011</span><span class="sxs-lookup"><span data-stu-id="aa124-461">All other codes with MSN of 0011</span></span> | <span data-ttu-id="aa124-462">Wszystkie niezdefiniowane zarezerwowane do użytku w przyszłości</span><span class="sxs-lookup"><span data-stu-id="aa124-462">Any Undefined Reserved for future use</span></span> |                                    |
| <span data-ttu-id="aa124-463">Wszystkie inne kody z usługą MSN of 1011</span><span class="sxs-lookup"><span data-stu-id="aa124-463">All other codes with MSN of 1011</span></span> | <span data-ttu-id="aa124-464">Dowolny zdefiniowany przez dostawcę typ zdefiniowany przez dostawcę: obraz</span><span class="sxs-lookup"><span data-stu-id="aa124-464">Any Vendor-Defined Vendor-Defined type: Image</span></span> |                                    |

### <a name="return-value"></a><span data-ttu-id="aa124-465">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-465">Return Value</span></span>

- <span data-ttu-id="aa124-466">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-466">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-468">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-468">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-469">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-469">Example</span></span>

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a><span data-ttu-id="aa124-470">ux_host_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="aa124-470">ux_host_class_pima_object_handles_get</span></span>

<span data-ttu-id="aa124-471">Uzyskaj uchwyty obiektów z obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-471">Obtain object handles from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-472">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-472">Prototype</span></span>

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a><span data-ttu-id="aa124-473">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-473">Description</span></span>

<span data-ttu-id="aa124-474">Zwraca tablicę dojść do obiektów znajdujących się w kontenerze magazynu wskazanym przez parametr storage_id.</span><span class="sxs-lookup"><span data-stu-id="aa124-474">Returns an array of Object Handles present in the storage container indicated by the storage_id parameter.</span></span> <span data-ttu-id="aa124-475">Jeśli wymagana jest lista zagregowana we wszystkich sklepach, ta wartość jest ustawiana na 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="aa124-475">If an aggregated list across all stores is desired, this value shall be set to 0xFFFFFFFF.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-476">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-476">Parameters</span></span>

- <span data-ttu-id="aa124-477">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-477">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-478">**pima_session**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-478">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-479">**object_handes_array**: zwrócono tablicę, w której są dojścia</span><span class="sxs-lookup"><span data-stu-id="aa124-479">**object_handes_array**: Array where handles are returned</span></span>
- <span data-ttu-id="aa124-480">**object_handles_length**: długość tablicy</span><span class="sxs-lookup"><span data-stu-id="aa124-480">**object_handles_length**: Length of the array</span></span>
- <span data-ttu-id="aa124-481">**storage_id**: Identyfikator kontenera magazynu</span><span class="sxs-lookup"><span data-stu-id="aa124-481">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="aa124-482">**object_format_code**: Formatuj kod dla obiektu (patrz tabela dla funkcji ux_host_class_pima_num_objects_get)</span><span class="sxs-lookup"><span data-stu-id="aa124-482">**object_format_code**: Format code for object (see table for function ux_host_class_pima_num_objects_get)</span></span>
- <span data-ttu-id="aa124-483">**object_handle_association**: opcjonalna wartość skojarzenia obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-483">**object_handle_association**: Optional object association value</span></span>

<span data-ttu-id="aa124-484">Skojarzenie uchwytu obiektu może być jedną z wartości z poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="aa124-484">The object handle association can be one of the value from the table below:</span></span>

| <span data-ttu-id="aa124-485">AssociationCode</span><span class="sxs-lookup"><span data-stu-id="aa124-485">AssociationCode</span></span>                        | <span data-ttu-id="aa124-486">Obiekt AssociationType</span><span class="sxs-lookup"><span data-stu-id="aa124-486">AssociationType</span></span>      | <span data-ttu-id="aa124-487">Interpretacja</span><span class="sxs-lookup"><span data-stu-id="aa124-487">Interpretation</span></span>       |
|----------------------------------------|----------------------|----------------------|
| <span data-ttu-id="aa124-488">0x0000</span><span class="sxs-lookup"><span data-stu-id="aa124-488">0x0000</span></span>                                 | <span data-ttu-id="aa124-489">Niezdefiniowane</span><span class="sxs-lookup"><span data-stu-id="aa124-489">Undefined</span></span>            | <span data-ttu-id="aa124-490">Niezdefiniowane</span><span class="sxs-lookup"><span data-stu-id="aa124-490">Undefined</span></span>            |
| <span data-ttu-id="aa124-491">0x0001</span><span class="sxs-lookup"><span data-stu-id="aa124-491">0x0001</span></span>                                 | <span data-ttu-id="aa124-492">GenericFolder</span><span class="sxs-lookup"><span data-stu-id="aa124-492">GenericFolder</span></span>        | <span data-ttu-id="aa124-493">Nieużywane</span><span class="sxs-lookup"><span data-stu-id="aa124-493">Unused</span></span>               |
| <span data-ttu-id="aa124-494">0x0002</span><span class="sxs-lookup"><span data-stu-id="aa124-494">0x0002</span></span>                                 | <span data-ttu-id="aa124-495">Albumu</span><span class="sxs-lookup"><span data-stu-id="aa124-495">Album</span></span>                | <span data-ttu-id="aa124-496">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="aa124-496">Reserved</span></span>             |
| <span data-ttu-id="aa124-497">0x0003</span><span class="sxs-lookup"><span data-stu-id="aa124-497">0x0003</span></span>                                 | <span data-ttu-id="aa124-498">TimeSequence</span><span class="sxs-lookup"><span data-stu-id="aa124-498">TimeSequence</span></span>         | <span data-ttu-id="aa124-499">DefaultPlaybackDelta</span><span class="sxs-lookup"><span data-stu-id="aa124-499">DefaultPlaybackDelta</span></span> |
| <span data-ttu-id="aa124-500">0x0004</span><span class="sxs-lookup"><span data-stu-id="aa124-500">0x0004</span></span>                                 | <span data-ttu-id="aa124-501">HorizontalPanoramic</span><span class="sxs-lookup"><span data-stu-id="aa124-501">HorizontalPanoramic</span></span>  | <span data-ttu-id="aa124-502">Nieużywane</span><span class="sxs-lookup"><span data-stu-id="aa124-502">Unused</span></span>               |
| <span data-ttu-id="aa124-503">0x0005</span><span class="sxs-lookup"><span data-stu-id="aa124-503">0x0005</span></span>                                 | <span data-ttu-id="aa124-504">VerticalPanoramic</span><span class="sxs-lookup"><span data-stu-id="aa124-504">VerticalPanoramic</span></span>    | <span data-ttu-id="aa124-505">Nieużywane</span><span class="sxs-lookup"><span data-stu-id="aa124-505">Unused</span></span>               |
| <span data-ttu-id="aa124-506">0x0006</span><span class="sxs-lookup"><span data-stu-id="aa124-506">0x0006</span></span>                                 | <span data-ttu-id="aa124-507">2DPanoramic</span><span class="sxs-lookup"><span data-stu-id="aa124-507">2DPanoramic</span></span>          | <span data-ttu-id="aa124-508">ImagesPerRow</span><span class="sxs-lookup"><span data-stu-id="aa124-508">ImagesPerRow</span></span>         |
| <span data-ttu-id="aa124-509">0x0007</span><span class="sxs-lookup"><span data-stu-id="aa124-509">0x0007</span></span>                                 | <span data-ttu-id="aa124-510">AncillaryData</span><span class="sxs-lookup"><span data-stu-id="aa124-510">AncillaryData</span></span>        | <span data-ttu-id="aa124-511">Niezdefiniowane</span><span class="sxs-lookup"><span data-stu-id="aa124-511">Undefined</span></span>            |
| <span data-ttu-id="aa124-512">Wszystkie inne wartości z bit 15 ustawione na 0</span><span class="sxs-lookup"><span data-stu-id="aa124-512">All other values with bit 15 set to 0</span></span>  | <span data-ttu-id="aa124-513">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="aa124-513">Reserved</span></span>             | <span data-ttu-id="aa124-514">Niezdefiniowane</span><span class="sxs-lookup"><span data-stu-id="aa124-514">Undefined</span></span>            |
| <span data-ttu-id="aa124-515">Wszystkie wartości z bit 15 ustawiony na 1</span><span class="sxs-lookup"><span data-stu-id="aa124-515">All values with bit 15 set to 1</span></span>        | <span data-ttu-id="aa124-516">Zdefiniowany przez dostawcę</span><span class="sxs-lookup"><span data-stu-id="aa124-516">Vendor-Defined</span></span>       | <span data-ttu-id="aa124-517">Zdefiniowany przez dostawcę</span><span class="sxs-lookup"><span data-stu-id="aa124-517">Vendor-Defined</span></span>       |

### <a name="return-value"></a><span data-ttu-id="aa124-518">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-518">Return Value</span></span>

- <span data-ttu-id="aa124-519">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-519">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-521">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-521">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-522">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-522">Example</span></span>

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="aa124-523">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="aa124-523">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="aa124-524">Uzyskaj informacje o obiekcie z obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-524">Obtain the object information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-525">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-525">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="aa124-526">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-526">Description</span></span>

<span data-ttu-id="aa124-527">Ta funkcja uzyskuje informacje o obiekcie dla uchwytu obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa124-527">This function obtains the object information for an object handle.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-528">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-528">Parameters</span></span>

- <span data-ttu-id="aa124-529">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-529">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-530">**pima_session**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-530">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-531">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-531">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="aa124-532">**Object**: wskaźnik do kontenera informacji o obiekcie</span><span class="sxs-lookup"><span data-stu-id="aa124-532">**object**: Pointer to object information container</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-533">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-533">Return Value</span></span>

- <span data-ttu-id="aa124-534">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-534">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-536">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-536">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-537">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-537">Example</span></span>

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="aa124-538">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="aa124-538">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="aa124-539">Wyślij informacje o obiekcie do obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-539">Send the object information to Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-540">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-540">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="aa124-541">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-541">Description</span></span>

<span data-ttu-id="aa124-542">Ta funkcja wysyła informacje o magazynie dla kontenera magazynu o wartości storage_id.</span><span class="sxs-lookup"><span data-stu-id="aa124-542">This function sends the storage information for a storage container of value storage_id.</span></span> <span data-ttu-id="aa124-543">Inicjator powinien użyć tego polecenia przed wysłaniem obiektu do obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-543">The Initiator should use this command before sending an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-544">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-544">Parameters</span></span>

- <span data-ttu-id="aa124-545">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-545">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-546">**pima_session**: wskaźnik do sesji Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-546">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="aa124-547">**storage_id**: docelowy identyfikator magazynu.</span><span class="sxs-lookup"><span data-stu-id="aa124-547">**storage_id**: Destination storage ID.</span></span>
- <span data-ttu-id="aa124-548">**parent_object_id**: element nadrzędny ObjectHandle na obiekcie odpowiadającym, na którym ma zostać umieszczony obiekt.</span><span class="sxs-lookup"><span data-stu-id="aa124-548">**parent_object_id**: Parent ObjectHandle on Responder where object should be placed.</span></span>
- <span data-ttu-id="aa124-549">**Object**: wskaźnik do kontenera informacji o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="aa124-549">**object**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-550">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-550">Return Value</span></span>

- <span data-ttu-id="aa124-551">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-551">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-553">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-553">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-554">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-554">Example</span></span>

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a><span data-ttu-id="aa124-555">ux_host_class_pima_object_open</span><span class="sxs-lookup"><span data-stu-id="aa124-555">ux_host_class_pima_object_open</span></span>

<span data-ttu-id="aa124-556">Otwórz obiekt przechowywany w obiekcie odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="aa124-556">Open an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-557">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-557">Prototype</span></span>

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="aa124-558">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-558">Description</span></span>

<span data-ttu-id="aa124-559">Ta funkcja otwiera obiekt obiektu odpowiadającego przed odczytem lub zapisem.</span><span class="sxs-lookup"><span data-stu-id="aa124-559">This function opens an object on the responder before reading or writing.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-560">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-560">Parameters</span></span>

- <span data-ttu-id="aa124-561">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-561">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-562">**pima_session**: wskaźnik do sesji Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-562">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="aa124-563">**object_handle**: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa124-563">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="aa124-564">**objec**: wskaźnik do kontenera informacji o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="aa124-564">**objec**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-565">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-565">Return Value</span></span>

- <span data-ttu-id="aa124-566">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-566">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-568">Obiekt **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="aa124-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Object already opened.</span></span>
- <span data-ttu-id="aa124-569">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-569">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-570">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-570">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="aa124-571">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="aa124-571">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="aa124-572">Pobierz obiekt przechowywany w obiekcie odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="aa124-572">Get an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-573">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-573">Prototype</span></span>

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a><span data-ttu-id="aa124-574">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-574">Description</span></span>

<span data-ttu-id="aa124-575">Ta funkcja pobiera obiekt obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-575">This function gets an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-576">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-576">Parameters</span></span>

- <span data-ttu-id="aa124-577">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-577">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-578">**pima_session**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-578">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-579">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-579">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="aa124-580">**Object**: wskaźnik do kontenera informacji o obiekcie</span><span class="sxs-lookup"><span data-stu-id="aa124-580">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="aa124-581">**object_buffer**: adres danych obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-581">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="aa124-582">**object_buffer_length**: Żądana długość obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-582">**object_buffer_length**: Requested length of object</span></span>
- <span data-ttu-id="aa124-583">**object_actual_length**: długość zwróconego obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-583">**object_actual_length**: Length of object returned</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-584">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-584">Return Value</span></span>

- <span data-ttu-id="aa124-585">**UX_SUCCESS**: (0x00) obiekt został przeniesiony</span><span class="sxs-lookup"><span data-stu-id="aa124-585">**UX_SUCCESS**: (0x00) The object was transfered</span></span>
- <span data-ttu-id="aa124-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-587">Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).</span><span class="sxs-lookup"><span data-stu-id="aa124-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="aa124-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) dostęp do obiektu odmowa</span><span class="sxs-lookup"><span data-stu-id="aa124-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="aa124-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) transfer jest niekompletny</span><span class="sxs-lookup"><span data-stu-id="aa124-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="aa124-590">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-590">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="aa124-591">**UX_TRANSFER_ERROR**: błąd transferu (0x23) podczas odczytywania obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-591">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object</span></span>

### <a name="example"></a><span data-ttu-id="aa124-592">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-592">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a><span data-ttu-id="aa124-593">ux_host_class_pima_object_send</span><span class="sxs-lookup"><span data-stu-id="aa124-593">ux_host_class_pima_object_send</span></span>

<span data-ttu-id="aa124-594">Wyślij obiekt przechowywany w obiekcie odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="aa124-594">Send an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-595">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-595">Prototype</span></span>

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a><span data-ttu-id="aa124-596">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-596">Description</span></span>

<span data-ttu-id="aa124-597">Ta funkcja wysyła obiekt do obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-597">This function sends an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-598">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-598">Parameters</span></span>

- <span data-ttu-id="aa124-599">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-599">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-600">**pima_sessio**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-600">**pima_sessio**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-601">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-601">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="aa124-602">**Object**: wskaźnik do kontenera informacji o obiekcie</span><span class="sxs-lookup"><span data-stu-id="aa124-602">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="aa124-603">**object_buffer**: adres danych obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-603">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="aa124-604">**object_buffer_length**: Żądana długość obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-604">**object_buffer_length**: Requested length of object</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-605">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-605">Return Value</span></span>

- <span data-ttu-id="aa124-606">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-606">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji</span><span class="sxs-lookup"><span data-stu-id="aa124-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="aa124-608">Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).</span><span class="sxs-lookup"><span data-stu-id="aa124-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="aa124-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) dostęp do obiektu odmowa</span><span class="sxs-lookup"><span data-stu-id="aa124-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="aa124-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) transfer jest niekompletny</span><span class="sxs-lookup"><span data-stu-id="aa124-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="aa124-611">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-611">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="aa124-612">**UX_TRANSFER_ERROR**: (0x23) błąd transferu podczas zapisywania obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-612">**UX_TRANSFER_ERROR**: (0x23) Transfer error while writing object</span></span>

### <a name="example"></a><span data-ttu-id="aa124-613">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-613">Example</span></span>

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="aa124-614">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="aa124-614">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="aa124-615">Pobierz obiekt kciuka przechowywany w obiekcie odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="aa124-615">Get a thumb object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-616">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-616">Prototype</span></span>

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a><span data-ttu-id="aa124-617">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-617">Description</span></span>

<span data-ttu-id="aa124-618">Ta funkcja pobiera obiekt kciuka na obiekt odpowiadający.</span><span class="sxs-lookup"><span data-stu-id="aa124-618">This function gets a thumb object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-619">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-619">Parameters</span></span>

- <span data-ttu-id="aa124-620">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-620">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-621">**pima_session**: wskaźnik do sesji Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-621">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="aa124-622">**object_handle**: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa124-622">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="aa124-623">**Object**: wskaźnik do kontenera informacji o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="aa124-623">**object**: Pointer to object information container.</span></span>
- <span data-ttu-id="aa124-624">**thumb_buffer**: adres danych obiektu kciuka.</span><span class="sxs-lookup"><span data-stu-id="aa124-624">**thumb_buffer**: Address of thumb object data.</span></span>
- <span data-ttu-id="aa124-625">**thumb_buffer_length**: Żądana długość obiektu kciuka.</span><span class="sxs-lookup"><span data-stu-id="aa124-625">**thumb_buffer_length**: Requested length of thumb object.</span></span>
- <span data-ttu-id="aa124-626">**thumb_actual_length**: długość zwróconego obiektu kciuka.</span><span class="sxs-lookup"><span data-stu-id="aa124-626">**thumb_actual_length**: Length of thumb object returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-627">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-627">Return Value</span></span>

- <span data-ttu-id="aa124-628">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-628">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).</span><span class="sxs-lookup"><span data-stu-id="aa124-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="aa124-630">Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).</span><span class="sxs-lookup"><span data-stu-id="aa124-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="aa124-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) dostęp do obiektu odmowa.</span><span class="sxs-lookup"><span data-stu-id="aa124-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied.</span></span>
- <span data-ttu-id="aa124-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) transfer jest niekompletny.</span><span class="sxs-lookup"><span data-stu-id="aa124-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete.</span></span>
- <span data-ttu-id="aa124-633">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-633">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="aa124-634">**UX_TRANSFER_ERROR**: (0x23) błąd transferu podczas odczytywania obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa124-634">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-635">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-635">Example</span></span>

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="aa124-636">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="aa124-636">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="aa124-637">Usuń obiekt przechowywany w obiekcie odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="aa124-637">Delete an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-638">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-638">Prototype</span></span>

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a><span data-ttu-id="aa124-639">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-639">Description</span></span>

<span data-ttu-id="aa124-640">Ta funkcja usuwa obiekt obiektu odpowiadającego</span><span class="sxs-lookup"><span data-stu-id="aa124-640">This function deletes an object on the responder</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-641">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-641">Parameters</span></span>

- <span data-ttu-id="aa124-642">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-642">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-643">**pima_session**: wskaźnik do sesji Pima</span><span class="sxs-lookup"><span data-stu-id="aa124-643">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="aa124-644">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="aa124-644">**object_handle**: handle of the object</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-645">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-645">Return Value</span></span>

- <span data-ttu-id="aa124-646">**UX_SUCCESS**: (0x00) obiekt został usunięty.</span><span class="sxs-lookup"><span data-stu-id="aa124-646">**UX_SUCCESS**: (0x00) The object was deleted.</span></span>
- <span data-ttu-id="aa124-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).</span><span class="sxs-lookup"><span data-stu-id="aa124-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="aa124-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) nie można usunąć obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa124-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Cannot delete object.</span></span>
- <span data-ttu-id="aa124-649">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-649">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-650">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-650">Example</span></span>

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="aa124-651">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="aa124-651">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="aa124-652">Zamknij obiekt przechowywany w obiekcie odpowiadającym</span><span class="sxs-lookup"><span data-stu-id="aa124-652">Close an object stored in the Responder</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-653">Prototype</span></span>

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="aa124-654">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-654">Description</span></span>

<span data-ttu-id="aa124-655">Ta funkcja zamyka obiekt obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="aa124-655">This function closes an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-656">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-656">Parameters</span></span>

- <span data-ttu-id="aa124-657">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-657">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="aa124-658">**pima_session**: wskaźnik do sesji Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-658">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="aa124-659">**object_handle**: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa124-659">**object_handle**: Handle of the object.</span></span>
- <span data-ttu-id="aa124-660">**Object**: wskaźnik do obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa124-660">**object**: Pointer to object.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-661">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-661">Return Value</span></span>

- <span data-ttu-id="aa124-662">**UX_SUCCESS**: (0x00) obiekt został zamknięty.</span><span class="sxs-lookup"><span data-stu-id="aa124-662">**UX_SUCCESS**: (0x00) The object was closed.</span></span>
- <span data-ttu-id="aa124-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).</span><span class="sxs-lookup"><span data-stu-id="aa124-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="aa124-664">Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).</span><span class="sxs-lookup"><span data-stu-id="aa124-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="aa124-665">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.</span><span class="sxs-lookup"><span data-stu-id="aa124-665">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-666">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-666">Example</span></span>

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a><span data-ttu-id="aa124-667">ux_host_class_gser_read</span><span class="sxs-lookup"><span data-stu-id="aa124-667">ux_host_class_gser_read</span></span>

<span data-ttu-id="aa124-668">Odczytaj z ogólnego interfejsu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="aa124-668">Read from the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-669">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-669">Prototype</span></span>

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="aa124-670">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-670">Description</span></span>

<span data-ttu-id="aa124-671">Ta funkcja odczytuje z ogólnego interfejsu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="aa124-671">This function reads from the generic serial interface.</span></span> <span data-ttu-id="aa124-672">Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.</span><span class="sxs-lookup"><span data-stu-id="aa124-672">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-673">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-673">Parameters</span></span>

- <span data-ttu-id="aa124-674">**gser**: wskaźnik do wystąpienia klasy gser.</span><span class="sxs-lookup"><span data-stu-id="aa124-674">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="aa124-675">**interface_index**: indeks interfejsu, z którego ma zostać odczytany.</span><span class="sxs-lookup"><span data-stu-id="aa124-675">**interface_index**: Interface index to read from.</span></span>
- <span data-ttu-id="aa124-676">**data_pointer**: wskaźnik na adres buforu ładunku danych.</span><span class="sxs-lookup"><span data-stu-id="aa124-676">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="aa124-677">**requested_length**: długość do odebrania.</span><span class="sxs-lookup"><span data-stu-id="aa124-677">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="aa124-678">**actual_length**: długość rzeczywiście odebrana.</span><span class="sxs-lookup"><span data-stu-id="aa124-678">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-679">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-679">Return Value</span></span>

- <span data-ttu-id="aa124-680">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-680">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-681">**UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, odczytywanie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="aa124-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-682">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-682">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a><span data-ttu-id="aa124-683">ux_host_class_gser_write</span><span class="sxs-lookup"><span data-stu-id="aa124-683">ux_host_class_gser_write</span></span>

<span data-ttu-id="aa124-684">Zapisz w ogólnym interfejsie szeregowym.</span><span class="sxs-lookup"><span data-stu-id="aa124-684">Write to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-685">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-685">Prototype</span></span>

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="aa124-686">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-686">Description</span></span>

<span data-ttu-id="aa124-687">Ta funkcja zapisuje do ogólnego interfejsu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="aa124-687">This function writes to the generic serial interface.</span></span> <span data-ttu-id="aa124-688">Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.</span><span class="sxs-lookup"><span data-stu-id="aa124-688">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-689">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-689">Parameters</span></span>

- <span data-ttu-id="aa124-690">**gser**: wskaźnik do wystąpienia klasy gser.</span><span class="sxs-lookup"><span data-stu-id="aa124-690">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="aa124-691">**interface_index**: interfejs, który ma zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="aa124-691">**interface_index**: Interface to which to write.</span></span>
- <span data-ttu-id="aa124-692">**data_pointer**: wskaźnik na adres buforu ładunku danych.</span><span class="sxs-lookup"><span data-stu-id="aa124-692">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="aa124-693">**requested_length**: długość do wysłania.</span><span class="sxs-lookup"><span data-stu-id="aa124-693">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="aa124-694">**actual_length**: długość faktycznie wysłana.</span><span class="sxs-lookup"><span data-stu-id="aa124-694">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-695">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-695">Return Value</span></span>

- <span data-ttu-id="aa124-696">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-696">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-697">**UX_TRANSFER_TIMEOUT**: (0x5c) limit czasu transferu, zapisywanie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="aa124-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="aa124-698">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-698">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a><span data-ttu-id="aa124-699">ux_host_class_gser_ioctl</span><span class="sxs-lookup"><span data-stu-id="aa124-699">ux_host_class_gser_ioctl</span></span>

<span data-ttu-id="aa124-700">Wykonaj funkcję IOCTL do ogólnego interfejsu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="aa124-700">Perform an IOCTL function to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-701">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-701">Prototype</span></span>

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a><span data-ttu-id="aa124-702">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-702">Description</span></span>

<span data-ttu-id="aa124-703">Ta funkcja wykonuje konkretną funkcję IOCTL do interfejsu gser.</span><span class="sxs-lookup"><span data-stu-id="aa124-703">This function performs a specific ioctl function to the gser interface.</span></span> <span data-ttu-id="aa124-704">Wywołanie jest blokowane i zwraca tylko wtedy, gdy występuje błąd lub po zakończeniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="aa124-704">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-705">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-705">Parameters</span></span>

- <span data-ttu-id="aa124-706">**gser**: wskaźnik do wystąpienia klasy gser.</span><span class="sxs-lookup"><span data-stu-id="aa124-706">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="aa124-707">**ioctl_function**: funkcja IOCTL, która ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="aa124-707">**ioctl_function**: ioctl function to be performed.</span></span> <span data-ttu-id="aa124-708">W poniższej tabeli znajduje się jedna z dozwolonych funkcji IOCTL.</span><span class="sxs-lookup"><span data-stu-id="aa124-708">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="aa124-709">**parametr**: Pointerto parametr specyficzny dla elementu IOCTL</span><span class="sxs-lookup"><span data-stu-id="aa124-709">**parameter**: Pointerto a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-710">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-710">Return Value</span></span>

- <span data-ttu-id="aa124-711">**UX_SUCCESS**: (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-711">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-712">**UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="aa124-712">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory.</span></span>
- <span data-ttu-id="aa124-713">**UX_HOST_CLASS_UNKNOWN**: (0X59) złe wystąpienie klasy</span><span class="sxs-lookup"><span data-stu-id="aa124-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Wrong class instance</span></span>
- <span data-ttu-id="aa124-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) nieznana funkcja IOCTL.</span><span class="sxs-lookup"><span data-stu-id="aa124-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="aa124-715">Funkcje IOCTL</span><span class="sxs-lookup"><span data-stu-id="aa124-715">IOCTL functions</span></span>

- <span data-ttu-id="aa124-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="aa124-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="aa124-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="aa124-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="aa124-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="aa124-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="aa124-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="aa124-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="aa124-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="aa124-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="aa124-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="aa124-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="aa124-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="aa124-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="aa124-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="aa124-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span></span>

### <a name="example"></a><span data-ttu-id="aa124-724">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-724">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a><span data-ttu-id="aa124-725">ux_host_class_gser_reception_start</span><span class="sxs-lookup"><span data-stu-id="aa124-725">ux_host_class_gser_reception_start</span></span>

<span data-ttu-id="aa124-726">Rozpocznij odbieranie w ogólnym interfejsie szeregowym</span><span class="sxs-lookup"><span data-stu-id="aa124-726">Start reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-727">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-727">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="aa124-728">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-728">Description</span></span>

<span data-ttu-id="aa124-729">Ta funkcja uruchamia odbieranie w interfejsie klasy uniwersalnej.</span><span class="sxs-lookup"><span data-stu-id="aa124-729">This function starts the reception on the generic serial class interface.</span></span> <span data-ttu-id="aa124-730">Ta funkcja umożliwia odbiór nieblokujący.</span><span class="sxs-lookup"><span data-stu-id="aa124-730">This function allows for non-blocking reception.</span></span> <span data-ttu-id="aa124-731">Po odebraniu buforu wywołanie zwrotne jest wywoływane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa124-731">When a buffer is received, a callback in invoked into the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-732">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-732">Parameters</span></span>

- <span data-ttu-id="aa124-733">**gser** Wskaźnik do wystąpienia klasy gser.</span><span class="sxs-lookup"><span data-stu-id="aa124-733">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="aa124-734">**gser_reception** Struktura zawierająca parametry odbioru</span><span class="sxs-lookup"><span data-stu-id="aa124-734">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-735">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-735">Return Value</span></span>

- <span data-ttu-id="aa124-736">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-736">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-737">**UX_HOST_CLASS_UNKNOWN** (0X59) złe wystąpienie klasy</span><span class="sxs-lookup"><span data-stu-id="aa124-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="aa124-738">Błąd **UX_ERROR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa124-738">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="aa124-739">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-739">Example</span></span>

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a><span data-ttu-id="aa124-740">ux_host_class_gser_reception_stop</span><span class="sxs-lookup"><span data-stu-id="aa124-740">ux_host_class_gser_reception_stop</span></span>

<span data-ttu-id="aa124-741">Zatrzymaj odbieranie w ogólnym interfejsie szeregowym</span><span class="sxs-lookup"><span data-stu-id="aa124-741">Stop reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="aa124-742">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa124-742">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="aa124-743">Opis</span><span class="sxs-lookup"><span data-stu-id="aa124-743">Description</span></span>

<span data-ttu-id="aa124-744">Ta funkcja przerywa odbieranie w interfejsie uniwersalnej klasy szeregowej.</span><span class="sxs-lookup"><span data-stu-id="aa124-744">This function stops the reception on the generic serial class interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa124-745">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa124-745">Parameters</span></span>

- <span data-ttu-id="aa124-746">**gser** Wskaźnik do wystąpienia klasy gser.</span><span class="sxs-lookup"><span data-stu-id="aa124-746">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="aa124-747">**gser_reception** Struktura zawierająca parametry odbioru</span><span class="sxs-lookup"><span data-stu-id="aa124-747">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="aa124-748">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa124-748">Return Value</span></span>

- <span data-ttu-id="aa124-749">**UX_SUCCESS** (0x00) transfer danych został ukończony.</span><span class="sxs-lookup"><span data-stu-id="aa124-749">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="aa124-750">**UX_HOST_CLASS_UNKNOWN** (0X59) złe wystąpienie klasy</span><span class="sxs-lookup"><span data-stu-id="aa124-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="aa124-751">Błąd **UX_ERROR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa124-751">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="aa124-752">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa124-752">Example</span></span>

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
