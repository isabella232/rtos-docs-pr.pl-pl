---
title: Rozdział 1 — Wprowadzenie do Azure RTOS stosu urządzeń USBX
description: USBX to w pełni funkcjonalny stos USB do aplikacji z głębokiego osadzoną pamięcią. W tym rozdziale oprowadzono usbx opisujący jego zalety i zastosowanie.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 0ec49e88c8dcb8ca200bc376da2f33eb5ddac340bf3693368dc3508f68220765
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791469"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a>Rozdział 1 — Wprowadzenie do Azure RTOS stosu urządzeń USBX

USBX to w pełni funkcjonalny stos USB do aplikacji z głębokiego osadzoną pamięcią. W tym rozdziale oprowadzono usbx, opisując jego aplikacje i korzyści 

## <a name="usbx-features"></a>Funkcje USBX

UsbX obsługuje trzy istniejące specyfikacje USB: 1.1, 2.0 i OTG. Została zaprojektowana tak, aby była skalowalna i zawiera proste topologie USB z tylko jednym połączonym urządzeniem, a także złożone topologie z wieloma urządzeniami i kaskadami. UsbX obsługuje wszystkie typy transferu danych protokołów USB: sterowanie, zbiorcze, przerywanie i izochroniczne.

Dysk USBX obsługuje zarówno stronę hosta, jak i stronę urządzenia. Każda strona składa się z trzech warstw.

- Warstwa kontrolera
- Warstwa stosu
- Warstwa klasy

Relacja między warstwami USB jest następująca:

![Warstwy USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Najważniejsze informacje o produkcie

- Pełna obsługa procesora ThreadX
- Brak tantiemów
- Uzupełnij kod źródłowy ANSI C
- Wydajność w czasie rzeczywistym
- Elastyczna pomoc techniczna
- Obsługa wielu klas
- Wiele wystąpień klas
- Integracja klas z ThreadX, FileX i NetX
- Obsługa urządzeń USB z wieloma konfiguracjami
- Obsługa złożonych urządzeń USB
- Obsługa zarządzania energią USB
- Obsługa portu USB OTG
- Eksportowanie zdarzeń śledzenia dla traceX

## <a name="powerful-services-of-usbx"></a>Zaawansowane usługi USBX

### <a name="complete-usb-device-framework-support"></a>Pełna obsługa struktury urządzeń USB

UsbX może obsługiwać najbardziej wymagające urządzenia USB, w tym wiele konfiguracji, wiele interfejsów i wiele ustawień alternatywnych.

### <a name="easy-to-use-apis"></a>Łatwe w użyciu interfejsy API

USBX zapewnia najlepszy głęboko osadzony stos USB w sposób łatwy do zrozumienia i użycia. Interfejs API USBX sprawia, że usługi są intuicyjne i spójne. Korzystając z dostarczonych interfejsów API klasy USBX, aplikacja użytkownika nie musi rozumieć złożoności protokołów USB.
