---
title: Rozdział 3 — Zagadnienia dotyczące klasy DPUMP USBX
description: UsbX zawiera klasę DPUMP po stronie hosta i urządzenia. Ta klasa sama w sobie nie jest klasą standardową, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych tam i z powrotem w tych dwóch potokach
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d453d9ee19b9bc7ca7809102f087f46fdde05dc62b756d9eb3f38f493805be4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791157"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a>Rozdział 3 — Zagadnienia dotyczące klasy DPUMP USBX

UsbX zawiera **klasę DPUMP** po stronie hosta i urządzenia. Ta klasa nie jest klasą standardową samą w sobie, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych tam i z powrotem w tych dwóch potokach. Klasa **DPUMP** może służyć do uruchamiania klasy niestandardowej lub starszych urządzeń RS232.

Wykres blokowy USB DPUMP:

![Wykres Flow DPUMP USB](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>Klasa urządzenia USBX DPUMP

Klasa **DPUMP urządzenia** używa wątku, który jest uruchomiony po nawiązaniu połączenia z hostem USB. Wątek czeka na pakiet przychodzący w punkcie końcowym operacji zbiorczych na zewnątrz. Po otrzymaniu pakietu kopiuje zawartość do buforu punktu końcowego zbiorczego i publikuje transakcję w tym punkcie końcowym, czekając, aż host wyda żądanie odczytu z tego punktu końcowego. Zapewnia to mechanizm sprzężenia zwrotnego między punktami końcowymi operacji zbiorczych i zbiorczych.
