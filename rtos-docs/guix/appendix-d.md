---
title: Dodatek D — atrybuty pędzla GUIX, kanwy i gradientu
description: Dowiedz się więcej o atrybutach pędzla GUIX, kanwy i gradientu.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9fbc98f1094cab6be4bc0826fef7c0feb77b50b066b22342cd52404bd85ff98e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784635"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a>Dodatek D — atrybuty pędzla GUIX, kanwy i gradientu

__**Style pędzla:**__

**GX_BRUSH_OUTLINE**
- Wartość: 0x0000
- Opis: Ten styl pędzla ma zastosowanie do funkcji rysowania kształtów, takich jak gx_canvas_rectangle_draw lub gx_canvas_polygon_draw. Ten styl wskazuje, że oprócz opcjonalnego wypełnienia kształt powinien być konturowany. Jeśli styl GX_BRUSH_OUTLINE jest ustawiony i GX_BRSUH_SOLID_FILL, kształt jest tylko określony.

**GX_BRUSH_SOLID_FILL**
- Wartość: 0x0001
- Opis: Ten styl pędzla ma zastosowanie do funkcji rysowania kształtów i wskazuje, że żądany kształt powinien zostać wypełniony pełnym kolorem przy użyciu bieżącego koloru wypełnienia pędzlem.

**GX_BRUSH_PIXELMAP_FILL**
- Wartość: 0x0002
- Opis: Ten styl pędzla ma zastosowanie do funkcji rysowania kształtów i wskazuje, że żądany kształt powinien być wzorcem wypełnionym bieżącą mapą pikseli pędzla.

**GX_BRUSH_ALIAS**
- Wartość: 0x0004
- Opis: Ten styl pędzla ma zastosowanie do wszystkich konturów kształtów i rysowania linii. Jeśli ta flaga jest ustawiona, linie i kontury są rysowane z bardziej dokładnymi, ale również czasochłonnym algorytmami rysowania z anty aliasami. Ta flaga stylu jest używana tylko w przypadku głębokości kolorów 16-bpp i wyższych.

**GX_BRUSH_UNDERLINE**
- Wartość: 0x0008
- Opis: Ta flaga ma zastosowanie do rysowania tekstu i wskazuje, że kolejny narysowany tekst powinien być podkreślony.

**GX_BRUSH_ROUND**
- Wartość: 0x0010
- Opis: Ta flaga dotyczy rysowania linii i wskazuje, że zakończenia linii są rysowane z okrągłym lub okrągłym kształtem, a nie domyślnym kształtem kwadratowym.

__**Flagi kanwy:**__

**GX_CANVAS_SIMPLE**
- Wartość: 0x01
- Opis: kanwa pamięci używana do rysowania poza ekranem.

**GX_CANVAS_MANAGED**
- Wartość: 0x02
- Opis: Kanwa, która jest automatycznie opróżniona do aktywnego ekranu w ramach złożonego procesu tworzenia lub w ramach operacji przełączania buforu dla architektur z jedną kanwą.

**GX_CANVAS_VISIBLE**
- Wartość: 0x04
- Opis: Ta flaga może służyć do włączanie i wyłączanie kanwy bez utraty zawartości rysowania kanwy.

**GX_CANVAS_MODIFIED**
- Wartość: 0x08
- Opis: Zarezerwowane do użytku w przyszłości.

**GX_CANVAS_COMPOSITE**
- Wartość: 0x20
- Opis: Ta flaga jest używana przez aplikację podczas konfigurowania systemu z wieloma kanwami, który będzie konfigurować wiele zarządzanych kanw w kanwę złożoną, a element złożony jest oparty na buforze ramek sprzętowych.

__**Typy gradientów:**__

**GX_GRADIENT_TYPE_VERTICAL**
- Wartość: 0x01
- Opis: tworzy pionowy gradient alfamapy.

**GX_GRADIENT_TYPE_ALPHA**
- Wartość: 0x02
- Opis: dodaje gradient w stylu mapy alfa. Jest to obecnie jedyny obsługiwany styl gradientu.

**GX_GRADIENT_TYPE_MIRROR**
- Wartość: 0x04
- Opis: Ta flaga wskazuje, że gradient powinien być szczytowy w środku zakresu szerokości/wysokości i wrócić do wartości wyjściowej, gdy osiągnie prawą/dolną krawędź. Bez tej flagi stylu gradient będzie gradientem liniowym od góry do dołu lub od lewej do prawej, w zależności od GX_GRADIENT_TYPE_VERTICAL flagi.