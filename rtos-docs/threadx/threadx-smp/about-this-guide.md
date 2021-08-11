---
title: O tym przewodniku
description: Ten przewodnik zawiera kompleksowe informacje o Azure RTOS SMP ThreadX, wysokiej wydajności osadzone jądra w czasie rzeczywistym firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6a8758bff2f205b06448905634172c05dd7fe189cce9fbe3977f6080c51eb95d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784788"
---
# <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik zawiera kompleksowe informacje o Azure RTOS SMP ThreadX, wysokiej wydajności osadzone jądra w czasie rzeczywistym firmy Microsoft.

Jest ona przeznaczona dla osadzonego dewelopera oprogramowania w czasie rzeczywistym. Deweloper powinien znać standardowe funkcje systemu operacyjnego w czasie rzeczywistym i język programowania C.

## <a name="organization"></a>Organizacja

| Rozdział       | Omówienie                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Rozdział 1** | Zawiera podstawowe omówienie funkcji SMP ThreadX i jej relacji z opracowywaniem osadzonych funkcji w czasie rzeczywistym.           |
| **Rozdział 2** | Zawiera podstawowe instrukcje dotyczące instalowania i używania funkcji ThreadX SMP w aplikacji *od razu po zainstalowaniu programu*.           |
| **Rozdział 3** | W tym artykule szczegółowo opisano działanie funkcjonalne threadx SMP, jądra SMP o wysokiej wydajności w czasie rzeczywistym.    |
| **Rozdział 4** | Szczegóły interfejsu aplikacji do SMP ThreadX.                                                        |
| **Rozdział 5** | Opisuje pisanie sterowników we/wy dla aplikacji SMP ThreadX.                                                |
| **Rozdział 6** | Opisuje aplikację demonstracyjną dostarczaną z każdym pakietem obsługi procesora SMP ThreadX. |
| **dodatek A** | ThreadX SMP API        |
| **Dodatek B** | Stałe SMP ThreadX  |
| **Dodatek C** | Typy danych SMP ThreadX |
| **Dodatek D** | Wykres ASCII            |

## <a name="guide-conventions"></a>Konwencje przewodników

- *Kursywa*  -  *element typeface oznacza tytuły książek, podkreśla* ważne słowa i wskazuje zmienne.
- **Pogrubienie**  -  **Element typeface oznacza nazwy plików, słowa kluczowe i dodatkowo** podkreśla ważne słowa i zmienne.

> [!IMPORTANT]
> Symbole informacyjne zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

> [!WARNING]
> Symbole ostrzegawcze zwracają uwagę na sytuacje, w których deweloperzy powinni zadbać o to, aby ich unikać, ponieważ mogą powodować błędy krytyczne.

## <a name="threadx-smp-data-types"></a>Typy danych SMP ThreadX

Oprócz niestandardowych typów danych struktury sterowania SMP ThreadX istnieje szereg specjalnych typów danych, które są używane w interfejsach wywołań usługi SMP ThreadX. Te specjalne typy danych są mapowe bezpośrednio na typy danych podstawowego kompilatora języka C. Ma to na celu zapewnianie przenośności między różnymi kompilatorami języka C. Dokładną implementację można znaleźć w ***pliku tx_port.h*** dołączonym do dysku dystrybucji.

Poniżej znajduje się lista typów danych wywołań usługi SMP ThreadX i skojarzonych z nimi znaczenia:

| Typ danych          | Znaczenie                                                          |
| --------- | --------------------------------------------------------- |
| **Uint**  | Podstawowa liczba całkowita bez znaku. Ten typ musi obsługiwać 8-bitowe niepodpisane dane; Jest on jednak mapowany na najbardziej wygodny typ danych bez podpisów. |
| **Ulong** | Niepodpisane typy długie. Ten typ musi obsługiwać 32-bitowe niepodpisane dane.                                                                     |
| **Void**  | Prawie zawsze odpowiada typowi void kompilatora.                                                                                |
| **Char**  | Najczęściej standardowy 8-bitowy typ znaku.                                                                                          |

Dodatkowe typy danych są używane w źródle SMP ThreadX. Znajdują się one również w ***pliku tx_port.h.***

## <a name="customer-support-center"></a>Centrum obsługi klienta

Adres e-mail pomocy [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) technicznej: strona internetowa: azure.com/rtos

### <a name="latest-product-information"></a>Najnowsze informacje o produkcie

Odwiedź witrynę azure.com/rtos sieci Web i wybierz opcję menu "Pomoc techniczna", aby znaleźć najnowsze informacje o pomocy technicznej online, w tym informacje o najnowszych wersjach produktów ThreadX SMP.

### <a name="what-we-need-from-you"></a>Czego potrzebujemy od Ciebie

Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i możliwość jego niezawodnego odtworzenia.
2. Szczegółowy opis wszelkich zmian w aplikacji i/lub threadX SMP, które poprzedzały problem.
3. Zawartość ciągu ***_tx_version_id** _ znajduje się w _ *_tx_port.h_** pliku dystrybucji. Ten ciąg zapewni nam cenne informacje dotyczące środowiska uruchomieniowego.
4. Zawartość w pamięci RAM zmiennej ***_tx_build_options*** ULONG. Ta zmienna będzie zawierała informacje na temat sposobu budu biblioteki SMP ThreadX.

### <a name="where-to-send-comments-about-this-guide"></a>Where to Send Comments About This Guide

Wszelkie komentarze i sugestie należy wysyłać pocztą e-mail do Centrum pomocy technicznej pod adresem Enter "ThreadX SMP User Guide" (Podręcznik użytkownika [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) threadX SMP) w wierszu tematu.
