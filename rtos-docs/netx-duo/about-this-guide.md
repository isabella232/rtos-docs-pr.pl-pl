---
title: Informacje o podręczniku użytkownika platformy Azure RTO NetX Duo
description: Ten przewodnik zawiera wyczerpujące informacje o platformie Azure RTO NetX Duo, czyli podwójnym stosie sieci IPv4/IPv6 o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822141"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Informacje o podręczniku użytkownika platformy Azure RTO NetX Duo

Ten przewodnik zawiera wyczerpujące informacje o platformie Azure RTO NetX Duo, czyli podwójnym stosie sieci IPv4/IPv6 o wysokiej wydajności. 

Jest ona przeznaczona dla wbudowanych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe pojęcia dotyczące sieci, Azure RTO ThreadX i języka programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) — wprowadzenie do usługi Azure RTO NetX Duo

[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalacji i używania platformy Azure RTO NetX Duo z aplikacją ThreadX

[Rozdział 3](chapter3.md) — zawiera przegląd funkcjonalny systemu Azure RTO NetX Duo oraz podstawowe informacje na temat standardów sieci TCP/IP

[Rozdział 4](chapter4.md) — szczegóły interfejsu aplikacji na platformie Azure RTO NetX Duo

[Rozdział 5](chapter5.md) — opis sterowników sieciowych dla usługi Azure RTO NetX Duo

[Dodatek A](appendix-a.md) — usługi Azure RTO NetX Duo

[Dodatek B](appendix-b.md) — stałe platformy Azure RTO NetX Duo

[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO NetX Duo

[Dodatek D](appendix-d.md) — interfejs API usługi BSD-Compatible Socket

[Dodatek E](appendix-e.md) -ASCII — wykres

## <a name="guide-conventions"></a>Konwencje przewodnika

Kursywa — oznacza tytuły książek, wyróżnia ważne słowa i określa zmienne.

**Pogrubiona** — kroje liter oznacza nazwy plików, słowa kluczowe i bardziej podkreśla ważne słowa i zmienne.

> [!IMPORTANT]
> Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.
 
> [!WARNING]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni unikać, ponieważ mogą spowodować błędy krytyczne.

## <a name="azure-rtos-netx-duo-data-types"></a>Typy danych usługi Azure RTO NetX Duo

Oprócz niestandardowych typów danych struktury kontroli usługi Azure RTO NetX Duo istnieje kilka specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO NetX Duo. Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C. Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć w pliku ***tx_port. h*** zawartym w dystrybucji ThreadX.

Poniżej znajduje się lista typów danych wywołań usługi Azure RTO NetX Duo i skojarzonych z nimi znaczenia:

**Uint**: podstawowa liczba całkowita bez znaku. Ten typ musi obsługiwać 32-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku.  
**ULONG**: typ Long unsigned. Ten typ musi obsługiwać 32-bitowe dane niepodpisane.
**Void**: prawie zawsze odpowiada typowi void kompilatora.  
**Char**: najczęściej jest to standardowy 8-bitowy typ znaku.  

Dodatkowe typy danych są używane w źródle Azure RTO NetX Duo. Znajdują się one w plikach ***tx_port. h** _ lub _ *_nx_port. h_**.

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO NetX Duo, który poprzedza problem.
3. Zawartość _tx_version_id i _nx_version_id ciągów znalezionych w plikach tx_port. h i nx_port. h dystrybucji. Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.
4. Zawartość w pamięci RAM następujących zmiennych ULONG:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Te zmienne będą zawierać informacje o sposobie kompilowania bibliotek Azure RTO ThreadX i Azure RTO NetX Duo.

5. Bufor śledzenia przechwycony natychmiast po wykryciu problemu. Jest to realizowane przez utworzenie bibliotek Azure RTO ThreadX i Azure RTO NetX Duo przy użyciu TX_ENABLE_EVENT_TRACE i wywołanie tx_trace_enable z informacjami o buforze śledzenia.
