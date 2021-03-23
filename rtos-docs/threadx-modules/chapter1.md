---
title: Rozdział 1 — omówienie
author: philmea
description: Ten artykuł zawiera omówienie modułów usługi Azure RTO ThreadX
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0c9698086468d7bb41c33ebe9fa9d1ebb61b5f1f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821402"
---
# <a name="chapter-1-overview"></a>Rozdział 1: przegląd

Składnik modułu ThreadX udostępnia infrastrukturę dla aplikacji do dynamicznego ładowania modułów, które są zbudowane niezależnie od rezydentnej części aplikacji. Jest to szczególnie przydatne w sytuacjach, gdy rozmiar kodu aplikacji przekracza dostępną pamięć. Może również pomóc, gdy do wdrożenia obrazu podstawowego jest wymagane dodanie nowych funkcji. Dodatkowo dynamiczne ładowanie modułów może być używane, gdy wymagane są częściowe aktualizacje oprogramowania układowego.

Ochrona pamięci dla załadowanego modułu jest opcjonalna na podstawie właściwości określonych w preambule modułu. W przypadku określenia ochrony pamięci sprzęt zarządzania pamięcią procesora jest skonfigurowany tak, aby wszystkie wątki modułu miały dostęp tylko do kodu modułu i pamięci danych. Każdy nadmiarowy dostęp do pamięci lub wykonanie spowoduje awarię pamięci i wątek modułu, który spowodował przerwanie działania. Jeśli aplikacja rejestruje wywołanie zwrotne powiadomienia o błędach pamięci, zostanie ona również wywołana w celu wygenerowania alertu dotyczącego błędu pamięci.

Składnik modułu ThreadX korzysta z aplikacji, aby zapewnić obszar pamięci, w którym można załadować moduły. Obszar instrukcji każdego modułu może zostać wykonany w miejscu lub być kopiowany do obszaru pamięci modułu RAM na potrzeby wykonania. We wszystkich przypadkach wymagania dotyczące pamięci danych modułu są przyliczane z obszaru pamięci modułu.

Nie ma ograniczeń dotyczących liczby modułów, które mogą być ładowane w tym samym czasie (oprócz ilości dostępnej pamięci), gdy istnieje tylko jedna kopia kodu programu rezydentnego modułu. Rysunek 1 ilustruje relację Menedżera modułów i samych modułów.

![Relacje modułów i Menedżera modułów](media/image2.png)

**Rysunek 1** Moduły i Menedżer modułów

Każdy moduł musi mieć własny obszar pamięci, który jest odpowiedzialny za zdefiniowanie aplikacji. Moduł i Menedżer modułów współdziałają za pośrednictwem funkcji wysyłania oprogramowania za pośrednictwem wstępnie zdefiniowanych identyfikatorów żądań, które odpowiadają usługom ThreadX żądanym przez moduł. Ponadto moduł jest wymagany do udostępnienia jednego punktu wejścia wątku, a także wymaganego rozmiaru stosu, priorytetu, identyfikatora modułu, rozmiaru stosu wątku wywołania zwrotnego i priorytetu itp. Te informacje są zdefiniowane w preambule każdego modułu.

Menedżer modułów jest odpowiedzialny za tworzenie początkowego wątku modułu i Inicjowanie jego wykonywania. Po wykonaniu wątku początkowego modułu Menedżer modułów jest odpowiedzialny za pole wszystkie żądania interfejsu API ThreadX wykonywane przez moduł. Moduł ma pełny dostęp do interfejsu API ThreadX, w tym możliwość tworzenia dodatkowych wątków w module.  
  
Konwencje nazewnictwa kodu źródłowego modułu są proste: wszystkie pliki źródłowe Menedżera modułów mają nazwę ***txm_module_manager_ \**** i wszystkie pliki skojarzone wyłącznie z modułem pomijają **część nazwy "_Manager_*_". Główny plik dołączany _*_txm_module. h_** jest współużytkowany przez Menedżera i kod źródłowy modułu.
