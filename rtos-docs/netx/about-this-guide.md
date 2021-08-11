---
title: Informacje o Azure RTOS netx
description: Ten przewodnik zawiera kompleksowe informacje o Azure RTOS NetX, stosie sieciowym o wysokiej wydajności firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d77997e8c5bac598f382e1169a56727af09ab108f57c90cc6265df0691b5926
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796416"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a>Informacje o Azure RTOS netx

Ten przewodnik zawiera kompleksowe informacje o Azure RTOS NetX, stosie sieciowym o wysokiej wydajności firmy Microsoft.

Jest ona przeznaczona dla osadzonych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe pojęcia dotyczące sieci, Azure RTOS ThreadX i język programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) — wprowadzenie do Azure RTOS NetX

[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalowania i używania Azure RTOS NetX z aplikacją ThreadX.

[Rozdział 3](chapter3.md) — zawiera omówienie funkcjonalności systemu NetX Azure RTOS i podstawowe informacje na temat standardów sieci TCP/IP.

[Rozdział 4](chapter4.md) . Szczegóły interfejsu aplikacji do Azure RTOS NetX.

[Rozdział 5](chapter5.md) — Opisuje sterowniki sieciowe dla Azure RTOS NetX.

[Dodatek A](appendix-a.md) — Azure RTOS NetX Services

[Dodatek B](appendix-b.md) — Azure RTOS NetX

[Dodatek C](appendix-c.md) — Azure RTOS danych NetX

[Dodatek D](appendix-d.md) — interfejs API BSD-Compatible Socket

[Dodatek E](appendix-e.md) — wykres ASCII

## <a name="azure-rtos-netx-data-types"></a>Azure RTOS danych NetX

Oprócz niestandardowych typów danych struktury Azure RTOS NetX istnieje kilka specjalnych typów danych, które są używane w interfejsach wywołań usługi NetX Azure RTOS NetX. Te specjalne typy danych są mapowe bezpośrednio na typy danych podstawowego kompilatora języka C. Ma to na celu zapewnienie przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć ***w pliku tx_port.h*** dołączonym do dystrybucji ThreadX.

Poniżej znajduje się lista typów danych wywołań Azure RTOS NetX oraz ich skojarzone znaczenie:

| Typy danych | Opis  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Uint**  | Podstawowa liczba całkowita bez znaku. Ten typ musi obsługiwać niepodpisane dane 32-bitowe; Jest on jednak mapowany na najbardziej wygodny typ danych bez przypisania. |
| **Ulong** | Niepodpisane typy długie. Ten typ musi obsługiwać niepodpisane dane 32-bitowe.                                                                      |
| **Void**  | Prawie zawsze równoważne typowi void kompilatora.                                                                                 |
| **Char**  | Najczęściej jest to standardowy 8-bitowy typ znaku.                                                                                           |

Dodatkowe typy danych są używane w źródle Azure RTOS NetX. Znajdują się one w plikach ***tx_port.h** _ lub _ *_nx_port.h*._*

## <a name="customer-support-center"></a>Centrum obsługi klienta

Aby uzyskać pytania lub pomoc, prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

1. Szczegółowy opis problemu, w tym częstotliwość jego występowania i to, czy można go niezawodnie odtworzyć.

2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTOS NetX, które poprzedzały problem.

3. Zawartość _tx_version_id  i **_nx_version_id** w plikach **_tx_port.h_ _ i *_*_nx_port.h_** dystrybucji. Te ciągi dostarczają nam cennych informacji dotyczących środowiska uruchomieniowego.

4. Zawartość w pamięci RAM następujących zmiennych **ULONG:**

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Te zmienne zawierają informacje na temat sposobu Azure RTOS ThreadX i Azure RTOS bibliotek NetX.

5. Bufor śledzenia przechwycony natychmiast po wykryciu problemu. Jest **to** realizowane przez tworzenie bibliotek Azure RTOS ThreadX i Azure RTOS NetX za pomocą TX_ENABLE_EVENT_TRACE  i wywoływanie tx_trace_enable z informacjami o buforze śledzenia. Szczegółowe informacje można znaleźć w Azure RTOS użytkownika tracex.
