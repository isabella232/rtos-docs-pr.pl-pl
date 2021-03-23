---
title: Rozdział 3 — zagadnienia dotyczące klasy USBX DPUMP
description: USBX zawiera klasę DPUMP dla hosta i urządzenia. Ta klasa nie jest klasą standardową w sobie, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych do tych dwóch potoków.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c7870f1984fe3104d30e3b9efd82010218acbe27
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824517"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a>Rozdział 3 — zagadnienia dotyczące klasy USBX DPUMP

USBX zawiera klasę **DPUMP** dla hosta i urządzenia. Ta klasa nie jest klasą standardową w sobie, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych z powrotem do tych dwóch potoków. Klasa **DPUMP** może służyć do uruchomienia klasy niestandardowej lub starszych urządzeń RS232.

Wykres przepływu DPUMP USB:

![Wykres przepływu DPUMP USB](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>Klasa urządzenia USBX DPUMP

Klasa Device **DPUMP** używa wątku uruchomionego po nawiązaniu połączenia z hostem USB. Wątek czeka na pakiet w punkcie końcowym zbiorczym. Po odebraniu pakietu program kopiuje zawartość do zbiorczo w buforze punktów końcowych i zapisuje transakcję w tym punkcie końcowym, czekając, aż Host wystawia żądanie odczytu z tego punktu końcowego. Zapewnia to mechanizm sprzężenia zwrotnego między zbiorczą i zbiorczo punktami końcowymi.
