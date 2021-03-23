---
title: Opis usługi Azure RTO USBX
description: Azure RTO USBX to osadzony stos hosta USB o wysokiej wydajności, urządzenia i (OTG), usługa Azure RTO USBX jest w pełni zintegrowana z platformą Azure RTO ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów platformy Azure RTO ThreadX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 87eb6ee9f8733db3201280d377aa832b87131871
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824373"
---
# <a name="overview-of-azure-rtos-usbx"></a>Omówienie usługi Azure RTO USBX

Azure RTO USBX to osadzony stos hosta USB o wysokiej wydajności, urządzenia i na platformie (OTG). Usługa Azure RTO USBX jest w pełni zintegrowana z platformą Azure RTO ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów. Podobnie jak w przypadku ThreadX, usługa Azure RTO USBX została zaprojektowana tak, aby miała niewielki rozmiar i wysoką wydajność, dzięki czemu idealnie sprawdza się w przypadku aplikacji, które wymagają interfejsu z urządzeniami USB.

## <a name="host-device-otg--extensive-class-support"></a>Obsługa usług host, Device i OTG & rozbudowanej klasy

Azure RTO USBX Host/Embedded USB Device Stack to rozwiązanie klasy przemysłowej Embedded USB zaprojektowane specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i IoT. Usługa Azure RTO USBX zapewnia obsługę hostów, urządzeń i OTG, a także rozbudowaną obsługę klas. Usługa Azure RTO USBX jest w pełni zintegrowana z systemami operacyjnymi ThreadX Real-Time, Azure RTO FileX Embedded, zgodnym z systemem plików, Azure RTO NetX i Azure RTO NetX Duo. Wszystko to, w połączeniu z bardzo małym zasięgiem, szybkim przeprowadzeniem i najbardziej łatwym w użyciu, dzięki czemu usługa Azure RTO USBX idealny wybór dla najbardziej wymagających aplikacji IoT, które wymagają połączenia USB.

### <a name="small-footprint"></a>Niewielkie rozmiary

Usługa Azure RTO USBX oferuje niezwykleą minimalną ilość pamięci (10,5 KB) na platformie FLASH i 5,1 KB w przypadku urządzeń z systemem Azure RTO USBX. Host usługi Azure RTO USBX wymaga co najmniej 18 KB rozmiaru FLASH i 25 KB pamięci RAM na potrzeby obsługi funkcji przechwytywania danych/ACM.

Do obsługi funkcji TCP jest wymagana dodatkowa ilość pamięci o wartości 10 KB do 13 KB. Użycie pamięci RAM usługi Azure RTO USBX zazwyczaj mieści się w zakresie od 2,6 KB do 3,6 KB oraz pamięci puli pakietów zdefiniowanej przez aplikację.

Podobnie jak w przypadku ThreadX, rozmiar usługi Azure RTO USBX automatycznie skaluje się w oparciu o usługi faktycznie używane przez aplikację. To praktycznie eliminuje konieczność tworzenia skomplikowanych parametrów konfiguracji i kompilacji, co ułatwia deweloperom.

### <a name="fast-execution"></a>Szybkie wykonywanie

Usługa Azure RTO USBX została zaprojektowana z założeniami, aby zapewnić szybkość i minimalną międzyplatformową wywołań funkcji oraz obsługę pamięci podręcznej i użycia DMA. Wszystkie te i ogólne zasady projektowania zorientowane na wydajność ułatwiają platformie Azure RTO USBX osiąganie najszybszej możliwej wydajności.

### <a name="simple-easy-to-use"></a>Proste i łatwe w użyciu

Korzystanie z usługi Azure RTO USBX jest proste. Interfejs API usługi Azure RTO USBX jest intuicyjny i wysoce funkcjonalny. Nazwy interfejsów API są prawdziwe mówiące i nie są nazwami "zup alfabetu" ani o dużej liczbie skróconych, które są często używane w innych produktach systemu plików. Wszystkie interfejsy API usługi Azure RTO USBX mają wiodące "ux_" i są zgodne z konwencją nazewnictwa czasowników. Ponadto istnieje spójność funkcjonalna w całym interfejsie API. Na przykład wszystkie interfejsy API, które zawieszają się, mają opcjonalny limit czasu, który działa w taki sam sposób w przypadku interfejsów API.

### <a name="usb-interoperability-verification"></a>Weryfikacja współdziałania USB

Stos urządzeń usługi Azure RTO USBX został rygorystycznie przetestowany przy użyciu USB, jeśli standardowe narzędzie testowania USBCV zapewnia pełną zgodność z specyfikacjami USB i współdziałaniem z różnymi systemami hosta.
Ponadto usługa Azure RTO USBX OTG Stack została zweryfikowana i certyfikowana przez niezależne laboratorium testowe Allion w Tajwanie.

### <a name="usb-host-controller-support"></a>Obsługa kontrolera hosta USB

Usługa Azure RTO USBX obsługuje główne standardy USB, takie jak OHCI i EHCI. Ponadto usługa Azure RTO USBX obsługuje zastrzeżone odrębne kontrolery hosta USB z Atmel, mikrochipu, Philips, Renesas, ST, TI i innych dostawców. Usługa Azure RTO USBX obsługuje również wiele kontrolerów hosta w tej samej aplikacji.
Kontroler urządzenia USB obsługujący usługę Azure RTO USBX obsługuje popularne kontrolery urządzeń USB z urządzeń analogowych, Atmel, chip, NXP, Philips, Renesas, ST, TI i innych dostawców.

### <a name="extensive-host-class-support"></a>Obsługa rozbudowanej klasy hosta

Host usługi Azure RTO USBX zapewnia obsługę większości popularnych klas, w tym ASIX, AUDIO, przełączeń/ACM, przełączenia/ECM, GSER, HID (klawiatura, mysz i zdalne sterowanie), HUB, PIMA (PTP/MTP), drukarka, mnóstwo i magazyn.

### <a name="extensive-usb-device-class-support"></a>Obsługa rozbudowanej klasy urządzeń USB

Usługa Azure RTO USBX zapewnia obsługę większości popularnych klas, w tym przechwytywania zmian/ACM, przechwytywania/ECM, DFU, HID, PIMA (PTP/MTP) (z/MTP), RNDIS i STORAGE. Dostępna jest również obsługa klas niestandardowych.

### <a name="pictbridge-support"></a>Obsługa technologii PictBridge

Usługa Azure RTO USBX obsługuje pełną implementację technologii PictBridge zarówno na hoście, jak i na urządzeniu. Usługa PictBridge znajduje się na szczycie klasy RTO USBX PIMA (PTP/MTP) na obu stronach. Standard PictBridge umożliwia połączenie cyfrowego aparatu fotograficznego lub inteligentnego telefonu bezpośrednio z drukarką bez komputera, co umożliwia bezpośrednie drukowanie na określonych drukarkach z obsługą technologii PictBridge. Gdy do drukarki jest podłączony aparat lub telefon, drukarka jest hostem USB, a aparat jest urządzeniem USB. Jednak w przypadku technologii PictBridge aparat będzie wyświetlany jako host, a polecenia są sterowane przez aparat. Aparat jest serwerem magazynu, drukarką klienta magazynu. Aparat jest klientem drukowania, a drukarka jest oczywiście serwerem wydruku. PictBridge korzysta z portów USB jako warstwy transportowej, ale korzysta z protokołu PTP (Picture Transfering Protocol) dla protokołu komunikacyjnego.

### <a name="custom-class-support"></a>Obsługa klasy niestandardowej

Hosty i urządzenia usługi Azure RTO USBX obsługują klasy niestandardowe. Przykładowa Klasa niestandardowa jest udostępniana w dystrybucji USBX usługi Azure RTO. Ta prosta Klasa pompy danych jest nazywana DPUMP i może być używana jako model niestandardowych klas aplikacji.
Zaawansowane technologie Azure RTO USBX Host i Device obsługują klasy niestandardowe. Przykładowa Klasa niestandardowa jest udostępniana w dystrybucji USBX usługi Azure RTO. Usługa Azure RTO USBX jest zaawansowaną technologią obejmującą następujące możliwości:

* Obsługa hostów, urządzeń i OTG
* Obsługa niskich, pełnych i szybkich szybkości USB
* Automatyczne skalowanie
* W pełni zintegrowane z ThreadX, Azure RTO FileX i Azure RTO NetX
* Opcjonalne metryki wydajności
* Obsługa analizy systemu Azure RTO TraceX

### <a name="fastest-time-to-market"></a>Najszybszy czas wprowadzenia na rynek

Usługa Azure RTO USBX ma niewielki zasięg z 9 KB do 15 KB w przypadku podstawowej obsługi protokołów IP i UDP. Usługa Azure RTO USBX umożliwia łatwe instalowanie, uczenie się, używanie, debugowanie, weryfikowanie, certyfikowanie i konserwowanie. W związku z tym usługa Azure RTO USBX jest jednym z najpopularniejszych rozwiązań USB dla osadzonych urządzeń IoT. Nasza spójna przedział czasu na rynek jest oparta na:

* Dokumentacja dotycząca jakości — zapoznaj się z naszymi przewodnikami użytkownika i hosta usługi Azure RTO USBX
* Ukończ dostępność kodu źródłowego
* Łatwy w użyciu interfejs API
* Kompleksowy i zaawansowany zestaw funkcji

## <a name="one-simple-license"></a>Jedna prosta licencja

Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.

## <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy o najwyższej jakości

W ciągu lat kod źródłowy usługi Azure RTO NetX ustawił na pasku jakość i łatwość interpretacji. Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.

### <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Usługa Azure RTO USBX działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, w tym:

* **Urządzenia analogowe**: SHARC, Blackfin, CM4xx
* **Andes rdzeń**: RISC-V
* **Ambiqmicro**: Apollo MCUs
* **ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M
* **Erze**: Xtensa, romb
* **Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi
* **Cypress**: RISC-V
* **EnSilica**: ESI-RISC
* **Infineon**: XMC1000, XMC4000, TriCore
* **Intel & Intel FPGA**: X36/Pentium, XScale, Nios II, Cyclone, Arria 10
* **Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32
* **Mikrośrednik**: RISC-V
* **NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, ColdFire, Kinetis Cortex-M3/M4
* **Renesas**: sh, HS, V850, RX, rz, synergia Silicon Labs: EFM32
* **SynopSYS**: Arc 600, 700, łuk em, łuk HS
* **St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7
* **: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C
* **Przetwarzanie Wave**: MIPS32 4K, 24 k, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

## <a name="azure-rtos-usbx-apis"></a>Interfejsy API usługi Azure RTO USBX

### <a name="azure-rtos-usbx-host-api"></a>Interfejs API hosta usługi Azure RTO USBX

Interfejs API hosta usługi Azure RTO USBX to intuicyjny i spójny interfejs API, zgodnie z konwencją nazewnictwa czasowników. Wszystkie interfejsy API mają wiodące ux_host_ *, aby łatwo identyfikować jako USBX. Wszystkie blokowane interfejsy API mają opcjonalny limit czasu wątku.

* ASIX
    - Minimum 0,3 KB, 4 KB pamięci RAM
    - Automatyczne śledzenie na poziomie scalingSystem za pomocą usługi Azure RTO TraceX
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_asix_**
* DŹWIĘKU
    - Minimum 1,2 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_audio_**
* PRZECHWYTYWANIE ZMIAN/ACM
    - Minimum 1,4 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_cdc_acm_**
* INTERFEJSU
    - Minimum 0,3 KB, 4 KB pamięci RAM
    - Klawiatura, mysz i pomoc zdalna
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_hid_** 
* Centralny
    - Minimum 1,7 KB, 2 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_hub_**
* PIMA (PTP/MTP)
    - Minimum 0,9 KB, 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_pima_**
* URZĄDZENIE
    - Minimum 0,8 KB, 8 KB pamięci RAM
    - Automatyczne skalowanie
    -  Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    -  Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_printer_**
* MNÓSTWO
    - Minimum 1,5 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_prolific_**
* Fold
    - Minimum 5,6 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie<br> Integracja z usługą Azure RTO FileX
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_class_storage_**
* STOS hosta USB
    - Obsługuje wiele kontrolerów hosta
    - Minimum 18 KB, 25 KB pamięci RAM
    - Automatyczne skalowanie
    - Obsługa wielu kontrolerów hosta na tej samej platformie
    -  Obsługa niskich, pełnych i szybkich szybkości USB
    -  Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    -  Intuicyjne interfejsy API hosta usługi Azure RTO USBX w tej formie: *ux_host_stack_* * 
* KONTROLERY hosta OHCI, EHCI, własności 

### <a name="azure-rtos-usbx-device-api"></a>Interfejs API urządzenia usługi Azure RTO USBX

Interfejs API urządzenia usługi Azure RTO USBX jest intuicyjnym i spójnym interfejsem API po konwencji nazewnictwa czasowników. Wszystkie interfejsy API mają wiodące ux_device_ *, aby łatwo identyfikować jako USBX. Blokowanie interfejsów API ma opcjonalny limit czasu wątku. Więcej informacji można znaleźć w [podręczniku użytkownika hosta usługi Azure RTO USBX](usbx-host-stack-about.md) .

* PRZECHWYTYWANIE ZMIAN/ACM
    - Minimum 0,8 KB, 2 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: * ux_device_class_cdc_acm_ * *.
* PRZECHWYTYWANIE ZMIAN/ECM
    - Minimum 1,5 KB, 4 KB do 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX<br> Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: * ux_device_class_cdc_ecm_ * *.
* DFU
    - Minimum 1,1 KB, 2 KB pamięci RAM
    -  Automatyczne skalowanie
    -  Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: *ux_device_class_dfu_** 
* GSER
    - Minimum 0,6 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: *ux_device_class_gser_**
* INTERFEJSU
    - Minimum 0,9 KB, 2 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: *ux_device_class_hid_** Pima (PTP/MTP)
    - Minimum 5,2 KB, 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: *ux_device_class_pima_** 
* MAGAZYN
    - Minimum 2,3 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: *ux_device_class_storage_**
* RNDIS
    - Minimum 2,3 KB, 4 KB do 8 KB pamięci RAM
    - Automatyczne skalowanie
    - Integracja z usługami Azure RTO NetX i Azure RTO NetX DUO
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: *ux_device_class_rndls_**
* STOS urządzeń usługi Azure RTO USBX
    - Minimum 2,3 KB, 4 KB pamięci RAM
    - Automatyczne skalowanie
    - Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
    - Intuicyjne interfejsy API urządzeń z usługą Azure RTO USBX w tej formie: *ux_device_class_storage_**
* WŁASNOŚCIowe kontrolery hosta

## <a name="next-steps"></a>Następne kroki

Rozpocznij pracę z hostem USBX i stosem urządzeń na platformie Azure RTO, postępując zgodnie z [przewodnikiem użytkownika stosu hosta](usbx-host-stack-about.md) lub [przewodnikiem użytkownika stosu urządzeń](usbx-device-stack-about.md).