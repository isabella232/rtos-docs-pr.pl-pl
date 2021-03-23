---
title: Dodatek D-GUIX pędzla, kanwy i atrybuty gradientu
description: Dowiedz się więcej na temat GUIX pędzla, kanwy i atrybutów gradientu.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823179"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a>Dodatek D-GUIX pędzla, kanwy i atrybuty gradientu

__**Style pędzla:**__

**GX_BRUSH_OUTLINE**
- Wartość: 0x0000
- Opis: ten styl pędzla dotyczy funkcji rysowania kształtów, takich jak gx_canvas_rectangle_draw lub gx_canvas_polygon_draw. Ten styl wskazuje, że kształt powinien być wyróżniony, oprócz opcjonalnego wypełnienia. Jeśli styl GX_BRUSH_OUTLINE jest ustawiony i GX_BRSUH_SOLID_FILL jest wyczyszczone, kształt jest tylko obramowany.

**GX_BRUSH_SOLID_FILL**
- Wartość: 0x0001
- Opis: ten styl pędzla ma zastosowanie do funkcji rysowania kształtów i wskazuje, że żądany kształt powinien być wypełniony pełnym kolorem przy użyciu bieżącego koloru wypełnienia pędzla.

**GX_BRUSH_PIXELMAP_FILL**
- Wartość: 0x0002
- Opis: ten styl pędzla ma zastosowanie do funkcji rysowania kształtów i wskazuje, że żądany kształt powinien być wypełniony deseniem z bieżącym Pixelmap pędzla.

**GX_BRUSH_ALIAS**
- Wartość: 0x0004
- Opis: ten styl pędzla dotyczy wszystkich rysowania linii i konturów kształtów. Jeśli ta flaga jest ustawiona, linie i konspekty są rysowane z dokładniejszą, ale również bardziej czasochłonne algorytmy rysowania z aliasami. Ta flaga stylu jest używana tylko dla głębi kolorów 16-BPP i wyższych.

**GX_BRUSH_UNDERLINE**
- Wartość: 0x0008
- Opis: Ta flaga ma zastosowanie do rysowania tekstu i wskazuje, że kolejny tekst rysowany powinien być podkreślony.

**GX_BRUSH_ROUND**
- Wartość: 0x0010
- Opis: Ta flaga ma zastosowanie do rysowania linii i wskazuje, że końcówki linii są rysowane przy użyciu okrągłego lub okrągłego kształtu, a nie domyślnego kształtu kwadratowego.

__**Flagi kanwy:**__

**GX_CANVAS_SIMPLE**
- Wartość: 0x01
- Opis: Kanwa pamięci, która jest używana do rysowania poza ekranem.

**GX_CANVAS_MANAGED**
- Wartość: 0x02
- Opis: Kanwa, która jest automatycznie opróżniana do aktywnego wyświetlania, w ramach procesu konstruowania złożonego lub jako część operacji przełączania buforu dla architektury jednej kanwy.

**GX_CANVAS_VISIBLE**
- Wartość: 0x04
- Opis: Ta flaga może służyć do włączania i wyłączania kanwy bez utraty zawartości rysunku kanwy.

**GX_CANVAS_MODIFIED**
- Wartość: 0x08
- Opis: zarezerwowane do użytku w przyszłości.

**GX_CANVAS_COMPOSITE**
- Wartość: 0x20
- Opis: Ta flaga jest używana przez aplikację podczas konfigurowania systemu wielokanwowego, który będzie złożonym wieloma zarządzanymi kanwami na kanwę kompozytową, a kompozyt jest kierowany do buforu ramki sprzętowej.

__**Typy gradientów:**__

**GX_GRADIENT_TYPE_VERTICAL**
- Wartość: 0x01
- Opis: Tworzy gradient alphamap w pionie.

**GX_GRADIENT_TYPE_ALPHA**
- Wartość: 0x02
- Opis: umożliwia tworzenie gradientu stylu mapy alfa. Jest to obecnie jedyny obsługiwany styl gradientu.

**GX_GRADIENT_TYPE_MIRROR**
- Wartość: 0x04
- Opis: Ta flaga wskazuje, że gradient ma być ustawiony na wartość szczytową w środku zakresu szerokość/wysokość, i wrócić do wartości początkowej, ponieważ osiągnie ona prawą/dolną krawędź. Bez tej flagi stylu gradient będzie gradientem liniowym od góry do dołu lub od lewej do prawej, w zależności od flagi GX_GRADIENT_TYPE_VERTICAL.