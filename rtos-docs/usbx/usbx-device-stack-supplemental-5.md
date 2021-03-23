---
title: Rozdział 5 — USBX OTG
description: USBX obsługuje funkcje OTG USB, gdy kontroler USB zgodny z OTG jest dostępny w projekcie sprzętu.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: da562fd843c6ef0fd17f0d979ca57bd37572748d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823317"
---
# <a name="chapter-5---usbx-otg"></a><span data-ttu-id="e78e5-103">Rozdział 5 — USBX OTG</span><span class="sxs-lookup"><span data-stu-id="e78e5-103">Chapter 5 - USBX OTG</span></span>

<span data-ttu-id="e78e5-104">USBX obsługuje funkcje OTG USB, gdy kontroler USB zgodny z OTG jest dostępny w projekcie sprzętu.</span><span class="sxs-lookup"><span data-stu-id="e78e5-104">USBX supports the OTG functionalities of USB when an OTG compliant USB controller is available in the hardware design.</span></span>

<span data-ttu-id="e78e5-105">USBX obsługuje OTG w podstawowym stosie USB.</span><span class="sxs-lookup"><span data-stu-id="e78e5-105">USBX supports OTG in the core USB stack.</span></span> <span data-ttu-id="e78e5-106">Jednak dla OTG do działania wymaga określonego kontrolera USB.</span><span class="sxs-lookup"><span data-stu-id="e78e5-106">But for OTG to function, it requires a specific USB controller.</span></span> <span data-ttu-id="e78e5-107">Funkcje kontrolera OTG USBX można znaleźć w katalogu usbx_otg.</span><span class="sxs-lookup"><span data-stu-id="e78e5-107">USBX OTG controller functions can be found in the usbx_otg directory.</span></span> <span data-ttu-id="e78e5-108">Bieżąca wersja USBX obsługuje tylko NXP LPC3131 z pełnymi możliwościami OTG.</span><span class="sxs-lookup"><span data-stu-id="e78e5-108">The current USBX version only supports the NXP LPC3131 with full OTG capabilities.</span></span>

<span data-ttu-id="e78e5-109">Funkcje sterownika regularnego kontrolera (hosta lub urządzenia) nadal można znaleźć w standardowej USBX usbx_device_controllers i usbx_host_controllers ale katalog usbx_otg zawiera określone funkcje OTG skojarzone z kontrolerem USB.</span><span class="sxs-lookup"><span data-stu-id="e78e5-109">The regular controller driver functions (host or device) can still be found in the standard USBX usbx_device_controllers and usbx_host_controllers but the usbx_otg directory contains the specific OTG functions associated with the USB controller.</span></span>

<span data-ttu-id="e78e5-110">Oprócz zwykłych funkcji hosta/urządzenia są dostępne cztery kategorie funkcji kontrolera OTG.</span><span class="sxs-lookup"><span data-stu-id="e78e5-110">There are four categories of functions for an OTG controller in addition to the usual host/device functions.</span></span>

- <span data-ttu-id="e78e5-111">VBUS określone funkcje</span><span class="sxs-lookup"><span data-stu-id="e78e5-111">VBUS specific functions</span></span>
- <span data-ttu-id="e78e5-112">Uruchamianie i zatrzymywanie kontrolera</span><span class="sxs-lookup"><span data-stu-id="e78e5-112">Start and Stop of the controller</span></span>
- <span data-ttu-id="e78e5-113">Menedżer roli USB</span><span class="sxs-lookup"><span data-stu-id="e78e5-113">USB role manager</span></span>
- <span data-ttu-id="e78e5-114">Programy obsługi przerwań</span><span class="sxs-lookup"><span data-stu-id="e78e5-114">Interrupt handlers</span></span>

## <a name="vbus-functions"></a><span data-ttu-id="e78e5-115">Funkcje VBUS</span><span class="sxs-lookup"><span data-stu-id="e78e5-115">VBUS functions</span></span>

<span data-ttu-id="e78e5-116">Każdy kontroler musi mieć Menedżera VBUS, aby zmienić stan VBUS na podstawie wymagań związanych z zarządzaniem zużyciem mocy.</span><span class="sxs-lookup"><span data-stu-id="e78e5-116">Each controller needs to have a VBUS manager to change the state of VBUS based on power management requirements.</span></span> <span data-ttu-id="e78e5-117">Zwykle ta funkcja wykonuje tylko Włączanie lub wyłączanie VBUS.</span><span class="sxs-lookup"><span data-stu-id="e78e5-117">Usually, this function only performs turning on or off VBUS.</span></span>

## <a name="start-and-stop-the-controller"></a><span data-ttu-id="e78e5-118">Uruchamianie i zatrzymywanie kontrolera</span><span class="sxs-lookup"><span data-stu-id="e78e5-118">Start and Stop the controller</span></span>

<span data-ttu-id="e78e5-119">W przeciwieństwie do zwykłej implementacji USB OTG wymaga, aby Host i/lub stos urządzenia zostały aktywowane i dezaktywowane po zmianie roli.</span><span class="sxs-lookup"><span data-stu-id="e78e5-119">Unlike a regular USB implementation, OTG requires the host and/or the device stack to be activated and deactivated when the role changes.</span></span>

## <a name="usb-role-manager"></a><span data-ttu-id="e78e5-120">Menedżer roli USB</span><span class="sxs-lookup"><span data-stu-id="e78e5-120">USB role Manager</span></span>

<span data-ttu-id="e78e5-121">Menedżer roli USB odbiera polecenia, aby zmienić stan portu USB.</span><span class="sxs-lookup"><span data-stu-id="e78e5-121">The USB role manager receives commands to change the state of the USB.</span></span> <span data-ttu-id="e78e5-122">Istnieje kilka stanów, które wymagają przejścia do i z:</span><span class="sxs-lookup"><span data-stu-id="e78e5-122">There are several states that need transitions to and from:</span></span>

| <span data-ttu-id="e78e5-123">Stan</span><span class="sxs-lookup"><span data-stu-id="e78e5-123">State</span></span>                    | <span data-ttu-id="e78e5-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="e78e5-124">Value</span></span> | <span data-ttu-id="e78e5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e78e5-125">Description</span></span>                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| <span data-ttu-id="e78e5-126">UX_OTG_IDLE</span><span class="sxs-lookup"><span data-stu-id="e78e5-126">UX_OTG_IDLE</span></span>            | <span data-ttu-id="e78e5-127">0</span><span class="sxs-lookup"><span data-stu-id="e78e5-127">0</span></span>     | <span data-ttu-id="e78e5-128">Urządzenie jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e78e5-128">The device is Idle.</span></span> <span data-ttu-id="e78e5-129">Brak połączenia ze wszystkimi elementami</span><span class="sxs-lookup"><span data-stu-id="e78e5-129">Not connected to anything</span></span> |
| <span data-ttu-id="e78e5-130">UX_OTG_IDLE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="e78e5-130">UX_OTG_IDLE_TO_HOST</span></span>  | <span data-ttu-id="e78e5-131">1</span><span class="sxs-lookup"><span data-stu-id="e78e5-131">1</span></span>     | <span data-ttu-id="e78e5-132">Urządzenie jest połączone z typem łącznika</span><span class="sxs-lookup"><span data-stu-id="e78e5-132">Device is connected with type A connector</span></span>             |
| <span data-ttu-id="e78e5-133">UX_OTG_IDLE_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="e78e5-133">UX_OTG_IDLE_TO_SLAVE</span></span> | <span data-ttu-id="e78e5-134">2</span><span class="sxs-lookup"><span data-stu-id="e78e5-134">2</span></span>     | <span data-ttu-id="e78e5-135">Urządzenie jest połączone z łącznikiem typu B</span><span class="sxs-lookup"><span data-stu-id="e78e5-135">Device is connected with type B connector</span></span>             |
| <span data-ttu-id="e78e5-136">UX_OTG_HOST_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="e78e5-136">UX_OTG_HOST_TO_IDLE</span></span>  | <span data-ttu-id="e78e5-137">3</span><span class="sxs-lookup"><span data-stu-id="e78e5-137">3</span></span>     | <span data-ttu-id="e78e5-138">Urządzenie hosta zostało rozłączone</span><span class="sxs-lookup"><span data-stu-id="e78e5-138">Host device got disconnected</span></span>                          |
| <span data-ttu-id="e78e5-139">UX_OTG_HOST_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="e78e5-139">UX_OTG_HOST_TO_SLAVE</span></span> | <span data-ttu-id="e78e5-140">4</span><span class="sxs-lookup"><span data-stu-id="e78e5-140">4</span></span>     | <span data-ttu-id="e78e5-141">Wymiana ról z hosta do podrzędnego</span><span class="sxs-lookup"><span data-stu-id="e78e5-141">Role swap from Host to Slave</span></span>                          |
| <span data-ttu-id="e78e5-142">UX_OTG_SLAVE_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="e78e5-142">UX_OTG_SLAVE_TO_IDLE</span></span> | <span data-ttu-id="e78e5-143">5</span><span class="sxs-lookup"><span data-stu-id="e78e5-143">5</span></span>     | <span data-ttu-id="e78e5-144">Urządzenie podrzędne zostało rozłączone</span><span class="sxs-lookup"><span data-stu-id="e78e5-144">Slave device is disconnected</span></span>                          |
| <span data-ttu-id="e78e5-145">UX_OTG_SLAVE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="e78e5-145">UX_OTG_SLAVE_TO_HOST</span></span> | <span data-ttu-id="e78e5-146">6</span><span class="sxs-lookup"><span data-stu-id="e78e5-146">6</span></span>     | <span data-ttu-id="e78e5-147">Wymiana ról z elementu podrzędnego na host</span><span class="sxs-lookup"><span data-stu-id="e78e5-147">Role swap from Slave to Host</span></span>                          |

## <a name="interrupt-handlers"></a><span data-ttu-id="e78e5-148">Programy obsługi przerwań</span><span class="sxs-lookup"><span data-stu-id="e78e5-148">Interrupt handlers</span></span>

<span data-ttu-id="e78e5-149">Sterowniki hosta i kontrolera urządzenia dla OTG potrzebują różnych programów obsługi przerwań do monitorowania sygnałów poza tradycyjne przerwania USB, w szczególności sygnałów spowodowanych przez SRP i VBUS.</span><span class="sxs-lookup"><span data-stu-id="e78e5-149">Both host and device controller drivers for OTG needs different interrupt handlers to monitor signals beyond traditional USB interrupts, in particular signals due to SRP and VBUS.</span></span>

<span data-ttu-id="e78e5-150">Jak zainicjować kontroler OTG USB.</span><span class="sxs-lookup"><span data-stu-id="e78e5-150">How to initialize a USB OTG controller.</span></span> <span data-ttu-id="e78e5-151">W tym przykładzie używamy LPC3131 NXP.</span><span class="sxs-lookup"><span data-stu-id="e78e5-151">We use the NXP LPC3131 as an example here.</span></span>

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

<span data-ttu-id="e78e5-152">W tym przykładzie zainicjujemy LPC3131 w trybie OTG, przekazując funkcję VBUS i wywołanie zwrotne dla zmiany trybu (od hosta do podrzędnego lub odwrotnie).</span><span class="sxs-lookup"><span data-stu-id="e78e5-152">In this example, we initialize the LPC3131 in OTG mode by passing a VBUS function and a callback for mode change (from host to slave or vice versa).</span></span>

<span data-ttu-id="e78e5-153">Funkcja wywołania zwrotnego powinna po prostu zarejestrować nowy tryb i wznowić wątek oczekujący do działania nowego stanu.</span><span class="sxs-lookup"><span data-stu-id="e78e5-153">The callback function should simply record the new mode and wake up a pending thread to act up the new state.</span></span>

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

<span data-ttu-id="e78e5-154">Przenoszona wartość trybu może mieć następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="e78e5-154">The mode value that is passed can have the following values.</span></span>

- <span data-ttu-id="e78e5-155">**UX_OTG_MODE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="e78e5-155">**UX_OTG_MODE_IDLE**</span></span>
- <span data-ttu-id="e78e5-156">**UX_OTG_MODE_SLAVE**</span><span class="sxs-lookup"><span data-stu-id="e78e5-156">**UX_OTG_MODE_SLAVE**</span></span>
- <span data-ttu-id="e78e5-157">**UX_OTG_MODE_HOST**</span><span class="sxs-lookup"><span data-stu-id="e78e5-157">**UX_OTG_MODE_HOST**</span></span>

<span data-ttu-id="e78e5-158">Aplikacja zawsze może sprawdzić zawartość urządzenia, przeglądając zmienną:</span><span class="sxs-lookup"><span data-stu-id="e78e5-158">The application can always check what the device is by looking at the variable:</span></span>

```C
_ux_system_otg -> ux_system_otg_device_type
```

<span data-ttu-id="e78e5-159">Mogą to być dowolne z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="e78e5-159">Its values can be any of the following.</span></span>

- <span data-ttu-id="e78e5-160">**UX_OTG_DEVICE_A**</span><span class="sxs-lookup"><span data-stu-id="e78e5-160">**UX_OTG_DEVICE_A**</span></span>
- <span data-ttu-id="e78e5-161">**UX_OTG_DEVICE_B**</span><span class="sxs-lookup"><span data-stu-id="e78e5-161">**UX_OTG_DEVICE_B**</span></span>
- <span data-ttu-id="e78e5-162">**UX_OTG_DEVICE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="e78e5-162">**UX_OTG_DEVICE_IDLE**</span></span>

<span data-ttu-id="e78e5-163">Urządzenie hosta OTG USB może zawsze żądać zamiany roli przez wystawienie następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e78e5-163">A USB OTG host device can always ask for a role swap by issuing the following command.</span></span>

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

<span data-ttu-id="e78e5-164">W przypadku urządzenia podrzędnego nie ma polecenia do wystawienia, ale urządzenie podrzędne może ustawić stan, aby zmienić rolę, która zostanie pobrana przez hosta, gdy wykryje **GET_STATUS** , a następnie zostanie zainicjowana wymiana.</span><span class="sxs-lookup"><span data-stu-id="e78e5-164">For a slave device, there is no command to issue but the slave device can set a state to change the role, which will be picked up by the host when it issues a **GET_STATUS** and the swap will then be initiated.</span></span>

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
