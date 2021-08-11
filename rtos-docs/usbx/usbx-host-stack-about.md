---
title: Azure RTOS użytkownika stosu hosta USBX
description: Ten przewodnik zawiera kompleksowe informacje o Azure RTOS USBX, wysokiej wydajności oprogramowania USB Foundation firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a41f1b386156be6f8fa773fe2b90bb873cff0fd0e8636bc4d3d8f75295bf7f19
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802553"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a>Azure RTOS użytkownika stosu hosta USBX

Ten przewodnik zawiera kompleksowe informacje o Azure RTOS USBX, wysokiej wydajności oprogramowania USB Foundation firmy Microsoft.

Jest ona przeznaczona dla osadzonego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym, specyfikację USB i język programowania C.

Aby uzyskać informacje techniczne dotyczące portu USB, zobacz Specyfikacje USB i Specyfikacje klas USB, które można pobrać pod [https://www.USB.org/developers](https://www.USB.org/developers)

## <a name="organization"></a>Organizacja

- [**Rozdział 1**](usbx-host-stack-1.md) — zawiera wprowadzenie do Azure RTOS USBX

- [**Rozdział 2**](usbx-host-stack-2.md) — zawiera podstawowe instrukcje dotyczące instalowania i używania Azure RTOS USBX z aplikacją Azure RTOS ThreadX

- [**Rozdział 3**](usbx-host-stack-3.md) — zawiera omówienie funkcji Azure RTOS USBX i podstawowe informacje o usb

- [**Rozdział 4**](usbx-host-stack-4.md) — szczegóły interfejsu aplikacji do Azure RTOS USBX w trybie hosta

- [**Rozdział 5**](usbx-host-stack-5.md) — opisuje interfejsy API Azure RTOS hostów USBX

- [**Rozdział 6**](usbx-host-stack-6.md) — opisuje Azure RTOS USBX CDC-ECM

## <a name="customer-support-center"></a>Centrum obsługi klienta

Prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal, aby uzyskać pytania lub pomoc, korzystając z kroków tutaj. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną.

1. Szczegółowy opis problemu, w tym częstotliwość występowania i możliwość jego niezawodnego odtworzenia.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTOS ThreadX, które poprzedzały problem.
3. Zawartość ciągu *_tx_version_id* znajduje się w *tx_port.h* twojej dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska uruchomieniowego.
4. Zawartość w pamięci RAM zmiennej *_tx_build_options* ULONG. Ta zmienna zawiera informacje na temat sposobu Azure RTOS biblioteki ThreadX.
