---
title: Rozdział 11 — format buforu śledzenia zdarzeń
description: ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług Azure RTO ThreadX Services, zmian stanu wątku i zdarzeń zdefiniowanych przez użytkownika.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823479"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a><span data-ttu-id="19261-103">Rozdział 11 — format buforu śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="19261-103">Chapter 11 - Format of event trace buffer</span></span>

<span data-ttu-id="19261-104">Usługa Azure RTO ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług ThreadX Services, zmian stanu wątku i zdarzeń zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="19261-104">Azure RTOS ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="19261-105">Aby użyć śledzenia zdarzeń, należy po prostu skompilować biblioteki ThreadX, NetX i FileX za pomocą **TX_ENABLE_EVENT_TRACE** zdefiniowanych i Włącz śledzenie, wywołując funkcję **_tx_trace_enable_** .</span><span class="sxs-lookup"><span data-stu-id="19261-105">To use event trace, simply build the ThreadX, NetX, and FileX libraries with **TX_ENABLE_EVENT_TRACE** defined and enable tracing by calling the **_tx_trace_enable_** function.</span></span> <span data-ttu-id="19261-106">Ten rozdział zawiera opis tego procesu.</span><span class="sxs-lookup"><span data-stu-id="19261-106">This chapter describes that process.</span></span>

## <a name="event-trace-format"></a><span data-ttu-id="19261-107">Format śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="19261-107">Event Trace Format</span></span>

<span data-ttu-id="19261-108">Format buforu śledzenia zdarzeń ThreadX jest podzielony na trzy sekcje, mianowicie nagłówek formantu, rejestr obiektów i wpisy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-108">The format of the ThreadX event trace buffer is divided into three sections, namely the control header, object registry, and the trace entries.</span></span> <span data-ttu-id="19261-109">Poniżej opisano ogólny układ buforu śledzenia zdarzeń ThreadX:</span><span class="sxs-lookup"><span data-stu-id="19261-109">The following describes the general layout of the ThreadX event trace buffer:</span></span>

<span data-ttu-id="19261-110">**Nagłówek formantu**</span><span class="sxs-lookup"><span data-stu-id="19261-110">**Control Header**</span></span>

<span data-ttu-id="19261-111">**Wpis rejestru obiektu 0**</span><span class="sxs-lookup"><span data-stu-id="19261-111">**Object Registry Entry 0**</span></span>

<span data-ttu-id="19261-112">**…**</span><span class="sxs-lookup"><span data-stu-id="19261-112">**…**</span></span>

<span data-ttu-id="19261-113">**Wpis rejestru obiektu "n"**</span><span class="sxs-lookup"><span data-stu-id="19261-113">**Object Register Entry "n"**</span></span>

<span data-ttu-id="19261-114">**Wpis śledzenia zdarzeń 0**</span><span class="sxs-lookup"><span data-stu-id="19261-114">**Event Trace Entry 0**</span></span>

<span data-ttu-id="19261-115">**…**</span><span class="sxs-lookup"><span data-stu-id="19261-115">**…**</span></span>

<span data-ttu-id="19261-116">**Wpis śledzenia zdarzeń "n"**</span><span class="sxs-lookup"><span data-stu-id="19261-116">**Event Trace Entry "n"**</span></span>

### <a name="event-trace-control-header"></a><span data-ttu-id="19261-117">Nagłówek formantu śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="19261-117">Event Trace Control Header</span></span>

<span data-ttu-id="19261-118">Nagłówek formantu definiuje dokładny układ buforu śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="19261-118">The control header defines the exact layout of the event trace buffer.</span></span> <span data-ttu-id="19261-119">Obejmuje to liczbę obiektów ThreadX, a także liczbę zdarzeń, które mogą być rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="19261-119">This includes how many ThreadX objects can be registered as well as how many events can be recorded.</span></span> <span data-ttu-id="19261-120">Ponadto nagłówek kontrolki definiuje, gdzie znajdują się poszczególne elementy buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-120">In addition, the control header defines where each of the elements of the trace buffer resides.</span></span> <span data-ttu-id="19261-121">Następująca struktura danych definiuje nagłówek formantu:</span><span class="sxs-lookup"><span data-stu-id="19261-121">The following data structure defines the control header:</span></span>

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a><span data-ttu-id="19261-122">Identyfikator nagłówka kontrolki</span><span class="sxs-lookup"><span data-stu-id="19261-122">Control Header ID</span></span>

<span data-ttu-id="19261-123">Identyfikator nagłówka kontrolki składa się z 32-bitowej wartości SZESNASTKOWej 0x54585442, która odnosi się do znaków ASCII ***TXTB***.</span><span class="sxs-lookup"><span data-stu-id="19261-123">The control header ID consists of the 32-bit HEX value of 0x54585442, which corresponds to the ASCII characters ***TXTB***.</span></span> <span data-ttu-id="19261-124">Ponieważ ta wartość jest zapisywana jako 32-bitowa zmienna bez znaku, może być również używana do wykrywania endian w buforze śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="19261-124">Since this value is written as a 32-bit unsigned variable, it can also be used to detect the endianness of the event trace buffer.</span></span> <span data-ttu-id="19261-125">Na przykład jeśli wartość w pierwszym cztery wartości bTak pamięci to 0x54, 0x58, 0x54, 0x42, bufor śledzenia zdarzeń został zapisany w formacie big endian.</span><span class="sxs-lookup"><span data-stu-id="19261-125">For example, if the value in the first four byes of memory is 0x54, 0x58, 0x54, 0x42, the event trace buffer was written in big endian format.</span></span> <span data-ttu-id="19261-126">W przeciwnym razie bufor śledzenia zdarzeń został zapisany w formacie little endian.</span><span class="sxs-lookup"><span data-stu-id="19261-126">Otherwise, the event trace buffer was written in little endian format.</span></span>

### <a name="timer-valid-mask"></a><span data-ttu-id="19261-127">Prawidłowa maska czasomierza</span><span class="sxs-lookup"><span data-stu-id="19261-127">Timer Valid Mask</span></span>

<span data-ttu-id="19261-128">Prawidłowa maska czasomierza określa, ile bitów sygnatury czasowej w rzeczywistych wpisach śledzenia zdarzeń są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="19261-128">The timer valid mask defines how many bits of the timestamp in the actual event trace entries are valid.</span></span> <span data-ttu-id="19261-129">Na przykład, jeśli źródło sygnatury czasowej ma 16 bitów, wartość w tym polu powinna być równa 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="19261-129">For example, if the time-stamp source has 16-bits, the value in this field should be 0xFFFF.</span></span> <span data-ttu-id="19261-130">32-bitowe Źródło sygnatury czasowej będzie miało wartość 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="19261-130">A 32-bit time-stamp source would have a value of 0xFFFFFFFF.</span></span> <span data-ttu-id="19261-131">Ta wartość jest definiowana przez znak \***TX_TRACE_TIME_MASK** _ w _ *_tx_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="19261-131">This value is defined by the ***TX_TRACE_TIME_MASK** _ constant in _*_tx_port.h_\*\*.</span></span>

### <a name="trace-base-address"></a><span data-ttu-id="19261-132">Adres podstawowy śledzenia</span><span class="sxs-lookup"><span data-stu-id="19261-132">Trace Base Address</span></span>

<span data-ttu-id="19261-133">Adres podstawowy bufora śledzenia to adres określony przez aplikację jako początek buforu śledzenia w wywołaniu ***tx_trace_enable*** .</span><span class="sxs-lookup"><span data-stu-id="19261-133">The trace buffer base address is the address the application specified as the start of the trace buffer in the ***tx_trace_enable*** call.</span></span> <span data-ttu-id="19261-134">Ten adres jest obsługiwany wyłącznie w celu wygenerowania przesunięć bufferrelative dla różnych elementów w buforze przy użyciu narzędzia do analizy.</span><span class="sxs-lookup"><span data-stu-id="19261-134">This address is maintained for the sole use of the analysis tool to derive bufferrelative offsets for the various elements in the buffer.</span></span> <span data-ttu-id="19261-135">Na przykład względne przesunięcie buforu bieżącego zdarzenia w buforze śledzenia jest obliczane przez proste odejmowanie adresu podstawowego od bieżącego adresu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-135">For example, the buffer relative offset of the current event in the trace buffer is calculated by simple subtraction of the base address from the current event address.</span></span>

### <a name="registry-start-and-end-pointers"></a><span data-ttu-id="19261-136">Wskaźniki początku i końca rejestru</span><span class="sxs-lookup"><span data-stu-id="19261-136">Registry Start and End Pointers</span></span>

<span data-ttu-id="19261-137">Wskaźnik rozpoczęcia rejestru wskazuje adres pierwszego wpisu rejestru obiektu, podczas gdy wskaźnik końcowy rejestru wskazuje na adres wiadomości błyskawicznych. /mediately po ostatnim wpisie rejestru.</span><span class="sxs-lookup"><span data-stu-id="19261-137">The registry start pointer points to the address of the first object registry entry, while the registry end pointer points to the address im../mediately following the last register entry.</span></span> <span data-ttu-id="19261-138">Te wartości są skonfigurowane podczas przetwarzania *tx_trace_enable* i nie są zmieniane w czasie trwania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-138">These values are setup during the *tx_trace_enable* processing and are not changed throughout the duration of tracing.</span></span>

### <a name="registry-name-size"></a><span data-ttu-id="19261-139">Rozmiar nazwy rejestru</span><span class="sxs-lookup"><span data-stu-id="19261-139">Registry Name Size</span></span>

<span data-ttu-id="19261-140">Rozmiar nazwy rejestru definiuje maksymalny rozmiar w bajtach dla każdej nazwy obiektu w wpisie rejestru i jest zdefiniowany przez symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span><span class="sxs-lookup"><span data-stu-id="19261-140">The registry name size defines maximum size in bytes for each object name in the registry entry and is defined by the symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span></span> <span data-ttu-id="19261-141">Wartość domyślna to 32 i jest definiowana w _*_tx_trace. h_*_.</span><span class="sxs-lookup"><span data-stu-id="19261-141">The default value is 32 and is defined in _*_tx_trace.h_*_.</span></span> <span data-ttu-id="19261-142">Nazwa obiektu odpowiada nazwie podanej przez aplikację podczas tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="19261-142">The object name corresponds to the name given by the application when the object was created.</span></span> <span data-ttu-id="19261-143">Na przykład nazwa rejestru obiektu dla wątku jest nazwą dostarczoną przez aplikację w wywołaniu _ *_tx_thread_create_* \*.</span><span class="sxs-lookup"><span data-stu-id="19261-143">For example, the object registry name for a thread is the name supplied by the application to the _\*_tx_thread_create_\*\*call.</span></span>

### <a name="buffer-start-and-end-pointers"></a><span data-ttu-id="19261-144">Wskaźniki początku i końca buforu</span><span class="sxs-lookup"><span data-stu-id="19261-144">Buffer Start and End Pointers</span></span>

<span data-ttu-id="19261-145">Wskaźnik startowy buforu śledzenia zdarzeń wskazuje adres pierwszego wpisu śledzenia, podczas gdy wskaźnik końcowy rejestru wskazuje na adres wiadomości błyskawicznych. /mediately po ostatnim wpisie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-145">The event trace buffer start pointer points to the address of the first trace entry, while the registry end pointer points to the address im../mediately following the last trace entry.</span></span> <span data-ttu-id="19261-146">Te wartości są skonfigurowane podczas ***tx_trace_enable</*** przetwarzania i nie są zmieniane w czasie trwania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-146">These values are setup during the ***tx_trace_enable</*** processing and are not changed throughout the duration of tracing.</span></span>

### <a name="current-buffer-pointer"></a><span data-ttu-id="19261-147">Bieżący wskaźnik buforu</span><span class="sxs-lookup"><span data-stu-id="19261-147">Current Buffer Pointer</span></span>

<span data-ttu-id="19261-148">Bieżący wskaźnik buforu śledzenia zdarzeń wskazuje na adres najstarszego wpisu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-148">The event trace buffer current pointer points to the address of the oldest trace entry.</span></span> <span data-ttu-id="19261-149">Ponieważ wpisy śledzenia są przechowywane na liście cyklicznej, bieżący wskaźnik buforu również reprezentuje Następny wpis śledzenia do zapisania.</span><span class="sxs-lookup"><span data-stu-id="19261-149">Since the trace entries are maintained in a circular list, the current buffer pointer is also represents the next trace entry to be written.</span></span> |

## <a name="event-trace-object-registry"></a><span data-ttu-id="19261-150">Rejestr obiektów śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="19261-150">Event Trace Object Registry</span></span>

<span data-ttu-id="19261-151">Rejestr obiektu śledzenia zdarzeń zawiera \***n** _ wpisów rejestru obiektów, które odpowiadają obiektom utworzonymi przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="19261-151">The event trace object registry contains \***n** _ object registry entries that correspond to the objects created by the application.</span></span> <span data-ttu-id="19261-152">Głównym celem rejestru obiektu jest dla zewnętrznych narzędzi do analizy skorelowanie rzeczywistych nazw obiektów z adresami obiektów wpisów buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-152">The main purpose of the object registry is for external analysis tools to correlate actual object names with the object addresses of the trace buffer entries.</span></span> <span data-ttu-id="19261-153">Liczba wpisów rejestru jest określana przez aplikację w wywołaniu _ \*_tx_trace_enable_\*\*.</span><span class="sxs-lookup"><span data-stu-id="19261-153">The number of registry entries is specified by the application in the _ *_tx_trace_enable_*\* call.</span></span>

<span data-ttu-id="19261-154">Każdy wpis w rejestrze obiektów zawiera informacje o konkretnym obiekcie ThreadX, który został wcześniej utworzony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="19261-154">Each object register entry contains information about a specific ThreadX object previously created by the application.</span></span> <span data-ttu-id="19261-155">Następująca struktura danych definiuje każdy wpis rejestru obiektów:</span><span class="sxs-lookup"><span data-stu-id="19261-155">The following data structure defines each object registry entry:</span></span>

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a><span data-ttu-id="19261-156">Flaga dostępnego obiektu</span><span class="sxs-lookup"><span data-stu-id="19261-156">Object Available Flag</span></span>

<span data-ttu-id="19261-157">Flaga dostępnego obiektu jest ustawiona na 1, Jeśli wpis rejestru obiektów jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="19261-157">The object available flag is set to 1 if the object registry entry is available.</span></span> <span data-ttu-id="19261-158">W przeciwnym razie, jeśli wartość nie jest równa 1, wpis rejestru obiektu jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="19261-158">Otherwise, if the value is not 1, the object registry entry is not available.</span></span> <span data-ttu-id="19261-159">Należy zauważyć, że wpis może nadal zawierać prawidłowe informacje, nawet jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="19261-159">Note that the entry could still contain valid information even though it is available.</span></span>

### <a name="object-entry-type"></a><span data-ttu-id="19261-160">Typ wpisu obiektu</span><span class="sxs-lookup"><span data-stu-id="19261-160">Object Entry Type</span></span>

<span data-ttu-id="19261-161">Typ wpisu obiektu identyfikuje typ obiektu w tym wpisie.</span><span class="sxs-lookup"><span data-stu-id="19261-161">The object entry type identifies the type of object in this entry.</span></span> <span data-ttu-id="19261-162">Poniżej znajduje się lista prawidłowych typów obiektów:</span><span class="sxs-lookup"><span data-stu-id="19261-162">The following is a list of the valid object types:</span></span>

| <span data-ttu-id="19261-163">**Wartość**</span><span class="sxs-lookup"><span data-stu-id="19261-163">**Value**</span></span> | <span data-ttu-id="19261-164">**Typ obiektu**</span><span class="sxs-lookup"><span data-stu-id="19261-164">**Object Type**</span></span> |
|---------- | --------------- |
| <span data-ttu-id="19261-165">0</span><span class="sxs-lookup"><span data-stu-id="19261-165">0</span></span>         | <span data-ttu-id="19261-166">Nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="19261-166">Not Valid</span></span>       |
| <span data-ttu-id="19261-167">1</span><span class="sxs-lookup"><span data-stu-id="19261-167">1</span></span>         | <span data-ttu-id="19261-168">Thread</span><span class="sxs-lookup"><span data-stu-id="19261-168">Thread</span></span>          |
| <span data-ttu-id="19261-169">2</span><span class="sxs-lookup"><span data-stu-id="19261-169">2</span></span>         | <span data-ttu-id="19261-170">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="19261-170">Timer</span></span> |
| <span data-ttu-id="19261-171">3</span><span class="sxs-lookup"><span data-stu-id="19261-171">3</span></span>         | <span data-ttu-id="19261-172">Kolejka</span><span class="sxs-lookup"><span data-stu-id="19261-172">Queue</span></span> |
| <span data-ttu-id="19261-173">4</span><span class="sxs-lookup"><span data-stu-id="19261-173">4</span></span>         | <span data-ttu-id="19261-174">Semaphore</span><span class="sxs-lookup"><span data-stu-id="19261-174">Semaphore</span></span> |
| <span data-ttu-id="19261-175">5</span><span class="sxs-lookup"><span data-stu-id="19261-175">5</span></span>         | <span data-ttu-id="19261-176">Mutex</span><span class="sxs-lookup"><span data-stu-id="19261-176">Mutex</span></span> |
| <span data-ttu-id="19261-177">6</span><span class="sxs-lookup"><span data-stu-id="19261-177">6</span></span>         | <span data-ttu-id="19261-178">Grupa flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="19261-178">Event Flags Group</span></span> |
| <span data-ttu-id="19261-179">7</span><span class="sxs-lookup"><span data-stu-id="19261-179">7</span></span>         | <span data-ttu-id="19261-180">Blokuj pulę</span><span class="sxs-lookup"><span data-stu-id="19261-180">Block Pool</span></span> |
| <span data-ttu-id="19261-181">8</span><span class="sxs-lookup"><span data-stu-id="19261-181">8</span></span>         | <span data-ttu-id="19261-182">Pula bajtów</span><span class="sxs-lookup"><span data-stu-id="19261-182">Byte Pool</span></span> |
| <span data-ttu-id="19261-183">9</span><span class="sxs-lookup"><span data-stu-id="19261-183">9</span></span>         | <span data-ttu-id="19261-184">.. /media</span><span class="sxs-lookup"><span data-stu-id="19261-184">../media</span></span> |
| <span data-ttu-id="19261-185">10</span><span class="sxs-lookup"><span data-stu-id="19261-185">10</span></span>        | <span data-ttu-id="19261-186">Plik</span><span class="sxs-lookup"><span data-stu-id="19261-186">File</span></span> |
| <span data-ttu-id="19261-187">11</span><span class="sxs-lookup"><span data-stu-id="19261-187">11</span></span>        | <span data-ttu-id="19261-188">Adres IP</span><span class="sxs-lookup"><span data-stu-id="19261-188">IP</span></span> |
| <span data-ttu-id="19261-189">12</span><span class="sxs-lookup"><span data-stu-id="19261-189">12</span></span>        | <span data-ttu-id="19261-190">Pula pakietów</span><span class="sxs-lookup"><span data-stu-id="19261-190">Packet Pool</span></span> |
| <span data-ttu-id="19261-191">13</span><span class="sxs-lookup"><span data-stu-id="19261-191">13</span></span>        | <span data-ttu-id="19261-192">Gniazdo TCP</span><span class="sxs-lookup"><span data-stu-id="19261-192">TCP Socket</span></span> |
| <span data-ttu-id="19261-193">14</span><span class="sxs-lookup"><span data-stu-id="19261-193">14</span></span>        | <span data-ttu-id="19261-194">Gniazdo UDP</span><span class="sxs-lookup"><span data-stu-id="19261-194">UDP Socket</span></span> |
| <span data-ttu-id="19261-195">15-20</span><span class="sxs-lookup"><span data-stu-id="19261-195">15-20</span></span>     | <span data-ttu-id="19261-196">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="19261-196">Reserved</span></span> |  
| <span data-ttu-id="19261-197">21</span><span class="sxs-lookup"><span data-stu-id="19261-197">21</span></span>        | <span data-ttu-id="19261-198">Urządzenie stosu hosta USB</span><span class="sxs-lookup"><span data-stu-id="19261-198">USB Host Stack Device</span></span> |
| <span data-ttu-id="19261-199">22</span><span class="sxs-lookup"><span data-stu-id="19261-199">22</span></span>        | <span data-ttu-id="19261-200">Interfejs stosu hosta USB</span><span class="sxs-lookup"><span data-stu-id="19261-200">USB Host Stack Interface</span></span> |
| <span data-ttu-id="19261-201">23</span><span class="sxs-lookup"><span data-stu-id="19261-201">23</span></span>        | <span data-ttu-id="19261-202">Punkt końcowy hosta USB</span><span class="sxs-lookup"><span data-stu-id="19261-202">USB Host Endpoint</span></span> |
| <span data-ttu-id="19261-203">24</span><span class="sxs-lookup"><span data-stu-id="19261-203">24</span></span>        | <span data-ttu-id="19261-204">Klasa hosta USB</span><span class="sxs-lookup"><span data-stu-id="19261-204">USB Host Class</span></span> |
| <span data-ttu-id="19261-205">25</span><span class="sxs-lookup"><span data-stu-id="19261-205">25</span></span>        | <span data-ttu-id="19261-206">Urządzenie USB</span><span class="sxs-lookup"><span data-stu-id="19261-206">USB Device</span></span> |
| <span data-ttu-id="19261-207">26</span><span class="sxs-lookup"><span data-stu-id="19261-207">26</span></span>        | <span data-ttu-id="19261-208">Interfejs urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="19261-208">USB Device Interface</span></span> |
| <span data-ttu-id="19261-209">27</span><span class="sxs-lookup"><span data-stu-id="19261-209">27</span></span>        | <span data-ttu-id="19261-210">Punkt końcowy urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="19261-210">USB Device Endpoint</span></span> |
| <span data-ttu-id="19261-211">28</span><span class="sxs-lookup"><span data-stu-id="19261-211">28</span></span>        | <span data-ttu-id="19261-212">Klasa urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="19261-212">USB Device Class</span></span> |

### <a name="object-pointer"></a><span data-ttu-id="19261-213">Wskaźnik obiektu</span><span class="sxs-lookup"><span data-stu-id="19261-213">Object Pointer</span></span>

<span data-ttu-id="19261-214">Wskaźnik obiektu określa adres obiektu, który jest używany do uzyskiwania dostępu do obiektu za pomocą interfejsu API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="19261-214">The object pointer specifies the object address that is used for accessing the object using the ThreadX API.</span></span>

### <a name="object-reserved-fields"></a><span data-ttu-id="19261-215">Pola zarezerwowane dla obiektu</span><span class="sxs-lookup"><span data-stu-id="19261-215">Object Reserved Fields</span></span>

<span data-ttu-id="19261-216">Dla wszystkich obiektów innych niż wątki pola zarezerwowane powinny mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="19261-216">For all objects other than threads, these reserved fields should be 0.</span></span> <span data-ttu-id="19261-217">W przypadku wątków priorytet wątku w czasie wprowadzania do rejestru jest umieszczany w tych dwóch zastrzeżonych polach.</span><span class="sxs-lookup"><span data-stu-id="19261-217">For threads, the priority of the thread at the time it is entered into the registry is placed in these two reserved fields.</span></span>

### <a name="object-parameters"></a><span data-ttu-id="19261-218">Parametry obiektu</span><span class="sxs-lookup"><span data-stu-id="19261-218">Object Parameters</span></span>

<span data-ttu-id="19261-219">Parametry obiektu zawierają dodatkowe informacje na temat obiektu.</span><span class="sxs-lookup"><span data-stu-id="19261-219">The object parameters contain supplemental information about the object.</span></span> <span data-ttu-id="19261-220">Poniżej opisano dodatkowe informacje dla każdego obiektu ThreadX:</span><span class="sxs-lookup"><span data-stu-id="19261-220">The following describes the supplemental information for each ThreadX object:</span></span>

| <span data-ttu-id="19261-221">**Typ obiektu**</span><span class="sxs-lookup"><span data-stu-id="19261-221">**Object Type**</span></span>        | <span data-ttu-id="19261-222">**Parametr 1**</span><span class="sxs-lookup"><span data-stu-id="19261-222">**Parameter 1**</span></span>  | <span data-ttu-id="19261-223">**Parametr 2**</span><span class="sxs-lookup"><span data-stu-id="19261-223">**Parameter 2**</span></span> |
|----------------------- | ---------------- | --------------- |
| <span data-ttu-id="19261-224">Thread</span><span class="sxs-lookup"><span data-stu-id="19261-224">Thread</span></span>                 | <span data-ttu-id="19261-225">Rozpoczęcie stosu</span><span class="sxs-lookup"><span data-stu-id="19261-225">Stack Start</span></span>      | <span data-ttu-id="19261-226">Rozmiar stosu</span><span class="sxs-lookup"><span data-stu-id="19261-226">Stack Size</span></span> |
| <span data-ttu-id="19261-227">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="19261-227">Timer</span></span>                  | <span data-ttu-id="19261-228">Początkowe Takty</span><span class="sxs-lookup"><span data-stu-id="19261-228">Initial Ticks</span></span> | <span data-ttu-id="19261-229">Zaplanuj ponownie Takty</span><span class="sxs-lookup"><span data-stu-id="19261-229">Reschedule Ticks</span></span> |
| <span data-ttu-id="19261-230">Kolejka</span><span class="sxs-lookup"><span data-stu-id="19261-230">Queue</span></span>                  | <span data-ttu-id="19261-231">Rozmiar kolejki</span><span class="sxs-lookup"><span data-stu-id="19261-231">Queue Size</span></span> | <span data-ttu-id="19261-232">Rozmiar komunikatu</span><span class="sxs-lookup"><span data-stu-id="19261-232">Message Size</span></span> |
| <span data-ttu-id="19261-233">Semaphore</span><span class="sxs-lookup"><span data-stu-id="19261-233">Semaphore</span></span>              | <span data-ttu-id="19261-234">Początkowe wystąpienia</span><span class="sxs-lookup"><span data-stu-id="19261-234">Initial Instances</span></span> | - |
| <span data-ttu-id="19261-235">Mutex</span><span class="sxs-lookup"><span data-stu-id="19261-235">Mutex</span></span>                  | <span data-ttu-id="19261-236">Flaga dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="19261-236">Inheritance Flag</span></span> | - |
| <span data-ttu-id="19261-237">Grupa flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="19261-237">Event Flags Group</span></span>      | - | - |
| <span data-ttu-id="19261-238">Blokuj pulę</span><span class="sxs-lookup"><span data-stu-id="19261-238">Block Pool</span></span>             | <span data-ttu-id="19261-239">Łączna liczba bloków</span><span class="sxs-lookup"><span data-stu-id="19261-239">Total Blocks</span></span> | <span data-ttu-id="19261-240">Rozmiar bloku</span><span class="sxs-lookup"><span data-stu-id="19261-240">Block Size</span></span> |
| <span data-ttu-id="19261-241">Pula bajtów</span><span class="sxs-lookup"><span data-stu-id="19261-241">Byte Pool</span></span>              | <span data-ttu-id="19261-242">Łączna liczba bajtów</span><span class="sxs-lookup"><span data-stu-id="19261-242">Total Bytes</span></span> | - |
| <span data-ttu-id="19261-243">.. /media</span><span class="sxs-lookup"><span data-stu-id="19261-243">../media</span></span>                  | <span data-ttu-id="19261-244">Rozmiar pamięci podręcznej FAT</span><span class="sxs-lookup"><span data-stu-id="19261-244">Fat Cache Size</span></span> | <span data-ttu-id="19261-245">Rozmiar pamięci podręcznej sektora</span><span class="sxs-lookup"><span data-stu-id="19261-245">Sector Cache Size</span></span> |
| <span data-ttu-id="19261-246">Plik</span><span class="sxs-lookup"><span data-stu-id="19261-246">File</span></span>                   | - | - |
| <span data-ttu-id="19261-247">Adres IP</span><span class="sxs-lookup"><span data-stu-id="19261-247">IP</span></span>                     | <span data-ttu-id="19261-248">Rozpoczęcie stosu</span><span class="sxs-lookup"><span data-stu-id="19261-248">Stack Start</span></span> | <span data-ttu-id="19261-249">Rozmiar stosu</span><span class="sxs-lookup"><span data-stu-id="19261-249">Stack Size</span></span> |
| <span data-ttu-id="19261-250">Pula pakietów</span><span class="sxs-lookup"><span data-stu-id="19261-250">Packet Pool</span></span>            | <span data-ttu-id="19261-251">Rozmiar pakietu</span><span class="sxs-lookup"><span data-stu-id="19261-251">Packet Size</span></span> | <span data-ttu-id="19261-252">Liczba pakietów</span><span class="sxs-lookup"><span data-stu-id="19261-252">Number of Packets</span></span> |
| <span data-ttu-id="19261-253">Gniazdo TCP</span><span class="sxs-lookup"><span data-stu-id="19261-253">TCP Socket</span></span>             | <span data-ttu-id="19261-254">Adres IP</span><span class="sxs-lookup"><span data-stu-id="19261-254">IP address</span></span> | <span data-ttu-id="19261-255">Rozmiar okna</span><span class="sxs-lookup"><span data-stu-id="19261-255">Window Size</span></span> |
| <span data-ttu-id="19261-256">Gniazdo UDP</span><span class="sxs-lookup"><span data-stu-id="19261-256">UDP Socket</span></span>             | <span data-ttu-id="19261-257">Adres IP</span><span class="sxs-lookup"><span data-stu-id="19261-257">IP address</span></span> | <span data-ttu-id="19261-258">Maksymalna liczba kolejek RX</span><span class="sxs-lookup"><span data-stu-id="19261-258">RX Queue Max</span></span> |

### <a name="object-name"></a><span data-ttu-id="19261-259">Nazwa obiektu</span><span class="sxs-lookup"><span data-stu-id="19261-259">Object Name</span></span>

<span data-ttu-id="19261-260">Nazwa obiektu zawiera nazwę obiektu ThreadX.</span><span class="sxs-lookup"><span data-stu-id="19261-260">The object name contains the name of the ThreadX object.</span></span> <span data-ttu-id="19261-261">Nazwa jest nazwą dostarczoną do ThreadX w momencie utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="19261-261">The name is the name provided to ThreadX at the time the object was created.</span></span> <span data-ttu-id="19261-262">Domyślnie nazwa obiektu ma maksymalnie 32 znaków.</span><span class="sxs-lookup"><span data-stu-id="19261-262">By default, the object name has a maximum of 32 characters.</span></span> <span data-ttu-id="19261-263">Rzeczywiste nazwy większe niż 32 znaków są obcinane.</span><span class="sxs-lookup"><span data-stu-id="19261-263">Actual names greater than 32 characters are truncated.</span></span>

## <a name="event-trace-entries"></a><span data-ttu-id="19261-264">Wpisy śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="19261-264">Event Trace Entries</span></span>

<span data-ttu-id="19261-265">Wpisy śledzenia zdarzeń znajdują się w dolnej części buforu śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="19261-265">The event trace entries are found in the bottom portion of the event trace buffer.</span></span> <span data-ttu-id="19261-266">Wpisy są przechowywane na liście cyklicznej, przy czym wskaźnik bieżącego wpisu wskazuje na najstarszą pozycję.</span><span class="sxs-lookup"><span data-stu-id="19261-266">The entries are maintained in a circular list, with the current entry pointer pointing to the oldest entry.</span></span> <span data-ttu-id="19261-267">Liczba wpisów na liście jest obliczana przez wywołanie ***tx_trace_enable*** .</span><span class="sxs-lookup"><span data-stu-id="19261-267">The number of entries in the list is calculated by the ***tx_trace_enable*** call.</span></span>

<span data-ttu-id="19261-268">Każdy wpis w rejestrze obiektów zawiera informacje o określonym zdarzeniu śledzenia ThreadX.</span><span class="sxs-lookup"><span data-stu-id="19261-268">Each object register entry contains information about a specific ThreadX trace event.</span></span> <span data-ttu-id="19261-269">Następująca struktura danych definiuje każdy wpis zdarzenia śledzenia:</span><span class="sxs-lookup"><span data-stu-id="19261-269">The following data structure defines each trace event entry:</span></span>

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a><span data-ttu-id="19261-270">Wskaźnik wątku</span><span class="sxs-lookup"><span data-stu-id="19261-270">Thread Pointer</span></span>

<span data-ttu-id="19261-271">Wskaźnik wątku zawiera adres wątku uruchomionego w czasie tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-271">The thread pointer contains the address of the thread running at the time of this event.</span></span> <span data-ttu-id="19261-272">Jeśli zdarzenie wystąpiło podczas inicjowania (brak działającego wątku), wartość tego wskaźnika to 0xF0F0F0F0.</span><span class="sxs-lookup"><span data-stu-id="19261-272">If the event occurred during initialization (no thread running), the value of this pointer is 0xF0F0F0F0.</span></span> <span data-ttu-id="19261-273">Jeśli zdarzenie wystąpiło w trakcie procedury usługi przerwania (ISR), wartość tego wskaźnika to 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="19261-273">If the event occurred during an Interrupt Service Routine (ISR), the value of this pointer is 0xFFFFFFFF.</span></span> <span data-ttu-id="19261-274">Jeśli wpis nie został jeszcze użyty, wartość tego wskaźnika wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="19261-274">If the entry has not yet been used, the value of this pointer is 0.</span></span>

### <a name="thread-priority"></a><span data-ttu-id="19261-275">Priorytet wątku</span><span class="sxs-lookup"><span data-stu-id="19261-275">Thread Priority</span></span>

<span data-ttu-id="19261-276">Pole priorytet wątku zawiera priorytet wątku i zastępujący — próg wątku, który był uruchomiony w czasie tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-276">The thread priority field contains the thread priority and preemption-threshold of the thread that was running at the time of this event.</span></span> <span data-ttu-id="19261-277">Jeśli jest obecny kontekst przerwania (wskaźnik wątku to 0xFFFFFFFF), wartość tego pola nie jest priorytetem, ale zamiast wartości ***_tx_thread_current_ptr*** w czasie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19261-277">If an interrupt context is present (thread pointer is 0xFFFFFFFF), the value of this field is not the priority but instead the value of ***_tx_thread_current_ptr*** at the time of the event.</span></span> <span data-ttu-id="19261-278">W przeciwnym razie wartość tego pola wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="19261-278">Otherwise, the value of this field is 0.</span></span>

### <a name="event-id"></a><span data-ttu-id="19261-279">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19261-279">Event ID</span></span>

<span data-ttu-id="19261-280">Identyfikator zdarzenia określa zdarzenie, które miało miejsce.</span><span class="sxs-lookup"><span data-stu-id="19261-280">The event ID specifies the event that took place.</span></span> <span data-ttu-id="19261-281">Prawidłowe identyfikatory zdarzeń śledzenia ThreadX mieszczą się w zakresie od 1 do 1024.</span><span class="sxs-lookup"><span data-stu-id="19261-281">Valid ThreadX trace event IDs range from 1 through 1024.</span></span> <span data-ttu-id="19261-282">Wartości zaczynające się od 1025 i powyżej są zarezerwowane dla zdarzeń specyficznych dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="19261-282">Values starting at 1025 and above are reserved for user-specific events.</span></span> <span data-ttu-id="19261-283">Zapoznaj się z plikiem ***tx_trace. h*** , aby uzyskać pełną definicję identyfikatorów zdarzeń ThreadX.</span><span class="sxs-lookup"><span data-stu-id="19261-283">Please refer to the ***tx_trace.h*** file for the complete definition of ThreadX event IDs.</span></span></td>

### <a name="information-fields-1-4"></a><span data-ttu-id="19261-284">Pola informacji (1-4)</span><span class="sxs-lookup"><span data-stu-id="19261-284">Information Fields (1-4)</span></span>

<span data-ttu-id="19261-285">Pola informacji zawierają dodatkowe informacje o konkretnym zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="19261-285">The information fields contain additional information about the specific event.</span></span> <span data-ttu-id="19261-286">Zapoznaj się z plikiem ***tx_trace. h*** , aby uzyskać pełny opis pól informacji dla każdego ze zdefiniowanych identyfikatorów zdarzeń ThreadX.</span><span class="sxs-lookup"><span data-stu-id="19261-286">Please refer to the ***tx_trace.h*** file for the complete description of the information fields for each of the defined ThreadX event IDs.</span></span>