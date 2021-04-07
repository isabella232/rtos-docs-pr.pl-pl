---
title: Rozdział 5 — USBX OTG
description: Dowiedz się, w jaki sposób USBX obsługuje funkcje OTG USB, gdy w projekcie sprzętu jest dostępny kontroler USB zgodny z OTG.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 64a3c44f84b9ffca31d9e616d14d3d5d87c56bd7
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550324"
---
# <a name="chapter-5---usbx-otg"></a>Rozdział 5 — USBX OTG

USBX obsługuje funkcje OTG USB, gdy kontroler USB zgodny z OTG jest dostępny w projekcie sprzętu.

USBX obsługuje OTG w podstawowym stosie USB. Jednak dla OTG do działania wymaga określonego kontrolera USB. Funkcje kontrolera OTG USBX można znaleźć w katalogu usbx_otg. Bieżąca wersja USBX obsługuje tylko NXP LPC3131 z pełnymi możliwościami OTG.

Funkcje sterownika regularnego kontrolera (hosta lub urządzenia) nadal można znaleźć w standardowej USBX usbx_device_controllers i usbx_host_controllers ale katalog usbx_otg zawiera określone funkcje OTG skojarzone z kontrolerem USB.

Oprócz zwykłych funkcji hosta/urządzenia są dostępne cztery kategorie funkcji kontrolera OTG.

- VBUS określone funkcje
- Uruchamianie i zatrzymywanie kontrolera
- Menedżer roli USB
- Programy obsługi przerwań

## <a name="vbus-functions"></a>Funkcje VBUS

Każdy kontroler musi mieć Menedżera VBUS, aby zmienić stan VBUS na podstawie wymagań związanych z zarządzaniem zużyciem mocy. Zwykle ta funkcja wykonuje tylko Włączanie lub wyłączanie VBUS.

## <a name="start-and-stop-the-controller"></a>Uruchamianie i zatrzymywanie kontrolera

W przeciwieństwie do zwykłej implementacji USB OTG wymaga, aby Host i/lub stos urządzenia zostały aktywowane i dezaktywowane po zmianie roli.

## <a name="usb-role-manager"></a>Menedżer roli USB

Menedżer roli USB odbiera polecenia, aby zmienić stan portu USB. Istnieje kilka stanów, które wymagają przejścia do i z:

| Stan                    | Wartość | Opis                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | Urządzenie jest w stanie bezczynności. Brak połączenia ze wszystkimi elementami |
| UX_OTG_IDLE_TO_HOST  | 1     | Urządzenie jest połączone z typem łącznika             |
| UX_OTG_IDLE_TO_SLAVE | 2     | Urządzenie jest połączone z łącznikiem typu B             |
| UX_OTG_HOST_TO_IDLE  | 3     | Urządzenie hosta zostało rozłączone                          |
| UX_OTG_HOST_TO_SLAVE | 4     | Wymiana ról z hosta do podrzędnego                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | Urządzenie podrzędne zostało rozłączone                          |
| UX_OTG_SLAVE_TO_HOST | 6     | Wymiana ról z elementu podrzędnego na host                          |

## <a name="interrupt-handlers"></a>Programy obsługi przerwań

Sterowniki hosta i kontrolera urządzenia dla OTG potrzebują różnych programów obsługi przerwań do monitorowania sygnałów poza tradycyjne przerwania USB, w szczególności sygnałów spowodowanych przez SRP i VBUS.

Jak zainicjować kontroler OTG USB. W tym przykładzie używamy LPC3131 NXP.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

W tym przykładzie zainicjujemy LPC3131 w trybie OTG, przekazując funkcję VBUS i wywołanie zwrotne dla zmiany trybu (od hosta do podrzędnego lub odwrotnie).

Funkcja wywołania zwrotnego powinna po prostu zarejestrować nowy tryb i wznowić wątek oczekujący do działania nowego stanu.

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

Przenoszona wartość trybu może mieć następujące wartości.

- **UX_OTG_MODE_IDLE**
- **UX_OTG_MODE_SLAVE**
- **UX_OTG_MODE_HOST**

Aplikacja zawsze może sprawdzić zawartość urządzenia, przeglądając zmienną:

```C
_ux_system_otg -> ux_system_otg_device_type
```

Mogą to być dowolne z następujących wartości.

- **UX_OTG_DEVICE_A**
- **UX_OTG_DEVICE_B**
- **UX_OTG_DEVICE_IDLE**

Urządzenie hosta OTG USB może zawsze żądać zamiany roli przez wystawienie następującego polecenia.

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

W przypadku urządzenia podrzędnego nie ma polecenia do wystawienia, ale urządzenie podrzędne może ustawić stan, aby zmienić rolę, która zostanie pobrana przez hosta, gdy wykryje **GET_STATUS** , a następnie zostanie zainicjowana wymiana.

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
