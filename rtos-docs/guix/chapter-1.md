---
title: Rozdział 1 — Wprowadzenie do graficznego interfejsu użytkownika
description: GUIX to implementacja graficznego interfejsu użytkownika (GUI) o wysokiej wydajności w czasie rzeczywistym przeznaczona wyłącznie dla Azure RTOS opartych na threadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e85aab43ba803212875f1fef3ba0bee8484c25b015e400d3b927d492177202b8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784120"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a>Rozdział 1 — Wprowadzenie do Azure RTOS GUIX

Azure RTOS GUIX (GUIX) to implementacja interfejsu graficznego o wysokiej wydajności w czasie rzeczywistym przeznaczona wyłącznie dla osadzonych aplikacji opartych na technologii ThreadX. Ten rozdział zawiera wprowadzenie do graficznego interfejsu użytkownika oraz opis jego aplikacji i korzyści.

## <a name="guix-feature-overview"></a>Przegląd funkcji GUIX

W przeciwieństwie do wielu innych implementacji graficznego interfejsu użytkownika, interfejs GUIX został zaprojektowany tak, aby był wszechstronny — łatwo skalować od małych aplikacji opartych na mikrokontrolecie do tych, które korzystają z zaawansowanych procesorów RISC i DSP. Jest to w dużym przeciwieństwie do domeny publicznej lub innych implementacji komercyjnych pierwotnie przeznaczonych dla środowisk stacji roboczych, ale następnie z osadzonymi projektami. Omówienie funkcji GUIX:

- Łatwe w użyciu z opartym na hoście narzędziem do projektowania GUIX Studio

- Środowisko uruchomieniowe WIN32 GUIX do kompletnego tworzenia hostowanych prototypów

- Obsługuje większość procesorów obsługiwanych przez ThreadX

- Napisane wyłącznie w języku ANSI C

- Neutralność endianowa

- Najmniejszy, fasted embedded GUI

- Konfigurowalne w czasie rzeczywistym, liczba obiektów, rozmiar ekranu itp.

- Łatwy do napisania interfejs sterowników wyświetlania

- Obsługa kolorów (do 32 bpp głębi kolorów), monochromatycznych i skalowania szarości

- Obsługa wielu języków za pośrednictwem kodowania ciągów UTF8 i zasobów ciągów

- Domyślne bezpłatne czcionki i łatwe dodawanie nowych czcionek

- Obsługiwana jest wiele kanwy do rysowania o różnych rozmiarach

- Wiele ekranów o różnych rozmiarach i obsługiwanych głębokościach kolorów

- Obsługa przechodzenia ekranu (zanikanie, zanikanie, szybkie przesuwanie itp.)

- Obsługa ekranu dotykowego, gestu i klawiatury wirtualnej

- Kompresja mapy bitowej

- Obsługa mieszania alfa

- Obsługa dither

- Obsługa aliasów

- Osłodzenie i motywy

- Łączenie kanwy

- Kompletne zarządzanie oknami

  - Relacja nadrzędny/podrzędny

  - Dynamiczne tworzenie, usuwanie, zmiana rozmiaru, przenoszenie
  - Oddzielne obsługę zdarzeń i rysowanie 
  - Porządek osi Z
  - Obcinanie i widoki

- Rozbudowany zestaw widżetów

  - Różne typy przycisków, suwaki i pokrętła

  - Lista rozwijana
  
  - Monit

  - Widok tekstu z wieloma wierszami
  
  - Wprowadzanie tekstu w jednym i wielu wierszach
  
  - Numeryczne i tekstowe kółka przewijania
  
  - Windows i paski przewijania
  
  - Pasek postępu promieniowego
  
  - Sprite

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C

GuiX jest napisany całkowicie w języku ANSI C i jest natychmiast przenośny do praktycznie dowolnej architektury procesora, która obsługuje kompilator ANSI C i ThreadX. Mimo że jest on napisany w języku ANSI C, guix używa modelu obiektowego i dziedziczenia.

### <a name="not-a-black-box"></a>Nie jest czarną skrzynką

Większość dystrybucji graficznego interfejsu użytkownika (GUIX) zawiera pełny kod źródłowy języka C. Eliminuje to problemy "czarnej skrzynki" występujące w wielu komercyjnych implementacjach graficznego interfejsu użytkownika. Korzystając z graficznego interfejsu użytkownika, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi graficzny interfejs użytkownika — nie ma żadnych wytłoków!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, na pewno korzystne jest możliwość modyfikowania graficznego interfejsu użytkownika, jeśli jest to wymagane. Te funkcje są szczególnie wygodne dla deweloperów, którzy są przywykli do pracy z produktami domeny firmowej lub publicznej. Oczekują oni kodu źródłowego i możliwości jego modyfikowania. GUIX to ostateczne oprogramowanie graficznego interfejsu użytkownika dla takich deweloperów.

## <a name="embedded-gui-applications"></a>Aplikacje z osadzonym graficznym interfejsem użytkownika

Osadzone aplikacje graficznego interfejsu użytkownika to aplikacje, które mają wymagania dotyczące interfejsu użytkownika i są wykonywane na mikroprocesorach ukrytych wewnątrz produktów, takich jak telefony komórkowe, sprzęt komunikacyjny, aparaty samochodowy, drukarki laserowe, urządzenia medyczne itd. Takie aplikacje prawie zawsze mają pewne ograniczenia dotyczące pamięci i wydajności. Innym rozróżnieniem osadzonego graficznego interfejsu użytkownika jest to, że ich oprogramowanie i sprzęt mają dedykowane przeznaczenie.

### <a name="real-time-gui-software"></a>Oprogramowanie z graficznym interfejsem użytkownika w czasie rzeczywistym

Zasadniczo oprogramowanie graficznego interfejsu użytkownika, które musi wykonywać  przetwarzanie w dokładnie krótkim czasie, jest nazywane oprogramowaniem z graficznym interfejsem użytkownika w czasie rzeczywistym, a gdy na aplikacje graficznego interfejsu użytkownika nakładane są ograniczenia czasowe, są one klasyfikowane jako aplikacje w czasie rzeczywistym. Osadzone aplikacje graficznego interfejsu użytkownika prawie zawsze są dostępne w czasie rzeczywistym ze względu na ich naturalną interakcję ze światem zewnętrznym.

## <a name="guix-benefits"></a>Korzyści związane z graficznym interfejsem użytkownika

Głównymi zaletami korzystania z graficznego interfejsu użytkownika dla aplikacji osadzonych są wymagania dotyczące wysokiej wydajności, rozbudowanych funkcji i bardzo małych ilości pamięci. GuiX jest również całkowicie zintegrowany z wysokowydajnym, wielozadaniowym systemem Azure RTOS ThreadX w czasie rzeczywistym.

### <a name="improved-responsiveness"></a>Ulepszona szybkość reagowania

Produkt GUIX o wysokiej wydajności umożliwia aplikacjom szybsze reagowanie niż kiedykolwiek wcześniej. Jest to szczególnie ważne w przypadku aplikacji osadzonych, które mają znaczną ilość informacji wizualnych lub ścisłe wymagania czasowe dotyczące wyświetlania takich informacji.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Użycie graficznego interfejsu użytkownika umożliwia deweloperom łatwe partycjonowanie aspektów graficznego interfejsu użytkownika osadzonej aplikacji. Partycjonowanie sprawia, że cały proces tworzenia oprogramowania jest prosty i znacząco usprawnia przyszłą konserwację oprogramowania.

### <a name="increased-throughput"></a>Zwiększona przepływność

Graficzny interfejs użytkownika zapewnia graficzny interfejs użytkownika o najwyższej wydajności, który jest przesyłany bezpośrednio do osadzonej aplikacji. Aplikacje GUIX mogą przetwarzać informacje o interfejsie użytkownika szybciej niż aplikacje inne niż GUIX.

### <a name="processor-isolation"></a>Izolacja procesora

GUIX zapewnia niezawodny, niezależny od procesora interfejs między aplikacją a bazowym procesorem i sprzętem do wyświetlania. Dzięki temu deweloperzy mogą skupić się na aspektach wysokiego poziomu interfejsu użytkownika, zamiast poświęcać dodatkowy czas na radzenie sobie z problemami ze sprzętem wyświetlania.

### <a name="ease-of-use"></a>Łatwość użycia

Interfejs GUIX został zaprojektowany z myślą o deweloperze aplikacji. Architektura GUIX i interfejs wywołania usługi są łatwe do zrozumienia. Dzięki temu deweloperzy z graficznym interfejsem użytkownika mogą szybko korzystać ze swoich zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Poprawianie czasu na rynek

Zaawansowane funkcje graficznego interfejsu użytkownika przyspieszają proces tworzenia oprogramowania. Graficzny interfejs użytkownika (GUIX) abstrakcję większości problemów ze sprzętem procesora i wyświetlania, co usuwa te problemy z większości implementacji interfejsu użytkownika aplikacji. Ta funkcja, w połączeniu z łatwym w użyciu i zaawansowanym zestawem funkcji, pozwala szybciej na rynek.

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

Interfejs GUIX jest napisany wyłącznie w języku ANSI C i jest w pełni zintegrowany z systemem operacyjnym Azure RTOS ThreadX w czasie rzeczywistym. Oznacza to, że aplikacje GUIX są natychmiast przenośne do wszystkich procesorów obsługiwanych przez ThreadX. Jeszcze lepiej, zupełnie nowa architektura procesora może być obsługiwana za pomocą threadX w ciągu kilku tygodni. W związku z tym użycie graficznego interfejsu użytkownika zapewnia ścieżkę migracji aplikacji i chroni oryginalną inwestycję deweloperską.
