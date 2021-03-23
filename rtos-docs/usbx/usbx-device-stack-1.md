---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO USBX Stack
description: USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji. W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824528"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO USBX Stack

USBX to w pełni funkcjonalny stos USB dla głęboko osadzonych aplikacji. W tym rozdziale wprowadzono USBX opisujące swoje aplikacje i korzyści 

## <a name="usbx-features"></a>Funkcje USBX

USBX obsługuje trzy istniejące specyfikacje USB: 1,1, 2,0 i OTG. Jest ona przeznaczona do skalowalności i będzie obsługiwać proste topologie USB z tylko jednym podłączonym urządzeniem, a także złożonymi topologiami z wieloma urządzeniami i kaskadowymi centrami. USBX obsługuje wszystkie typy transferu danych protokołów USB: Control, bulk, interrupt i Isochronous.

USBX obsługuje zarówno po stronie hosta, jak i po stronie urządzenia. Każda strona składa się z trzech warstw.

- Warstwa kontrolera
- Warstwa stosu
- Warstwa klasy

Relacje między warstwami USB są następujące:

![Warstwy USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Najważniejsze informacje o produkcie

- Ukończ obsługę procesora ThreadX
- Bez opłat
- Pełny kod źródłowy ANSI C
- Wydajność w czasie rzeczywistym
- Reagowanie na pomoc techniczną
- Obsługa wielu klas
- Wiele wystąpień klasy
- Integracja klas z ThreadX, FileX i NetX
- Obsługa urządzeń USB z wieloma konfiguracjami
- Obsługa urządzeń złożonych USB
- Obsługa zarządzania mocą USB
- Obsługa OTG USB
- Eksportuj zdarzenia śledzenia dla TraceX

## <a name="powerful-services-of-usbx"></a>Zaawansowane usługi USBX

### <a name="complete-usb-device-framework-support"></a>Pełna obsługa platformy USB

USBX może obsługiwać najbardziej wymagające urządzenia USB, w tym wiele konfiguracji, wiele interfejsów i wiele ustawień alternatywnych.

### <a name="easy-to-use-apis"></a>Łatwe w użyciu interfejsy API

USBX zapewnia najlepszy, głęboko osadzony stos USB w sposób, który jest łatwy do zrozumienia i użycia. Interfejs API USBX zapewnia intuicyjną i spójność usług. Korzystając z dostarczonych interfejsów API klasy USBX, aplikacja użytkownika nie musi zrozumieć złożoności protokołów USB.
