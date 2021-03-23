---
title: Podręcznik użytkownika usługi Azure RTOS GUIX
description: Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO GUIX, produkt graficzny GUI o wysokiej wydajności od firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823196"
---
# <a name="about-guix-user-guide"></a>Informacje o podręczniku użytkownika GUIX

Ten przewodnik zawiera wyczerpujące informacje o usłudze Azure RTO GUIX, produkt graficzny GUI o wysokiej wydajności od firmy Microsoft. Jest ona przeznaczona dla wbudowanych deweloperów oprogramowania w czasie rzeczywistym, którzy znają podstawowe koncepcje graficznego interfejsu użytkownika, platformy Azure RTO ThreadX i języka programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1 — wprowadzenie do usługi Azure RTO GUIX](chapter-1.md)

[Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO GUIX](chapter-2.md)

[Rozdział 3 — Omówienie funkcjonalne usługi Azure RTO GUIX](chapter-3.md)

[Rozdział 4 — Opis usług Azure RTO GUIX Services](chapter-4.md)

[Rozdział 5 — sterowniki ekranu usługi Azure RTO GUIX](chapter-5.md)  

[Przykład usługi Azure RTO GUIX](guix-example.md)

[Dodatek A — definicje kolorów usługi Azure RTO GUIX](appendix-a.md)

[Dodatek B — formaty kolorów w usłudze Azure RTO GUIX](appendix-b.md)

[Dodatek C — style widżetu GUIX usługi Azure RTO](appendix-c.md)

[Dodatek D — RTO GUIX, obszar roboczy i atrybuty gradientu platformy Azure](appendix-d.md)

[Dodatek E-Azure RTO GUIX — opis zdarzenia](appendix-e.md)

[Dodatek F-Azure RTO GUIX RTO bind Services](appendix-f.md)

[Dodatek G — struktura czcionki GUIX usługi Azure RTO](appendix-g.md)

[Dodatek H-Azure RTO GUIX Build-Time flagi konfiguracji](appendix-h.md)

[Dodatek I — struktura informacji GUIX usługi Azure RTO](appendix-i.md)

## <a name="guide-conventions"></a>Konwencje przewodnika

*Kursywa* — oznacza tytuły książek, wyróżnia ważne słowa i określa zmienne.

**Pogrubiona** — kroje liter oznacza nazwy plików, słowa kluczowe i bardziej podkreśla ważne słowa i zmienne.

> [!IMPORTANT]
> Symbole informacji zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

## <a name="azure-rtos-guix-data-types"></a>Azure RTO — typy danych GUIX

Oprócz niestandardowych typów danych struktury formantów GUIX usługi Azure RTO, istnieje kilka specjalnych typów danych, które są używane w interfejsie wywołań usługi Azure RTO GUIX. Te specjalne typy danych są mapowane bezpośrednio na typy danych podstawowego kompilatora języka C. Jest to realizowane w celu zapewnienia przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć w pliku ***tx_port. h*** zawartym w dystrybucji ThreadX.

Poniżej znajduje się lista typów danych wywołań usługi Azure RTO GUIX i skojarzonych z nimi znaczenia:

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **UINT**             | Podstawowa niepodpisana liczba całkowita. Ten typ jest mapowany na najbardziej wygodny typ danych bez znaku.                                |
| **INT**              | Podstawowa liczba całkowita ze znakiem. Ten typ jest mapowany na najbardziej wygodny typ danych ze znakiem.                                    |
| **ULONG**            | Typ Long unsigned. Ten typ musi obsługiwać 32-bitowe dane niepodpisane.                                                      |
| **POZYCJĘ**             | Prawie zawsze jest równoważne z typem void kompilatora.                                                                 |
| **GX_CHAR**         | Najczęściej jest to element typedef w postaci typu char zdefiniowanego przez kompilator.                                                               |
| **GX_BYTE**          | 8-bitowy typ podpisany.                                                                                                    |
| **GX_UBYTE**         | 8-bitowy typ unsigned.                                                                                                  |
| **GX_VALUE**        | 16 lub 32 Typ ze znakiem. Zdefiniowane w razie potrzeby w celu uzyskania najlepszej wydajności w systemie docelowym.                                |
| **GX_FIXED_VAL**   | Stały typ danych liczbowych.                                                                                        |
| **GX_RESOURCE_ID** | Typ Long unsigned.                                                                                                   |
| **GX_COLOR**        | Typ Long unsigned.                                                                                                   |
| **GX_STRING**       | Struktura zawierająca GX_CHAR \* gx_string_ptr i UINT gx_string_length.                                          |
| **GX_POINT**        | Struktura zawierająca gx_point_x i gx_point_y.                                                                   |
| **GX_RECTANGLE**    | Struktura zawierająca pola gx_rectangle_left, gx_rectangle_top, gx_rectangle_right i gx_rectangle_bottom. |
| **GX_GLYPH**        | Struktura zawierająca metryki symboli.                                                                                   |
| **GX_FONT**         | Struktura zawierająca metryki czcionki.                                                                                    |
| **GX_BRUSH**        | Struktura zawierająca metryki pędzla.                                                                               |
**GX_PIXELMAP**       | Struktura zawierająca metryki Pixelmap.

Dodatkowe typy danych są używane w źródle GUIX usługi Azure RTO. Znajdują się one w plikach ***tx_port. h** _ lub _ *_gx_port. h_**.

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Przekaż nam następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i tego, czy może być niezawodnie odtwarzany.

2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTO GUIX, który poprzedza problem.

3. Zawartość _tx_version_id i _gx_version_id ciągów znalezionych w plikach ***tx_port. h**_ i _ *_gx_port. h_** dystrybucji. Te ciągi dostarczają nam cenne informacje dotyczące środowiska czasu wykonywania.

4. Zawartość w pamięci RAM następujących zmiennych ULONG:

    **_tx_build_options** **_gx_system_build_options**

    Te zmienne zawierają informacje o sposobie kompilowania bibliotek RTO ThreadX i Azure RTO GUIX.

5. Zawartość w pamięci RAM następujących zmiennych ULONG:

    **_gx_system_last_error** **_gx_system_error_count**

    Te zmienne śledzą wewnętrzne błędy systemu w usłudze Azure RTO GUIX. Jeśli _gx_system_error_count jest większa niż jeden, należy ustawić punkt przerwania dla funkcji Return w funkcji _gx_system_error_process i podać wartość _gx_system_last_error w tym momencie. Spowoduje to zwrócenie pierwszego wewnętrznego błędu systemu Azure RTO GUIX.

6. Bufor śledzenia przechwycony natychmiast po wykryciu problemu. Jest to realizowane przez utworzenie bibliotek Azure RTO ThreadX i Azure RTO GUIX przy użyciu TX_ENABLE_EVENT_TRACE i wywołanie tx_trace_enable z informacjami o buforze śledzenia.

7. Używany projekt platformy Azure RTO GUIX Studio (jeśli dotyczy) lub co najmniej mały projekt wystarczający do zademonstrowania zgłaszanych niedoborów.
