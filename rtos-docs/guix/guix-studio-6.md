---
title: Kod wygenerowany w programie GUIX Studio
description: Po zakończeniu edytowania ekranów i zasobów program GUIX Studio tworzy zestaw plików wyjściowych, które można włączyć do osadzonej aplikacji.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 78b1ec1eea3ec2fcae48c64ad15931f44f34538c876dc8a267c2b1a84234320a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785706"
---
# <a name="chapter-6-guix-studio-generated-code"></a>Rozdział 6. Kod wygenerowany w programie GUIX Studio

Po zakończeniu edytowania ekranów i zasobów program GUIX Studio tworzy zestaw plików wyjściowych, które można włączyć do osadzonej aplikacji. Pliki wyjściowe są generowane przez wybranie pozycji ***** Generuj pliki zasobów _ i *___* Generuj specyfikacje * z Project menu. Pliki kodu źródłowego języka "c" wygenerowane przez program GUIX Studio mają być kompilowane i łączone z osadzonym kodem źródłowym aplikacji. W przypadku produkcji pliku zasobów w formacie binarnym ten plik powinien być zaprogramowany w obszarze magazynu trwałego w miejscu docelowym, a funkcja interfejsu API GUIX gx_binres_theme_install powinna być używana do instalowania zasobów binarnych w czasie wykonywania.

Kod aplikacji osadzonej użytkownika tworzy odwołania do kodu wygenerowanego przez program GUIX Studio. Ponadto kod wygenerowany w programie GUIX Studio oczekuje, że wszystkie niestandardowe funkcje rysowania widżetów, obsługi zdarzeń i alokacji pamięci określone w projekcie zostaną zdefiniowane w kodzie osadzonej aplikacji użytkownika. Jeśli tak nie jest, podczas tworzenia aplikacji będą obecne błędy linków.

> [!NOTE]
> Użytkownik nigdy nie powinien modyfikować kodu wygenerowanego przez program GUIX Studio i nie powinien się o tym opierać. Wszystkie modyfikacje interfejsu użytkownika powinny być wprowadzone w skojarzonym projekcie GUIX Studio. Pozwoli to zachować synchronizację projektu z aplikacją osadzoną.

## <a name="generating-resource-files"></a>Generowanie plików zasobów

Pliki zasobów generowane przez program GUIX Studio zawierają wstępnie zdefiniowane struktury danych, które definiują wszystkie zasoby programu GUIX Studio (kolory, czcionki, mapy pikseli i ciągi), ***co w*** praktyce oznacza wszystkie zasoby zdefiniowane w Widok zasobów projektu. Te pliki zasobów mogą być generowane w kodzie źródłowym lub w postaci binarnej.

Domyślnie są generowane dwa pliki, jeden jest standardowym plikiem kodu źródłowego C, a drugi to plik nagłówka C, który zawiera odwołania zewnętrzne i stałe, które są niezbędne do uzyskania dostępu do zasobów GUIX zdefiniowanych w projekcie przez kod aplikacji. Nazwy plików mają postać:

**{*nazwa projektu*}_resources.h**

**{*project-name*}_resources.c**

Na przykład pliki zasobów utworzone dla ***"prostego" projektu*** GUIX Studio to:

**simple_resources.h**

**simple_resources.c**

Generowanie plików zasobów jest realizowane przez wybranie opcji ***** Generuj pliki zasobów _ w Project _*_menu._*_ Miejsce docelowe plików zasobów jest określone w oknie dialogowym _*_Konfigurowanie_*_ Project, które jest dostępne za pośrednictwem opcji _*_Project/Wyświetla_*_ w pozycji menu *__Konfiguruj_**.

W przypadku zasobów Pixelmap i Font można określić niestandardową nazwę pliku wyjściowego dla każdej mapy pikseli i czcionkę w oknach dialogowych edycji skojarzonych zasobów. Ta funkcja umożliwia umieszczanie bardzo dużych zasobów w odrębnych plikach zamiast umieszczania wszystkich zasobów w jednym wspólnym pliku wyjściowym. Jeśli nie określisz zastąpionej nazwy pliku dla zasobu czcionki lub pixelmap, te zasoby zostaną zapisane we wspólnym pliku zasobów.

Jeśli wolisz używać zasobów binarnych, możesz określić nieprzetworzone lub standardowe formaty danych wyjściowych rekordu S. Zasoby binarne nie są kompilowane ani łączone z kodem aplikacji, ale zamiast tego są ładowane w czasie wykonywania przy użyciu interfejsu API gx_binres_them_load(). Ta usługa interfejsu API tworzy tabele zasobów, które wskazują zasoby przechowywane w pamięci trwałej. Następnie można zainstalować te zasoby z określonym ekranem przy użyciu funkcji gx_display_theme_install();

## <a name="generating-specification-code"></a>Generowanie kodu specyfikacji

Pliki Specification wygenerowane przez program GUIX Studio zawierają cały kod języka C w celu utworzenia interfejsu użytkownika zaprojektowanego w programie GUIX Studio. Ten kod odwołuje się również do plików zasobów wygenerowanych dla tego projektu. Kod aplikacji użytkownika będzie tworzyć wywołania do tego kodu w celu utworzenia obiektów interfejsu użytkownika zdefiniowanych w projekcie. Ponadto kod aplikacji użytkownika zawiera wszystkie niestandardowe funkcje rysowania widżetów, obsługi zdarzeń i alokacji pamięci określone w projekcie. Domyślnie są generowane dwa pliki, jeden jest standardowym plikiem kodu źródłowego C, a drugi jest plikiem nagłówkowym C, który zawiera odwołania zewnętrzne i stałe, które są niezbędne do uzyskania dostępu kodu aplikacji do specyfikacji GUIX Studio. Nazwy plików mają postać:

**{*nazwa projektu*}_specifications.h**

**{*project-name*}_specifications.c**

Na przykład pliki Specification utworzone dla ***"prostego"*** projektu GUIX Studio to:

**simple_specifications.h**

**simple_specifications.c**

Generowanie plików specyfikacji jest realizowane przez wybranie opcji ***** Generuj pliki specyfikacji _ w _*_Project_*_ menu. Miejsce docelowe plików Specification jest określone w oknie dialogowym _*_Konfigurowanie_*_ Project, które jest dostępne za pośrednictwem opcji _*_Project/Wyświetla_*_ w pozycji menu _ *_Konfiguruj_**.

## <a name="integrating-with-user-code"></a>Integracja z kodem użytkownika

Integracja plików resource i specification generowanych przez program GUIX Studio jest prosta. Po prostu wykonaj następujące kroki:

1. Skopiuj lub udostępnij pliki Resource and Specification za pośrednictwem ustawień ścieżki do osadzonego środowiska kompilacji
2. Dodawanie wszystkich plików zasobów i specyfikacji do osadzonego projektu IDE lub pliku make
3. Upewnij się, że kod osadzony aplikacji wywołuje funkcje niezbędne do zainicjowania i utworzenia interfejsu użytkownika zawartego w plikach Resource and Specification
4. Upewnij się, że kod osadzony aplikacji zawiera wszystkie niezbędne niestandardowe funkcje rysowania widżetów, obsługi zdarzeń i alokacji pamięci
5. Kompilowanie aplikacji (kompilowanie i łączenie)
6. Wykonaj aplikację!