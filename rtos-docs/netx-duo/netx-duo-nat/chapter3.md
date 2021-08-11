---
title: Rozdział 3 — Opcje konfiguracji nat
description: Na poniższej liście znajdują się wszystkie opcje i ich funkcja opisana szczegółowo
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c7f2de88b5d70646284d946fdb6fbc743f08b3486430befb4fcda1d7e23e9b9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797284"
---
# <a name="chapter-3---nat-configuration-options"></a>Rozdział 3 — Opcje konfiguracji nat

Konfigurowalne opcje interfejsu API NAT netX Duo można znaleźć w jęz. *nx_nat.h* z wyjątkiem pierwszego, NX_DISABLE_ERROR_CHECKING który znajduje się w  *nx_nat.c.* Na poniższej liście opisano szczegółowo wszystkie opcje i ich funkcje:

- **NX_NAT_DISABLE_ERROR_CHECKING** Ta opcja, jeśli jest zdefiniowana, usuwa podstawowe sprawdzanie błędów nat. Jest on zwykle używany po debugowaniu aplikacji. Domyślny stan nat NetX Duo jest zdefiniowany (włączony).
- **NX_NAT_ENABLE_REPLACEMENT** Ta opcja, jeśli jest zdefiniowana, umożliwia automatyczne zastępowanie, gdy pamięć podręczna nat jest pełna.
  > [!NOTE]
  > Zastąp tylko najstarszą sesję bez protokołu TCP.
- **NX_NAT_MIN_ENTRY_COUNT** Ta opcja określa minimalną liczbę wpisów tłumaczenia. Domyślna liczba to 3.
- **NX_NAT_TCP_SESSION_TIMEOUT** Ta opcja ustawia limit czasu dla wpisu tłumaczenia dla sesji TCP. Domyślny limit czasu to 24 godziny.
- **NX_NAT_NON_TCP_SESSION_TIMEOUT** Ta opcja ustawia limit czasu dla wpisu tłumaczenia dla sesji innych niż TCP. Domyślny limit czasu to 240 sekund.
- **NX_NAT_START_TCP_PORT** Ta opcja ustawia wartość początkową dla znajdowania nieużywanego portu TCP w celu przypisania wychodzącego pakietu TCP. Wartość domyślna to 20000.
- **NX_NAT_END_TCP_PORT** Ta opcja ustawia górny limit portu TCP w celu przypisania wychodzącego pakietu TCP. Wartość domyślna to 30000.
- **NX_NAT_START_UDP_PORT** Ta opcja ustawia wartość początkową dla znajdowania nieużywanego portu UDP w celu przypisania wychodzącego pakietu UDP. Wartość domyślna to 20000.
- **NX_NAT_END_UDP_PORT** Ta opcja ustawia górny limit portu UDP w celu przypisania wychodzącego pakietu UDP. Wartość domyślna to 30000.
- **NX_NAT_START_ICMP_QUERY_ID** Ta opcja ustawia wartość początkową dla znajdowania nieużywanego identyfikatora zapytania w celu przypisania wychodzącego pakietu zapytań ICMP. Wartość domyślna to 20000.
- **NX_NAT_END_ICMP_QUERY_ID** Ta opcja ustawia górny limit identyfikatorów zapytań w celu przypisania wychodzącego pakietu zapytań ICMP. Wartość domyślna to 30000.
