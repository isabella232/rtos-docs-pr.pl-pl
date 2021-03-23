---
title: Podręcznik użytkownika programu GUIX Studio
description: Ten przewodnik zawiera wyczerpujące informacje na temat GUIX Studio, szybkiego środowiska programistycznego opartego na systemie Microsoft Windows, specjalnie zaprojektowanego dla biblioteki środowiska uruchomieniowego GUIX firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823076"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>Rozdział 1: wprowadzenie do usługi Azure RTO GUIX Studio

Azure RTO GUIX Studio to środowisko programistyczne szybkiego interfejsu użytkownika oparte na systemie Microsoft Windows zaprojektowane specjalnie dla biblioteki środowiska uruchomieniowego GUIX firmy Microsoft.

Osadzoni deweloperzy interfejsu użytkownika mogą korzystać z projektanta ekranu GUIX Studio WYSIWYG, aby szybko utworzyć i zaktualizować osadzony interfejs użytkownika przy użyciu środowiska wykonawczego GUIX. Projekty GUIX Studio są zapisywane i obsługiwane w pliku projektu GUIX Studio, który ma rozszerzenie. GXP. Gdy projekt jest gotowy do wykonania na obiekcie docelowym, GUIX Studio generuje kod C, który zawiera wszystkie niezbędne informacje o interfejsie użytkownika i kod.

## <a name="guix-studio-requirements"></a>Wymagania dotyczące programu GUIX Studio

Aby zapewnić prawidłowe działanie, firma Microsoft GUIX Studio wymaga *systemu Windows XP* (lub nowszego). System powinien mieć co najmniej 200 MB pamięci RAM, 2 GB dostępnego miejsca na dysku twardym oraz minimalny wyświetlacz 1024x768 z 256 kolorów. Ponadto aplikacja osadzona musi być uruchomiona w systemie *ThreadX/GUIX v 6.0* lub nowszym.

Jeśli chcesz mieć możliwość kompilowania i uruchamiania osadzonej aplikacji interfejsu użytkownika jako autonomicznego pliku wykonywalnego systemu Microsoft Windows, potrzebny będzie również kompilator lub środowisko kompilacji, które umożliwi kompilowanie kodu źródłowego C w celu utworzenia pliku wykonywalnego systemu Microsoft Windows. Pakiet ewaluacyjny zawarty w programie GUIX Studio zawiera również zgodne z programem Visual Studio 2019 pliki projektu i rozwiązania dla każdego z podanych przykładowych aplikacji. Jeśli używasz innego kompilatora, musisz utworzyć własne pliki projektu lub utworzyć pliki do celów tworzenia przykładowych aplikacji lub skontaktować się z pomocą techniczną pod adresem https://aka.ms/azrtos-support .

## <a name="guix-studio-constraints"></a>Ograniczenia GUIX Studio

Narzędzie projektowania interfejsu użytkownika programu GUIX Studio ma kilka ograniczeń, w następujący sposób:

- Maksymalnie 4 wyświetlenia na projekt.
- Maksymalna liczba elementów widget 100 000 na projekt GUIX Studio.
- Maksymalnie 100 000 różnych zasobów, na przykład kolory, czcionki, pixelmaps, ciągi itd.