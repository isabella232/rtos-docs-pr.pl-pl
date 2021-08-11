---
title: Dodatek G — struktura czcionek GUIX
description: Dowiedz się więcej o strukturze czcionek GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4c7cedb49268f97f8e1fc4cd28329b0b61e697d57562865896f0502bdd1d45f1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784193"
---
# <a name="appendix-g---guix-font-structure"></a>Dodatek G — struktura czcionek GUIX

Czcionki GUIX są zwykle produkowane przez aplikację GUIX Studio, a glyphs czcionek są renderowane przez sterownik wyświetlania GUIX. Oprogramowanie aplikacji musi określić tylko czcionkę i kolory, których powinien używać każdy widżet wyświetlania tekstu. Struktury danych czcionek GUIX zostały udokumentowane tutaj, aby uzyskać pełną dokumentację i umożliwić deweloperom tworzenie własnych metod generowania lub konwertowania innych czcionek do formatu czcionek GUIX.

Każda czcionka GUIX rozpoczyna się od GX_FONT struktury. Struktura GX_FONT definiuje globalne parametry czcionki, takie jak znak uwzględniony w czcionce i wysokość wiersza czcionki. Struktura GX_FONT punkty na tablicy GX_GLYPH struktur. Każda GX_GLYPH definiuje szerokość, wysokość i przesunięcie linii bazowej jednego określonego znaku. Struktura GX_GLYPH wskazuje również rzeczywiste dane mapy bitowej glifów (które mogą mieć wartość NULL dla znaków odstępu).

Struktura GX_FONT, zawarta w gx_api.h, jest zadeklarowana w następujący sposób:

```c
typedef struct GX_FONT_STRUCT
{
    GX_UBYTE                     gx_font_format
    GX_UBYTE                     gx_font_prespace
    GX_UBYTE                     gx_font_postspace
    GX_UBYTE                     gx_font_line_height 
    GX_UBYTE                     gx_font_baseline
    USHORT                       gx_font_first_glyph
    USHORT                       gx_font_last_glyph 
    GX_CONST GX_GLYPH           *gx_font_glyphs
    const struct GX_FONT_STRUCT *gx_font_next_page
} GX_FONT;
```

Pole gx_font_format definiuje czcionkę bity na piksel i inne flagi, zgodnie z definicją w pliku nagłówka gx_api.h.

Ten gx_font_prespace definiuje obszar pikseli, który ma być pomijany nad każdym wierszem tekstu na ekranie tekstowym z wieloma wierszami.

Pole gx_font_postspace definiuje przestrzeń pikseli, która ma być pomijana poniżej każdego wiersza tekstu na ekranie tekstowym z wieloma wierszami.

Pole gx_font_line_height definiuje wysokość najwyższego symbolu w czcionki.

Pole gx_font_baseline definiuje odległość (w pikselach) od górnego wiersza pikseli symbolu do linii bazowej czcionki.

Pole gx_font_first_glyph definiuje pierwsze kodowanie znaków Unicode zawarte na tej stronie czcionki.

Pole gx_font_last_glyph definiuje ostatnie kodowanie znaków Unicode zawarte na tej stronie czcionki.

Wskaźnik gx_font_glyphs wskazuje na tablicę GX_GLYPH struktur. Ta tablica musi mieć taki sam rozmiar jak liczba znaków zawartych na tej stronie czcionki, tj. (gx_font_last_glyph – gx_font_first_glyph) + 1.

Ten gx_font_next_page jest używany w przypadku wielu czcionek stron. Wiele czcionek stron jest używanych w rozszerzonych zestawach znaków i do optymalizowania rozmiaru GX_GLYPH tablic struktur. Jeśli wszystkie znaki czcionki znajdują się na jednej stronie czcionki lub jeśli jest to ostatnia strona czcionki, oznacza to, że gx_font_next_page jest ustawiony na GX_NULL.

Jak wspomniano powyżej, GX_FONT powyżej zawiera wskaźnik do tablicy GX_GLYPHS struktur. Dla każdego znaku na stronie czcionki musi GX_GLYPH jedna struktura. Struktura GX_GLYPH jest zdefiniowana jako:

```c
typedef struct GX_GLYPH_STRUCT
{
    GX_CONST GX_UBYTE *gx_glyph_map;
    GX_BYTE            gx_glyph_ascent;
    GX_BYTE            gx_glyph_descent;
    GX_BYTE            gx_glyph_advance;
    GX_BYTE            gx_glyph_leading;
    GX_UBYTE           gx_glyph_width;
    GX_UBYTE           gx_glyph_height;
} GX_GLYPH;
```

Wskaźnik gx_glyph_map wskazuje mapę bitową glifów. Ten wskaźnik może być GX_NULL znaków odstępu. Dane mapy bitowej są kodowane jako 1 bpp, 2 bpp, 4 bpp lub 8 wartości alfa bpp. W przypadku danych 1-bitowych wartość 1 wskazuje, że piksel powinien być zapisany w kolorze pierwszego planu, a wartość 0 oznacza, że piksel jest przezroczysty. W przypadku danych 8-bitowych wartości z zakresu od 0 (w pełni przezroczyste) do 255 (w pełni opague). Wszystkie wartości pośrednie reprezentują wartość mieszania dla czcionek anty aliasów. Dane mapy bitowej glifów są zawsze dopełnione w celu pełnego wyrównania bajtów dla formatów używających wartości danych mniejszej niż 8bpp.

Symbol gx_glyph_ascent i gx_glyph_descent są pozycjonowane w pionie względem linii bazowej czcionki.

Wartości gx_glyph_width i gx_glyph_height określają rozmiar danych mapy bitowej glifów.

Wartość gx_glyph_advance określa szerokość pikseli, aby przejść do pozycji rysowania po narysować glif (może to nie być równe szerokości glifów).

Wartość gx_glyph_leading określa piksele, które mają przejść w kierunku x przed renderowaniem glifów.