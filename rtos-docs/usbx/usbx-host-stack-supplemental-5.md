---
title: USBX OTG
description: UsbX obsługuje funkcje OTG USB, gdy kontroler USB zgodny z OTG jest dostępny w projekcie sprzętu.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bb9a0b98ed3f843ee690dfe419a3684562f1255e6839ddb06ded9d8f6023adcc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798269"
---
# <a name="chapter-5-usbx-otg"></a>Rozdział 5: USBX OTG

UsbX obsługuje funkcje OTG USB, gdy kontroler USB zgodny z OTG jest dostępny w projekcie sprzętu.

UsbX obsługuje OTG w podstawowym stosie USB. Jednak aby OTG działało, wymaga określonego kontrolera USB. Funkcje kontrolera USBX OTG można znaleźć w ***usbx_otg*** katalogu. Bieżąca wersja USBX obsługuje tylko NXP LPC3131 z pełnymi możliwościami OTG.

Zwykłe funkcje sterowników kontrolera (hosta lub urządzenia) nadal można znaleźć w standardzie USBX usbx_device_controllers i usbx_host_controllers ale ***katalog usbx_otg*** zawiera określone funkcje OTG skojarzone z kontrolerem USB.

Istnieją cztery kategorie funkcji kontrolera OTG oprócz zwykłych funkcji hosta/urządzenia.

- Funkcje specyficzne dla VBUS
- Uruchamianie i zatrzymywanie kontrolera
- Menedżer ról USB
- Programy obsługi przerwań

## <a name="vbus-functions"></a>Funkcje VBUS

Każdy kontroler musi mieć menedżera VBUS, aby zmienić stan VBUS na podstawie wymagań dotyczących zarządzania energią. Zazwyczaj ta funkcja wykonuje tylko włączanie lub wyłączanie VBUS

## <a name="start-and-stop-the-controller"></a>Uruchamianie i zatrzymywanie kontrolera

W przeciwieństwie do zwykłej implementacji USB, OTG wymaga aktywowania i dezaktywowania hosta i/lub stosu urządzenia po zmianie roli.

## <a name="usb-role-manager"></a>Menedżer ról USB

Menedżer ról USB odbiera polecenia zmiany stanu USB. Istnieje kilka stanów, które wymagają przejścia do i z stanów podanych w poniższej tabeli.

| Stan                    | Wartość | Opis                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | Urządzenie jest bezczynne. Nie połączono z niczym |
| UX_OTG_IDLE_TO_HOST  | 1     | Urządzenie jest połączone za pomocą łącznika typu A             |
| UX_OTG_IDLE_TO_SLAVE | 2     | Urządzenie jest połączone za pomocą łącznika typu B             |
| UX_OTG_HOST_TO_IDLE  | 3     | Urządzenie hosta zostało odłączone                          |
| UX_OTG_HOST_TO_SLAVE | 4     | Zamiana ról z hosta na podrzędny                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | Urządzenie podrzędne jest rozłączone                          |
| UX_OTG_SLAVE_TO_HOST | 6     | Zamiana ról z podrzędnej na host                          |

## <a name="interrupt-handlers"></a>Programy obsługi przerwań

Zarówno sterowniki hosta, jak i kontrolera urządzeń dla sieci OTG potrzebują różnych programów obsługi przerwań do monitorowania sygnałów wykraczających poza tradycyjne przerwania USB, w szczególności sygnałów spowodowanych przez SRP i VBUS.

Jak zainicjować kontroler USB OTG. Jako przykładu używamy nxp LPC3131.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

W tym przykładzie zainicjowano LPC3131 w trybie OTG przez przekazanie funkcji VBUS i wywołania zwrotnego dla zmiany trybu (z hosta na podrzędny lub odwrotnie).

Funkcja wywołania zwrotnego powinna po prostu zarejestrować nowy tryb i wznowić oczekujący wątek, aby wywołać nowy stan.

```C
void tx_demo_change_mode_callback(ULONG mode)
{
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

Przekazywana wartość trybu może mieć następujące wartości.

- UX_OTG_MODE_IDLE
- UX_OTG_MODE_SLAVE
- UX_OTG_MODE_HOST

Aplikacja może zawsze sprawdzić, czym jest urządzenie, patrząc na zmienną .

```C
ux_system_otg ->ux_system_otg_device_type
```

Jej wartości mogą być jednym z następujących.

- UX_OTG_DEVICE_A
- UX_OTG_DEVICE_B
- UX_OTG_DEVICE_IDLE

Urządzenie hosta USB OTG zawsze może poprosić o zamianę roli, wydając polecenie .

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */

ux_host_stack_role_swap(storage ->ux_host_class_storage_device);
```

W przypadku urządzenia podrzędnego nie ma polecenia do wystawienia, ale urządzenie podrzędne może ustawić stan zmiany roli, który zostanie odebrany przez hosta w przypadku wystawienia GET_STATUS i zamiana zostanie zainicjowana.

```C
/* We are a B device, ask for role swap. The next GET_STATUS from the host will get the status change and do the HNP. */

ux_system_otg ->ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
