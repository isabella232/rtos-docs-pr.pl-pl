---
title: Informacje o podręczniku usługi Azure RTO ThreadX
description: Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO ThreadX, jądrze w czasie rzeczywistym firmy Microsoft o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822495"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Informacje o podręczniku usługi Azure RTO ThreadX

Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO ThreadX, jądrze w czasie rzeczywistym firmy Microsoft o wysokiej wydajności. 

Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym i język programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) — zawiera podstawowe Omówienie usługi Azure RTO ThreadX i jej relacji z programowaniem osadzonym w czasie rzeczywistym

[Rozdział 2](chapter2.md) — zawiera podstawowe kroki umożliwiające zainstalowanie i użycie usługi Azure RTO ThreadX w aplikacji bezpośrednio *z poziomu pola*

[Rozdział 3](chapter3.md) — szczegółowe omówienie działania funkcjonalnego platformy Azure RTO ThreadX, jądra o wysokiej wydajności w czasie rzeczywistym

[Rozdział 4](chapter4.md) — szczegółowe informacje o interfejsie aplikacji do usługi Azure RTO ThreadX

[Rozdział 5](chapter5.md) . informacje na temat pisania sterowników we/wy dla aplikacji ThreadX usługi Azure RTO

[Rozdział 6](chapter6.md) — opis aplikacji demonstracyjnej, która jest dostarczana z każdym pakietem obsługi procesora usługi Azure RTO ThreadX

[Dodatek A](appendix-a.md) — interfejs API usługi Azure RTO ThreadX

[Dodatek B](appendix-b.md) — stałe usługi Azure RTO ThreadX

[Dodatek C](appendix-c.md) — typy danych usługi Azure RTO ThreadX

[Dodatek D](appendix-d.md) — wykres ASCII

## <a name="guide-conventions"></a>Konwencje przewodnika

*Kursywa* — oznacza tytuły książek, podkreśla ważne słowa i wskazuje parametry.

**Pogrubiona** — kroje liter oznacza słowa kluczowe, stałe, nazwy typów, elementy interfejsu użytkownika, nazwy zmiennych i dalsze akcenty ważnych wyrazów.

***Kursywa i pogrubiona*** — oznacza nazwy plików i nazwy funkcji.

> [!IMPORTANT]
> Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

> [!WARNING]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni zachować ostrożność, ponieważ mogą spowodować błędy krytyczne.

## <a name="azure-rtos-threadx-data-types"></a>Azure RTO — typy danych ThreadX

Oprócz niestandardowych typów danych struktury formantu ThreadX usługi Azure RTO istnieje szereg specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO ThreadX. Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C. Jest to konieczne w celu zapewnienia przenośności między różnymi kompilatorami języka C. Dokładną implementację można znaleźć w pliku ***tx_port. h*** dołączonym do źródła.

Poniżej znajduje się lista typów danych wywołań usługi Azure RTO ThreadX i skojarzonych z nimi znaczenia:

| Typ danych  | Opis |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **UINT** | Podstawowa niepodpisana liczba całkowita. Ten typ musi obsługiwać 8-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku. |
| **ULONG** | Typ Long unsigned. Ten typ musi obsługiwać 32-bitowe dane niepodpisane. |
| **POZYCJĘ** | Prawie zawsze jest równoważne z typem void kompilatora. |
| **DELIKATN** | Najczęściej jest to standardowy 8-bitowy typ znaku. |
|  |  |

Dodatkowe typy danych są używane w źródle ThreadX usługi Azure RTO. Znajdują się one również w pliku ***tx_port. h*** .

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO ThreadX, który poprzedza problem.
3. Zawartość ciągu *_tx_version_id* można znaleźć w pliku *tx_port. h* dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.
4. Zawartość w pamięci RAM _tx_build_options zmiennej  **ULONG** . Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki ThreadX usługi Azure RTO.
