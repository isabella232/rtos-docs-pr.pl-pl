---
title: Podręcznik użytkownika usługi Azure RTO TraceX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO TraceX, narzędzia do analizy systemu opartego na systemie Microsoft Windows firmy Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823773"
---
# <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO TraceX, narzędzia do analizy systemu opartego na systemie Microsoft Windows dla Microsoft Azure RTO.

Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym przy użyciu usługi Azure RTO ThreadX Real-Time system operacyjny (RTO) i składniki dodatków. Deweloper powinien znać Standard platformy Azure RTO ThreadX Azure RTO FileX oraz koncepcje platformy Azure RTO NetX.

## <a name="organization"></a>Organizacja

- [Rozdział 1](chapter1.md) — zawiera podstawowe Omówienie usługi Azure RTO TraceX i opisuje jej relacje z programowaniem w czasie rzeczywistym.
- [Rozdział 2](chapter2.md) — zawiera podstawowe kroki umożliwiające zainstalowanie i użycie usługi Azure RTO TraceX w celu przeanalizowania aplikacji od razu.
- [Rozdział 3](chapter3.md) — opis głównych funkcji usługi Azure RTO TraceX.
- [Rozdział 4](chapter4.md) — Szczegóły funkcji analizy wydajności usługi Azure RTO TraceX.
- [Rozdział 5](chapter5.md) — opis sposobu konfigurowania usługi Azure RTO ThreadX, platformy Azure RTO FileX i platformy Azure RTO NetX w celu wygenerowania bufora śledzenia, który można wyświetlić w usłudze Azure RTO TraceX.
- [Rozdział 6](chapter6.md) — szczegółowe omówienie zdarzeń usługi Azure RTO TraceX.
- [Rozdział 7](chapter7.md) — szczegółowe omówienie zdarzeń usługi Azure RTO FileX.
- [Rozdział 8](chapter8.md) — szczegółowe omówienie zdarzeń usługi Azure RTO NetX.
- [Rozdział 9](chapter9.md) — szczegółowe omówienie zdarzeń usługi Azure RTO USBX.
- [Rozdział 10](chapter10.md) — omówienie tworzenia niestandardowych zdarzeń użytkownika.
- [Rozdział 11](chapter11.md) — opisuje szczegóły wewnętrznego buforu śledzenia.
- [Dodatek A](appendix-a.md) — Azure RTO ThreadX plik specyficzny dla portu ze źródłem sygnatury czasowej do zbierania zdarzeń śledzenia.
- [Dodatek B](appendix-b.md) -Azure rto ThreadX *tx_trace. h* , który zawiera szczegółowe informacje dotyczące implementacji buforu śledzenia zdarzeń.
- [Dodatek C](appendix-c.md) — zawiera podsumowanie narzędzi wiersza polecenia do konwertowania różnych formatów plików na odpowiednie pliki binarne usługi Azure RTO TraceX.
- [Dodatek D](appendix-d.md) -przykłady zatopienia plików śledzenia z różnych narzędzi programistycznych.

## <a name="guide-conventions"></a>Konwencje przewodnika

*Kursywa* — oznacza tytuły książek, wyróżnia ważne słowa i określa zmienne.

**Pogrubiona** — kroje liter oznacza nazwy plików, słowa kluczowe i bardziej podkreśla ważne słowa i zmienne.

> [!NOTE]
> Wskazuje informacje o notatce.

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.
3. Zawartość ciągu *_tx_version_id* można znaleźć w pliku *tx_port. h* dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.
4. Zawartość w pamięci RAM *_tx_build_options* zmiennej ulong. Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.
