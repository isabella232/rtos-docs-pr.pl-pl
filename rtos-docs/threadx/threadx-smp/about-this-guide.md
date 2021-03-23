---
title: O tym przewodniku
description: Ten przewodnik zawiera wyczerpujące informacje na temat platformy Azure RTO ThreadX SMP, wbudowanego jądra w czasie rzeczywistym firmy Microsoft o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2399666b5b4d7c34db50d539e200c90f06f7235f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821349"
---
# <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik zawiera wyczerpujące informacje na temat platformy Azure RTO ThreadX SMP, wbudowanego jądra w czasie rzeczywistym firmy Microsoft o wysokiej wydajności.

Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym i język programowania C.

## <a name="organization"></a>Organizacja

| Rozdział       | Omówienie                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Rozdział 1** | Zawiera podstawowe Omówienie ThreadX SMP i jego relacji z programowaniem osadzonym w czasie rzeczywistym.           |
| **Rozdział 2** | Zawiera podstawowe kroki umożliwiające zainstalowanie i użycie ThreadX SMP w aplikacji *od* razu.           |
| **Rozdział 3** | Opisuje szczegółowo funkcjonalne działanie ThreadX SMP, jądra SMP o wysokiej wydajności w czasie rzeczywistym.    |
| **Rozdział 4** | Szczegóły interfejsu aplikacji do ThreadX SMP.                                                        |
| **Rozdział 5** | Opisuje zapisywanie sterowników we/wy dla aplikacji ThreadX SMP.                                                |
| **Rozdział 6** | Zawiera opis aplikacji demonstracyjnej, która jest dostarczana z każdym pakietem obsługiwałym procesor SMP ThreadX. |
| **dodatek A** | Interfejs API SMP ThreadX        |
| **Dodatek B** | ThreadX stałe SMP  |
| **Dodatek C** | ThreadX typy danych SMP |
| **Dodatek D** | Wykres ASCII            |

## <a name="guide-conventions"></a>Konwencje przewodnika

- *Kursywa*  -  *krój kroju oznacza tytuły książek, podkreśla ważne słowa i określa zmienne.*
- **Pogrubiony**  -  **krój kroju oznacza nazwy plików, słowa kluczowe i dalsze akcenty ważne słowa i zmienne.**

> [!IMPORTANT]
> Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

> [!WARNING]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni zachować ostrożność, ponieważ mogą spowodować błędy krytyczne.

## <a name="threadx-smp-data-types"></a>ThreadX typy danych SMP

Oprócz niestandardowych typów danych struktur kontroli SMP ThreadX istnieje szereg specjalnych typów danych, które są używane w interfejsie wywołań usługi SMP ThreadX. Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C. Jest to konieczne w celu zapewnienia przenośności między różnymi kompilatorami języka C. Dokładną implementację można znaleźć w pliku ***tx_port. h*** zawartym na dysku dystrybucyjnym.

Poniżej znajduje się lista typów danych wywołań usługi SMP ThreadX i skojarzonych z nimi znaczenia:

| Typ danych          | Znaczenie                                                          |
| --------- | --------------------------------------------------------- |
| **UINT**  | Podstawowa niepodpisana liczba całkowita. Ten typ musi obsługiwać 8-bitowe dane niepodpisane; Jednak jest on mapowany na najbardziej wygodny typ danych bez znaku. |
| **ULONG** | Typ Long unsigned. Ten typ musi obsługiwać 32-bitowe dane niepodpisane.                                                                     |
| **POZYCJĘ**  | Prawie zawsze jest równoważne z typem void kompilatora.                                                                                |
| **DELIKATN**  | Najczęściej jest to standardowy 8-bitowy typ znaku.                                                                                          |

W źródle SMP ThreadX są używane dodatkowe typy danych. Znajdują się one również w pliku ***tx_port. h*** .

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Adres e-mail pomocy technicznej: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Strona sieci Web: Azure.com/RTOS

### <a name="latest-product-information"></a>Najnowsze informacje o produkcie

Odwiedź witrynę sieci Web azure.com/rtos i wybierz opcję menu "Pomoc techniczna", aby znaleźć najnowsze informacje o pomocy technicznej online, w tym informacje o najnowszych wersjach produktów ThreadX SMP.

### <a name="what-we-need-from-you"></a>Czego potrzebujemy

Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub ThreadX SMP, który poprzedza problem.
3. Zawartość ciągu ***_tx_version_id** _ znaleziono w pliku _ *_tx_port. h_** dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska czasu wykonywania.
4. Zawartość w pamięci RAM ***_tx_build_options*** zmiennej ulong. Ta zmienna zapewni nam informacje o sposobie skompilowania biblioteki SMP ThreadX.

### <a name="where-to-send-comments-about-this-guide"></a>Gdzie można wysłać komentarze dotyczące tego przewodnika

Wyślij wszelkie komentarze i sugestie w centrum pomocy technicznej, [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) w wierszu tematu wpisz "Podręcznik użytkownika THREADX SMP".
