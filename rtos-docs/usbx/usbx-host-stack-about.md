---
title: Przewodnik użytkownika stosu hosta usługi Azure RTO USBX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO USBX, czyli oprogramowania USB Foundation o wysokiej wydajności od firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 243b12c4757ee945def8fea01c0d4114e39312ce
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823233"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a>Przewodnik użytkownika stosu hosta usługi Azure RTO USBX

Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO USBX, czyli oprogramowania USB Foundation o wysokiej wydajności od firmy Microsoft.

Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym, specyfikację USB i język programowania C.

Aby uzyskać informacje techniczne dotyczące technologii USB, zobacz specyfikację USB i specyfikacje klasy USB, które można pobrać w [https://www.USB.org/developers](https://www.USB.org/developers)

## <a name="organization"></a>Organizacja

- [**Rozdział 1**](usbx-host-stack-1.md) — zawiera wprowadzenie do usługi Azure RTO USBX

- [**Rozdział 2**](usbx-host-stack-2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO USBX z aplikacją Azure RTO ThreadX

- [**Rozdział 3**](usbx-host-stack-3.md) — zawiera przegląd funkcjonalny usługi Azure RTO USBX i podstawowe informacje o USB

- [**Rozdział 4**](usbx-host-stack-4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO USBX w trybie hosta

- [**Rozdział 5**](usbx-host-stack-5.md) — opis interfejsów API klas hosta usługi Azure RTO USBX

- [**Rozdział 6**](usbx-host-stack-6.md) — opis klasy ECM usługi Azure RTO USBX — Klasa

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej.

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.
3. Zawartość ciągu *_tx_version_id* można znaleźć w pliku *tx_port. h* dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.
4. Zawartość w pamięci RAM *_tx_build_options* zmiennej ulong. Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.
