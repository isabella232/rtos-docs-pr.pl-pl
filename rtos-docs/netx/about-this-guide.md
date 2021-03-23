---
title: Podręcznik użytkownika usługi Azure RTO NetX — informacje
description: Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO NetX, stosie sieci o wysokiej wydajności firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8e1c23892c4360ddc8783b04ae8f23e371899f1d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822824"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a>Podręcznik użytkownika usługi Azure RTO NetX — informacje

Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO NetX, stosie sieci o wysokiej wydajności firmy Microsoft.

Jest ona przeznaczona dla wbudowanych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe pojęcia dotyczące sieci, Azure RTO ThreadX i języka programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) — wprowadzenie do usługi Azure RTO NetX

[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO NetX z aplikacją ThreadX.

[Rozdział 3](chapter3.md) — zawiera przegląd funkcjonalny systemu Azure RTO NetX i podstawowe informacje o standardach sieci TCP/IP.

[Rozdział 4](chapter4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO NetX.

[Rozdział 5](chapter5.md) — opis sterowników sieciowych dla usługi Azure RTO NetX.

[Dodatek A](appendix-a.md) — Azure RTO NetX Services

[Dodatek B](appendix-b.md) — stałe usługi Azure RTO NetX

[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO NetX

[Dodatek D](appendix-d.md) — interfejs API usługi BSD-Compatible Socket

[Dodatek E](appendix-e.md) -ASCII — wykres

## <a name="azure-rtos-netx-data-types"></a>Azure RTO — typy danych NetX

Oprócz niestandardowych typów danych struktury formantów NetX usługi Azure RTO, istnieje kilka specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO NetX. Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C. Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć w pliku ***tx_port. h*** zawartym w dystrybucji ThreadX.

Poniżej znajduje się lista typów danych wywołań usługi Azure RTO NetX i skojarzonych z nimi znaczenia:

| <!-- -->    | <!-- -->    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **UINT**  | Podstawowa niepodpisana liczba całkowita. Ten typ musi obsługiwać 32-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku. |
| **ULONG** | Typ Long unsigned. Ten typ musi obsługiwać 32-bitowe dane niepodpisane.                                                                      |
| **POZYCJĘ**  | Prawie zawsze jest równoważne z typem void kompilatora.                                                                                 |
| **DELIKATN**  | Najczęściej jest to standardowy 8-bitowy typ znaku.                                                                                           |

Dodatkowe typy danych są używane w źródle NetX usługi Azure RTO. Znajdują się one w plikach ***tx_port. h** _ lub _ *_nx_port. h_**.

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.

2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO NetX, który poprzedza problem.

3. Zawartość **_tx_version_id** i **_nx_version_id** ciągów znalezionych w **_tx_port. h_*_ i _*_nx_port. h_** plików dystrybucji. Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.

4. Zawartość w pamięci RAM następujących zmiennych **ULONG** :

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Te zmienne zawierają informacje o sposobie kompilowania bibliotek RTO ThreadX i Azure RTO NetX.

5. Bufor śledzenia przechwycony natychmiast po wykryciu problemu. Jest to realizowane przez utworzenie bibliotek Azure RTO ThreadX i Azure RTO NetX przy użyciu **TX_ENABLE_EVENT_TRACE** i wywołanie **tx_trace_enable** z informacjami o buforze śledzenia. Aby uzyskać szczegółowe informacje, zobacz Podręcznik użytkownika usługi Azure RTO TraceX.
