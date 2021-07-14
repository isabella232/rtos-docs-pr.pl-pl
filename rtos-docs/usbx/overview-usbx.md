---
title: Opis Azure RTOS USBX
description: Azure RTOS USBX jest wysokiej wydajności hosta USB, urządzenia i na-go (OTG) osadzony stos, Azure RTOS USBX jest w pełni zintegrowany z systemem Azure RTOS ThreadX i dostępne dla wszystkich procesorów obsługiwanych przez Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3c214a49f7dd1af20c20f07412fb072dd785b16f
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754832"
---
# <a name="overview-of-azure-rtos-usbx"></a>Omówienie Azure RTOS USBX

Azure RTOS USBX to wysokiej wydajności host USB, urządzenie i wbudowany stos na urządzeniu (OTG). Azure RTOS USBX jest w pełni zintegrowany z Azure RTOS ThreadX i jest dostępny dla wszystkich procesorów obsługiwanych przez ThreadX. Podobnie jak ThreadX, Azure RTOS USBX zaprojektowano tak, aby mieć niewielki rozmiar i wysoką wydajność, dzięki czemu idealnie nadaje się do aplikacji z głębokiej osadzoną pamięcią, które wymagają interfejsu z urządzeniami USB.

## <a name="host-device-otg--extensive-class-support"></a>Host, urządzenie, OTG & rozbudowana obsługa klas

Azure RTOS usbx hosta/urządzenia osadzony stos protokołu USB to rozwiązanie USB klasy przemysłowej przeznaczone specjalnie dla aplikacji z głębokiego osadzoną, w czasie rzeczywistym i IoT. Azure RTOS USBX zapewnia obsługę hosta, urządzenia i OTG, a także rozbudowane wsparcie klasy. Azure RTOS USBX jest w pełni zintegrowany z systemem operacyjnym ThreadX Real-Time, osadzonym systemem plików FAT systemu plików Azure RTOS FileX, osadzonymi stosami TCP/IP Azure RTOS NetX i Azure RTOS NetX Duo. Wszystko to, w połączeniu z bardzo małym zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia, sprawiają, że Azure RTOS USBX jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT wymagających łączności USB.

### <a name="usbx-memory-footprint"></a>Zużycie pamięci USBX

Azure RTOS USBX ma bardzo małe minimalne zużycie 10,5 KB pamięci FLASH i 5,1 KB pamięci RAM dla Azure RTOS USBX urządzenia CDC/ACM obsługi. Azure RTOS usbx wymaga co najmniej 18 KB pamięci FLASH i 25 KB pamięci RAM do obsługi CDC/ACM.

Dodatkowa pamięć obszaru instrukcji o rozmiarze od 10 KB do 13 KB jest potrzebna na potrzeby funkcji protokołu TCP. Azure RTOS pamięci RAM USBX zwykle obejmuje zakres od 2,6 KB do 3,6 KB oraz pamięć puli pakietów, która jest definiowana przez aplikację.

Podobnie jak ThreadX, rozmiar Azure RTOS USBX jest automatycznie skalowany na podstawie usług faktycznie używanych przez aplikację. W ten sposób praktycznie nie ma potrzeby skomplikowanej konfiguracji i parametrów kompilacji, co ułatwia deweloperom pracę.

### <a name="usb-interoperability-verification"></a>Weryfikacja współdziałania USB

Azure RTOS stos urządzeń USBX został rygorystycznie przetestowany za pomocą standardowego narzędzia do testowania USB IF USBCV w celu zapewnienia pełnej zgodności ze specyfikacjami USB i współdziałania z różnymi systemami hosta.
Ponadto stos Azure RTOS USBX OTG został zweryfikowany i certyfikowany przez niezależne laboratorium testowe Allion w Chinach.

### <a name="usb-host-controller-support"></a>Obsługa kontrolera hosta USB

Azure RTOS USBX obsługuje główne standardy USB, takie jak OHCI i EHCI. Ponadto system Azure RTOS USBX obsługuje zastrzeżone dyskretne kontrolery hosta USB firm Atmel, Microchip, Marks, Renesas, ST, TI i innych dostawców. Azure RTOS USBX obsługuje również wiele kontrolerów hostów w tej samej aplikacji.
Obsługa kontrolerów urządzeń USB Azure RTOS USBX obsługuje popularne kontrolery urządzeń USB z urządzeń analogowych, Atmel, Microchip, NXP,Zeni, Renesas, ST, TI i innych dostawców.

### <a name="extensive-host-class-support"></a>Rozbudowana obsługa klas hostów

Azure RTOS HOST USBX zapewnia obsługę najbardziej popularnych klas, w tym ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (klawiatura, mysz i zdalne sterowanie), HUB, PIMA (PTP/MTP), PRINTER, PROLIFIC i STORAGE.

### <a name="extensive-usb-device-class-support"></a>Rozbudowana obsługa klas urządzeń USB

Azure RTOS USBX zapewnia obsługę najpopularniejszych klas, w tym CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (w/MTP), RNDIS i STORAGE. Dostępna jest również obsługa klas niestandardowych.

### <a name="pictbridge-support"></a>Obsługa aplikacji Pictbridge

Azure RTOS USBX obsługuje pełną implementację pictbridge zarówno na hoście, jak i na urządzeniu. Pictbridge znajduje się na Azure RTOS USBX PIMA (PTP/MTP) po obu stronach. Standard PictBridge umożliwia połączenie cyfrowego aparatu fotograficznego lub inteligentnego telefonu bezpośrednio z drukarką bez komputera, umożliwiając bezpośrednie drukowanie do niektórych drukarek z systemem Pictbridge. Gdy aparat lub telefon jest podłączony do drukarki, drukarka jest hostem USB, a aparat jest urządzeniem USB. Jednak dzięki aplikacji Pictbridge aparat będzie wyświetlany jako host, a polecenia są sterowane z aparatu. Aparat jest serwerem magazynu, czyli drukarką klienta magazynu. Aparat jest klientem drukowania, a drukarką jest oczywiście serwer wydruku. Pictbridge używa USB jako warstwy transportu, ale opiera się na PTP (Picture Transfer Protocol) dla protokołu komunikacyjnego.

### <a name="custom-class-support"></a>Obsługa klas niestandardowych

Azure RTOS hostÓW USBX i urządzenia obsługują klasy niestandardowe. Przykładowa klasa niestandardowa jest dostarczana w Azure RTOS dystrybucji USBX. Ta prosta klasa pompy danych nosi nazwę DPUMP i może służyć jako model dla niestandardowych klas aplikacji.
Zaawansowana technologia Azure RTOS hostów USBX i urządzeń obsługuje klasy niestandardowe. Przykładowa klasa niestandardowa jest dostarczana w Azure RTOS dystrybucji USBX. Azure RTOS USBX to zaawansowana technologia, która obejmuje:

* Obsługa hosta, urządzenia i usługi OTG
* Obsługa usb o niskiej, pełnej i dużej szybkości
* Automatyczne skalowanie
* W pełni zintegrowane z ThreadX, Azure RTOS FileX i Azure RTOS NetX
* Opcjonalne metryki wydajności
* Azure RTOS analizy systemu TraceX

## <a name="azure-rtos-usbx-apis"></a>Azure RTOS INTERFEJSÓW API USBX

### <a name="azure-rtos-usbx-host-api"></a>Azure RTOS interfejsu API hosta USBX

Interfejs API Azure RTOS USBX jest intuicyjnym i spójnym interfejsem API zgodnym z konwencją nazewnictwa rzeczowników. Wszystkie interfejsy API mają wiodące ux_host_* do łatwego identyfikowania jako USBX. Wszystkie blokujące interfejsy API mają opcjonalny limit czasu wątku.

* ASIX
    - Minimalna 0,3 KB pamięci FLASH, 4 KB pamięci RAM
    - Automatyczne skalowanieŚledzenia na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_asix_**
* Audio
    - Minimalna pamięć FLASH 1,2 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_audio_**
* CDC/ACM
    - Minimalna pamięć FLASH 1,4 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_cdc_acm_**
* Hid
    - Minimalna 0,3 KB pamięci FLASH, 4 KB pamięci RAM
    - Klawiatura, mysz i zdalna obsługa
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_hid_** 
* Koncentratora
    - Minimalna pamięć FLASH 1,7 KB, 2 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_hub_**
* PIMA (PTP/MTP)
    - Minimalna 0,9 KB pamięci FLASH, 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_pima_**
* Drukarki
    - Minimalna 0,8 KB pamięci FLASH, 8 KB pamięci RAM
    - Automatyczne skalowanie
    -  Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    -  Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_printer_**
* Płodny
    - Minimalna 1,5 KB pamięci FLASH, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_prolific_**
* STORAG
    - Minimalna 5,6 KB pamięci FLASH, 4 KB pamięci RAM
    - Automatyczne skalowanie<br> Integracja z Azure RTOS FileX
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_class_storage_**
* STOS HOSTA USB
    - Obsługuje wiele kontrolerów hosta
    - Minimalna 18 KB pamięci FLASH, 25 KB pamięci RAM
    - Automatyczne skalowanie
    - Obsługa wielu kontrolerów hostów na tej samej platformie
    -  Obsługa usb o niskiej, pełnej i dużej szybkości
    -  Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    -  Intuicyjne Azure RTOS interfejsów API hosta USBX w tej postaci: *ux_host_stack_* * 
* OHCI, EHCI, ZASTRZEŻONE KONTROLERY hostÓW 

### <a name="azure-rtos-usbx-device-api"></a>Azure RTOS interfejsu API urządzenia USBX

Interfejs API Azure RTOS USBX jest intuicyjnym i spójnym interfejsem API zgodnym z konwencją nazewnictwa rzeczownikowego. Wszystkie interfejsy API mają wiodące ux_device_* do łatwego identyfikowania jako USBX. Blokujące interfejsy API mają opcjonalny limit czasu wątku. Zobacz Azure RTOS [użytkownika hosta USBX,](usbx-host-stack-about.md) aby uzyskać więcej informacji.

* CDC/ACM
    - Minimalna 0,8 KB pamięci FLASH, 2 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_cdc_acm_**.
* CDC/ECM
    - Minimalna pamięć FLASH 1,5 KB, od 4 KB do 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX<br> Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_cdc_ecm_**.
* Dfu
    - Minimalna 1,1 KB pamięci FLASH, 2 KB pamięci RAM
    -  Automatyczne skalowanie
    -  Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_dfu_** 
* GSER
    - Minimalna pamięć FLASH 0,6 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS INTERFEJSY API urządzenia USBX w tej postaci: *ux_device_class_gser_**
* Hid
    - Minimalna 0,9 KB pamięci FLASH, 2 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_hid_** PIMA (PTP/MTP)
    - Minimalna 5,2 KB pamięci FLASH, 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_pima_** 
* MAGAZYN
    - Minimalna 2,3 KB pamięci FLASH, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_storage_**
* Rndis
    - Minimalna pamięć FLASH 2,3 KB, od 4 KB do 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Integracja z Azure RTOS NetX i Azure RTOS NetX DUO
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_rndls_**
* Azure RTOS stosu urządzenia USBX
    - Minimalna 2,3 KB pamięci FLASH, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
    - Intuicyjne Azure RTOS interfejsów API urządzenia USBX w tej postaci: *ux_device_class_storage_**
* ZASTRZEŻONE KONTROLERY HOSTÓW

## <a name="next-steps"></a>Następne kroki

Rozpocznij pracę z hostem Azure RTOS USBX i [](usbx-host-stack-about.md) stosem urządzeń, korzystając z podręcznika użytkownika stosu hosta lub podręcznika [użytkownika stosu urządzeń.](usbx-device-stack-about.md)