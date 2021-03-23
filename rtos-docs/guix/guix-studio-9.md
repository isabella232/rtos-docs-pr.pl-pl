---
title: GUIX Studio — wiersz polecenia
description: Program GUIX Studio udostępnia wywołanie wiersza polecenia, które jest przydatne w przypadku potoków kompilacji, które są wymagane do aktualizacji plików wyjściowych generowanych przez program Studio.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822195"
---
# <a name="chapter-9-guix-studio-command-line"></a>Rozdział 9: GUIX Studio — wiersz polecenia

Program GUIX Studio obsługuje wywoływanie wiersza polecenia, co jest przydatne w przypadku potoków kompilacji, które są wymagane do aktualizacji plików wyjściowych generowanych przez program Studio.

## <a name="command-line-usage"></a>Użycie Command-Line

**Użycie:** guix_studio \[ \] \[ argument opcji\]

Otwórz projekt *. GXP* .

Otwórz projekt Studio i Wygeneruj żądane pliki wyjściowe.


**Przykłady:**

`guix_studio demo.gxp`  
Otwórz projekt "demonstracyjne. GXP"


`guix_studio.exe –p demo.gxp`  
Otwórz projekt "demonstracyjne. GXP"


`guix_studio.exe –n –p demo.gxp`  
Generuj wszystkie pliki wyjściowe projektu demonstracyjnego. GXP.

`guix_studio.exe –n –r –p demo.gxp`  
Generuj pliki zasobów dla demonstracji. GXP projektu


## <a name="command-line-options"></a>Opcje Command-Line

```C
***-n --nogui***  
```

Opcja "nogui". Poinformuj GUIX Studio o konieczności uruchomienia bez uruchamiania interfejsu interfejsu użytkownika okna.

```C
***-o pathname***  
***--log***  
```

Log — opcja, określ plik dziennika.

```C
***-b***  
***--binary***  
```

Opcja zasobów binarnych. Tworzy plik zasobów binarnych, a nie plik C.

```C
***-d display1, display2***  
***--display***  
```

Opcja wyświetlania nazw. Jeśli ta opcja jest używana, tylko określone nazwy wyświetlane są zawarte w wygenerowanych plikach zasobów lub specyfikacji. Jeśli ta opcja nie jest używana, są uwzględniane wszystkie ekrany.

```C
***-t theme1, theme2***  
***--theme***  
```

Nazwa motywu — opcja. Jeśli ta opcja jest używana, tylko określone nazwy motywu są zawarte w wygenerowanych plikach zasobów lub specyfikacji. Jeśli ta opcja nie jest używana, zostaną uwzględnione wszystkie motywy.

```C
***-l langage1, language2***  
***--language***  
```

Nazwa języka (s). Jeśli ta opcja jest używana, określone nazwy języków są zawarte w wygenerowanych plikach zasobów lub specyfikacji. W przeciwnym razie są uwzględniane wszystkie nazwy języków.

```C
***-r [filename]***  
***--resource***  
```

Opcja zasobu określa, że program Studio ma generować plik zasobów dla wcześniej wydanych ekranów, motywów i języków.

```C
***-s [filename]***  
***--specification***  
```

Opcja Specyfikacja określa, że Studio ma generować plik specyfikacji dla wyszukanych wyświetlaczy, motywów i języków.

```C
***-p project_pathname***  
***--project***  
```

Opcja Nazwa ścieżki projektu, określ przykładowy projekt do załadowania.

```C
***-i [pathname]***  
***--import***  
```

Importuj ciąg z pliku w formacie XLIFF lub CSV.

***--big_endian***  
Generowanie danych zasobów w formacie big-endian.
