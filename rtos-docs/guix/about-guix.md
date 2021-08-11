---
title: Podręcznik użytkownika usługi Azure RTOS GUIX
description: Ten przewodnik zawiera kompleksowe informacje na temat Azure RTOS GUIX, produktu graficznego interfejsu użytkownika o wysokiej wydajności firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: e7cc1f44648111a75cd6b28d6b98480b721af9c8521e8fcb8cdac6f24c5514e7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784703"
---
# <a name="about-guix-user-guide"></a>Informacje o podręczniku użytkownika guix

Ten przewodnik zawiera kompleksowe informacje na temat Azure RTOS GUIX, produktu graficznego interfejsu użytkownika o wysokiej wydajności firmy Microsoft. Jest ona przeznaczona dla deweloperów oprogramowania osadzonego w czasie rzeczywistym zaznajomionych z podstawowymi pojęciami z graficznym interfejsem użytkownika, Azure RTOS ThreadX i językiem programowania C.

## <a name="organization"></a>Organizacja

[Rozdział 1 — Wprowadzenie do Azure RTOS GUIX](chapter-1.md)

[Rozdział 2 — Instalowanie i używanie Azure RTOS GUIX](chapter-2.md)

[Rozdział 3 — omówienie funkcjonalności Azure RTOS GUIX](chapter-3.md)

[Rozdział 4 — Opis Azure RTOS GUIX](chapter-4.md)

[Rozdział 5 — Azure RTOS sterowników wyświetlania GUIX](chapter-5.md)  

[Azure RTOS GUIX Example](guix-example.md)

[Dodatek A — Azure RTOS kolorów GUIX](appendix-a.md)

[Dodatek B — Azure RTOS formaty kolorów GUIX](appendix-b.md)

[Dodatek C — style Azure RTOS GUIX](appendix-c.md)

[Dodatek D — Azure RTOS GUIX, atrybuty kanwy i gradientu](appendix-d.md)

[Dodatek E — Azure RTOS guix opis zdarzenia](appendix-e.md)

[Dodatek F — Azure RTOS usług powiązania GUIX RTOS](appendix-f.md)

[Dodatek G — Azure RTOS czcionki GUIX](appendix-g.md)

[Dodatek H — Azure RTOS flagi konfiguracji Build-Time GUIX](appendix-h.md)

[Dodatek I — Azure RTOS informacji GUIX](appendix-i.md)

## <a name="guide-conventions"></a>Konwencje przewodników

*Kursywa —* element Typeface oznacza tytuły książek, podkreśla ważne słowa i wskazuje zmienne.

**Boldface** — element Typeface oznacza nazwy plików, słowa kluczowe i dodatkowo podkreśla ważne słowa i zmienne.

> [!IMPORTANT]
> Symbole informacyjne zwracają uwagę na ważne lub dodatkowe informacje, które mogą mieć wpływ na wydajność lub funkcję.

## <a name="azure-rtos-guix-data-types"></a>Azure RTOS danych GUIX

Oprócz typów danych struktury Azure RTOS niestandardowych GUIX istnieje kilka specjalnych typów danych, które są używane w interfejsach wywołań usługi Azure RTOS GUIX. Te specjalne typy danych są mapowe bezpośrednio na typy danych podstawowego kompilatora języka C. Ma to na celu zapewnienie przenośności między różnymi kompilatorami języka C. Dokładna implementacja jest dziedziczona z ThreadX i można ją znaleźć w ***pliku tx_port.h*** dołączonym do dystrybucji ThreadX.

Poniżej znajduje się lista typów danych wywołań Azure RTOS z interfejsem GUIX oraz powiązanych z nimi znaczeniach:

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Uint**             | Podstawowa liczba całkowita bez znaku. Ten typ jest mapowany na najbardziej wygodny typ danych bez podpisów.                                |
| **INT**              | Podstawowa liczba całkowita ze podpisanym podpisem. Ten typ jest mapowany na najbardziej wygodny typ danych ze podpisanym podpisem.                                    |
| **Ulong**            | Niepodpisane typy długie. Ten typ musi obsługiwać 32-bitowe niepodpisane dane.                                                      |
| **Void**             | Prawie zawsze odpowiada typowi void kompilatora.                                                                 |
| **GX_CHAR**         | Najczęściej typedefed jako kompilator zdefiniowany typ char.                                                               |
| **GX_BYTE**          | 8-bitowy typ ze podpisem.                                                                                                    |
| **GX_UBYTE**         | Typ niepodpisanych 8-bitowych.                                                                                                  |
| **GX_VALUE**        | Typ ze podpisem 16-bitowym lub 32-bitowym. Zdefiniowana zgodnie z potrzebami, aby uzyskać najlepszą wydajność w systemie docelowym.                                |
| **GX_FIXED_VAL**   | Stały typ danych liczbowych punktów.                                                                                        |
| **GX_RESOURCE_ID** | Niepodpisane typy długie.                                                                                                   |
| **GX_COLOR**        | Niepodpisane typy długie.                                                                                                   |
| **GX_STRING**       | Struktura zawierająca GX_CHAR \* gx_string_ptr i UINT gx_string_length.                                          |
| **GX_POINT**        | Struktura zawierająca gx_point_x i gx_point_y.                                                                   |
| **GX_RECTANGLE**    | Struktura zawierająca gx_rectangle_left, gx_rectangle_top, gx_rectangle_right i gx_rectangle_bottom pola. |
| **GX_GLYPH**        | Struktura zawierająca metryki glifów.                                                                                   |
| **GX_FONT**         | Struktura zawierająca metryki czcionek.                                                                                    |
| **GX_BRUSH**        | Struktura zawierająca metryki pędzla.                                                                               |
**GX_PIXELMAP**       | Struktura zawierająca metryki pixelmap.

Dodatkowe typy danych są używane w Azure RTOS GUIX. Znajdują się one w plikach ***tx_port.h** _ lub _ *_gx_port.h*._*

## <a name="customer-support-center"></a>Centrum obsługi klienta

Prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal, aby uzyskać pytania lub pomoc, korzystając z kroków tutaj. Podaj następujące informacje w wiadomości e-mail, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

1. Szczegółowy opis problemu, w tym częstotliwość występowania i możliwość jego niezawodnego odtworzenia.

2. Szczegółowy opis wszelkich zmian w aplikacji i/lub Azure RTOS GUIX, które poprzedzały problem.

3. Zawartość plików _tx_version_id i gx_version_id w plikach _***tx_port.h**_ i _ *_gx_port.h_** dystrybucji. Te ciągi dostarczają nam cennych informacji dotyczących środowiska uruchomieniowego.

4. Zawartość w pamięci RAM następujących zmiennych ULONG:

    **_tx_build_options** **_gx_system_build_options**

    Te zmienne zawierają informacje na temat sposobu, w jaki Azure RTOS ThreadX i Azure RTOS biblioteki GUIX zostały sbudowaną.

5. Zawartość w pamięci RAM następujących zmiennych ULONG:

    **_gx_system_last_error** **_gx_system_error_count**

    Te zmienne śledzą wewnętrzne błędy systemu w Azure RTOS GUIX. Jeśli wartość _gx_system_error_count większa niż jeden, ustaw punkt przerwania dla funkcji zwracanej przez funkcję _gx_system_error_process i podaj wartość _gx_system_last_error w tym momencie. Spowoduje to uzyskanie pierwszego wewnętrznego błędu Azure RTOS GUIX.

6. Bufor śledzenia przechwycony natychmiast po wykryciu problemu. W tym celu należy sbudować biblioteki Azure RTOS ThreadX i Azure RTOS GUIX za pomocą TX_ENABLE_EVENT_TRACE i wywołując tx_trace_enable z informacjami o buforze śledzenia.

7. Projekt Azure RTOS GUIX Studio, z których korzystasz(jeśli ma to zastosowanie), lub co najmniej mały projekt wystarczający do zademonstrować zgłaszaną braki.
