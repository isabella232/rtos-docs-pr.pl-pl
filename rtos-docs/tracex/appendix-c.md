---
title: Dodatek C — narzędzia wiersza polecenia DOS
description: W instalacji narzędzia TraceX systemu Azure RTOS podkatalogu Utilities znajdują się trzy narzędzia wiersza polecenia systemu DOS.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1a89f8be7e21e416659b904f0ec5b2a3a8f666cdb9a861786e652a38564db48f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791554"
---
# <a name="appendix-c---dos-command-line-utilities"></a>Dodatek C — narzędzia wiersza polecenia DOS

W instalacji narzędzia TraceX w podkatalogu ***Utilities*** znajdują się trzy narzędzia wiersza polecenia DOS.

Dostępne narzędzia są wymienione poniżej:

| **Narzędzie**                              | **Cel**                               | **Definicje wiersza polecenia** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | Konwertuje plik śledzenia ea2tracex wygenerowany przez ThreadX w original_file skojarzenia z narzędziami GHS converted_file format pliku śledzenia TraceX. Narzędzie ThreadX dla narzędzi GHS generuje inny format śledzenia niż ThreadX dla narzędzi innych niż GHS, dlatego to narzędzie konwersji jest potrzebne. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | Konwertuje plik śledzenia wygenerowany przez ThreadX, ale zrzucony z narzędzia deweloperski w formacie Intel HEX do formatu binarnego pliku śledzenia TraceX. TraceX V5 i jego powyżej mogą otwierać pliki HEX bez ich konwertowania. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | Konwertuje plik śledzenia wygenerowany przez narzędzie ThreadX, ale zrzucony z narzędzia deweloperski w formacie S-Record Firmy OS do formatu binarnego pliku śledzenia TraceX. TraceX V5 i jego powyżej mogą otwierać pliki S-Record bez ich konwertowania. | ``` > mot2tracex mot_file converted_file <cr> ```|