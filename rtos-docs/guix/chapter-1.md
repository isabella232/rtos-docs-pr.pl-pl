---
title: Rozdział 1 — wprowadzenie do GUIX
description: GUIX to implementacja (GUI) o wysokiej wydajności w czasie rzeczywistym zaprojektowana wyłącznie dla osadzonych aplikacji opartych na platformie Azure RTO ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823107"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO GUIX

Usługa Azure RTO GUIX (GUIX) to implementacja interfejsu graficznego o wysokiej wydajności w czasie rzeczywistym zaprojektowana wyłącznie dla osadzonych aplikacji opartych na ThreadX. Ten rozdział zawiera wprowadzenie do GUIX oraz opis jego aplikacji i korzyści.

## <a name="guix-feature-overview"></a>Omówienie funkcji GUIX

W przeciwieństwie do wielu innych implementacji graficznego interfejsu użytkownika, GUIX został zaprojektowany jako uniwersalny — można łatwo skalować od małych aplikacji opartych na kontrolerze przy użyciu zaawansowanych procesorów RISC i DSP. Jest to bardzo zróżnicowane dla domeny publicznej lub innych implementacji komercyjnych pierwotnie przeznaczonych dla środowisk stacji roboczych, ale a następnie zostały podzielone na osadzone projekty. Omówienie funkcji GUIX:

- Łatwe korzystanie z narzędzia projektowania opartego na hoście GUIX Studio

- Środowisko uruchomieniowe Win32 GUIX dla pełnego prototypu hostowanego

- Obsługuje większość procesorów obsługiwanych przez ThreadX

- Zapisywane wyłącznie w ANSI C

- Neutralne

- Najmniejszy, Fast graficzny interfejs użytkownika

- Konfigurowalny czas wykonywania, liczba obiektów, rozmiar ekranu itp.

- Łatwy do zapisu interfejs sterownika wyświetlania

- Kolor (do 32 BPP głębi kolorów), obsługa monochromatyczna i Skala szarości

- Obsługa wielu języków za pomocą kodowania ciągów UTF8 i zasobów ciągów

- Domyślne czcionki bezpłatne i łatwe dodawanie nowych czcionek

- Obsługiwane są różne kanwy rysowania o różnych rozmiarach

- Obsługiwane są wiele ekranów o różnych rozmiarach i głębiach kolorów

- Obsługa przejścia ekranu (zanikanie, ściemnianie, przesuwanie itp.)

- Obsługa ekranu dotykowego, gestu i klawiatury wirtualnej

- Kompresja mapy bitowej

- Obsługa mieszania alfa

- Obsługa symulacji

- Obsługa antyaliasów

- Karnacje i motywy

- Mieszanie kanwy

- Zakończenie zarządzania oknem

  - Relacja nadrzędny/podrzędny

  - Dynamiczne tworzenie, usuwanie, zmiana rozmiarów, przechodzenie
  - Oddzielanie obsługi i rysowania zdarzeń 
  - Porządek osi Z
  - Przycinanie i widoki

- Obszerny zestaw elementów widget

  - Różne typy przycisków, suwaki i numery telefonów

  - Lista rozwijana
  
  - Monit

  - Widok tekstu wielowierszowego
  
  - Pojedyncze i wielowierszowe wprowadzanie tekstu
  
  - Pokrętła przewijania liczbowego i tekstowego
  
  - Okna i paski przewijania
  
  - Pasek postępu promieniowego
  
  - Klasy

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C

GUIX jest zapisywana całkowicie w standardzie ANSI C i jest natychmiast przenośny do praktycznie dowolnej architektury procesora, która ma kompilator ANSI C i obsługę ThreadX. Mimo że Zapisano w standardzie ANSI C, GUIX korzysta z modelu zorientowanego obiektowo i dziedziczenia.

### <a name="not-a-black-box"></a>To nie jest czarne pole

Większość dystrybucji GUIX obejmuje pełny kod źródłowy języka C. Eliminuje to problemy "z czarnym pudełkem" występujące w wielu komercyjnych implementacjach graficznego interfejsu użytkownika. Korzystając z GUIX, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi graficzny interfejs użytkownika — nie ma Mysteries!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, korzystne jest, aby mieć możliwość modyfikacji graficznego interfejsu użytkownika, jeśli jest to wymagane. Te funkcje są szczególnie wygodne dla deweloperów przyzwyczajonych do pracy z produktami wewnętrznymi lub publicznymi. Powinny one mieć kod źródłowy i możliwość jego modyfikacji. GUIX to Ultimate oprogramowanie graficznego interfejsu użytkownika dla takich deweloperów.

## <a name="embedded-gui-applications"></a>Osadzone aplikacje graficznego interfejsu użytkownika

Osadzone aplikacje GUI są aplikacjami, które mają wymagania dotyczące interfejsu użytkownika i są wykonywane w mikroprocesorach ukrytych w produktach, takich jak telefony komórkowe, sprzęt komunikacyjny, silniki motoryzacyjne, drukarki laserowe, urządzenia medyczne itd. Takie aplikacje prawie zawsze mają pewne ograniczenia dotyczące pamięci i wydajności. Innym rozróżnieniem osadzonego interfejsu użytkownika jest to, że oprogramowanie i sprzęt mają dedykowany cel.

### <a name="real-time-gui-software"></a>Oprogramowanie graficznego interfejsu użytkownika w czasie rzeczywistym

W istocie oprogramowanie graficznego interfejsu użytkownika, które musi wykonać przetwarzanie w określonym czasie, jest nazywane oprogramowaniem *graficznego interfejsu użytkownika w czasie rzeczywistym* , a w przypadku wystąpienia ograniczeń czasowych w aplikacjach graficznego interfejsu użytkownika są one klasyfikowane jako aplikacje w czasie rzeczywistym. Wbudowane aplikacje graficznego interfejsu użytkownika są prawie zawsze w czasie rzeczywistym ze względu na ich nieodłączną współpracę z zewnętrznym światem.

## <a name="guix-benefits"></a>Korzyści z GUIX

Podstawową zaletą korzystania z GUIX dla aplikacji osadzonych są wysoka wydajność, bogate funkcje i bardzo małe wymagania dotyczące pamięci. GUIX jest również całkowicie zintegrowany z wysoką wydajnością i wielostronicowym systemem operacyjnym Azure RTO ThreadX.

### <a name="improved-responsiveness"></a>Zwiększona czas odpowiedzi

Produkt GUIX o wysokiej wydajności umożliwia aplikacjom reagowanie szybciej niż kiedykolwiek wcześniej. Jest to szczególnie ważne w przypadku aplikacji osadzonych, które mają znaczną ilość informacji wizualnych lub rygorystyczne wymagania dotyczące chronometrażu na potrzeby wyświetlania takich informacji.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Korzystanie z programu GUIX umożliwia deweloperom łatwe partycjonowanie aspektów graficznego interfejsu użytkownika aplikacji osadzonej. Takie partycjonowanie sprawia, że cały proces tworzenia oprogramowania jest łatwy i znacząco ulepsza konserwację w przyszłości.

### <a name="increased-throughput"></a>Zwiększona przepływność

Program GUIX zapewnia dostęp do najwyższej jakości graficznego interfejsu użytkownika, który jest bezpośrednio przesyłany do osadzonej aplikacji. Aplikacje GUIX mogą przetwarzać informacje o interfejsie użytkownika szybciej niż aplikacje, które nie są GUIX.

### <a name="processor-isolation"></a>Izolacja procesora

GUIX zapewnia niezawodny, niezależny od procesora interfejs między aplikacją a podstawowym procesorem i wyświetlaczem sprzętowym. Pozwala to deweloperom skoncentrować się na aspektach wysokiego poziomu interfejsu użytkownika, a nie poświęca dodatkowych czasu na rozwiązywanie problemów ze sprzętem.

### <a name="ease-of-use"></a>Łatwość użycia

GUIX jest zaprojektowana z myślą o deweloperu aplikacji. Interfejs GUIX i architektura wywołania usługi są łatwe do zrozumienia. W związku z tym GUIX deweloperzy mogą szybko korzystać z zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Popraw czas wprowadzenia na rynek

Zaawansowane funkcje GUIX przyspieszają proces tworzenia oprogramowania. GUIX abstrakcje większości procesorów i wyświetlania problemów sprzętowych, usuwając te problemy z większości implementacji interfejsu użytkownika aplikacji. Ta funkcja, która jest powiązana z łatwym w użyciu i zaawansowanym zestawem funkcji, skutkuje szybszym czasem wprowadzenia na rynek.

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

GUIX jest zapisywana wyłącznie w standardzie ANSI C i jest w pełni zintegrowana z systemem operacyjnym Azure RTO ThreadX w czasie rzeczywistym. Oznacza to, że aplikacje GUIX są natychmiast przenośne do wszystkich obsługiwanych procesorów ThreadX. Jeszcze lepiej można obsługiwać całkowicie nową architekturę procesora z ThreadX w ciągu kilku tygodni. W związku z tym użycie GUIX gwarantuje, że ścieżka migracji aplikacji i chroni pierwotne inwestycje rozwojowe.
