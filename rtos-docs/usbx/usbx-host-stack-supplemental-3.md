---
title: Zagadnienia dotyczące klasy DPUMP USBX
description: UsbX zawiera klasę DPUMP po stronie hosta i urządzenia.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 72aa9c1e2200049bf81d64543b690edd001c4ecf9c2cdeb4c3bea5f1b03aa5b8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802581"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a>Rozdział 3: Zagadnienia dotyczące klasy DPUMP USBX

UsbX zawiera klasę DPUMP po stronie hosta i urządzenia. Ta klasa nie jest klasą standardową samą w sobie, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych tam i z powrotem w tych dwóch potokach. Klasa DPUMP może służyć do uruchamiania klasy niestandardowej lub starszych urządzeń RS232.

Wykres blokowy USB DPUMP:

![Wykres blokowy USB DPUMP](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>Klasa hosta USBX DPUMP

Strona hosta klasy DPUMP ma dwie funkcje: jedną do wysyłania danych i jedną do odbierania danych:

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

Obie funkcje blokują, aby ułatwić działanie aplikacji DPUMP. Jeśli konieczne jest, aby oba potoki (IN i OUT) były uruchomione w tym samym czasie, aplikacja będzie wymagana do utworzenia wątku przesyłania i wątku odbioru.

Prototyp funkcji pisania jest następujący.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

Gdzie:

- dpump to wystąpienie klasy
- data_pointer jest wskaźnikiem do buforu do wysłania
- requested_length to długość do wysłania
- actual_length to długość wysłana po zakończeniu transferu, pomyślna lub częściowa.

Prototyp funkcji odbieracej jest podobny.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

Oto przykład klasy DPUMP hosta, w której aplikacja zapisuje pakiet po stronie urządzenia i odbiera ten sam pakiet w odbiorze:

```C
/* We start with a 'A' in buffer. */
current_char = 'A';

while(1)
{
    /* Initialize the write buffer. */
    ux_utility_memory_set(out_buffer, current_char,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE);

    /* Increment the character in buffer. */
    current_char++;

    /* Check for upper alphabet limit. */
    if (current_char > 'Z')
        current_char = 'A';

    /* Write to the Data Pump Bulk out endpoint. */
    status = ux_host_class_dpump_write (dpump, out_buffer,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE,
        &actual_length);

    /* Verify that the status and the amount of data is correct. */
    if ((status == UX_SUCCESS) && actual_length == UX_HOST_CLASS_DPUMP_PACKET_SIZE)
    {
        /* Read to the Data Pump Bulk out endpoint. */
        status = ux_host_class_dpump_read (dpump, in_buffer,
            UX_HOST_CLASS_DPUMP_PACKET_SIZE, &actual_length);
    }
}
```

## <a name="usbx-dpump-device-class"></a>Klasa urządzenia USBX DPUMP

Klasa DPUMP urządzenia używa wątku, który jest uruchomiony po nawiązaniu połączenia z hostem USB. Wątek czeka na pakiet przychodzący w punkcie końcowym operacji zbiorczych na zewnątrz. Po otrzymaniu pakietu kopiuje zawartość do buforu punktu końcowego zbiorczego i publikuje transakcję w tym punkcie końcowym, czekając, aż host wyda żądanie odczytu z tego punktu końcowego. Zapewnia to mechanizm sprzężenia zwrotnego między punktami końcowymi operacji zbiorczych i zbiorczych.
