---
title: Rozdział 5 — sterowniki urządzeń dla usługi Azure RTO ThreadX SMP
description: Ten rozdział zawiera opis sterowników urządzeń dla usługi Azure RTO ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: acfb54a25cc8bc27b7d0aaeff48956529d90c9e1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823922"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a><span data-ttu-id="24681-103">Rozdział 5 — sterowniki urządzeń dla usługi Azure RTO ThreadX SMP</span><span class="sxs-lookup"><span data-stu-id="24681-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX SMP</span></span>

<span data-ttu-id="24681-104">Ten rozdział zawiera opis sterowników urządzeń dla usługi Azure RTO ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="24681-104">This chapter contains a description of device drivers for Azure RTOS ThreadX SMP.</span></span> <span data-ttu-id="24681-105">Informacje przedstawione w tym rozdziale zaprojektowano w celu ułatwienia deweloperom pisanie sterowników określonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="24681-105">The information presented in this chapter is designed to help developers write application specific drivers.</span></span> 

## <a name="device-driver-introduction"></a><span data-ttu-id="24681-106">Wprowadzenie do sterownika urządzenia</span><span class="sxs-lookup"><span data-stu-id="24681-106">Device Driver Introduction</span></span>

<span data-ttu-id="24681-107">Komunikacja ze środowiskiem zewnętrznym jest ważnym składnikiem większości aplikacji osadzonych.</span><span class="sxs-lookup"><span data-stu-id="24681-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="24681-108">Ta komunikacja jest realizowana za pomocą urządzeń sprzętowych, które są dostępne dla oprogramowania aplikacji osadzonej.</span><span class="sxs-lookup"><span data-stu-id="24681-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="24681-109">Składniki oprogramowania odpowiedzialne za zarządzanie takimi urządzeniami są zwykle nazywane *sterownikami urządzeń*.</span><span class="sxs-lookup"><span data-stu-id="24681-109">The software components responsible for managing such devices are commonly called *Device Drivers*.</span></span>

<span data-ttu-id="24681-110">Sterowniki urządzeń w osadzonych systemach czasu rzeczywistego są zależne od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24681-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="24681-111">Jest to prawdziwe w przypadku dwóch głównych przyczyn: ogromnej różnorodności sprzętu docelowego i równie ogromnych wymagań dotyczących wydajności nałożonych na aplikacje w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="24681-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="24681-112">Z tego powodu praktycznie niemożliwe jest dostarczenie wspólnego zestawu sterowników, który będzie spełniał wymagania każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24681-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="24681-113">Z tego względu informacje przedstawione w tym rozdziale zaprojektowano w celu ułatwienia użytkownikom dostosowywania sterowników urządzeń SMP *w* ThreadX i pisania własnych sterowników.</span><span class="sxs-lookup"><span data-stu-id="24681-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX SMP device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="24681-114">Funkcje sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-114">Driver Functions</span></span>

<span data-ttu-id="24681-115">Sterowniki urządzeń SMP ThreadX składają się z ośmiu podstawowych obszarów funkcjonalnych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="24681-115">ThreadX SMP device drivers are composed of eight basic functional areas, as follows:</span></span>

- <span data-ttu-id="24681-116">**Inicjowanie sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-116">**Driver Initialization**</span></span>
- <span data-ttu-id="24681-117">**Kontrolka sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-117">**Driver Control**</span></span>
- <span data-ttu-id="24681-118">**Dostęp do sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-118">**Driver Access**</span></span>
- <span data-ttu-id="24681-119">**Dane wejściowe sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-119">**Driver Input**</span></span>
- <span data-ttu-id="24681-120">**Dane wyjściowe sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-120">**Driver Output**</span></span>
- <span data-ttu-id="24681-121">**Przerwania sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="24681-122">**Stan sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-122">**Driver Status**</span></span>
- <span data-ttu-id="24681-123">**Zakończenie sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-123">**Driver Termination**</span></span>

<span data-ttu-id="24681-124">Z wyjątkiem inicjalizacji każdy obszar funkcjonalny sterownika jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="24681-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="24681-125">Ponadto dokładne przetwarzanie w poszczególnych obszarach jest specyficzne dla sterownika urządzenia.</span><span class="sxs-lookup"><span data-stu-id="24681-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="24681-126">Inicjowanie sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-126">Driver Initialization</span></span> 
<span data-ttu-id="24681-127">Ten obszar funkcjonalny jest odpowiedzialny za Inicjowanie rzeczywistego urządzenia sprzętowego i wewnętrznych struktur danych sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="24681-128">Wywoływanie innych usług sterowników jest niedozwolone do momentu ukończenia inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="24681-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24681-129">Składnik funkcji inicjowania sterownika jest zazwyczaj wywoływany z funkcji **tx_application_define** lub z wątku inicjującego.</span><span class="sxs-lookup"><span data-stu-id="24681-129">The driver’s initialization function component is typically called from the **tx_application_define** function or from an initialization thread.</span></span>

### <a name="driver-control"></a><span data-ttu-id="24681-130">Kontrolka sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-130">Driver Control</span></span> 
<span data-ttu-id="24681-131">Po zainicjowaniu sterownika i przygotowaniu go do działania ten obszar funkcjonalny jest odpowiedzialny za kontrolę w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="24681-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="24681-132">Zwykle kontrola w czasie wykonywania składa się z wprowadzania zmian w podstawowym urządzeniu sprzętowym.</span><span class="sxs-lookup"><span data-stu-id="24681-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="24681-133">Przykłady obejmują zmianę szybkości transmisji urządzenia szeregowego lub wyszukanie nowego sektora na dysku.</span><span class="sxs-lookup"><span data-stu-id="24681-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="24681-134">Dostęp do sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-134">Driver Access</span></span> 
<span data-ttu-id="24681-135">Niektóre sterowniki urządzeń są wywoływane tylko z jednego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24681-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="24681-136">W takich przypadkach ten obszar funkcjonalny nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="24681-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="24681-137">Jednak w aplikacjach, w których wiele wątków wymaga jednoczesnego dostępu do sterowników, ich interakcje muszą być kontrolowane przez dodanie funkcji Przypisz/Zwolnij do sterownika urządzenia.</span><span class="sxs-lookup"><span data-stu-id="24681-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="24681-138">Alternatywnie aplikacja może używać semafora do kontrolowania dostępu do sterowników i uniknięcia dodatkowych obciążeń i komplikacji w obrębie sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span> 

### <a name="driver-input"></a><span data-ttu-id="24681-139">Dane wejściowe sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-139">Driver Input</span></span> 
<span data-ttu-id="24681-140">Ten obszar funkcjonalny jest odpowiedzialny za wszystkie dane wejściowe urządzenia.</span><span class="sxs-lookup"><span data-stu-id="24681-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="24681-141">Główne problemy związane z wejściem sterownika zwykle obejmują, jak dane wejściowe są buforowane i jak wątki oczekują na takie dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="24681-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span> 

### <a name="driver-output"></a><span data-ttu-id="24681-142">Dane wyjściowe sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-142">Driver Output</span></span> 
<span data-ttu-id="24681-143">Ten obszar funkcjonalny jest odpowiedzialny za wszystkie dane wyjściowe urządzenia.</span><span class="sxs-lookup"><span data-stu-id="24681-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="24681-144">Główne problemy związane z danymi wyjściowymi sterowników zwykle obejmują, jak dane wyjściowe są buforowane i jak wątki oczekują na wykonanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="24681-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span> 

### <a name="driver-interrupts"></a><span data-ttu-id="24681-145">Przerwania sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-145">Driver Interrupts</span></span> 
<span data-ttu-id="24681-146">Większość systemów w czasie rzeczywistym polega na przerwaniu sprzętowym w celu powiadomienia sterownika o zdarzeniach wejściowych, wyjściowych, kontroli i błędach urządzenia.</span><span class="sxs-lookup"><span data-stu-id="24681-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="24681-147">Przerwania zapewniają gwarantowany czas odpowiedzi na takie zdarzenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="24681-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="24681-148">Zamiast przerwań oprogramowanie sterownika może okresowo sprawdzać sprzęt zewnętrzny pod kątem takich zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="24681-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="24681-149">Ta technika jest nazywana *sondowaniem*.</span><span class="sxs-lookup"><span data-stu-id="24681-149">This technique is called *polling*.</span></span> <span data-ttu-id="24681-150">Jest mniej w czasie rzeczywistym niż przerwania, ale sondowanie może mieć sens w przypadku niektórych aplikacji w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="24681-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span> 

### <a name="driver-status"></a><span data-ttu-id="24681-151">Stan sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-151">Driver Status</span></span> 
<span data-ttu-id="24681-152">Ten obszar funkcji jest odpowiedzialny za zapewnienie stanu środowiska uruchomieniowego i statystyk skojarzonych z operacją sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-152">This function area is responsible for providing runtime status and statistics associated with the driver operation.</span></span> <span data-ttu-id="24681-153">Informacje zarządzane przez ten obszar funkcji zwykle obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="24681-153">Information managed by this function area typically includes the following:</span></span> 
- <span data-ttu-id="24681-154">Bieżący stan urządzenia</span><span class="sxs-lookup"><span data-stu-id="24681-154">Current device status</span></span>
- <span data-ttu-id="24681-155">Bajty wejściowe</span><span class="sxs-lookup"><span data-stu-id="24681-155">Input bytes</span></span>
- <span data-ttu-id="24681-156">Bajty wyjściowe</span><span class="sxs-lookup"><span data-stu-id="24681-156">Output bytes</span></span>
- <span data-ttu-id="24681-157">Liczba błędów urządzeń</span><span class="sxs-lookup"><span data-stu-id="24681-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="24681-158">Zakończenie sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-158">Driver Termination</span></span> 
<span data-ttu-id="24681-159">Ten obszar funkcjonalny jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="24681-159">This functional area is optional.</span></span> <span data-ttu-id="24681-160">Jest to wymagane tylko wtedy, gdy sterownik i/lub fizyczne urządzenie sprzętowe należy wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="24681-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="24681-161">Po zakończeniu należy ponownie wywołać sterownik, dopóki nie zostanie ponownie zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="24681-161">After being terminated, the driver must not be called again until it is re-initialized.</span></span> 

## <a name="simple-driver-example"></a><span data-ttu-id="24681-162">Przykład prostego sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-162">Simple Driver Example</span></span>

<span data-ttu-id="24681-163">Przykładem jest najlepszy sposób opisywania sterownika urządzenia.</span><span class="sxs-lookup"><span data-stu-id="24681-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="24681-164">W tym przykładzie sterownik przyjmuje proste urządzenie szeregowe z rejestrem konfiguracji, rejestrem wejściowym i rejestrem wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="24681-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="24681-165">Ten prosty przykład sterownika ilustruje obszar funkcjonalności inicjalizacji, wejścia, wyjścia i przerwania.</span><span class="sxs-lookup"><span data-stu-id="24681-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="24681-166">Prosta Inicjalizacja sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-166">Simple Driver Initialization</span></span> 
<span data-ttu-id="24681-167">Funkcja ***tx_sdriver_initialize*** prostego sterownika tworzy dwa semafory zliczania, które są używane do zarządzania operacjami wejścia i wyjścia sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver’s input and output operation.</span></span> <span data-ttu-id="24681-168">Semafor wejściowy jest ustawiany przez wejście w trybie ISR, gdy znak jest odbierany przez urządzenie sprzętowe szeregowe.</span><span class="sxs-lookup"><span data-stu-id="24681-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="24681-169">Z tego powodu semafor wejściowy jest tworzony z początkową liczbą równą zero.</span><span class="sxs-lookup"><span data-stu-id="24681-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="24681-170">Z drugiej strony semafor wyjściowy wskazuje dostępność rejestru transmisji sprzętu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="24681-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="24681-171">Jest tworzony z wartością jednego, aby wskazać, że rejestr przesyłania jest początkowo dostępny.</span><span class="sxs-lookup"><span data-stu-id="24681-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="24681-172">Funkcja inicjowania jest również odpowiedzialna za Instalowanie obsługi wektorów przerwania niskiego poziomu na potrzeby powiadomień wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="24681-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="24681-173">Podobnie jak w przypadku innych procedur usługi przerwania SMP ThreadX, obsługa niskiego poziomu musi wywoływać \***_tx_thread_context_save** _ przed wywołaniem prostego procedury ISR sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-173">Like other ThreadX SMP interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="24681-174">Po powrocie przez funkcję ISR sterownika procedura obsługi niskiego poziomu musi wywołać _ \* _ _tx_thread_context_restore_\* \*.</span><span class="sxs-lookup"><span data-stu-id="24681-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24681-175">Ważne jest, aby Inicjalizacja była wywoływana przed żadną inną funkcje sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-175">It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="24681-176">Zazwyczaj Inicjalizacja sterownika jest wywoływana z **tx_application_define**.</span><span class="sxs-lookup"><span data-stu-id="24681-176">Typically, driver initialization is called from **tx_application_define**.</span></span>

<span data-ttu-id="24681-177">Zobacz rysunek 9 na stronie 306 dla kodu źródłowego inicjalizacji prostego sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-177">See Figure 9 on page 306 for the initialization source code of the simple driver.</span></span>

```C
VOID     tx_sdriver_initialize(VOID)
{

    /* Initialize the two counting semaphores used to control
       the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                       "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                       "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
       The initial vector handling should call the ISRs
       defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
       generation, baud rate, stop bits, etc. */
}
```
<span data-ttu-id="24681-178">**RYSUNEK 9. Prosta Inicjalizacja sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-178">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="24681-179">Proste wprowadzanie sterowników</span><span class="sxs-lookup"><span data-stu-id="24681-179">Simple Driver Input</span></span> 
<span data-ttu-id="24681-180">Dane wejściowe dla prostych centrów sterowników wokół semafora wejściowego.</span><span class="sxs-lookup"><span data-stu-id="24681-180">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="24681-181">Po odebraniu przerwań wejścia urządzenia szeregowego zostanie ustawiony semafor wejściowy.</span><span class="sxs-lookup"><span data-stu-id="24681-181">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="24681-182">Jeśli co najmniej jeden wątek oczekuje na znak ze sterownika, wątek czekający najdłuższy zostanie wznowiony.</span><span class="sxs-lookup"><span data-stu-id="24681-182">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="24681-183">Jeśli żadne wątki nie oczekują, semafor po prostu pozostaje ustawiony do momentu wywołania przez wątek funkcji wejścia stacji.</span><span class="sxs-lookup"><span data-stu-id="24681-183">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="24681-184">Istnieje kilka ograniczeń związanych z prostą obsługą wejścia sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-184">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="24681-185">Najbardziej znaczącym jest potencjalną przyczyną porzucania znaków wejściowych.</span><span class="sxs-lookup"><span data-stu-id="24681-185">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="24681-186">Jest to możliwe, ponieważ nie ma możliwości buforowania znaków wejściowych, które docierają przed przetworzeniem poprzedniego znaku.</span><span class="sxs-lookup"><span data-stu-id="24681-186">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="24681-187">Jest to łatwo obsługiwane przez dodanie wejściowego buforu znaków.</span><span class="sxs-lookup"><span data-stu-id="24681-187">This is easily handled by adding an input character buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24681-188">Tylko wątki mogą wywołać funkcję **tx_sdriver_input** .</span><span class="sxs-lookup"><span data-stu-id="24681-188">Only threads are allowed to call the **tx_sdriver_input** function.</span></span>

<span data-ttu-id="24681-189">Rysunek 10 pokazuje kod źródłowy skojarzony z prostym wejściem sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-189">Figure 10 shows the source code associated with simple driver input.</span></span>

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
<span data-ttu-id="24681-190">**RYSUNEK 10. Proste wprowadzanie sterowników**</span><span class="sxs-lookup"><span data-stu-id="24681-190">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="24681-191">Proste wyjście sterownika</span><span class="sxs-lookup"><span data-stu-id="24681-191">Simple Driver Output</span></span> 
<span data-ttu-id="24681-192">Przetwarzanie danych wyjściowych wykorzystuje semafor wyjściowy do sygnalizowania, kiedy rejestr transmisji urządzenia szeregowego jest bezpłatny.</span><span class="sxs-lookup"><span data-stu-id="24681-192">Output processing utilizes the output semaphore to signal when the serial device’s transmit register is free.</span></span> <span data-ttu-id="24681-193">Przed faktycznym zapisaniem na urządzeniu znaku wyjściowego zostanie uzyskany semafor wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="24681-193">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="24681-194">Jeśli ta wartość jest niedostępna, poprzednia Transmisja nie została jeszcze ukończona.</span><span class="sxs-lookup"><span data-stu-id="24681-194">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="24681-195">Wyjście ISR jest odpowiedzialne za obsługę przerwania przesyłania.</span><span class="sxs-lookup"><span data-stu-id="24681-195">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="24681-196">Przetwarzanie ilości danych wyjściowych ISR do ustawiania semafora wyjściowego, co pozwala na wyjście innego znaku.</span><span class="sxs-lookup"><span data-stu-id="24681-196">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24681-197">Tylko wątki mogą wywołać funkcję **tx_sdriver_output** .</span><span class="sxs-lookup"><span data-stu-id="24681-197">Only threads are allowed to call the **tx_sdriver_output** function.</span></span>

<span data-ttu-id="24681-198">Rysunek 11 przedstawia kod źródłowy skojarzony z prostym wyjściem sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-198">Figure 11 shows the source code associated with simple driver output.</span></span>

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="24681-199">**RYSUNEK 11. Proste wyjście sterownika**</span><span class="sxs-lookup"><span data-stu-id="24681-199">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="24681-200">Proste braki sterowników</span><span class="sxs-lookup"><span data-stu-id="24681-200">Simple Driver Shortcomings</span></span> 
<span data-ttu-id="24681-201">Ten prosty przykład sterownika urządzenia ilustruje podstawowy pomysł dotyczący sterownika urządzenia ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="24681-201">This simple device driver example illustrates the basic idea of a ThreadX SMP device driver.</span></span> <span data-ttu-id="24681-202">Jednak ponieważ prosty sterownik urządzenia nie rozwiąże buforowania danych ani nie występują żadne problemy, nie reprezentuje w pełni rzeczywistych sterowników SMP ThreadX.</span><span class="sxs-lookup"><span data-stu-id="24681-202">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX SMP drivers.</span></span> <span data-ttu-id="24681-203">W poniższej sekcji opisano niektóre bardziej zaawansowane problemy związane z sterownikami urządzeń.</span><span class="sxs-lookup"><span data-stu-id="24681-203">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="24681-204">Zaawansowane problemy ze sterownikiem</span><span class="sxs-lookup"><span data-stu-id="24681-204">Advanced Driver Issues</span></span>

<span data-ttu-id="24681-205">Jak wspomniano wcześniej, sterowniki urządzeń mają wymagania, które są unikatowe jako aplikacje.</span><span class="sxs-lookup"><span data-stu-id="24681-205">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="24681-206">Niektóre aplikacje mogą wymagać nadmiernej ilości buforów danych, a inna aplikacja może wymagać zoptymalizowanego procedury ISR sterownika z powodu przerwań urządzeń o wysokiej częstotliwości.</span><span class="sxs-lookup"><span data-stu-id="24681-206">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="24681-207">Buforowanie we/wy</span><span class="sxs-lookup"><span data-stu-id="24681-207">I/O Buffering</span></span> 
<span data-ttu-id="24681-208">Buforowanie danych w aplikacjach osadzonych w czasie rzeczywistym wymaga znacznego zaplanowania.</span><span class="sxs-lookup"><span data-stu-id="24681-208">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="24681-209">Niektóre z tych projektów są podyktowane przez bazowe urządzenie sprzętowe.</span><span class="sxs-lookup"><span data-stu-id="24681-209">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="24681-210">Jeśli urządzenie zapewnia podstawowe bajty we/wy, prawdopodobnie jest to prosty bufor cykliczny.</span><span class="sxs-lookup"><span data-stu-id="24681-210">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="24681-211">Jeśli jednak urządzenie zapewnia blok, dostęp DMA lub we/wy, prawdopodobnie jest to schemat zarządzania buforem.</span><span class="sxs-lookup"><span data-stu-id="24681-211">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span> 

### <a name="circular-byte-buffers"></a><span data-ttu-id="24681-212">Cykliczne bufory bajtów</span><span class="sxs-lookup"><span data-stu-id="24681-212">Circular Byte Buffers</span></span> 
<span data-ttu-id="24681-213">Cykliczne bufory bajtów są zwykle używane w sterownikach, które zarządzają prostym urządzeniem sprzętowym, takim jak UART.</span><span class="sxs-lookup"><span data-stu-id="24681-213">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="24681-214">Dwa bufory cykliczne są najczęściej używane w takich sytuacjach — jeden dla danych wejściowych i jeden dla danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="24681-214">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="24681-215">Każdy kolisty bufor bajtowy składa się z obszaru pamięci bajtów (zazwyczaj jest to tablica UCHARs), wskaźnik odczytu i wskaźnik zapisu.</span><span class="sxs-lookup"><span data-stu-id="24681-215">Each circular byte buffer is comprised of a byte memory area (typically an array of UCHARs), a read pointer, and a write pointer.</span></span> <span data-ttu-id="24681-216">Bufor jest uważany za pusty, gdy wskaźnik odczytu i wskaźniki zapisu odwołują się do tej samej lokalizacji pamięci w buforze.</span><span class="sxs-lookup"><span data-stu-id="24681-216">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="24681-217">Inicjalizacja sterownika ustawia wskaźniki buforu odczytu i zapisu na adres początkowy buforu.</span><span class="sxs-lookup"><span data-stu-id="24681-217">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="24681-218">Cykliczne wejście buforu</span><span class="sxs-lookup"><span data-stu-id="24681-218">Circular Buffer Input</span></span> 
<span data-ttu-id="24681-219">Bufor wejściowy jest używany do przechowywania znaków, które docierają do tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24681-219">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="24681-220">Po odebraniu znaku wejściowego (zazwyczaj w procedurze usługi przerwania) nowy znak zostanie pobrany z urządzenia sprzętowego i umieszczony w buforze wejściowym w lokalizacji wskazywanej przez wskaźnik zapisu.</span><span class="sxs-lookup"><span data-stu-id="24681-220">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="24681-221">Wskaźnik zapisu jest zaawansowany do następnej pozycji w buforze.</span><span class="sxs-lookup"><span data-stu-id="24681-221">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="24681-222">Jeśli następna pozycja znajduje się poza końcem buforu, wskaźnik zapisu jest ustawiany na początku buforu.</span><span class="sxs-lookup"><span data-stu-id="24681-222">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="24681-223">Pełny warunek kolejki jest obsługiwany przez anulowanie przybierania wskaźnika zapisu, jeśli nowy wskaźnik zapisu jest taki sam jak wskaźnik odczytu.</span><span class="sxs-lookup"><span data-stu-id="24681-223">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="24681-224">Żądania bajtów wejściowych aplikacji do sterownika najpierw przeanalizują wskaźniki odczytu i zapisu w buforze wejściowym.</span><span class="sxs-lookup"><span data-stu-id="24681-224">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="24681-225">Jeśli wskaźniki odczytu i zapisu są identyczne, bufor jest pusty.</span><span class="sxs-lookup"><span data-stu-id="24681-225">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="24681-226">W przeciwnym razie, jeśli wskaźnik odczytu nie jest taki sam, bajt wskazywany przez wskaźnik odczytu jest kopiowany z buforu wejściowego, a wskaźnik odczytu jest zaawansowany do następnej lokalizacji buforu.</span><span class="sxs-lookup"><span data-stu-id="24681-226">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="24681-227">Jeśli nowy wskaźnik odczytu znajduje się poza końcem buforu, zostanie zresetowany do początku.</span><span class="sxs-lookup"><span data-stu-id="24681-227">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="24681-228">Rysunek 12 przedstawia logikę cyklicznego buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="24681-228">Figure 12 shows the logic for the circular input buffer.</span></span>

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
<span data-ttu-id="24681-229">**RYSUNEK 12. Logika dla cyklicznego buforu wejściowego**</span><span class="sxs-lookup"><span data-stu-id="24681-229">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24681-230">Aby zapewnić niezawodne działanie, może być konieczne zablokowanie przerwań podczas manipulowania wskaźnikami odczytu i zapisu zarówno wejściowych, jak i wyjściowych buforów cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="24681-230">For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span>

### <a name="circular-output-buffer"></a><span data-ttu-id="24681-231">Cykliczny bufor wyjściowy</span><span class="sxs-lookup"><span data-stu-id="24681-231">Circular Output Buffer</span></span> 
<span data-ttu-id="24681-232">Bufor wyjściowy jest używany do przechowywania znaków, które dotarły do danych wyjściowych, zanim urządzenie sprzętowe zakończy wysyłanie poprzedniego bajtu.</span><span class="sxs-lookup"><span data-stu-id="24681-232">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="24681-233">Przetwarzanie buforu wyjściowego jest podobne do przetwarzania buforu wejściowego, z wyjątkiem tego, że przetwarzanie przerwania przesyłania zostało wykonane, manipuluje wskaźnikiem odczytywania danych wyjściowych, podczas gdy żądanie danych wyjściowych aplikacji wykorzystuje wskaźnik zapisu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="24681-233">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span> <span data-ttu-id="24681-234">W przeciwnym razie przetwarzanie buforu wyjściowego jest takie samo.</span><span class="sxs-lookup"><span data-stu-id="24681-234">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="24681-235">Rysunek 13shows logikę cyklicznego buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="24681-235">Figure 13shows the logic for the circular output buffer.</span></span>

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
<span data-ttu-id="24681-236">**RYSUNEK 13. Logika cyklicznego buforu wyjściowego**</span><span class="sxs-lookup"><span data-stu-id="24681-236">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="24681-237">Zarządzanie buforowaniem we/wy</span><span class="sxs-lookup"><span data-stu-id="24681-237">Buffer I/O Management</span></span> 
<span data-ttu-id="24681-238">Aby zwiększyć wydajność osadzonych mikroprocesorów, wiele urządzeń urządzeń peryferyjnych przesyła i odbiera dane przy użyciu buforów dostarczonych przez oprogramowanie.</span><span class="sxs-lookup"><span data-stu-id="24681-238">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="24681-239">W niektórych implementacjach wiele buforów może służyć do przesyłania lub odbierania pojedynczych pakietów danych.</span><span class="sxs-lookup"><span data-stu-id="24681-239">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span> 

<span data-ttu-id="24681-240">Rozmiar i lokalizacja buforów we/wy jest określana przez oprogramowanie aplikacji i/lub sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-240">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="24681-241">Zazwyczaj bufory mają ustalony rozmiar i są zarządzane w puli pamięci ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="24681-241">Typically, buffers are fixed in size and managed within a ThreadX SMP block memory pool.</span></span> <span data-ttu-id="24681-242">Rysunek 14describes typowy bufor we/wy i ThreadXy blok pamięci SMP, który zarządza ich alokacją.</span><span class="sxs-lookup"><span data-stu-id="24681-242">Figure 14describes a typical I/O buffer and a ThreadX SMP block memory pool that manages their allocation.</span></span>

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
   "free_memory_ptr"points to an available memory area that
   is 64 KBytes in size. */

tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```
<span data-ttu-id="24681-243">**RYSUNEK 14. Bufor we/wy**</span><span class="sxs-lookup"><span data-stu-id="24681-243">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="24681-244">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="24681-244">TX_IO_BUFFER</span></span> 
<span data-ttu-id="24681-245">Element typedef TX_IO_BUFFER składa się z dwóch wskaźników.</span><span class="sxs-lookup"><span data-stu-id="24681-245">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="24681-246">Wskaźnik \***tx_next_packet** _ służy do łączenia wielu pakietów na liście danych wejściowych lub wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="24681-246">The \***tx_next_packet** _ pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="24681-247">Wskaźnik _ *_tx_next_buffer_*\* służy do łączenia razem buforów, które składają się na pojedynczy pakiet danych z urządzenia.</span><span class="sxs-lookup"><span data-stu-id="24681-247">The _ *_tx_next_buffer_*\* pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="24681-248">Oba te wskaźniki są ustawione na wartość NULL, gdy bufor jest przypisywany z puli.</span><span class="sxs-lookup"><span data-stu-id="24681-248">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="24681-249">Ponadto niektóre urządzenia mogą wymagać innego pola, aby wskazać, jaka część obszaru buforowego zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="24681-249">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="24681-250">Zalety buforowanej operacji we/wy</span><span class="sxs-lookup"><span data-stu-id="24681-250">Buffered I/O Advantage</span></span> 
<span data-ttu-id="24681-251">Jakie są zalety schematu we/wy buforu?</span><span class="sxs-lookup"><span data-stu-id="24681-251">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="24681-252">Największą korzyść polega na tym, że dane nie są kopiowane między rejestrami urządzeń i pamięcią aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24681-252">The biggest advantage is that data is not copied between the device registers and the application’s memory.</span></span> <span data-ttu-id="24681-253">Zamiast tego sterownik dostarcza urządzenie z serią wskaźników buforów.</span><span class="sxs-lookup"><span data-stu-id="24681-253">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="24681-254">We/wy urządzenia fizycznego jest używana bezpośrednio pamięć buforu.</span><span class="sxs-lookup"><span data-stu-id="24681-254">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="24681-255">Użycie procesora do kopiowania pakietów wejściowych lub wyjściowych informacji jest niezwykle kosztowne i należy je unikać w każdej sytuacji dużej przepływności we/wy.</span><span class="sxs-lookup"><span data-stu-id="24681-255">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="24681-256">Kolejną zaletą operacji wejścia/wyjścia na sekundę jest to, że listy wejściowe i wyjściowe nie mają pełnych warunków.</span><span class="sxs-lookup"><span data-stu-id="24681-256">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="24681-257">Wszystkie dostępne bufory mogą znajdować się w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="24681-257">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="24681-258">Jest to kontrast z prostymi buforami dwubajtowymi przedstawionymi wcześniej w rozdziale.</span><span class="sxs-lookup"><span data-stu-id="24681-258">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="24681-259">Każdy miał ustalony rozmiar ustalony podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="24681-259">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="24681-260">Zakresy obowiązków sterownika w buforze</span><span class="sxs-lookup"><span data-stu-id="24681-260">Buffered Driver Responsibilities</span></span> 
<span data-ttu-id="24681-261">Buforowane sterowniki urządzeń są objęte wyłącznie zarządzaniem połączonymi listami buforów we/wy.</span><span class="sxs-lookup"><span data-stu-id="24681-261">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="24681-262">Lista buforów wejściowych jest utrzymywana dla pakietów, które są odbierane, zanim oprogramowanie aplikacji jest gotowe.</span><span class="sxs-lookup"><span data-stu-id="24681-262">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="24681-263">Z drugiej strony Lista buforów wyjściowych jest utrzymywana dla pakietów wysyłanych szybciej niż urządzenia sprzętowe mogą je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="24681-263">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="24681-264">Rysunek 15 na stronie 314 zawiera proste dane wejściowe i wyjściowe połączone listy pakietów danych i buforów, które składają się na każdy pakiet.</span><span class="sxs-lookup"><span data-stu-id="24681-264">Figure 15 on page 314 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

![Zakresy obowiązków sterownika w buforze](media/image11.png)

<span data-ttu-id="24681-266">**RYSUNEK 15. Listy Input-Output**</span><span class="sxs-lookup"><span data-stu-id="24681-266">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="24681-267">Interfejs aplikacji z buforowanymi sterownikami z takimi samymi buforami we/wy.</span><span class="sxs-lookup"><span data-stu-id="24681-267">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="24681-268">W przypadku przesyłania oprogramowanie aplikacji udostępnia sterownik z co najmniej jednym buforem do przesłania.</span><span class="sxs-lookup"><span data-stu-id="24681-268">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="24681-269">Gdy oprogramowanie aplikacji żąda danych wejściowych, sterownik zwraca dane wejściowe w buforach we/wy.</span><span class="sxs-lookup"><span data-stu-id="24681-269">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24681-270">W niektórych aplikacjach warto utworzyć interfejs wejściowy sterownika, który wymaga, aby aplikacja mogła wymienić bezpłatny bufor dla buforu wejściowego ze sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-270">In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver.</span></span> <span data-ttu-id="24681-271">Może to zmniejszyć część przetwarzania alokacji buforu w ramach sterownika.</span><span class="sxs-lookup"><span data-stu-id="24681-271">This might alleviate some buffer allocation processing inside of the driver.</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="24681-272">Zarządzanie przerwami</span><span class="sxs-lookup"><span data-stu-id="24681-272">Interrupt Management</span></span> 
<span data-ttu-id="24681-273">W niektórych aplikacjach częstotliwość przerwań urządzenia może uniemożliwić zapisanie procedury ISR w języku C lub współdziałanie z ThreadX SMP dla każdego przerwania.</span><span class="sxs-lookup"><span data-stu-id="24681-273">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX SMP on each interrupt.</span></span> <span data-ttu-id="24681-274">Na przykład jeśli 25us do zapisywania i przywracania przerwanego kontekstu, nie zaleca się przeprowadzania pełnego kontekstu zapisywania, jeśli częstotliwość przerwań została 50us.</span><span class="sxs-lookup"><span data-stu-id="24681-274">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="24681-275">W takich przypadkach do obsługi większości przerwań urządzenia jest używany mały język asemblera.</span><span class="sxs-lookup"><span data-stu-id="24681-275">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="24681-276">Ten lowoverhead ISR będzie współpracujący z ThreadX SMP, gdy będzie to konieczne.</span><span class="sxs-lookup"><span data-stu-id="24681-276">This lowoverhead ISR would only interact with ThreadX SMP when necessary.</span></span>

<span data-ttu-id="24681-277">Podobne dyskusje można znaleźć w omówieniu zarządzania przerwami na końcu rozdziału 3.</span><span class="sxs-lookup"><span data-stu-id="24681-277">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

> [!NOTE]
> <span data-ttu-id="24681-278">Jeśli blokada przerwania ma być używana do ochrony krytycznych sekcji kodu sterownika z poziomu procedury ISR sterownika, kod sterownika poziomu wątku musi zawsze być wykonywany na tym samym rdzeniu, w którym jest przetwarzany proces ISR.</span><span class="sxs-lookup"><span data-stu-id="24681-278">If interrupt lockout is to be used to protect critical sections of driver code from driver ISR code, the thread level driver code must always execute on the same core that the ISR is processed on.</span></span> <span data-ttu-id="24681-279">W przeciwnym razie podstawowe elementy podstawowe SMP ThreadX, takie jak TX_DISABLE i TX_RESTORE, powinny być używane, które również mają wbudowaną ochronę międzyrdzeniową.</span><span class="sxs-lookup"><span data-stu-id="24681-279">Otherwise, internal ThreadX SMP primitives like TX_DISABLE and TX_RESTORE should be used that also have inter-core protection built-in.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="24681-280">Zawieszenie wątku</span><span class="sxs-lookup"><span data-stu-id="24681-280">Thread Suspension</span></span> 
<span data-ttu-id="24681-281">W prostym przykładzie sterownika przedstawionym wcześniej w tym rozdziale, obiekt wywołujący usługi wejściowej zawiesza się, jeśli znak nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="24681-281">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="24681-282">W niektórych aplikacjach może to nie być akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="24681-282">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="24681-283">Na przykład jeśli wątek odpowiedzialny za przetwarzanie danych wejściowych z sterownika również ma inne obowiązki, wstrzymanie tylko wejścia sterownika prawdopodobnie nie będzie działało.</span><span class="sxs-lookup"><span data-stu-id="24681-283">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="24681-284">Zamiast tego sterownik należy dostosować do przetwarzania żądania podobnego do sposobu, w jaki inne żądania przetwarzania są wykonywane do wątku.</span><span class="sxs-lookup"><span data-stu-id="24681-284">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="24681-285">W większości przypadków bufor wejściowy jest umieszczany na połączonej liście, a wejściowy komunikat zdarzenia jest wysyłany do kolejki wejściowej wątku.</span><span class="sxs-lookup"><span data-stu-id="24681-285">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread’s input queue.</span></span>