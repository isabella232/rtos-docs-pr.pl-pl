---
title: Rozdział 1 — wprowadzenie do stosu hosta usługi Azure RTO USBX
description: USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji. W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ee49903e764e20316438be16b47d2d9208b1363
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824450"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a>Rozdział 1 — wprowadzenie do stosu hosta usługi Azure RTO USBX

USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji. W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści.

## <a name="usbx-features"></a>Funkcje USBX

USBX obsługiwać trzy istniejące specyfikacje USB: 1,1, 2,0 i OTG. Jest ona przeznaczona do skalowalności i będzie obsługiwać proste topologie USB z tylko jednym podłączonym urządzeniem, a także złożonymi topologiami z wieloma urządzeniami i kaskadowymi centrami. USBX obsługuje wszystkie typy transferu danych protokołów USB: Control, bulk, interrupt i Isochronous.

USBX obsługuje zarówno po stronie hosta, jak i po stronie urządzenia. Każda strona składa się z trzech warstw.

- Warstwa kontrolera
- Warstwa stosu
- Warstwa klasy

Relacje między warstwami USB są następujące.

![Warstwy USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Najważniejsze informacje o produkcie

- Ukończ obsługę procesora ThreadX
- Bez opłat
- Pełny kod źródłowy ANSI C
- Wydajność w czasie rzeczywistym
- Reagowanie na pomoc techniczną
- Obsługa wielu kontrolerów hosta
- Obsługa wielu klas
- Wiele wystąpień klasy
- Integracja klas z ThreadX, FileX i NetX
- Obsługa urządzeń USB z wieloma konfiguracjami
- Obsługa urządzeń złożonych USB
- Obsługa kaskadowych centrów
- Obsługa zarządzania mocą USB
- Obsługa OTG USB
- Eksportuj zdarzenia śledzenia dla TraceX

## <a name="powerful-services-of-usbx"></a>Zaawansowane usługi USBX

### <a name="multiple-host-controller-support"></a>Obsługa wielu kontrolerów hosta

USBX może obsługiwać wiele kontrolerów hosta USB uruchomionych współbieżnie. Ta funkcja umożliwia USBXom obsługę standardu USB 2,0 przy użyciu schematu zgodności z poprzednimi wersjami skojarzonego z większością kontrolerów USB 2,0 na rynku.

### <a name="usb-software-scheduler"></a>Harmonogram oprogramowania USB

USBX zawiera harmonogram oprogramowania USB, który jest wymagany do obsługi kontrolerów USB, które nie mają przetwarzania na liście sprzętowej. Harmonogram oprogramowania USBX zorganizuje transfery USB z poprawną częstotliwością usługi i priorytetem, a następnie nakazuje kontrolerowi USB wykonywanie każdego transferu.

### <a name="complete-usb-device-framework-support"></a>Pełna obsługa platformy USB

USBX może obsługiwać najbardziej wymagające urządzenia USB, w tym wiele konfiguracji, wiele interfejsów i wiele ustawień alternatywnych.

### <a name="easy-to-use-apis"></a>Łatwe w użyciu interfejsy API

USBX zapewnia bardzo najlepszy, głęboko osadzony stos USB w sposób, który jest łatwy do zrozumienia i użycia. Interfejs API USBX zapewnia intuicyjną i spójność usług. Korzystając z dostarczonych interfejsów API klasy USBX, aplikacja użytkownika nie musi zrozumieć złożoności protokołów USB.
