---
title: Azure RTOS użytkownika stosu urządzeń USBX
description: Ten przewodnik zawiera kompleksowe informacje o Azure RTOS USBX, wysokowydajne oprogramowanie USB Foundation firmy Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 042398377766a3e73f72d4dbba0478ba707d378a379fd33de7808675eb96f257
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788766"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Azure RTOS użytkownika stosu urządzeń USBX

Ten przewodnik zawiera kompleksowe informacje o Azure RTOS USBX, wysokiej wydajności oprogramowanie USB foundation firmy Microsoft.

Jest ona przeznaczona dla osadzonego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym, specyfikację USB i język programowania C.

Aby uzyskać informacje techniczne dotyczące portu USB, zobacz Specyfikacje USB i Specyfikacje klas USB, które można pobrać pod https://www.USB.org/developers

## <a name="organization"></a>Organizacja

- [**Rozdział 1**](usbx-device-stack-1.md) — zawiera wprowadzenie do Azure RTOS USBX

- [**Rozdział 2**](usbx-device-stack-2.md) — zawiera podstawowe instrukcje dotyczące instalowania i używania Azure RTOS USBX z aplikacją ThreadX

- [**Rozdział 3**](usbx-device-stack-3.md) — opis składników funkcjonalnych stosu Azure RTOS USBX

- [**Rozdział 4**](usbx-device-stack-4.md) — opis Azure RTOS stosu urządzeń USBX

- [**Rozdział 5**](usbx-device-stack-5.md) — opisuje każdą klasę Azure RTOS USBX wraz z ich interfejsami API

## <a name="customer-support-center"></a>Centrum obsługi klienta

Prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal, aby uzyskać pytania lub pomoc, korzystając z kroków tutaj. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i możliwość jego niezawodnego odtworzenia.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTOS ThreadX, które poprzedzały problem.
3. Zawartość ciągu **_tx_version_id** w pliku **_tx_port.h_** twojej dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska uruchomieniowego.
4. Zawartość w pamięci RAM *_tx_build_options* **ULONG.** Ta zmienna zawiera informacje na temat sposobu Azure RTOS biblioteki ThreadX.
