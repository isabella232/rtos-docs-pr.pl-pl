---
title: Rozdział 3 — opcje konfiguracji NAT
description: Poniższa lista zawiera wszystkie opcje i ich funkcje opisane szczegółowo.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c10d6f0d2f36d2794ab1229081799f0032cada8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821763"
---
# <a name="chapter-3---nat-configuration-options"></a>Rozdział 3 — opcje konfiguracji NAT

Konfigurowalne opcje interfejsu API NetX Duo można znaleźć w *nx_nat. h* z wyjątkiem pierwszego, **NX_DISABLE_ERROR_CHECKING** który znajduje się w *nx_nat. c*. Poniższa lista zawiera wszystkie opcje i ich funkcje opisane szczegółowo:

- **NX_NAT_DISABLE_ERROR_CHECKING** Ta opcja, jeśli zdefiniowana, usuwa podstawowe sprawdzanie błędów NAT. Jest on zazwyczaj używany po debugowaniu aplikacji. Domyślny stan translatora adresów sieciowych NetX Duo jest zdefiniowany (włączony).
- **NX_NAT_ENABLE_REPLACEMENT** Ta opcja, jeśli została zdefiniowana, włącza automatyczną wymianę, gdy pamięć podręczna NAT jest pełna.
  > [!NOTE]
  > Zastąp tylko najstarszą sesję niebędącą protokołem TCP.
- **NX_NAT_MIN_ENTRY_COUNT** Ta opcja ustawia minimalną liczbę dla wpisu tłumaczenia. Domyślna liczba to 3.
- **NX_NAT_TCP_SESSION_TIMEOUT** Ta opcja ustawia limit czasu dla wpisu tłumaczenia dla sesji protokołu TCP. Domyślny limit czasu wynosi 24 godziny.
- **NX_NAT_NON_TCP_SESSION_TIMEOUT** Ta opcja ustawia limit czasu dla wpisu tłumaczenia dla sesji innych niż TCP. Domyślny limit czasu wynosi 240 sekund.
- **NX_NAT_START_TCP_PORT** Ta opcja ustawia wartość początkową do znalezienia nieużywanego portu TCP w celu przypisania wychodzącego pakietu TCP. Wartość domyślna to 20000.
- **NX_NAT_END_TCP_PORT** Ta opcja ustawia upperlimit portu TCP, aby przypisać wychodzący pakiet TCP. Wartość domyślna to 30000.
- **NX_NAT_START_UDP_PORT** Ta opcja ustawia wartość początkową do znalezienia nieużywanego portu UDP do przypisania wychodzącego pakietu UDP. Wartość domyślna to 20000.
- **NX_NAT_END_UDP_PORT** Ta opcja ustawia upperlimit portu UDP, aby przypisać wychodzący pakiet UDP. Wartość domyślna to 30000.
- **NX_NAT_START_ICMP_QUERY_ID** Ta opcja ustawia wartość początkową do znalezienia nieużywanego identyfikatora zapytania w celu przypisania wychodzącego zapytania protokołu ICMP. Wartość domyślna to 20000.
- **NX_NAT_END_ICMP_QUERY_ID** Ta opcja ustawia upperlimit identyfikatorów zapytań, aby przypisać wychodzący pakiet zapytań protokołu ICMP. Wartość domyślna to 30000.
