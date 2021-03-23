---
title: Co to jest Microsoft Azure RTO?
description: Usługa Azure RTO to system operacyjny w czasie rzeczywistym (RTO) dla urządzeń IoT i brzegowych, które są obsługiwane przez mikrokontroler jednostek (MCUs).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3b1c63135f6069652d7f66fc976b9d770a4dfeb2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822501"
---
# <a name="what-is-microsoft-azure-rtos"></a>Co to jest Microsoft Azure RTO

Usługa Azure RTO to system operacyjny w czasie rzeczywistym (RTO) dla urządzeń IoT i brzegowych, które są obsługiwane przez mikrokontroler jednostek (MCUs). Usługa Azure RTO została zaprojektowana tak, aby obsługiwała najbardziej ograniczone urządzenia (zasilane z baterii i ma mniej niż 64 KB pamięci flash).
 
Usługa Azure RTO jest wstępnie certyfikowana dla różnych standardów zabezpieczeń. Obejmują one certyfikaty IEC 61508 SIL 4, IEC 62304 Class C i ISO 26262 ASIL D. Usługa Azure RTO ThreadX to również certyfikat 178.

Usługa Azure RTO udostępnia certyfikowane środowiska Criteria EAL4 + Common Security, w tym pełne zabezpieczenia warstwy IP za pośrednictwem protokołu IPsec i usługi Socket Layer Security za pośrednictwem protokołów TLS i DTLS. Nasza biblioteka kryptograficzna oprogramowania osiągnęła certyfikat FIPS 140-2. Wykorzystujemy również możliwości kryptograficzne sprzętowego, ochronę pamięci za pośrednictwem modułów ThreadX oraz obsługę funkcji zabezpieczeń TrustZone ARMv8-M usługi ARM.

## <a name="components-of-azure-rtos"></a>Składniki platformy Azure RTO

Platforma Azure RTO to kolekcja rozwiązań w czasie wykonywania, w tym Azure RTO ThreadX, Azure RTO FileX, Azure RTO GUIX, Azure RTO NetX, Azure RTO NetX Duo i Azure RTO USBX.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

System ThreadX usługi Azure RTOS to zaawansowany system operacyjny czasu rzeczywistego zaprojektowany specjalnie pod kątem głęboko osadzonych aplikacji. Wśród wielu zalet usługi Azure RTO ThreadX dostępne są zaawansowane funkcje planowania, przekazywania komunikatów, zarządzania przerwami i obsługi komunikatów. Usługa Azure RTO ThreadX ma wiele zaawansowanych funkcji, w tym jej architekturę picokernel, planowanie progu zastępujące, łańcuchy zdarzeń i bogaty zestaw usług systemowych.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Usługa Azure RTO FileX to system plików zgodny z systemem FAT o wysokiej wydajności. Jest ona w pełni zintegrowana z usługą Azure RTO ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów. Podobnie jak w przypadku platformy Azure RTO ThreadX, usługa Azure RTO FileX została zaprojektowana tak, aby miała niewielki rozmiar i wysoką wydajność, dzięki czemu jest idealnym rozwiązaniem dla współczesnych aplikacji, które wymagają operacji na plikach. Usługa Azure RTO FileX obsługuje większość nośników fizycznych, w tym dysk RAM, USBX, kartę SD i ni/lub Flash, za pośrednictwem platformy Azure RTO LevelX.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure RTO GUIX to pakiet profesjonalnego interfejsu użytkownika o wysokiej jakości, który został utworzony w celu spełnienia wymagań deweloperów systemów osadzonych. W przeciwieństwie do alternatyw, usługa Azure RTO GUIX jest mała, szybka i łatwa w obsłudze w praktycznie dowolnej konfiguracji sprzętowej obsługującej graficzne wyjście. Usługa Azure RTO GUIX zapewnia również wyjątkową atrakcyjność wizualną oraz intuicyjny i zaawansowany interfejs API do tworzenia interfejsu użytkownika na poziomie aplikacji.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Usługa Azure RTO NetX to implementacja standardów protokołów TCP/IP o wysokiej wydajności. Jest ona w pełni zintegrowana z usługą Azure RTO ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów. Usługa Azure RTO NetX ma unikatową architekturę Piconet. W połączeniu z interfejsem API o zerowej kopii jest to idealne rozwiązanie dla współczesnych aplikacji, które wymagają łączności sieciowej.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Usługa Azure RTO NetX Duo to zaawansowane stosy sieci TCP/IP klasy przemysłowej zaprojektowane specjalnie dla aplikacji głęboko osadzonych, w czasie rzeczywistym i IoT. Azure RTO NetX Duo to stos sieciowy z podwójnym protokołem IPv4 i IPv6, natomiast NetX to oryginalny stos sieciowy IPv4, w rzeczywistości z podzbiorem platformy Azure RTO NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure RTO USBX to osadzony stos hosta USB o wysokiej wydajności, urządzenia i na platformie (OTG). Jest ona w pełni zintegrowana z usługą ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów platformy Azure RTO ThreadX. Podobnie jak w przypadku platformy Azure RTO ThreadX, usługa Azure RTO USBX została zaprojektowana tak, aby miała niewielki rozmiar i wysoką wydajność, dzięki czemu jest idealnym rozwiązaniem dla aplikacji głęboko osadzonych, które wymagają interfejsu z urządzeniami USB.

### <a name="windows-tools"></a>Narzędzia systemu Windows

Usługa Azure RTO GUIX Studio zapewnia kompletne środowisko projektowania aplikacji graficznego interfejsu użytkownika, ułatwiając tworzenie i konserwację wszystkich elementów graficznych w graficznym interfejsie użytkownika aplikacji. Usługa Azure RTO GUIX Studio automatycznie generuje kod C zgodny z biblioteką GUIX RTO platformy Azure, gotowy do skompilowania i uruchomienia w miejscu docelowym.

Azure RTO TraceX to narzędzie do analizy oparte na hoście, które udostępnia deweloperom graficzny widok zdarzeń systemu w czasie rzeczywistym i pozwala im wizualizować i lepiej zrozumieć zachowanie systemów w czasie rzeczywistym.

## <a name="in-the-context-of-azure-iot"></a>W kontekście usługi Azure IoT

Oprócz bezpośredniego łączenia się z usługą Azure IoT lub pośredniego nawiązywania połączenia za pomocą Azure IoT Edge usługa Azure RTO jest również dostępna na urządzeniach Azure Sphere. Połączenie usługi Azure RTO i Azure Sphere zapewniają najlepsze w klasie przetwarzanie w czasie rzeczywistym i zabezpieczenia w jednym urządzeniu.
