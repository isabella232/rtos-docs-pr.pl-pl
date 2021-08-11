---
title: Azure RTOS użytkownika pliku FileX
description: Ten przewodnik zawiera kompleksowe informacje o Azure RTOS FileX, wysokowydajnego systemu plików w czasie rzeczywistym firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fe70fc3cff6e656328d38b2583116e58a6c98510d5f0554f81a7b728f95457
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782408"
---
# <a name="about-this-filex-user-guide"></a>Informacje o tym podręczniku użytkownika pliku FileX

Ten przewodnik zawiera kompleksowe informacje o Azure RTOS FileX, wysokowydajnego, osadzonego systemu plików w czasie rzeczywistym firmy Microsoft. Aby jak najlepiej zapoznać się z tym przewodnikiem, należy zapoznać się ze standardowymi funkcjami systemu operacyjnego w czasie rzeczywistym, usługami systemu plików FAT i językiem programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1](chapter1.md) — Wprowadzenie Azure RTOS FileX

[Rozdział 2](chapter2.md) . Zawiera podstawowe instrukcje dotyczące instalowania i używania Azure RTOS FileX z aplikacją Azure RTOS ThreadX

[Rozdział 3](chapter3.md) — omówienie funkcjonalne systemu plików Azure RTOS FileX oraz podstawowe informacje na temat formatów systemu plików FAT

[Rozdział 4](chapter4.md) . Szczegóły interfejsu aplikacji do Azure RTOS FileX

[Rozdział 5](chapter5.md) — opis dostarczonego sterownika Azure RTOS RAM FileX oraz sposobu pisania własnych niestandardowych sterowników Azure RTOS FileX

[Rozdział 6](chapter6.md) — Opis Azure RTOS odporności na błędy FileX

[Dodatek A](appendix-a.md) — Azure RTOS FileX Services

[Dodatek B](appendix-b.md) — Azure RTOS FileX, stałe

[Dodatek C](appendix-c.md) — Azure RTOS typów danych FileX

[Dodatek D](appendix-d.md) — wykres ASCII

## <a name="guide-conventions"></a>Konwencje przewodników

*Kursywa —* element Typeface oznacza tytuły książek, podkreśla ważne słowa i wskazuje zmienne.

**Boldface** — element Typeface oznacza nazwy plików, słowa kluczowe i dodatkowo podkreśla ważne słowa i zmienne.

> [!NOTE]
> Symbole informacyjne zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

> [!IMPORTANT]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, których deweloperzy powinni unikać, ponieważ mogą powodować błędy krytyczne.

## <a name="filex-data-types"></a>Typy danych FileX

Oprócz niestandardowych typów danych struktury Azure RTOS FileX istnieje szereg specjalnych typów danych, które są używane w interfejsach wywołań usługi Azure RTOS FileX. Te specjalne typy danych są mapowe bezpośrednio na typy danych podstawowego kompilatora języka C. Ma to na celu zapewnienie przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z Azure RTOS ThreadX i znajduje się w pliku tx_port.h dołączonym do dystrybucji Azure RTOS ThreadX.

Poniżej znajduje się lista typów danych wywołań usługi Azure RTOS FileX oraz powiązanych z nimi znaczenia.

| Typ  | Opis  |
|---|---|
| **Uint** | Podstawowa liczba całkowita bez znaku. Ten typ musi obsługiwać 8-bitowe niepodpisane dane; Jest on jednak mapowany na najbardziej wygodny typ danych bez podpisów. |
| **Ulong** | Niepodpisane typy długie. Ten typ musi obsługiwać 32-bitowe niepodpisane dane. |
| **Void** | Prawie zawsze odpowiada typowi void kompilatora. |
| **Char** | Najczęściej standardowy 8-bitowy typ znaku. |
| **ULONG64** | 64-bitowy typ danych liczb całkowitych bez znaku. |

Dodatkowe typy danych są używane w źródle FileX. Znajdują się one w plikach ***tx_port.h** _ lub _ *_fx_port.h_**.

## <a name="customer-support-center"></a>Centrum obsługi klienta

Prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal, aby uzyskać pytania lub pomoc, korzystając z kroków tutaj. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną.

1. Szczegółowy opis problemu, w tym częstotliwość występowania i możliwość jego niezawodnego odtworzenia.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub PlikuX, które poprzedzały problem.
3. Zawartość _tx_version_id i fx_version_id w plikach _***tx_port.h**_ i _ *_fx_port.h_** dystrybucji. Te ciągi dostarczają nam cennych informacji dotyczących środowiska uruchomieniowego.
4. Zawartość w pamięci RAM następujących zmiennych **ULONG.** Te zmienne zawierają informacje na temat sposobu budów bibliotek ThreadX i FileX:

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
