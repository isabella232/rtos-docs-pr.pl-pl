---
title: Dodatek C-narzędzia wiersza polecenia systemu DOS
description: Istnieją trzy narzędzia wiersza polecenia systemu DOS dostępne w instalacji usługi Azure RTO TraceX w podkatalogu Utilities.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: e1ec852a97a6735a4a055706f55283950d3f8d6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823725"
---
# <a name="appendix-c---dos-command-line-utilities"></a>Dodatek C-narzędzia wiersza polecenia systemu DOS

W ramach instalacji TraceX w podkatalogu ***Utilities*** są dostępne trzy narzędzia wiersza polecenia systemu DOS.

Podane narzędzia są wymienione poniżej:

| **Narzędzie**                              | **Cel**                               | **Definicje wiersza polecenia** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | Konwertuje plik śledzenia ea2tracex wygenerowany przez ThreadX w skojarzeniu original_file z narzędziami GHS converted_file do formatu TraceX pliku śledzenia. ThreadX dla narzędzi GHS tworzy inny format śledzenia niż ThreadX dla narzędzi innych niż GHS, co jest przyczyną tego narzędzia do konwersji. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | Konwertuje plik śledzenia wygenerowany przez ThreadX, ale zrzucany z narzędzia deweloperskiego w formacie SZESNASTKOWym Intel do formatu binarnego pliku śledzenia TraceX. TraceX w wersji 5 i nowszej mogą otwierać pliki SZESNASTKOWe bez ich konwertowania. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | Konwertuje plik śledzenia wygenerowany przez ThreadX, ale zrzucany z narzędzia deweloperskiego w formacie rekordu w firmie Motorola S-Record do formatu binarnego pliku śledzenia TraceX. TraceX w wersji 5 i nowszej mogą otwierać pliki S-Record bez ich konwertowania. | ``` > mot2tracex mot_file converted_file <cr> ```|