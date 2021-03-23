---
title: Rozdział 1 — Omówienie usługi Azure RTO LevelX
description: Usługa Azure RTO LevelX zapewnia ni i lub Flash funkcje do wyrównywania zużycia w aplikacjach osadzonych.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 045446fec74164f125bc0ad27e8b7a904be14ab2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822177"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a>Rozdział 1 — Omówienie usługi Azure RTO LevelX

Usługa Azure RTO LevelX zapewnia ni i lub Flash funkcje do wyrównywania zużycia w aplikacjach osadzonych. Ponieważ zarówno ni, jak i lub flash pamięci można wymazać tylko przez wiele razy, ma krytyczne znaczenie dla równomiernego dystrybuowania pamięci flash. Jest to zwykle nazywane "bilansowaniem" i jest celem za LevelX.

Algorytm wybierający, który blok Flash do ponownego użycia jest przede wszystkim oparty na liczbie wymazywania, ale nie w całości. Blok o najmniejszej liczbie wymazywań może nie zostać wybrany, jeśli istnieje inny blok, który ma liczbę wymazywań w akceptowalnej wartości delta z minimalnej liczby wymazywań i ma większą liczbę przestarzałych mapowań. W takich przypadkach blok o największej liczbie przestarzałych mapowań zostanie wymazany i ponownie użyty, co spowoduje oszczędności wynikające z przeniesienia prawidłowych wpisów mapowania.

LevelX obsługuje wiele wystąpień ni i/lub lub części, tj. aplikacja może korzystać z oddzielnych wystąpień LevelX w ramach tej samej aplikacji. Każde wystąpienie wymaga własnego bloku kontroli dostarczonego przez aplikację oraz własnego sterownika Flash.

LevelX przedstawia użytkownikowi tablicę sektorów logicznych, które są mapowane na fizyczną pamięć flash wewnątrz LevelX. Aby zwiększyć wydajność, LevelX udostępnia również pamięć podręczną najnowszych mapowań sektora logicznego. Rozmiar tej pamięci podręcznej jest definiowany przez programistę. Aplikacje mogą używać LevelX w połączeniu z FileX lub mogą bezpośrednio odczytywać i zapisywać sektory logiczne. LevelX nie ma zależności od FileX i bardzo mało zależności od ThreadX (używane są tylko pierwotne typy danych ThreadX).

LevelX jest zaprojektowana pod kątem odporności na uszkodzenia. Aktualizacje programu Flash są wykonywane w procesie wieloetapowym, który można przerwać w każdym kroku. LevelX automatycznie przywraca optymalny stan podczas kolejnej operacji.

LevelX wymaga sterownika Flash do fizycznego dostępu do źródłowej pamięci flash. Przykłady ni i i symulowanych sterowników są dostarczane i mogą być używane jako dobry punkt wyjścia do implementowania rzeczywistych sterowników LevelX. Ponadto wymagania dotyczące sterowników są szczegółowo opisane w dalszej części tej dokumentacji.

W poniższych tematach opisano operację funkcjonalną dla ni i LevelX.
