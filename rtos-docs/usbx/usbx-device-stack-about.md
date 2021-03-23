---
title: Przewodnik użytkownika stosu urządzeń usługi Azure RTO USBX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO USBX, czyli oprogramowania USB Foundation o wysokiej wydajności firmy Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821331"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Przewodnik użytkownika stosu urządzeń usługi Azure RTO USBX

Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO USBX, czyli oprogramowaniu High Performance USB Foundation od firmy Microsoft.

Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym, specyfikację USB i język programowania C.

Aby uzyskać informacje techniczne dotyczące technologii USB, zobacz specyfikację USB i specyfikacje klasy USB, które można pobrać w https://www.USB.org/developers

## <a name="organization"></a>Organizacja

- [**Rozdział 1**](usbx-device-stack-1.md) — zawiera wprowadzenie do usługi Azure RTO USBX

- [**Rozdział 2**](usbx-device-stack-2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO USBX z aplikacją ThreadX

- [**Rozdział 3**](usbx-device-stack-3.md) — Opis składników funkcjonalnych stosu urządzeń usługi Azure RTO USBX

- [**Rozdział 4**](usbx-device-stack-4.md) — Opis usługi Azure RTO USBX Stack

- [**Rozdział 5**](usbx-device-stack-5.md) — opis każdej klasy urządzeń usługi Azure RTO USBX, w tym interfejsów API

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.
3. Zawartość ciągu **_tx_version_id** można znaleźć w pliku **_tx_port. h_** dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.
4. Zawartość w pamięci RAM _tx_build_options zmiennej  **ULONG** . Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.
