---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO TraceX
description: Azure RTO TraceX to narzędzie do analizy systemu firmy Microsoft, które wyświetla informacje o zdarzeniu systemowym zebrane przez ThreadX uruchomione w osadzonym miejscu docelowym.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823587"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO TraceX

Azure RTO TraceX to narzędzie do analizy systemu firmy Microsoft, które wyświetla informacje o zdarzeniu systemowym zebrane przez ThreadX uruchomione w osadzonym miejscu docelowym. Użytkownik jest odpowiedzialny za transfer buforu śledzenia przechowywanego w pamięci RAM w osadzonym miejscu docelowym do pliku binarnego na komputerze-hoście. Następnie użytkownik może otworzyć ten plik za pomocą TraceX i graficznie analizować zdarzenia docelowe, diagnozować problemy z systemem i dostrajać działającą aplikację w celu zwiększenia wydajności i zarządzania zasobami.

## <a name="tracex-requirements"></a>Wymagania TraceX

TraceX wymaga systemu Windows XP (lub nowszego). System powinien mieć co najmniej 192 MB pamięci RAM, 2 GB dostępnego miejsca na dysku twardym oraz minimalny wyświetlacz o rozmiarze 1024x768 i 256 kolorów. Ponadto aplikacja musi działać w systemie ThreadX V 5.0 lub nowszym.

TraceX wymaga również zainstalowania platformy Microsoft .NET, którą Instalator TraceX automatycznie.

## <a name="tracex-constraints"></a>Ograniczenia TraceX

TraceX ma następujące ograniczenia:

- Pliki TraceX są ograniczone do maksymalnie 32 768 zdarzeń (około 1 MB).
- Źródło sygnatur czasowych musi mieć odpowiednie rozwiązanie. Jeśli rozwiązanie jest zbyt niskie, zdarzenia będą nakładać się na siebie. Jeśli rozwiązanie jest zbyt wysokie, istnieje potencjalne przerwy między zdarzeniami.
- TraceX nie może dokładnie mierzyć interwałów między zdarzeniami większymi niż okres czasomierza.
