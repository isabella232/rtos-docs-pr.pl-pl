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
# <a name="chapter-9-guix-studio-command-line"></a><span data-ttu-id="baa48-103">Rozdział 9: GUIX Studio — wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="baa48-103">Chapter 9: GUIX Studio Command Line</span></span>

<span data-ttu-id="baa48-104">Program GUIX Studio obsługuje wywoływanie wiersza polecenia, co jest przydatne w przypadku potoków kompilacji, które są wymagane do aktualizacji plików wyjściowych generowanych przez program Studio.</span><span class="sxs-lookup"><span data-stu-id="baa48-104">GUIX Studio supports command-line invocation,  which is useful for build pipelines that are required to update of the Studio-generated output files.</span></span>

## <a name="command-line-usage"></a><span data-ttu-id="baa48-105">Użycie Command-Line</span><span class="sxs-lookup"><span data-stu-id="baa48-105">Command-Line Usage</span></span>

<span data-ttu-id="baa48-106">**Użycie:** guix_studio \[ \] \[ argument opcji\]</span><span class="sxs-lookup"><span data-stu-id="baa48-106">**Usage:** guix_studio \[OPTION\] \[ARGUMENT\]</span></span>

<span data-ttu-id="baa48-107">Otwórz projekt *. GXP* .</span><span class="sxs-lookup"><span data-stu-id="baa48-107">Open the *.gxp* project.</span></span>

<span data-ttu-id="baa48-108">Otwórz projekt Studio i Wygeneruj żądane pliki wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="baa48-108">Open the Studio project and generate desired output files.</span></span>


<span data-ttu-id="baa48-109">**Przykłady:**</span><span class="sxs-lookup"><span data-stu-id="baa48-109">**Examples:**</span></span>

`guix_studio demo.gxp`  
<span data-ttu-id="baa48-110">Otwórz projekt "demonstracyjne. GXP"</span><span class="sxs-lookup"><span data-stu-id="baa48-110">Open "demo.gxp" project</span></span>


`guix_studio.exe –p demo.gxp`  
<span data-ttu-id="baa48-111">Otwórz projekt "demonstracyjne. GXP"</span><span class="sxs-lookup"><span data-stu-id="baa48-111">Open "demo.gxp" project</span></span>


`guix_studio.exe –n –p demo.gxp`  
<span data-ttu-id="baa48-112">Generuj wszystkie pliki wyjściowe projektu demonstracyjnego. GXP.</span><span class="sxs-lookup"><span data-stu-id="baa48-112">Generate all output files of demo.gxp project.</span></span>

`guix_studio.exe –n –r –p demo.gxp`  
<span data-ttu-id="baa48-113">Generuj pliki zasobów dla demonstracji. GXP projektu</span><span class="sxs-lookup"><span data-stu-id="baa48-113">Generate resource files of demo.gxp project</span></span>


## <a name="command-line-options"></a><span data-ttu-id="baa48-114">Opcje Command-Line</span><span class="sxs-lookup"><span data-stu-id="baa48-114">Command-Line Options</span></span>

```C
***-n --nogui***  
```

<span data-ttu-id="baa48-115">Opcja "nogui".</span><span class="sxs-lookup"><span data-stu-id="baa48-115">The "nogui" option.</span></span> <span data-ttu-id="baa48-116">Poinformuj GUIX Studio o konieczności uruchomienia bez uruchamiania interfejsu interfejsu użytkownika okna.</span><span class="sxs-lookup"><span data-stu-id="baa48-116">Tell GUIX Studio to run without starting the windowing UI interface.</span></span>

```C
***-o pathname***  
***--log***  
```

<span data-ttu-id="baa48-117">Log — opcja, określ plik dziennika.</span><span class="sxs-lookup"><span data-stu-id="baa48-117">Log option, specify a log file.</span></span>

```C
***-b***  
***--binary***  
```

<span data-ttu-id="baa48-118">Opcja zasobów binarnych.</span><span class="sxs-lookup"><span data-stu-id="baa48-118">Binary resource option.</span></span> <span data-ttu-id="baa48-119">Tworzy plik zasobów binarnych, a nie plik C.</span><span class="sxs-lookup"><span data-stu-id="baa48-119">Produces a binary resource file rather than a C file.</span></span>

```C
***-d display1, display2***  
***--display***  
```

<span data-ttu-id="baa48-120">Opcja wyświetlania nazw.</span><span class="sxs-lookup"><span data-stu-id="baa48-120">Display names option.</span></span> <span data-ttu-id="baa48-121">Jeśli ta opcja jest używana, tylko określone nazwy wyświetlane są zawarte w wygenerowanych plikach zasobów lub specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="baa48-121">If this option is used, then only the specified display names are included in any generated resource or specification files.</span></span> <span data-ttu-id="baa48-122">Jeśli ta opcja nie jest używana, są uwzględniane wszystkie ekrany.</span><span class="sxs-lookup"><span data-stu-id="baa48-122">If this option is not used,  all displays are included.</span></span>

```C
***-t theme1, theme2***  
***--theme***  
```

<span data-ttu-id="baa48-123">Nazwa motywu — opcja.</span><span class="sxs-lookup"><span data-stu-id="baa48-123">Theme name(s) option.</span></span> <span data-ttu-id="baa48-124">Jeśli ta opcja jest używana, tylko określone nazwy motywu są zawarte w wygenerowanych plikach zasobów lub specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="baa48-124">If this option is used, then only the specified theme names are included in any generated resource or specification files.</span></span> <span data-ttu-id="baa48-125">Jeśli ta opcja nie jest używana, zostaną uwzględnione wszystkie motywy.</span><span class="sxs-lookup"><span data-stu-id="baa48-125">If this option is not used, all themes are included.</span></span>

```C
***-l langage1, language2***  
***--language***  
```

<span data-ttu-id="baa48-126">Nazwa języka (s).</span><span class="sxs-lookup"><span data-stu-id="baa48-126">Language name(s) option.</span></span> <span data-ttu-id="baa48-127">Jeśli ta opcja jest używana, określone nazwy języków są zawarte w wygenerowanych plikach zasobów lub specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="baa48-127">If this option is used,  the specified language names are included in the generated resource or specification files.</span></span> <span data-ttu-id="baa48-128">W przeciwnym razie są uwzględniane wszystkie nazwy języków.</span><span class="sxs-lookup"><span data-stu-id="baa48-128">Otherwise all language names are included.</span></span>

```C
***-r [filename]***  
***--resource***  
```

<span data-ttu-id="baa48-129">Opcja zasobu określa, że program Studio ma generować plik zasobów dla wcześniej wydanych ekranów, motywów i języków.</span><span class="sxs-lookup"><span data-stu-id="baa48-129">The resource option, specifies that Studio should produce a resource file for previously designated display(s), theme(s), and language(s).</span></span>

```C
***-s [filename]***  
***--specification***  
```

<span data-ttu-id="baa48-130">Opcja Specyfikacja określa, że Studio ma generować plik specyfikacji dla wyszukanych wyświetlaczy, motywów i języków.</span><span class="sxs-lookup"><span data-stu-id="baa48-130">The specification option, specify that studio should produce a specification file for designated display(s), theme(s), and language(s).</span></span>

```C
***-p project_pathname***  
***--project***  
```

<span data-ttu-id="baa48-131">Opcja Nazwa ścieżki projektu, określ przykładowy projekt do załadowania.</span><span class="sxs-lookup"><span data-stu-id="baa48-131">Project pathname option, specify the example project to be loaded.</span></span>

```C
***-i [pathname]***  
***--import***  
```

<span data-ttu-id="baa48-132">Importuj ciąg z pliku w formacie XLIFF lub CSV.</span><span class="sxs-lookup"><span data-stu-id="baa48-132">Import string from xliff or csv format file.</span></span>

<span data-ttu-id="baa48-133">***--big_endian***</span><span class="sxs-lookup"><span data-stu-id="baa48-133">***--big_endian***</span></span>  
<span data-ttu-id="baa48-134">Generowanie danych zasobów w formacie big-endian.</span><span class="sxs-lookup"><span data-stu-id="baa48-134">Generate resource data in big-endian format.</span></span>
