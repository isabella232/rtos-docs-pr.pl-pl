---
title: Podręcznik użytkownika programu GUIX Studio
description: Ten przewodnik zawiera kompleksowe informacje na temat programu GUIX Studio, opartego na technologii Microsoft Windows szybkiego tworzenia interfejsu użytkownika specjalnie zaprojektowanego dla biblioteki środowiska uruchomieniowego GUIX firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 2c36fb794816cb1acd51ec81f48c0dabe509336f27914050b6206f19bf8ceeff
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789837"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>Rozdział 1. Wprowadzenie do Azure RTOS GUIX Studio

Azure RTOS GUIX Studio to oparte na platformie Microsoft Windows środowisko do szybkiego tworzenia interfejsu użytkownika zaprojektowane specjalnie dla biblioteki środowiska uruchomieniowego GUIX firmy Microsoft.

Deweloperzy osadzonego interfejsu użytkownika mogą używać projektanta ekranu GUIX Studio WYSIWYG do szybkiego tworzenia i aktualizowania osadzonego interfejsu użytkownika przy użyciu środowiska uruchomieniowego GUIX. Projekty GUIX Studio są zapisywane i utrzymywane w pliku projektu GUIX Studio z rozszerzeniem .gxp. Gdy projekt jest gotowy do wykonania na komputerze docelowym, program GUIX Studio generuje kod języka C, który zawiera wszystkie niezbędne informacje i kod interfejsu użytkownika.

## <a name="guix-studio-requirements"></a>Wymagania programu GUIX Studio

Aby program GUIX Studio firmy Microsoft działał prawidłowo, wymaga *Windows XP* (lub więcej). System powinien mieć co najmniej 200 MB pamięci RAM, 2 GB dostępnego miejsca na dysku twardym i minimalny ekran 1024 x 768 z 256 kolorami. Ponadto aplikacja osadzona musi być uruchomiona w *threadx/GUIX w wersji 6.0 lub* nowszej.

Jeśli chcesz mieć możliwość kompilowania i uruchamiania osadzonej aplikacji interfejsu użytkownika jako autonomicznego pliku wykonywalnego programu Microsoft Windows, potrzebujesz również kompilatora lub środowiska kompilacji umożliwiającego kompilowanie kodu źródłowego języka C w celu uzyskania pliku wykonywalnego programu Microsoft Windows. Pakiet ewaluacyjny dołączony do programu GUIX Studio Visual Studio plików projektów i rozwiązań zgodnych z programem Visual Studio 2019 dla każdej z podanych przykładowych aplikacji. Jeśli używasz innego kompilatora, musisz utworzyć własne pliki projektu lub utworzyć pliki na potrzeby tworzenia przykładowych aplikacji lub skontaktować się z pomocą techniczną pod adres https://aka.ms/azrtos-support .

## <a name="guix-studio-constraints"></a>Ograniczenia programu GUIX Studio

Narzędzie do projektowania interfejsu użytkownika GUIX Studio ma kilka ograniczeń:

- Maksymalnie 4 wyświetla na projekt.
- Maksymalnie 100 000 widżetów na projekt GUIX Studio.
- Maksymalnie 100 000 różnych zasobów, np. kolorów, czcionek, map pikseli, ciągów itp.