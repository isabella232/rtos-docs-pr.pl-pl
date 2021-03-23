---
title: Zagadnienia dotyczące klasy USBX DPUMP
description: USBX zawiera klasę DPUMP dla hosta i urządzenia.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9960b391418fa2f9203e761115bcba71cc3619e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823977"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a>Rozdział 3: zagadnienia dotyczące klasy USBX DPUMP

USBX zawiera klasę DPUMP dla hosta i urządzenia. Ta klasa nie jest klasą standardową w sobie, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych z powrotem do tych dwóch potoków. Klasa DPUMP może służyć do uruchomienia klasy niestandardowej lub starszych urządzeń RS232.

Wykres przepływu DPUMP USB:

![Wykres przepływu DPUMP USB](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>Klasa hosta USBX DPUMP

Strona hosta klasy DPUMP ma dwie funkcje, jeden do wysyłania danych i jeden do odbioru danych:

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

Obie funkcje blokują, aby ułatwić aplikacji DPUMP. Jeśli konieczne jest uruchamianie obu potoków (w i OUT) w tym samym czasie, aplikacja będzie wymagana do utworzenia wątku przesyłania i wątku odbierania.

Prototyp funkcji pisania jest następujący:.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

Gdzie:

- dpump jest wystąpieniem klasy
- data_pointer jest wskaźnikiem do buforu do wysłania
- requested_length to długość do wysłania
- actual_length jest długością wysłaną po zakończeniu transferu — pomyślnie lub częściowo.

Prototyp dla funkcji odbiorczej jest podobny.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

Poniżej znajduje się przykład klasy DPUMP hosta, w której aplikacja zapisuje pakiet po stronie urządzenia i odbiera ten sam pakiet w odniesieniu:

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

Klasa Device DPUMP używa wątku uruchomionego po nawiązaniu połączenia z hostem USB. Wątek czeka na pakiet w punkcie końcowym zbiorczym. Po odebraniu pakietu program kopiuje zawartość do zbiorczo w buforze punktów końcowych i zapisuje transakcję w tym punkcie końcowym, czekając, aż Host wystawia żądanie odczytu z tego punktu końcowego. Zapewnia to mechanizm sprzężenia zwrotnego między zbiorczą i zbiorczo punktami końcowymi.
