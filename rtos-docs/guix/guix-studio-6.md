---
title: Kod wygenerowany przez GUIX Studio
description: Po zakończeniu edycji ekranów i zasobów program GUIX Studio tworzy zestaw plików wyjściowych, które mogą być włączone do aplikacji osadzonej.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: f8868ec770aa8f7f35d2866b99e3eb8f501281a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823034"
---
# <a name="chapter-6-guix-studio-generated-code"></a>Rozdział 6: kod wygenerowany przez GUIX Studio

Po zakończeniu edycji ekranów i zasobów program GUIX Studio tworzy zestaw plików wyjściowych, które mogą być włączone do aplikacji osadzonej. Pliki wyjściowe są generowane przez wybranie polecenia ***Generuj pliki zasobów** _ i _ *_Generuj specyfikacje_** z elementu menu projektu. Pliki kodu źródłowego języka c generowane przez program GUIX Studio mają być kompilowane i połączone z osadzonym kodem źródłowym aplikacji. Jeśli plik zasobów w formacie binarnym zostanie utworzony, ten plik powinien zostać zaprogramowany do obszaru magazynu nietrwałego w miejscu docelowym, a funkcja interfejsu API GUIX gx_binres_theme_install powinna zostać użyta do zainstalowania zasobów binarnych w czasie wykonywania.

Kod aplikacji osadzonej użytkownika tworzy odwołania do kodu wygenerowanego przez GUIX Studio. Ponadto kod wygenerowany przez program GUIX Studio oczekuje, że wszystkie niestandardowe funkcje rysowania widżetu, obsługi zdarzeń i alokacji pamięci określone w projekcie, które mają być zdefiniowane w osadzonym kodzie aplikacji użytkownika. W przeciwnym razie błędy łączy będą obecne podczas kompilowania aplikacji.

> [!NOTE]
> Użytkownik nigdy nie musi modyfikować kodu wygenerowanego przez program GUIX Studio i powinien go odporny. Wszystkie modyfikacje interfejsu użytkownika należy wprowadzać w skojarzonym projekcie GUIX Studio. Spowoduje to zsynchronizowanie projektu z aplikacją osadzoną.

## <a name="generating-resource-files"></a>Generowanie plików zasobów

Pliki zasobów wygenerowane przez program GUIX Studio zawierają wstępnie zdefiniowane struktury danych, które definiują wszystkie zasoby programu GUIX Studio (kolory, czcionki, pixelmaps i ciągi), które są efektywnie wszystkie zasoby zdefiniowane w ***Widok zasobów*** projektu. Te pliki zasobów można generować w kodzie źródłowym lub w postaci binarnej.

Domyślnie są generowane dwa pliki, jeden plik jest plikiem standardowego kodu źródłowego C, a drugi to plik nagłówka C, który zawiera zewnętrzne odwołania i stałe, które są niezbędne, aby kod aplikacji mógł uzyskać dostęp do zasobów GUIX zdefiniowanych w projekcie. Nazwy plików mają postać:

**{*Project-Name*} _resources. h**

**{*Project-Name*} _resources. c**

Na przykład pliki zasobów utworzone dla projektu "***Simple***" GUIX Studio są następujące:

**simple_resources. h**

**simple_resources. c**

Generowanie plików zasobów jest realizowane przez wybranie opcji ***Generuj pliki zasobów** _ w opcji menu _*_projektu_*_ . Miejsce docelowe plików zasobów jest określone w oknie dialogowym _*_Konfigurowanie projektu_*_ , które jest dostępne za pośrednictwem opcji _*_Konfiguruj projekt/Wyświetl_*_ w elemencie menu _ *_Konfiguracja_**.

W przypadku Pixelmap i zasobów czcionek można określić niestandardową nazwę pliku wyjściowego dla każdej Pixelmap i czcionki w oknach dialogowych edytowania skojarzonych zasobów. Ta funkcja umożliwia umieszczenie bardzo dużych zasobów w oddzielnych plikach zamiast umieszczania wszystkich zasobów w jednym wspólnym pliku wyjściowym. Jeśli nie określisz przesłoniętej nazwy pliku dla czcionki lub zasobu Pixelmap, te zasoby są zapisywane w pliku wspólnych zasobów.

Jeśli wolisz używać zasobów binarnych, możesz określić format wyjściowy rekordu Raw lub standard. Zasoby binarne nie są kompilowane ani połączone z kodem aplikacji, ale są ładowane w czasie wykonywania za pomocą interfejsu API gx_binres_them_load (). Ta usługa API kompiluje tabele zasobów wskazujące zasoby przechowywane w pamięci nieulotnej. Następnie można zainstalować te zasoby z określonym ekranem przy użyciu gx_display_theme_install ().

## <a name="generating-specification-code"></a>Generowanie kodu specyfikacji

Pliki specyfikacji wygenerowane przez program GUIX Studio zawierają cały kod C, aby utworzyć interfejs użytkownika zaprojektowany w programie GUIX Studio. Ten kod odwołuje się również do plików zasobów wygenerowanych dla tego projektu. Kod aplikacji użytkownika wykona wywołania do tego kodu w celu utworzenia obiektów interfejsu użytkownika zdefiniowanych w projekcie. Ponadto kod aplikacji użytkownika zawiera wszystkie niestandardowe funkcje rysowania widżetu, obsługi zdarzeń i alokacji pamięci określone w projekcie. Domyślnie są generowane dwa pliki, jeden plik jest plikiem standardowego kodu źródłowego C, a drugi to plik nagłówka C, który zawiera zewnętrzne odwołania i stałe, które są niezbędne do uzyskania dostępu do specyfikacji programu GUIX Studio w kodzie aplikacji. Nazwy plików mają postać:

**{*Project-Name*} _specifications. h**

**{*Project-Name*} _specifications. c**

Na przykład pliki specyfikacji utworzone dla projektu "***Simple***" GUIX Studio są następujące:

**simple_specifications. h**

**simple_specifications. c**

Generowanie plików specyfikacji jest realizowane przez wybranie opcji ***Generuj pliki specyfikacji** _ w opcji menu _*_projektu_*_ . Miejsce docelowe plików specyfikacji jest określone w oknie dialogowym _*_Konfigurowanie projektu_*_ , które jest dostępne za pośrednictwem opcji _*_Konfiguruj projekt/Wyświetl_*_ w elemencie menu _ *_Konfiguracja_**.

## <a name="integrating-with-user-code"></a>Integrowanie z kodem użytkownika

Integracja plików zasobów i specyfikacji wygenerowanych przez program GUIX Studio jest prosta, po prostu wykonaj następujące kroki:

1. Skopiuj lub Udostępnij pliki zasobów i specyfikacji za pośrednictwem ustawień ścieżki w osadzonym środowisku kompilacji
2. Dodaj wszystkie pliki zasobów i specyfikacji do osadzonego projektu IDE lub pliku reguł programu make
3. Upewnij się, że osadzony kod aplikacji wywołuje niezbędne funkcje, aby zainicjować i utworzyć interfejs użytkownika zawarty w plikach zasobów i specyfikacji
4. Upewnij się, że osadzony kod aplikacji zawiera wszystkie niezbędne niestandardowe rysunki widżetu, obsługę zdarzeń i funkcje alokacji pamięci
5. Kompilowanie aplikacji (kompilacja i link)
6. Wykonaj aplikację.