---
title: Rozdział 1 — Wprowadzenie do Azure RTOS stosu hosta USBX
description: W tym rozdziale oprowadzono stos hosta USBX, opisując jego aplikacje i korzyści.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: abe9b3e4f36a50af9c1267b2e6285b77feecd946660bf23691e70cb66f8bc042
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791004"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a>Rozdział 1 — Wprowadzenie do Azure RTOS stosu hosta USBX

USBX to w pełni funkcjonalny stos USB do aplikacji z głębokiego osadzoną pamięcią. W tym rozdziale oprowadzono USBX, opisując jego aplikacje i korzyści.

## <a name="usbx-features"></a>Funkcje USBX

UsbX obsługuje trzy istniejące specyfikacje USB: 1.1, 2.0 i OTG. Została zaprojektowana tak, aby była skalowalna i zawiera proste topologie USB z tylko jednym połączonym urządzeniem, a także złożone topologie z wieloma urządzeniami i kaskadami. UsbX obsługuje wszystkie typy transferu danych protokołów USB: sterowanie, zbiorcze, przerywanie i izochroniczne.

Dysk USBX obsługuje zarówno stronę hosta, jak i stronę urządzenia. Każda strona składa się z trzech warstw.

- Warstwa kontrolera
- Warstwa stosu
- Warstwa klasy

Relacja między warstwami USB jest następująca.

![Warstwy USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Najważniejsze informacje o produkcie

- Pełna obsługa procesora ThreadX
- Brak tantiemów
- Uzupełnij kod źródłowy ANSI C
- Wydajność w czasie rzeczywistym
- Elastyczna pomoc techniczna
- Obsługa wielu kontrolerów hosta
- Obsługa wielu klas
- Wiele wystąpień klas
- Integracja klas z ThreadX, FileX i NetX
- Obsługa urządzeń USB z wieloma konfiguracjami
- Obsługa złożonych urządzeń USB
- Obsługa centrów kaskadowych
- Obsługa zarządzania energią USB
- Obsługa portu USB OTG
- Eksportowanie zdarzeń śledzenia dla traceX

## <a name="powerful-services-of-usbx"></a>Zaawansowane usługi USBX

### <a name="multiple-host-controller-support"></a>Obsługa wielu kontrolerów hosta

UsbX może obsługiwać wiele kontrolerów hosta USB uruchomionych jednocześnie. Ta funkcja umożliwia USBX do obsługi standardu USB 2.0 przy użyciu schematu zgodności z poprzednimi wersjami skojarzonego z większości kontrolerów hostów USB 2.0 na rynku.

### <a name="usb-software-scheduler"></a>Harmonogram oprogramowania USB

UsbX zawiera harmonogram oprogramowania USB niezbędne do obsługi kontrolerów USB, które nie mają przetwarzania listy sprzętu. Harmonogram oprogramowania USBX zorganizuje transfery USB z prawidłową częstotliwością usługi i priorytetu i poinstruuje kontroler USB, aby wykonać każdy transfer.

### <a name="complete-usb-device-framework-support"></a>Pełna obsługa struktury urządzeń USB

UsbX może obsługiwać najbardziej wymagające urządzenia USB, w tym wiele konfiguracji, wiele interfejsów i wiele ustawień alternatywnych.

### <a name="easy-to-use-apis"></a>Łatwe w użyciu interfejsy API

USBX zapewnia bardzo najlepsze głęboko osadzony stos USB w sposób, który jest łatwy do zrozumienia i użycia. Interfejs API USBX sprawia, że usługi są intuicyjne i spójne. Korzystając z dostarczonych interfejsów API klasy USBX, aplikacja użytkownika nie musi rozumieć złożoności protokołów USB.
