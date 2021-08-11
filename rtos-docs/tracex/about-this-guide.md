---
title: Azure RTOS użytkownika tracex
description: Ten przewodnik zawiera kompleksowe informacje o Azure RTOS TraceX, czyli Windows firmy Microsoft do analizy systemu opartego na rozwiązaniach firmy Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 89a39112d6fc6d231408179ebb3867c21f927326930a1610529b142aa71a1027
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784074"
---
# <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik zawiera kompleksowe informacje na temat Azure RTOS TraceX, opartego na platformie Microsoft Windows narzędzia do analizy systemu Microsoft Azure RTOS.

Jest ona przeznaczona dla osadzonego dewelopera oprogramowania działającego w czasie rzeczywistym przy użyciu Azure RTOS ThreadX Real-Time Operating System (RTOS) i składników dodatków. Deweloper powinien znać standardowe pojęcia Azure RTOS ThreadX Azure RTOS FileX i Azure RTOS NetX.

## <a name="organization"></a>Organizacja

- [Rozdział 1](chapter1.md) — zawiera podstawowe omówienie Azure RTOS TraceX i opisuje jego relację z opracowywaniem w czasie rzeczywistym.
- [Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalowania i używania narzędzia Azure RTOS TraceX do analizowania aplikacji od razu po instalacji.
- [Rozdział 3](chapter3.md) — opisuje główne funkcje Azure RTOS TraceX.
- [Rozdział 4](chapter4.md) . Szczegóły funkcji analizy wydajności Azure RTOS TraceX.
- [Rozdział 5](chapter5.md) — opisuje sposób skonfigurowania platform Azure RTOS ThreadX, Azure RTOS FileX i Azure RTOS NetX w celu wygenerowania buforu śledzenia, który jest Azure RTOS TraceX.
- [Rozdział 6](chapter6.md) — Azure RTOS zdarzenia TraceX.
- [Rozdział 7](chapter7.md) — Azure RTOS zdarzenia FileX.
- [Rozdział 8](chapter8.md) — Azure RTOS zdarzenia NetX.
- [Rozdział 9 —](chapter9.md) Azure RTOS zdarzenia USBX.
- [Rozdział 10 —](chapter10.md) szczegółowo opisano tworzenie niestandardowych zdarzeń użytkownika.
- [Rozdział 11 —](chapter11.md) szczegółowy opis wewnętrznego bufora śledzenia.
- [Dodatek A](appendix-a.md) — Azure RTOS pliku specyficznego dla portu ThreadX ze źródłem sygnatury czasowej do zbierania zdarzeń śledzenia.
- [Dodatek B](appendix-b.md) — Azure RTOS ThreadX *tx_trace.h,* który pokazuje szczegóły implementacji dotyczące buforu śledzenia zdarzeń.
- [Dodatek C](appendix-c.md) — podsumowuje narzędzia wiersza polecenia do konwertowania różnych formatów plików do odpowiednich Azure RTOS plików binarnych TraceX.
- [Dodatek D](appendix-d.md) — Przykłady zrzucania plików śledzenia z różnych narzędzi programistów.

## <a name="guide-conventions"></a>Konwencje przewodników

*Kursywa —* element Typeface oznacza tytuły książek, podkreśla ważne słowa i wskazuje zmienne.

**Boldface** — element Typeface oznacza nazwy plików, słowa kluczowe i dodatkowo podkreśla ważne słowa i zmienne.

> [!NOTE]
> Wskazuje informacje o uwagach.

## <a name="customer-support-center"></a>Centrum obsługi klienta

Prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal, aby uzyskać pytania lub pomoc, korzystając z kroków tutaj. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i możliwość jego niezawodnego odtworzenia.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTOS ThreadX, które poprzedzały problem.
3. Zawartość ciągu *_tx_version_id* w pliku *tx_port.h* twojej dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska uruchomieniowego.
4. Zawartość w pamięci RAM zmiennej *_tx_build_options* ULONG. Ta zmienna zawiera informacje na temat sposobu Azure RTOS biblioteki ThreadX.
