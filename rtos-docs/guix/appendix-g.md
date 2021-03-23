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
# <a name="appendix-g---guix-font-structure"></a><span data-ttu-id="47f74-103">Dodatek G-GUIX — struktura czcionek</span><span class="sxs-lookup"><span data-stu-id="47f74-103">Appendix G - GUIX Font Structure</span></span>

<span data-ttu-id="47f74-104">Czcionki GUIX są zwykle tworzone przez aplikację GUIX Studio, a glify czcionek są renderowane przez sterownik wyświetlania GUIX.</span><span class="sxs-lookup"><span data-stu-id="47f74-104">GUIX fonts are normally produced by the GUIX Studio application, and font glyphs are rendered by the GUIX display driver.</span></span> <span data-ttu-id="47f74-105">Oprogramowanie aplikacji musi określać tylko czcionkę i kolory, które powinny być używane dla każdego widżetu wyświetlania tekstu.</span><span class="sxs-lookup"><span data-stu-id="47f74-105">The application software need only specify the font and colors that each text display widget should use.</span></span> <span data-ttu-id="47f74-106">Struktury danych czcionek GUIX są udokumentowane w tym miejscu pod kątem kompletności i umożliwiają deweloperom tworzenie własnych metod generowania lub konwertowania innych czcionek w formacie czcionki GUIX.</span><span class="sxs-lookup"><span data-stu-id="47f74-106">The GUIX font data structures are documented here for completeness, and to enable developers to create their own methods for generating or converting other fonts into the GUIX font format.</span></span>

<span data-ttu-id="47f74-107">Każda czcionka GUIX rozpoczyna się od struktury GX_FONT.</span><span class="sxs-lookup"><span data-stu-id="47f74-107">Each GUIX font starts with a GX_FONT structure.</span></span> <span data-ttu-id="47f74-108">Struktura GX_FONT definiuje globalne parametry czcionki, takie jak znak zawarty w czcionce i wysokość linii czcionki.</span><span class="sxs-lookup"><span data-stu-id="47f74-108">The GX_FONT structure defines global font parameters, such as the character included within the font and the line height of the font.</span></span> <span data-ttu-id="47f74-109">Struktura GX_FONT wskazuje na tablicę struktur GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="47f74-109">The GX_FONT structure points at an array of GX_GLYPH structures.</span></span> <span data-ttu-id="47f74-110">Każda struktura GX_GLYPH definiuje szerokość, Wysokość i Przesunięcie linii bazowej jednego określonego glifu znakowego.</span><span class="sxs-lookup"><span data-stu-id="47f74-110">Each GX_GLYPH structure defines the width, height, and baseline offset of one specific character glyph.</span></span> <span data-ttu-id="47f74-111">Struktura GX_GLYPH wskazuje również rzeczywiste dane mapy bitowej symboli (które mogą mieć wartość NULL w przypadku znaków odstępu).</span><span class="sxs-lookup"><span data-stu-id="47f74-111">The GX_GLYPH structure also points to the actual glyph bitmap data (which may be NULL for whitespace characters).</span></span>

<span data-ttu-id="47f74-112">Struktura GX_FONT, zawarte w gx_api. h, jest zadeklarowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="47f74-112">The GX_FONT structure, contained in gx_api.h, is declared as follows:</span></span>

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

<span data-ttu-id="47f74-113">Pole gx_font_format definiuje bity czcionki w pikselach i innych flagach, zgodnie z definicją w pliku nagłówkowym gx_api. h.</span><span class="sxs-lookup"><span data-stu-id="47f74-113">The gx_font_format field defines the font bits-per-pixel and other flags, as defined in the gx_api.h header file.</span></span>

<span data-ttu-id="47f74-114">Gx_font_prespace definiuje miejsce w pikselach, aby pominąć każdy wiersz tekstu w wielowierszowym wyświetlaniu tekstu.</span><span class="sxs-lookup"><span data-stu-id="47f74-114">The gx_font_prespace defines the pixel space to skip above each line of text in a multi-line text display.</span></span>

<span data-ttu-id="47f74-115">Pole gx_font_postspace definiuje odstęp w pikselach, który zostanie pominięty poniżej każdego wiersza tekstu w wielowierszowym wyświetlaniu tekstu.</span><span class="sxs-lookup"><span data-stu-id="47f74-115">The gx_font_postspace field defines the pixel space to skip below each line of text in a multi-line text display.</span></span>

<span data-ttu-id="47f74-116">Pole gx_font_line_height definiuje wysokość najwyższego glifu w czcionce.</span><span class="sxs-lookup"><span data-stu-id="47f74-116">The gx_font_line_height field defines the height of the tallest glyph in the font.</span></span>

<span data-ttu-id="47f74-117">Pole gx_font_baseline definiuje odległość (w pikselach) od górnego wiersza pikseli symboli do linii bazowej czcionki.</span><span class="sxs-lookup"><span data-stu-id="47f74-117">The gx_font_baseline field defines the distance, in pixels, from the top row of glyph pixels to the font baseline.</span></span>

<span data-ttu-id="47f74-118">Pole gx_font_first_glyph definiuje pierwsze kodowanie znaków Unicode zawarte na tej stronie czcionki.</span><span class="sxs-lookup"><span data-stu-id="47f74-118">The gx_font_first_glyph field defines the first Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="47f74-119">Pole gx_font_last_glyph definiuje ostatnie kodowanie znaków Unicode zawarte na tej stronie czcionki.</span><span class="sxs-lookup"><span data-stu-id="47f74-119">The gx_font_last_glyph field defines the last Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="47f74-120">Wskaźnik gx_font_glyphs wskazuje tablicę GX_GLYPH struktur.</span><span class="sxs-lookup"><span data-stu-id="47f74-120">The gx_font_glyphs pointer points to an array of GX_GLYPH structures.</span></span> <span data-ttu-id="47f74-121">Ta tablica musi mieć rozmiar równy liczbie znaków znajdujących się na tej stronie czcionki, tj.</span><span class="sxs-lookup"><span data-stu-id="47f74-121">This array must be equal in size to the number of characters contained on this font page, i.e</span></span> <span data-ttu-id="47f74-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span><span class="sxs-lookup"><span data-stu-id="47f74-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span></span>

<span data-ttu-id="47f74-123">Element członkowski gx_font_next_page jest używany w przypadku wielu czcionek strony.</span><span class="sxs-lookup"><span data-stu-id="47f74-123">The gx_font_next_page member is used for multiple page fonts.</span></span> <span data-ttu-id="47f74-124">Dla rozszerzonych zestawów znaków i optymalizacji rozmiaru tablic struktury GX_GLYPH są używane różne czcionki strony.</span><span class="sxs-lookup"><span data-stu-id="47f74-124">Multiple page fonts are used for extended character sets and to optimize the size of the GX_GLYPH structure arrays.</span></span> <span data-ttu-id="47f74-125">Jeśli wszystkie znaki czcionki znajdują się w jednej stronie czcionki lub jeśli jest to Ostatnia strona czcionki, w której znajduje się gx_font_next_page element członkowski jest ustawiony na GX_NULL.</span><span class="sxs-lookup"><span data-stu-id="47f74-125">If all of the characters of the font are contained within one font page, or if this is the last page of the font in question, the gx_font_next_page member is set to GX_NULL.</span></span>

<span data-ttu-id="47f74-126">Jak wspomniano powyżej, powyższa struktura GX_FONT zawiera wskaźnik do tablicy GX_GLYPHS struktur.</span><span class="sxs-lookup"><span data-stu-id="47f74-126">As noted above, the GX_FONT structure above contains a pointer to an array of GX_GLYPHS structures.</span></span> <span data-ttu-id="47f74-127">Dla każdego znaku na stronie czcionki musi istnieć jedna struktura GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="47f74-127">There must be one GX_GLYPH structure for each character on the font page.</span></span> <span data-ttu-id="47f74-128">Struktura GX_GLYPH jest definiowana jako:</span><span class="sxs-lookup"><span data-stu-id="47f74-128">The GX_GLYPH structure is defined as:</span></span>

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

<span data-ttu-id="47f74-129">Wskaźnik gx_glyph_map wskazuje mapę bitową symboli.</span><span class="sxs-lookup"><span data-stu-id="47f74-129">The gx_glyph_map pointer points to the glyph bitmap.</span></span> <span data-ttu-id="47f74-130">Ten wskaźnik może być GX_NULL dla białych znaków.</span><span class="sxs-lookup"><span data-stu-id="47f74-130">This pointer may be GX_NULL for whitespace characters.</span></span> <span data-ttu-id="47f74-131">Dane mapy bitowej są kodowane jako 1 BPP, 2 BPP, 4 BPP lub 8 BPP wartości alpha.</span><span class="sxs-lookup"><span data-stu-id="47f74-131">The bitmap data is encoded as 1 bpp, 2 bpp, 4 bpp, or 8 bpp alpha values.</span></span> <span data-ttu-id="47f74-132">W przypadku danych 1-bitowych wartość 1 oznacza, że piksela powinna być zapisywana w kolorze pierwszego planu, a wartość 0 oznacza, że piksel jest przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="47f74-132">For 1 bit data, a value of 1 indicates that the pixel should be written in the foreground color, and a value of 0 indicates that the pixel is transparent.</span></span> <span data-ttu-id="47f74-133">W przypadku 8-bitowych danych wartości z zakresu od 0 (w pełni przezroczyste) do 255 (w pełni nieprzezroczyste).</span><span class="sxs-lookup"><span data-stu-id="47f74-133">For 8 bit data, the values range from 0 (fully transparent) to 255 (fully opague).</span></span> <span data-ttu-id="47f74-134">Cała wartość pośrednia reprezentuje wartość mieszania dla czcionek antyaliasowych.</span><span class="sxs-lookup"><span data-stu-id="47f74-134">All intermediate value represent a blending value for anti-aliased fonts.</span></span> <span data-ttu-id="47f74-135">Dane mapy bitowej symboli są zawsze dopełniane do pełnego wyrównania bajtowego dla formatów przy użyciu mniej niż 8bpp wartości danych.</span><span class="sxs-lookup"><span data-stu-id="47f74-135">The glyph bitmap data is always padded to full byte alignment for formats using less than 8bpp data values.</span></span>

<span data-ttu-id="47f74-136">Wartości gx_glyph_ascent i gx_glyph_descent umieszczają symbol w pionie w odniesieniu do linii bazowej czcionki.</span><span class="sxs-lookup"><span data-stu-id="47f74-136">The gx_glyph_ascent and gx_glyph_descent values position the glyph vertically with respect to the font baseline.</span></span>

<span data-ttu-id="47f74-137">Wartości gx_glyph_width i gx_glyph_height określają rozmiar danych mapy bitowej symboli.</span><span class="sxs-lookup"><span data-stu-id="47f74-137">The gx_glyph_width and gx_glyph_height values specify the size of the glyph bitmap data.</span></span>

<span data-ttu-id="47f74-138">Wartość gx_glyph_advance Określa szerokość pikseli, aby przejść do pozycji rysowania po narysowaniu glifu (może nie być taka sama jak szerokość glifu).</span><span class="sxs-lookup"><span data-stu-id="47f74-138">The gx_glyph_advance value specifies the pixel width to advance the drawing position after drawing the glyph (this may not be equal to the glyph width).</span></span>

<span data-ttu-id="47f74-139">Wartość gx_glyph_leading określa piksele do założenia w kierunku x przed renderowaniem glifu.</span><span class="sxs-lookup"><span data-stu-id="47f74-139">The gx_glyph_leading value specifies the pixels to advance in the x-direction prior to rendering the glyph.</span></span>