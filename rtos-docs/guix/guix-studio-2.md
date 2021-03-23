---
title: Instalowanie i korzystanie z programu GUIX Studio
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia projektowania systemu interfejsu użytkownika GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823071"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>Rozdział 2. Instalowanie i korzystanie z programu GUIX Studio

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia projektowania systemu interfejsu użytkownika GUIX Studio. 

## <a name="product-distribution"></a>Dystrybucja produktu

Aplikację GUIX Studio można uzyskać ze [sklepu Microsoft App Store](https://microsoft.com/store/apps) , wyszukując GUIX Studio lub przechodząc bezpośrednio do [strony programu GUIX Studio](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab). Następnie wykonaj następujące czynności.

1. Na stronie GUIX Studio w sklepie App Store kliknij przycisk **Pobierz** lub **Zainstaluj** , aby pobrać program GUIX Studio.

1. W przeglądarce może zostać wyświetlony komunikat z pytaniem, czy chcesz otworzyć Microsoft Store, jak pokazano na poniższej ilustracji. Jeśli tak, wybierz przycisk **Otwórz** .
![Wybierz pozycję Otwórz, aby zainstalować program GUIX Studio.](./media/guix-studio/open-ms-store.png)

1. Po zakończeniu instalacji wybierz przycisk **Uruchom** .

1. Przy pierwszym uruchomieniu programu GUIX Studio zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz sklonować repozytorium GUIX na komputerze lokalnym. Można wybrać klonowanie repozytorium, wskazać miejsce, w którym zostało już Sklonowane repozytorium, lub zrezygnować z klonowania repozytorium. w takim przypadku na komputerze jest zainstalowany jeden przykładowy projekt.
![Wybierz klonowanie repozytorium, wskaż już Sklonowane repozytorium lub Pomiń.](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> Możesz powrócić do tego okna dialogowego w dowolnym momencie, wybierając pozycję **Konfiguruj** z menu głównego GUIX stuido, a następnie **repozytorium GUIX**.

Po zakończeniu procesu uruchamiania będzie można korzystać z programu GUIX Studio.

## <a name="using-guix-studio"></a>Korzystanie z programu GUIX Studio

Korzystanie z programu GUIX Studio jest proste — wystarczy uruchomić program GUIX Studio za pomocą przycisku "***Start***". W tym momencie zobaczysz interfejs użytkownika programu GUIX Studio. Teraz można przystąpić do tworzenia graficznego interfejsu użytkownika przy użyciu programu GUIX Studio. W tym miejscu utworzysz nowy projekt lub Otwórz istniejący projekt, w tym przykładowe projekty GUIX.

> [!NOTE]
> Możesz również kliknąć dwukrotnie dowolny plik projektu GUIX Studio o rozszerzeniu "**GXP",** co spowoduje automatyczne uruchomienie GUIX Studio i otwarcie przywoływanego projektu.

## <a name="guix-studio-project-samples"></a>Przykłady projektu GUIX Studio

Seria przykładowych plików projektu GUIX Studio o rozszerzeniu "***GXP**_" znajduje się w_ * podkatalogu "_Samples_* *" instalacji. Te wstępnie skompilowane projekty pomogą Ci uzyskać komfort korzystania z programu GUIX Studio.

Jeden przykładowy plik projektu, który jest zawsze obecny to plik ***Samples/demo_guix_simple/guix_simple. GXP** _. Ten przykładowy plik projektu pokazuje definicję prostego interfejsu użytkownika GUIX, zgodnie z opisem w *_rozdziale 7_** tego dokumentu.

![Zrzut ekranu przedstawiający interfejs użytkownika programu GUIX Studio.](./media/guix-studio/image_10.png)

**Rysunek 1**

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

- **Ctrl + N:** Nowy projekt
- **Ctrl + O:** Otwórz projekt
- **Ctrl + S:** Zapisz projekt
- **Ctrl + Shift + S:** Zapisz projekt jako
- **Alt + F4:** Opuść
