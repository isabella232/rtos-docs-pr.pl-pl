---
title: Informacje o Azure RTOS użytkownika NetX Duo
description: Ten przewodnik zawiera kompleksowe informacje na temat Azure RTOS NetX Duo, podwójnego stosu sieciowego IPv4/IPv6 firmy Microsoft o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 032cca3ccdaa7600732d52894d63e5bef366010abaa1145417201f48cb034ab5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790177"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Informacje o Azure RTOS użytkownika NetX Duo

Ten przewodnik zawiera kompleksowe informacje na temat Azure RTOS NetX Duo, podwójnego stosu sieciowego IPv4/IPv6 firmy Microsoft o wysokiej wydajności. 

Jest ona przeznaczona dla osadzonych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe pojęcia dotyczące sieci, Azure RTOS ThreadX i język programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) — wprowadzenie do Azure RTOS NetX Duo

[Rozdział 2](chapter2.md) . Zawiera podstawowe kroki instalowania i używania Azure RTOS NetX Duo z aplikacją ThreadX

[Rozdział 3](chapter3.md) . Zawiera funkcjonalny przegląd systemu NetX Duo Azure RTOS oraz podstawowe informacje na temat standardów sieciowych TCP/IP

[Rozdział 4](chapter4.md) . Szczegóły interfejsu aplikacji do Azure RTOS NetX Duo

[Rozdział 5](chapter5.md) — Opis sterowników sieciowych dla Azure RTOS NetX Duo

[Dodatek A](appendix-a.md) — Azure RTOS NetX Duo Services

[Dodatek B](appendix-b.md) — Azure RTOS NetX Duo

[Dodatek C](appendix-c.md) — Azure RTOS danych NetX Duo

[Dodatek D](appendix-d.md) — interfejs API BSD-Compatible Socket

[Dodatek E](appendix-e.md) — wykres ASCII

## <a name="guide-conventions"></a>Konwencje przewodników

Kursywa — element Typeface oznacza tytuły książek, kładzie nacisk na ważne słowa i wskazuje zmienne.

**Boldface** — element Typeface oznacza nazwy plików, słowa kluczowe i dodatkowo podkreśla ważne słowa i zmienne.

> [!IMPORTANT]
> Symbole informacyjne zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub działanie.
 
> [!WARNING]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, których deweloperzy powinni unikać, ponieważ mogą powodować błędy krytyczne.

## <a name="azure-rtos-netx-duo-data-types"></a>Azure RTOS danych NetX Duo

Oprócz niestandardowych typów danych struktury Azure RTOS NetX Duo istnieje kilka specjalnych typów danych, które są używane w interfejsach wywołań usługi Azure RTOS NetX Duo. Te specjalne typy danych są mapowe bezpośrednio na typy danych podstawowego kompilatora języka C. Ma to na celu zapewnienie przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć ***w pliku tx_port.h*** dołączonym do dystrybucji ThreadX.

Poniżej znajduje się lista typów danych wywołań Azure RTOS NetX Duo oraz ich skojarzone znaczenie:

**UINT:** podstawowa liczba całkowita bez znaku. Ten typ musi obsługiwać niepodpisane dane 32-bitowe; Jest on jednak mapowany na najbardziej wygodny typ danych bez przypisania.  
**ULONG:** niepodpisane typy długie. Ten typ musi obsługiwać niepodpisane dane 32-bitowe.
**VOID:** prawie zawsze równoważne typowi void kompilatora.  
**CHAR:** Najczęściej jest to standardowy 8-bitowy typ znaku.  

Dodatkowe typy danych są używane w źródle Azure RTOS NetX Duo. Znajdują się one w plikach ***tx_port.h** _ lub _ *_nx_port.h*._*

## <a name="customer-support-center"></a>Centrum obsługi klienta

Aby uzyskać pytania lub pomoc, prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

1. Szczegółowy opis problemu, w tym częstotliwość jego występowania i to, czy można go niezawodnie odtworzyć.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTOS NetX Duo, które poprzedzały problem.
3. Zawartość plików _tx_version_id i _nx_version_id znajduje się w plikach tx_port.h i nx_port.h dystrybucji. Te ciągi dostarczają nam cennych informacji dotyczących środowiska uruchomieniowego.
4. Zawartość w pamięci RAM następujących zmiennych ULONG:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Te zmienne zawierają informacje na temat sposobu, w jaki Azure RTOS ThreadX i Azure RTOS Biblioteki NetX Duo.

5. Bufor śledzenia przechwycony natychmiast po wykryciu problemu. Można to osiągnąć, tworząc biblioteki Azure RTOS ThreadX i Azure RTOS NetX Duo za pomocą TX_ENABLE_EVENT_TRACE i wywołując tx_trace_enable z informacjami o buforze śledzenia.
