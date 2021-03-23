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
# <a name="chapter-3---usbx-dpump-class-considerations"></a><span data-ttu-id="046e9-104">Rozdział 3 — zagadnienia dotyczące klasy USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="046e9-104">Chapter 3 - USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="046e9-105">USBX zawiera klasę **DPUMP** dla hosta i urządzenia.</span><span class="sxs-lookup"><span data-stu-id="046e9-105">USBX contains a **DPUMP** class for the host and device side.</span></span> <span data-ttu-id="046e9-106">Ta klasa nie jest klasą standardową w sobie, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych z powrotem do tych dwóch potoków.</span><span class="sxs-lookup"><span data-stu-id="046e9-106">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="046e9-107">Klasa **DPUMP** może służyć do uruchomienia klasy niestandardowej lub starszych urządzeń RS232.</span><span class="sxs-lookup"><span data-stu-id="046e9-107">The **DPUMP** class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="046e9-108">Wykres przepływu DPUMP USB:</span><span class="sxs-lookup"><span data-stu-id="046e9-108">USB DPUMP flow chart:</span></span>

![Wykres przepływu DPUMP USB](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="046e9-110">Klasa urządzenia USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="046e9-110">USBX DPUMP Device Class</span></span>

<span data-ttu-id="046e9-111">Klasa Device **DPUMP** używa wątku uruchomionego po nawiązaniu połączenia z hostem USB.</span><span class="sxs-lookup"><span data-stu-id="046e9-111">The device **DPUMP** class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="046e9-112">Wątek czeka na pakiet w punkcie końcowym zbiorczym.</span><span class="sxs-lookup"><span data-stu-id="046e9-112">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="046e9-113">Po odebraniu pakietu program kopiuje zawartość do zbiorczo w buforze punktów końcowych i zapisuje transakcję w tym punkcie końcowym, czekając, aż Host wystawia żądanie odczytu z tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="046e9-113">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="046e9-114">Zapewnia to mechanizm sprzężenia zwrotnego między zbiorczą i zbiorczo punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="046e9-114">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
