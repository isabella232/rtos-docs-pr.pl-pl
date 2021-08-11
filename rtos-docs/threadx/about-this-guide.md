---
title: Informacje o Azure RTOS ThreadX
description: Ten przewodnik zawiera kompleksowe informacje o Azure RTOS ThreadX, jądra firmy Microsoft o wysokiej wydajności w czasie rzeczywistym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28f088409fdd5e2c075cbf90b21d3d260c811806066e74bffc395207cde0239c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802128"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Informacje o Azure RTOS ThreadX

Ten przewodnik zawiera kompleksowe informacje na temat Azure RTOS ThreadX, jądra firmy Microsoft o wysokiej wydajności w czasie rzeczywistym. 

Jest ona przeznaczona dla osadzonego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym i język programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) . Zawiera podstawowe omówienie Azure RTOS ThreadX i jej relacji z opracowywaniem osadzonych funkcji w czasie rzeczywistym

[Rozdział 2](chapter2.md) . Zawiera podstawowe kroki instalowania i używania Azure RTOS ThreadX w aplikacji *od razu po instalacji*

[Rozdział 3](chapter3.md) — szczegółowo opisuje działanie funkcjonalne Azure RTOS ThreadX, jądra o wysokiej wydajności w czasie rzeczywistym

[Rozdział 4](chapter4.md) . Szczegóły interfejsu aplikacji do Azure RTOS ThreadX

[Rozdział 5](chapter5.md) — Opis pisania sterowników we/wy dla Azure RTOS ThreadX

[Rozdział 6](chapter6.md) — Opis aplikacji demonstracyjnej dostarczanej z każdym pakietem obsługi procesora Azure RTOS ThreadX

[Dodatek A](appendix-a.md) — interfejs API Azure RTOS ThreadX

[Dodatek B](appendix-b.md) — Azure RTOS ThreadX

[Dodatek C](appendix-c.md) — Azure RTOS danych ThreadX

[Dodatek D](appendix-d.md) — wykres ASCII

## <a name="guide-conventions"></a>Konwencje przewodników

*Kursywa —* kropka oznacza tytuły książek, podkreśla ważne słowa i wskazuje parametry.

**Boldface** — element typeface oznacza słowa kluczowe, stałe, nazwy typów, elementy interfejsu użytkownika, nazwy zmiennych i dodatkowo podkreśla ważne słowa.

***Kursywa i pogrubienie*** — kropka oznacza nazwy plików i nazwy funkcji.

> [!IMPORTANT]
> Symbole informacyjne zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

> [!WARNING]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni zadbać o to, aby ich unikać, ponieważ mogą powodować błędy krytyczne.

## <a name="azure-rtos-threadx-data-types"></a>Azure RTOS typów danych ThreadX

Oprócz niestandardowych typów danych struktury Azure RTOS ThreadX istnieje szereg specjalnych typów danych, które są używane w interfejsach wywołań usługi Azure RTOS ThreadX. Te specjalne typy danych są mapowe bezpośrednio na typy danych podstawowego kompilatora języka C. Ma to na celu zapewnianie przenośności między różnymi kompilatorami języka C. Dokładną implementację można znaleźć w ***pliku tx_port.h*** dołączonym do źródła.

Poniżej przedstawiono listę typów danych wywołań Azure RTOS ThreadX oraz ich skojarzone znaczenia:

| Typ danych  | Opis |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Uint** | Podstawowa liczba całkowita bez znaku. Ten typ musi obsługiwać 8-bitowe dane niepodpisane; Jest on jednak mapowany na najbardziej wygodny typ danych bez podpisów. |
| **Ulong** | Niepodpisane typy długie. Ten typ musi obsługiwać 32-bitowe niepodpisane dane. |
| **Void** | Prawie zawsze odpowiada typowi void kompilatora. |
| **Char** | Najczęściej standardowy 8-bitowy typ znaku. |
|  |  |

Dodatkowe typy danych są używane w źródle Azure RTOS ThreadX. Znajdują się one również w ***pliku tx_port.h.***

## <a name="customer-support-center"></a>Centrum obsługi klienta

Prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal, aby uzyskać pytania lub pomoc, korzystając z kroków tutaj. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i możliwość jego niezawodnego odtworzenia.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTOS ThreadX, które poprzedzały problem.
3. Zawartość ciągu *_tx_version_id* znajduje się w *tx_port.h* twojej dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska uruchomieniowego.
4. Zawartość w pamięci RAM **_tx_build_options** **ULONG.** Ta zmienna zawiera informacje na temat sposobu Azure RTOS biblioteki ThreadX.
