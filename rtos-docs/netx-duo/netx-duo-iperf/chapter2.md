---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS NetX Duo Iperf
description: Ten rozdział zawiera instrukcje dotyczące instalowania i używania przykładu Iperf.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7e80d89a334ceec3467b23574ab5c231a15f68a1
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609957"
---
# <a name="chapter-2-installation-and-use"></a>Rozdział 2 Instalacja i użycie

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem pokazu NetX Duo Iperf.

## <a name="installing-the-demonstration"></a>Instalowanie pokazu

Postępuj zgodnie z instrukcjami instalacji dotyczącymi określonej platformy podanymi w dystrybucji.

## <a name="installing-iperf"></a>Instalowanie aplikacji Iperf

Istnieje wiele różnych programów Iperf, których możesz użyć. Jednak przykłady w tym dokumencie są oparte na języku Java ***Jperf 2.0.2,*** który jest dostępny z wielu źródeł w Internecie.

> [Uwaga] *Program Jperf wymaga zainstalowania języka Java na maszynie hosta.*

## <a name="setting-the-ip-address"></a>Ustawianie adresu IP

Domyślnie adres IP pokazu NetX Duo Iperf jest ustawiony na **192.2.2.149.** Ta konfiguracja jest konfigurowana **_w pliku demo_netx_duo_iperf.c_*_*** jako parametr wywołania funkcji _ nx_ip_create .

## <a name="network-assumptions"></a>Założenia dotyczące sieci

W tym pokazie przyjęto założenie, że maszyna hosta Iperf i tablica docelowa z uruchomionym programem NetX Duo Iperf Demonstration są połączone z przełącznikiem Ethernet pełnodupleksowym 100 Mb/s. Aby osiągnąć najlepszą wydajność, w sieci testowej nie powinien być żadnego innego ruchu.

Istnieje również możliwość podłączenia hosta Iperf i płyty docelowej NetX Duo z powrotem do tyłu za pomocą kabla Ethernet krzyżowego.

## <a name="running-the-demonstration"></a>Uruchamianie pokazu

Uruchamianie pokazu jest łatwe. po prostu załaduj, skompilowaj i wykonaj projekt pokazowy NetX Duo Iperf — zwykle o ***nazwie demo_netx_duo_iperf***.

## <a name="browse-to-the-demonstration"></a>Przejdź do pokazu

Przejdź do tablicy docelowej za pośrednictwem przeglądarki na platformie hosta Iperf. Przy założeniu, że docelowy adres IP tablicy **to 192.2.2.149,** poniżej przedstawiono przykład początkowej strony internetowej NetX Duo Iperf Demonstration.

![Przykład początkowej strony internetowej Iperf](media/Picture1.jpg)

## <a name="running-jperf"></a>Uruchamianie aplikacji Jperf

Uruchamianie programu Jperf jest proste. Wystarczy kliknąć dwukrotnie plik Windows wsadowy ***jperf.bat** _. To uruchamia ideę Jperf, jak pokazano poniżej. Po wyświetlaniu środowiska IDE programu Jperf pole _ *Adres* serwera * musi być ustawione na adres IP tablicy docelowej NetX Duo Iperf Demonstration. W tym przykładzie adres IP tablicy docelowej NetX Duo to **192.2.2.149.** Warto również zauważyć pola Przepustowość **UDP** i **Rozmiar pakietu UDP.** Należy je skonfigurować w celu uzyskania optymalnej wydajności odbierania protokołu UDP, jak pokazano poniżej.

![Optymalizacja wydajności protokołu UDP.](media/Picture2.jpg)
