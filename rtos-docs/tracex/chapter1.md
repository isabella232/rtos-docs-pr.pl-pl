---
title: Rozdział 1 — Wprowadzenie do Azure RTOS TraceX
description: Azure RTOS TraceX to narzędzie do analizy systemu firmy Microsoft, które wyświetla informacje o zdarzeniach systemowych zebrane przez ThreadX uruchomione na osadzonym docelowym.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 70eb06341e5d57f59c74888046bda3bbf95dc88cac56332be640d9576551796f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785060"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>Rozdział 1 — Wprowadzenie do Azure RTOS TraceX

Azure RTOS TraceX to narzędzie do analizy systemu firmy Microsoft, które wyświetla informacje o zdarzeniach systemowych zebrane przez ThreadX uruchomione na osadzonym docelowym. Użytkownik jest odpowiedzialny za transferowanie buforu śledzenia przechowywanego w pamięci RAM w osadzonym miejscu docelowym do pliku binarnego na komputerze hosta. Użytkownik może następnie otworzyć ten plik za pomocą narzędzia TraceX i analizować graficznie zdarzenia docelowe, diagnozowanie problemów z systemem i dostrajanie roboczej aplikacji w celu zwiększenia wydajności i zarządzania zasobami.

## <a name="tracex-requirements"></a>Wymagania dotyczące tracex

TraceX wymaga Windows XP (lub więcej). System powinien mieć co najmniej 192 MB pamięci RAM, 2 GB dostępnego miejsca na dysku twardym i minimalny ekran 1024 x 768 z 256 kolorami. Ponadto aplikacja musi być uruchomiona w wersji ThreadX 5.0 lub nowszej.

TraceX wymaga również zainstalowania Microsoft .NET, co instalator TraceX robi automatycznie.

## <a name="tracex-constraints"></a>Ograniczenia TraceX

TraceX ma następujące ograniczenia:

- Pliki TraceX są ograniczone do maksymalnie 32 768 zdarzeń (około 1 MB).
- Źródło sygnatury czasowej musi mieć uzasadnione rozwiązanie. Jeśli rozdzielczość jest zbyt niska, zdarzenia nakładają się na siebie. Jeśli rozdzielczość jest zbyt wysoka, mogą pojawiać się długie przerwy między zdarzeniami.
- TraceX nie może dokładnie mierzyć interwałów między zdarzeniami większymi niż okres czasomierza.
