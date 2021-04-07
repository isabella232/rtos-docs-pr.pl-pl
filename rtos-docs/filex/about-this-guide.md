---
title: Podręcznik użytkownika usługi Azure RTO FileX
description: Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO FileX, systemu plików o wysokiej wydajności w czasie rzeczywistym firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 640d9ed4c8037d3af6c5f45158c9496ad1258a3c
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550103"
---
# <a name="about-this-filex-user-guide"></a>Informacje o tym podręczniku użytkownika FileX

Ten przewodnik zawiera wyczerpujące informacje na temat usługi Azure RTO FileX, systemu plików o wysokiej wydajności w czasie rzeczywistym od firmy Microsoft. Aby najlepiej wykorzystać ten przewodnik, należy zapoznać się ze standardowymi funkcjami systemu operacyjnego w czasie rzeczywistym, usługami systemu plików FAT i językiem programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) — wprowadzenie do usługi Azure RTO FileX

[Rozdział 2](chapter2.md) — zawiera podstawowe kroki instalacji i używania usługi Azure RTO FileX z aplikacją Azure RTO ThreadX

[Rozdział 3](chapter3.md) — zawiera przegląd funkcjonalny systemu Azure RTO FileX i podstawowe informacje na temat formatów systemu plików FAT

[Rozdział 4](chapter4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO FileX

[Rozdział 5](chapter5.md) — opis dostarczonego sterownika ram usługi Azure RTO FileX i sposobu pisania własnych niestandardowych sterowników usługi Azure RTO FileX

[Rozdział 6](chapter6.md) — Opis modułu odpornego na błędy usługi Azure RTO FileX

[Dodatek A](appendix-a.md) — Azure RTO FileX Services

[Dodatek B](appendix-b.md) — stałe usługi Azure RTO FileX

[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO FileX

[Dodatek D](appendix-d.md) — wykres ASCII

## <a name="guide-conventions"></a>Konwencje przewodnika

*Kursywa* — oznacza tytuły książek, wyróżnia ważne słowa i określa zmienne.

**Pogrubiona** — kroje liter oznacza nazwy plików, słowa kluczowe i bardziej podkreśla ważne słowa i zmienne.

> [!NOTE]
> Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

> [!IMPORTANT]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni unikać, ponieważ mogą spowodować błędy krytyczne.

## <a name="filex-data-types"></a>FileX — typy danych

Oprócz niestandardowych typów danych struktury formantu FileX usługi Azure RTO istnieje szereg specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO FileX. Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C. Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z usługi Azure RTO ThreadX i można ją znaleźć w pliku tx_port. h zawartym w dystrybucji usługi Azure RTO ThreadX.

Poniżej znajduje się lista typów danych wywołań usługi Azure RTO FileX i skojarzonych z nimi znaczenia.

| Typ  | Opis  |
|---|---|
| **UINT** | Podstawowa niepodpisana liczba całkowita. Ten typ musi obsługiwać 8-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku. |
| **ULONG** | Typ Long unsigned. Ten typ musi obsługiwać 32-bitowe dane niepodpisane. |
| **POZYCJĘ** | Prawie zawsze jest równoważne z typem void kompilatora. |
| **DELIKATN** | Najczęściej jest to standardowy 8-bitowy typ znaku. |
| **ULONG64** | 64-bitowy typ danych Liczba całkowita bez znaku. |

W źródle FileX są używane dodatkowe typy danych. Znajdują się one w plikach ***tx_port. h** _ lub _ *_fx_port. h_**.

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej.

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub FileX, które poprzedzają problem.
3. Zawartość _tx_version_id i _fx_version_id ciągów znalezionych w plikach ***tx_port. h**_ i _ *_fx_port. h_** dystrybucji. Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.
4. Zawartość w pamięci RAM następujących zmiennych **ULONG** . Te zmienne zawierają informacje o sposobie kompilowania bibliotek ThreadX i FileX:

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
