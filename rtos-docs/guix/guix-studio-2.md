---
title: Instalacja i korzystanie z programu GUIX Studio
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem narzędzia do projektowania systemu interfejsu użytkownika GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 55d2b0ac08bdceebdf286effe4bbc679320541243ff78359deafe0858a7b597e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786476"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>Rozdział 2. Instalacja i korzystanie z programu GUIX Studio

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem narzędzia do projektowania systemu interfejsu użytkownika GUIX Studio. 

## <a name="product-distribution"></a>Dystrybucja produktów

Aplikację GUIX Studio można uzyskać z witryny [Microsoft App Store,](https://microsoft.com/store/apps) wyszukując program GUIX Studio lub przechodząc bezpośrednio do [strony GUIX Studio.](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab) Następnie wykonaj następujące czynności.

1. Na stronie GUIX Studio w App Store kliknij przycisk  **Pobierz** lub zainstaluj, aby pobrać program GUIX Studio.

1. W przeglądarce może zostać wyświetlony komunikat z pytaniem, czy chcesz otworzyć Microsoft Store, jak pokazano na poniższej ilustracji. Jeśli tak, wybierz **przycisk** Otwórz.
![Wybierz pozycję Otwórz, aby zainstalować program GUIX Studio.](./media/guix-studio/open-ms-store.png)

1. Po zakończeniu instalacji wybierz przycisk **Uruchom.**

1. Przy pierwszym uruchomieniu programu GUIX Studio zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz sklonować repo GUIX na komputer lokalny. Możesz sklonować repozytorium, wskazać miejsce, do którego zostało już sklonowane repozytorium, lub w ogóle nie klonować repozytorium (w takim przypadku na komputerze jest zainstalowany jeden przykładowy projekt).
![Wybierz sklonowanie, wskaż już sklonowane lub pomiń.](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> W dowolnym momencie możesz wrócić do tego okna dialogowego, wybierając pozycję **Konfiguruj** z menu głównego guix stuido, a następnie **pozycję GUIX Repository (Repozytorium GUIX).**

Po zakończeniu procesu uruchamiania wszystko będzie gotowe do korzystania z programu GUIX Studio.

## <a name="using-guix-studio"></a>Korzystanie z programu GUIX Studio

Korzystanie z programu GUIX Studio jest łatwe — wystarczy uruchomić program GUIX Studio za pomocą ***przycisku "Uruchom".*** W tym momencie będziesz obserwować interfejs użytkownika programu GUIX Studio. Teraz możesz użyć programu GUIX Studio do graficznego utworzenia osadzonego interfejsu użytkownika. W tym miejscu utworzysz nowy projekt lub otworzysz istniejący projekt, w tym przykładowe projekty GUIX.

> [!NOTE]
> Możesz również kliknąć dwukrotnie dowolny plik projektu GUIX Studio z rozszerzeniem "**gxp, ",** co spowoduje automatyczne uruchomienie programu GUIX Studio i otwarcie przywołynego projektu.

## <a name="guix-studio-project-samples"></a>Przykłady Project GUIX Studio

Seria przykładowych plików projektu GUIX Studio z rozszerzeniem "***gxp**" znajduje się w podkatalerze * _"Przykłady_**" twojej instalacji. Te wstępnie sbudowaną przykładowe projekty ułatwiają korzystanie z programu GUIX Studio.

Jednym z przykładowych plików projektu, który jest zawsze obecny, jest plik ***samples/demo_guix_simple/guix_simple.gxp** _. Ten przykładowy plik projektu przedstawia definicję prostego interfejsu użytkownika GUIX, jak opisano w rozdziale *_7_** tego dokumentu.

![Zrzut ekranu przedstawiający interfejs użytkownika programu GUIX Studio.](./media/guix-studio/image_10.png)

**Rysunek 1**

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

- **Ctrl + N:** Nowe Project
- **Ctrl + O:** Otwórz Project
- **Ctrl + S:** Zapisz Project
- **Ctrl + Shift + S:** Zapisz Project jako
- **Alt + F4:** Wyjścia
