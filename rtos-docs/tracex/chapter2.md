---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO TraceX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia do analizy systemu Azure RTO TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823478"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO TraceX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia do analizy systemu Azure RTO TraceX. 

## <a name="product-distribution"></a>Dystrybucja produktu

Aplikację TraceX można uzyskać ze [sklepu Microsoft App Store](https://microsoft.com/store/apps) , wyszukując TraceX lub przechodząc bezpośrednio do [strony TraceX](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab). Następnie wykonaj następujące czynności.

1. Na stronie TraceX w sklepie App Store kliknij przycisk **Pobierz** lub **Zainstaluj** , aby zainstalować TraceX.

1. W przeglądarce może zostać wyświetlony komunikat z pytaniem, czy chcesz otworzyć Microsoft Store, jak pokazano na poniższej ilustracji. Jeśli tak, wybierz przycisk **Otwórz** .
![Wybierz pozycję Otwórz, aby zainstalować TraceX.](../guix/media/guix-studio/open-ms-store.png)

1. Po zakończeniu instalacji wybierz przycisk **Uruchom** . 

## <a name="using-tracex"></a>Korzystanie z TraceX

Korzystanie z TraceX jest tak proste, jak otwieranie pliku śledzenia w TraceX! Uruchom TraceX za pomocą przycisku ***Start** _. W tym momencie zostanie zaobserwuj graficzny interfejs użytkownika (GUI) TraceX. Teraz można przystąpić do korzystania z TraceX, aby wyświetlić graficznie istniejący docelowy bufor śledzenia. Można to łatwo zrobić, klikając pozycję _ *_plik-> Otwórz,_* a następnie wprowadzając plik śledzenia binarnego.

>[!IMPORTANT]
>*Możesz również kliknąć dwukrotnie dowolny plik śledzenia z rozszerzeniem **TRX,** co spowoduje automatyczne uruchomienie TraceX.*

![Zrzut ekranu przedstawiający graficzny interfejs użytkownika TraceX.](./media/user-guide/screen_shot_8.png)

**RYSUNEK 1**

>[!IMPORTANT]
>*Zapoznaj się z **rozdziałem 5** , aby uzyskać instrukcje dotyczące sposobu generowania buforów śledzenia w miejscu docelowym przy użyciu ThreadX.*

## <a name="tracex-examples"></a>Przykłady TraceX

Przy pierwszym uruchomieniu aplikacji TraceX lub zaktualizowaniu aplikacji TraceX zostanie wyświetlony monit o zainstalowanie przykładowych plików śledzenia TraceX i pliku custom_events. trxc do katalogu zdefiniowanego przez użytkownika na komputerze lokalnym.

Po zakończeniu tego kroku instalacji, przykładowe pliki śledzenia z rozszerzeniem **TRX** są dostępne w podkatalogu **TraceFiles** folderu instalacyjnego. Te wstępnie skompilowane przykłady ułatwią uzyskanie komfortu korzystania z TraceX w buforach śledzenia generowanych przez ThreadX z aplikacją.

Jeden przykład zawsze obecny plik śledzenia to plik ***demo_threadx. TRX** _. Ten przykładowy plik śledzenia przedstawia wykonywanie standardowego demona ThreadX, zgodnie z opisem w rozdziale 6 podręcznika użytkownika _ThreadX *.

![Zrzut ekranu okna dialogowego Otwieranie w programie TraceX.](./media/user-guide/screen_shot_9.png)

**RYSUNEK 2**
