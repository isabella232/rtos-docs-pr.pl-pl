---
title: Rozdział 1 — omówienie
author: philmea
description: Ten artykuł zawiera omówienie Azure RTOS ThreadX
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9018c10e6fe92b2237ec94b633f2f0030ad1cef4bcbcb7afa5ace20548f012ed
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799436"
---
# <a name="chapter-1-overview"></a>Rozdział 1. Omówienie

Składnik ThreadX Module zapewnia infrastrukturę dla aplikacji do dynamicznego ładowania modułów, które są tworzone niezależnie od części aplikacji. Jest to szczególnie przydatne w sytuacjach, gdy rozmiar kodu aplikacji przekracza dostępną pamięć. Może to również pomóc w sytuacji, gdy po wdrożeniu obrazu podstawowego wymagane jest dodanie nowych funkcji. Ponadto moduły ładowania dynamicznego mogą być używane, gdy są wymagane częściowe aktualizacje oprogramowania układowego.

Ochrona pamięci dla załadowanego modułu jest opcjonalna w oparciu o właściwości określone w module. W przypadku ustawienia ochrony pamięci sprzęt do zarządzania pamięcią procesora jest skonfigurowany w taki sposób, że wszystkie wątki modułu mają dostęp tylko do kodu i pamięci danych modułu. Każdy dodatkowy dostęp do pamięci lub jego wykonanie spowoduje błąd pamięci, a wątek modułu, który zostanie przerwany, zostanie przerwany. Jeśli aplikacja zarejestruje wywołanie zwrotne powiadomień o błędach pamięci, zostanie to również wywołane w celu alertu aplikacji o błędach pamięci.

Składnik modułu ThreadX opiera się na aplikacji w celu zapewnienia obszaru pamięci, w którym można ładować moduły. Obszar instrukcji każdego modułu może zostać wykonany w miejscu lub skopiowany do obszaru pamięci modułu PAMIĘCI RAM w celu wykonania. We wszystkich przypadkach wymagania dotyczące pamięci danych modułu są przydzielane z obszaru pamięci modułu.

Nie ma żadnych ograniczeń liczby modułów, które mogą być ładowane w tym samym czasie (oprócz ilości dostępnej pamięci), podczas gdy istnieje tylko jedna kopia kodu menedżera modułów znajduje się. Rysunek 1 ilustruje relację między menedżerem modułów a samymi modułami.

![Relacje modułów i menedżera modułów](media/image2.png)

**Rysunek 1** Moduły i Menedżer modułów

Każdy moduł musi mieć własny obszar pamięci, który jest odpowiedzialny za definiowanie przez aplikację. Moduł i Menedżer modułów wchodzą w interakcje za pośrednictwem funkcji wysyłania oprogramowania za pośrednictwem wstępnie zdefiniowanych identyfikatorów żądań, które odpowiadają usługom ThreadX żądanym przez moduł. Ponadto moduł jest wymagany do zapewnienia punktu wejścia pojedynczego wątku, a także wymaganego rozmiaru stosu, priorytetu, identyfikatora modułu, rozmiaru/priorytetu stosu wątku wywołania zwrotnego itp. Te informacje są definiowane w poszczególnych modułach.

Menedżer modułów jest odpowiedzialny za tworzenie początkowego wątku modułu i inicjowanie jego wykonywania. Po wykonaniu początkowego wątku modułu Menedżer modułów jest odpowiedzialny za pola wszystkich żądań interfejsu API ThreadX wykonanych przez moduł. Moduł ma pełny dostęp do interfejsu API ThreadX, w tym możliwość tworzenia dodatkowych wątków w module.  
  
Konwencje nazewnictwa kodu źródłowego modułu są proste: wszystkie pliki źródłowe menedżera modułów mają nazwę ***txm_module_manager_, a \**** wszystkie pliki skojarzone wyłącznie z modułem pomijają część nazwy **_"manager_*_". Główny plik dołączany _*_txm_module.h_** jest współużytowany przez kod źródłowy menedżera i modułu.
