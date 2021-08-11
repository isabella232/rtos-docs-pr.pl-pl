---
title: Rozdział 1 — omówienie Azure RTOS LevelX
description: Azure RTOS LevelX zapewnia osadzonym aplikacjom funkcje wyrównania zużycia pamięci flash NAND i NOR.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73c06d48b98081291d83635e049e6cf8641714c87efe815f9399f3fbab3a6211
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790602"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a>Rozdział 1 — omówienie Azure RTOS LevelX

Azure RTOS LevelX zapewnia osadzonym aplikacjom funkcje wyrównania zużycia pamięci flash NAND i NOR. Ponieważ pamięci flash NAND i NOR można wymazać tylko skończoną liczbę razy, niezwykle ważne jest równomierne dystrybuowanie pamięci flash. Jest to zwykle nazywane "poziomem zużycia" i jest celem na poziomie LevelX.

Algorytm, który wybiera blok flash do ponownego użycia, zależy przede wszystkim od liczby wymazywania, ale nie całkowicie. Blok o najniższej liczbie wymazywania może nie zostać wybrany, jeśli istnieje inny blok, który ma liczbę wymazywania w ramach dopuszczalnej różnicy od minimalnej liczby wymazywania i który ma większą liczbę przestarzałych mapowań. W takich przypadkach blok o największej liczbie przestarzałych mapowań zostanie usunięty i ponownie użyty, co pozwala zaoszczędzić narzut podczas przenoszenia prawidłowych wpisów mapowania.

LevelX obsługuje wiele wystąpień części NAND i/lub NOR, tj. aplikacja może korzystać z oddzielnych wystąpień levelX w ramach tej samej aplikacji. Każde wystąpienie wymaga własnego bloku sterowania dostarczonego przez aplikację oraz własnego sterownika flash.

LevelX przedstawia użytkownikowi tablicę sektorów logicznych, które są mapowane na fizyczną pamięć flash wewnątrz levelX. Aby zwiększyć wydajność, levelX udostępnia również pamięć podręczną najnowszych mapowań sektorów logicznych. Rozmiar tej pamięci podręcznej jest definiowany przez programistę. Aplikacje mogą używać levelX w połączeniu z FileX lub mogą bezpośrednio odczytywać/zapisywać sektory logiczne. LevelX nie jest zależny od pliku FileX i bardzo mała zależność od ThreadX (używane są tylko pierwotne typy danych ThreadX).

LevelX zaprojektowano pod kątem odporności na uszkodzenia. Aktualizacje flash są wykonywane w procesie wieloetapowym, który może zostać przerwany w każdym kroku. LevelX automatycznie odzyskuje optymalny stan podczas następnej operacji.

System LevelX wymaga sterownika flash w celu fizycznego dostępu do bazowej pamięci flash. Dostępne są przykładowe symulowane sterowniki NAND i NOR, które mogą służyć jako dobry punkt wyjścia do implementowania rzeczywistych sterowników LevelX. Ponadto wymagania dotyczące sterowników zostały szczegółowo opisane w dalszej części tej dokumentacji.

W poniższych rozdziałach opisano operację funkcjonalną dla obsługi NAND i NOR LevelX.
