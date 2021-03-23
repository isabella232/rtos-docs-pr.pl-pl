---
title: Dodatek G-GUIX — struktura czcionek
description: Dowiedz się więcej na temat struktury czcionek GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5f0232e6c21851014b85cfe7b07795062fd1e8d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823172"
---
# <a name="appendix-g---guix-font-structure"></a>Dodatek G-GUIX — struktura czcionek

Czcionki GUIX są zwykle tworzone przez aplikację GUIX Studio, a glify czcionek są renderowane przez sterownik wyświetlania GUIX. Oprogramowanie aplikacji musi określać tylko czcionkę i kolory, które powinny być używane dla każdego widżetu wyświetlania tekstu. Struktury danych czcionek GUIX są udokumentowane w tym miejscu pod kątem kompletności i umożliwiają deweloperom tworzenie własnych metod generowania lub konwertowania innych czcionek w formacie czcionki GUIX.

Każda czcionka GUIX rozpoczyna się od struktury GX_FONT. Struktura GX_FONT definiuje globalne parametry czcionki, takie jak znak zawarty w czcionce i wysokość linii czcionki. Struktura GX_FONT wskazuje na tablicę struktur GX_GLYPH. Każda struktura GX_GLYPH definiuje szerokość, Wysokość i Przesunięcie linii bazowej jednego określonego glifu znakowego. Struktura GX_GLYPH wskazuje również rzeczywiste dane mapy bitowej symboli (które mogą mieć wartość NULL w przypadku znaków odstępu).

Struktura GX_FONT, zawarte w gx_api. h, jest zadeklarowana w następujący sposób:

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

Pole gx_font_format definiuje bity czcionki w pikselach i innych flagach, zgodnie z definicją w pliku nagłówkowym gx_api. h.

Gx_font_prespace definiuje miejsce w pikselach, aby pominąć każdy wiersz tekstu w wielowierszowym wyświetlaniu tekstu.

Pole gx_font_postspace definiuje odstęp w pikselach, który zostanie pominięty poniżej każdego wiersza tekstu w wielowierszowym wyświetlaniu tekstu.

Pole gx_font_line_height definiuje wysokość najwyższego glifu w czcionce.

Pole gx_font_baseline definiuje odległość (w pikselach) od górnego wiersza pikseli symboli do linii bazowej czcionki.

Pole gx_font_first_glyph definiuje pierwsze kodowanie znaków Unicode zawarte na tej stronie czcionki.

Pole gx_font_last_glyph definiuje ostatnie kodowanie znaków Unicode zawarte na tej stronie czcionki.

Wskaźnik gx_font_glyphs wskazuje tablicę GX_GLYPH struktur. Ta tablica musi mieć rozmiar równy liczbie znaków znajdujących się na tej stronie czcionki, tj. (gx_font_last_glyph – gx_font_first_glyph) + 1.

Element członkowski gx_font_next_page jest używany w przypadku wielu czcionek strony. Dla rozszerzonych zestawów znaków i optymalizacji rozmiaru tablic struktury GX_GLYPH są używane różne czcionki strony. Jeśli wszystkie znaki czcionki znajdują się w jednej stronie czcionki lub jeśli jest to Ostatnia strona czcionki, w której znajduje się gx_font_next_page element członkowski jest ustawiony na GX_NULL.

Jak wspomniano powyżej, powyższa struktura GX_FONT zawiera wskaźnik do tablicy GX_GLYPHS struktur. Dla każdego znaku na stronie czcionki musi istnieć jedna struktura GX_GLYPH. Struktura GX_GLYPH jest definiowana jako:

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

Wskaźnik gx_glyph_map wskazuje mapę bitową symboli. Ten wskaźnik może być GX_NULL dla białych znaków. Dane mapy bitowej są kodowane jako 1 BPP, 2 BPP, 4 BPP lub 8 BPP wartości alpha. W przypadku danych 1-bitowych wartość 1 oznacza, że piksela powinna być zapisywana w kolorze pierwszego planu, a wartość 0 oznacza, że piksel jest przezroczysty. W przypadku 8-bitowych danych wartości z zakresu od 0 (w pełni przezroczyste) do 255 (w pełni nieprzezroczyste). Cała wartość pośrednia reprezentuje wartość mieszania dla czcionek antyaliasowych. Dane mapy bitowej symboli są zawsze dopełniane do pełnego wyrównania bajtowego dla formatów przy użyciu mniej niż 8bpp wartości danych.

Wartości gx_glyph_ascent i gx_glyph_descent umieszczają symbol w pionie w odniesieniu do linii bazowej czcionki.

Wartości gx_glyph_width i gx_glyph_height określają rozmiar danych mapy bitowej symboli.

Wartość gx_glyph_advance Określa szerokość pikseli, aby przejść do pozycji rysowania po narysowaniu glifu (może nie być taka sama jak szerokość glifu).

Wartość gx_glyph_leading określa piksele do założenia w kierunku x przed renderowaniem glifu.