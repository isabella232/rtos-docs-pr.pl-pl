---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS TraceX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS analizy systemu TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1a375975ef80cfb7b56466f5d91ed9a0ca00a20a38108e1b81f4fe8e5d85278d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802201"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS TraceX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS analizy systemu TraceX. 

## <a name="product-distribution"></a>Dystrybucja produktów

Aplikację TraceX można uzyskać z witryny [Microsoft App Store,](https://microsoft.com/store/apps) wyszukując dane TraceX lub przechodząc bezpośrednio [do strony TraceX.](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab) Następnie wykonaj następujące czynności.

1. Na stronie TraceX w App Store kliknij przycisk **Pobierz** lub **Zainstaluj,** aby zainstalować program TraceX.

1. W przeglądarce może zostać wyświetlony komunikat z pytaniem, czy chcesz otworzyć Microsoft Store, jak pokazano na poniższej ilustracji. Jeśli tak, wybierz **przycisk** Otwórz.
![Wybierz pozycję Otwórz, aby zainstalować program TraceX.](../guix/media/guix-studio/open-ms-store.png)

1. Po zakończeniu instalacji wybierz przycisk **Uruchom.** 

## <a name="using-tracex"></a>Korzystanie z narzędzia TraceX

Korzystanie z narzędzia TraceX jest tak proste, jak otwieranie pliku śledzenia wewnątrz narzędzia TraceX! Uruchom program TraceX za pomocą **przycisku*** Uruchom _. W tym momencie będzie można obserwować graficzny interfejs użytkownika (GUI) TraceX. Teraz możesz używać narzędzia TraceX do graficznego wyświetlania istniejącego docelowego buforu śledzenia. Można to łatwo zrobić, klikając pozycję _ *_Plik -> Otwórz, *,_* a następnie wprowadzając binarny plik śledzenia.

>[!IMPORTANT]
>*Możesz również kliknąć dwukrotnie dowolny plik śledzenia z rozszerzeniem **trx,** co spowoduje automatyczne uruchomienie traceX.*

![Zrzut ekranu przedstawiający graficzny interfejs użytkownika TraceX.](./media/user-guide/screen_shot_8.png)

**RYSUNEK 1**

>[!IMPORTANT]
>*Zapoznaj się z **rozdziałem 5,** aby uzyskać instrukcje dotyczące generowania buforów śledzenia w celu przy użyciu threadX.*

## <a name="tracex-examples"></a>Przykłady traceX

Przy pierwszym uruchomieniu aplikacji TraceX lub zaktualizowania aplikacji TraceX zostanie wyświetlony monit o zainstalowanie przykładowych plików śledzenia TraceX i pliku custom_events.trxc w katalogu zdefiniowanym przez użytkownika na komputerze lokalnym.

Po ukończeniu tego kroku instalacji przykładowe pliki śledzenia z rozszerzeniem **trx** znajdują się w podkatalogu **TraceFiles** folderu instalacyjnego. Te wstępnie sfabrykowane przykłady ułatwiają korzystanie z funkcji TraceX w buforach śledzenia generowanych przez threadX uruchomionych w aplikacji.

Jednym z przykładowych plików śledzenia zawsze jest plik ***demo_threadx.trx** _. Ten przykładowy plik śledzenia przedstawia wykonanie standardowej demonstracji ThreadX zgodnie z opisem w rozdziale 6 _ThreadX Podręcznika użytkownika*.

![Zrzut ekranu przedstawiający otwarte okno dialogowe w programie TraceX.](./media/user-guide/screen_shot_9.png)

**RYSUNEK 2**
