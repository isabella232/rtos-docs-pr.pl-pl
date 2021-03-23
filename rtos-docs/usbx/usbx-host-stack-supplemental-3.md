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
# <a name="chapter-3-usbx-dpump-class-considerations"></a><span data-ttu-id="b0d90-103">Rozdział 3: zagadnienia dotyczące klasy USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="b0d90-103">Chapter 3: USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="b0d90-104">USBX zawiera klasę DPUMP dla hosta i urządzenia.</span><span class="sxs-lookup"><span data-stu-id="b0d90-104">USBX contains a DPUMP class for the host and device side.</span></span> <span data-ttu-id="b0d90-105">Ta klasa nie jest klasą standardową w sobie, ale raczej przykładem, który ilustruje sposób tworzenia prostego urządzenia przy użyciu dwóch potoków zbiorczych i wysyłania danych z powrotem do tych dwóch potoków.</span><span class="sxs-lookup"><span data-stu-id="b0d90-105">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="b0d90-106">Klasa DPUMP może służyć do uruchomienia klasy niestandardowej lub starszych urządzeń RS232.</span><span class="sxs-lookup"><span data-stu-id="b0d90-106">The DPUMP class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="b0d90-107">Wykres przepływu DPUMP USB:</span><span class="sxs-lookup"><span data-stu-id="b0d90-107">USB DPUMP flow chart:</span></span>

![Wykres przepływu DPUMP USB](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a><span data-ttu-id="b0d90-109">Klasa hosta USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="b0d90-109">USBX DPUMP Host Class</span></span>

<span data-ttu-id="b0d90-110">Strona hosta klasy DPUMP ma dwie funkcje, jeden do wysyłania danych i jeden do odbioru danych:</span><span class="sxs-lookup"><span data-stu-id="b0d90-110">The host side of the DPUMP Class has two functions, one for sending data and one for receiving data:</span></span>

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

<span data-ttu-id="b0d90-111">Obie funkcje blokują, aby ułatwić aplikacji DPUMP.</span><span class="sxs-lookup"><span data-stu-id="b0d90-111">Both functions are blocking to make the DPUMP application easier.</span></span> <span data-ttu-id="b0d90-112">Jeśli konieczne jest uruchamianie obu potoków (w i OUT) w tym samym czasie, aplikacja będzie wymagana do utworzenia wątku przesyłania i wątku odbierania.</span><span class="sxs-lookup"><span data-stu-id="b0d90-112">If it is necessary to have both pipes (IN and OUT) running at the same time, the application will be required to create a transmit thread and a receive thread.</span></span>

<span data-ttu-id="b0d90-113">Prototyp funkcji pisania jest następujący:.</span><span class="sxs-lookup"><span data-stu-id="b0d90-113">The prototype for the writing function is as follows.</span></span>

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

<span data-ttu-id="b0d90-114">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="b0d90-114">Where:</span></span>

- <span data-ttu-id="b0d90-115">dpump jest wystąpieniem klasy</span><span class="sxs-lookup"><span data-stu-id="b0d90-115">dpump is the instance of the class</span></span>
- <span data-ttu-id="b0d90-116">data_pointer jest wskaźnikiem do buforu do wysłania</span><span class="sxs-lookup"><span data-stu-id="b0d90-116">data_pointer is the pointer to the buffer to be sent</span></span>
- <span data-ttu-id="b0d90-117">requested_length to długość do wysłania</span><span class="sxs-lookup"><span data-stu-id="b0d90-117">requested_length is the length to send</span></span>
- <span data-ttu-id="b0d90-118">actual_length jest długością wysłaną po zakończeniu transferu — pomyślnie lub częściowo.</span><span class="sxs-lookup"><span data-stu-id="b0d90-118">actual_length is the length sent after completion of the transfer, either successfully or partially.</span></span>

<span data-ttu-id="b0d90-119">Prototyp dla funkcji odbiorczej jest podobny.</span><span class="sxs-lookup"><span data-stu-id="b0d90-119">The prototype for the receiving function is similar.</span></span>

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

<span data-ttu-id="b0d90-120">Poniżej znajduje się przykład klasy DPUMP hosta, w której aplikacja zapisuje pakiet po stronie urządzenia i odbiera ten sam pakiet w odniesieniu:</span><span class="sxs-lookup"><span data-stu-id="b0d90-120">Here is an example of the host DPUMP class where an application writes a packet to the device side and receives the same packet on the reception:</span></span>

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

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="b0d90-121">Klasa urządzenia USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="b0d90-121">USBX DPUMP Device Class</span></span>

<span data-ttu-id="b0d90-122">Klasa Device DPUMP używa wątku uruchomionego po nawiązaniu połączenia z hostem USB.</span><span class="sxs-lookup"><span data-stu-id="b0d90-122">The device DPUMP class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="b0d90-123">Wątek czeka na pakiet w punkcie końcowym zbiorczym.</span><span class="sxs-lookup"><span data-stu-id="b0d90-123">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="b0d90-124">Po odebraniu pakietu program kopiuje zawartość do zbiorczo w buforze punktów końcowych i zapisuje transakcję w tym punkcie końcowym, czekając, aż Host wystawia żądanie odczytu z tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b0d90-124">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="b0d90-125">Zapewnia to mechanizm sprzężenia zwrotnego między zbiorczą i zbiorczo punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="b0d90-125">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
