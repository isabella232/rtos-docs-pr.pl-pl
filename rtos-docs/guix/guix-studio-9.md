---
title: Wiersz polecenia programu GUIX Studio
description: Program GUIX Studio udostępnia wywołania wiersza polecenia przydatne w przypadku potoków kompilacji, które są wymagane do aktualizowania plików wyjściowych generowanych przez program Studio.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bd88054d974aabea30b50c6f4e10b4c5df9994db03ab84a4a5d8f9394b4d6ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785400"
---
# <a name="chapter-9-guix-studio-command-line"></a>Rozdział 9. Wiersz polecenia programu GUIX Studio

Program GUIX Studio obsługuje wywołania wiersza polecenia, co jest przydatne w przypadku potoków kompilacji wymaganych do aktualizacji plików wyjściowych generowanych przez program Studio.

## <a name="command-line-usage"></a>Command-Line użycia

**Użycie:** guix_studio \[ ARGUMENT OPCJI \] \[\]

Otwórz *projekt .gxp.*

Otwórz projekt Studio i wygeneruj żądane pliki wyjściowe.


**Przykłady:**

`guix_studio demo.gxp`  
Otwieranie projektu "demo.gxp"


`guix_studio.exe –p demo.gxp`  
Otwieranie projektu "demo.gxp"


`guix_studio.exe –n –p demo.gxp`  
Wygeneruj wszystkie pliki wyjściowe projektu demo.gxp.

`guix_studio.exe –n –r –p demo.gxp`  
Generowanie plików zasobów projektu demo.gxp


## <a name="command-line-options"></a>Command-Line opcji

```C
***-n --nogui***  
```

Opcja "nogui". Poinformuj program GUIX Studio, aby działał bez uruchamiania interfejsu użytkownika obsługi okien.

```C
***-o pathname***  
***--log***  
```

Opcja Dziennika, określ plik dziennika.

```C
***-b***  
***--binary***  
```

Opcja zasobu binarnego. Tworzy plik zasobów binarnych, a nie plik C.

```C
***-d display1, display2***  
***--display***  
```

Opcja Nazwy wyświetlane. Jeśli ta opcja jest używana, wówczas tylko określone nazwy wyświetlane są uwzględniane w plikach wygenerowanych zasobów lub specyfikacji. Jeśli ta opcja nie jest używana, uwzględniane są wszystkie ekrany.

```C
***-t theme1, theme2***  
***--theme***  
```

Nazwa motywu, opcja. Jeśli ta opcja jest używana, wówczas tylko nazwy określonego motywu są uwzględniane w plikach wygenerowanych zasobów lub specyfikacji. Jeśli ta opcja nie jest używana, wszystkie motywy są uwzględniane.

```C
***-l langage1, language2***  
***--language***  
```

Nazwa(y) języka. Jeśli ta opcja jest używana, określone nazwy języków są uwzględniane w wygenerowanych plikach zasobów lub specyfikacji. W przeciwnym razie uwzględniane są wszystkie nazwy języków.

```C
***-r [filename]***  
***--resource***  
```

Opcja zasobu określa, że program Studio powinien tworzyć plik zasobów dla wcześniej wyznaczonych ekranów, motywów i języków.

```C
***-s [filename]***  
***--specification***  
```

Opcja specyfikacji określa, że program Studio powinien tworzyć plik specyfikacji dla wyznaczonych ekranów, motywów i języków.

```C
***-p project_pathname***  
***--project***  
```

Project pathname określ przykładowy projekt do załadowania.

```C
***-i [pathname]***  
***--import***  
```

Zaimportuj ciąg z pliku w formacie xliff lub csv.

***— big_endian***  
Generowanie danych zasobów w formacie big endian.
