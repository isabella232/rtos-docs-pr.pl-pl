---
title: Rozdział 6 — Azure RTOS z tolerancją błędów FileX
description: Ten rozdział zawiera opis modułu odporności na błędy systemu Azure RTOS FileX, który został zaprojektowany w celu zachowania integralności systemu plików w przypadku utraty zasilania lub wysunięcia nośnika w trakcie operacji zapisu pliku.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 66bffa2dbf52bc458bfaf124aa006a79e810100ac2e926c17444daf090519e66
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783752"
---
# <a name="chapter-6---azure-rtos-filex-fault-tolerant-module"></a>Rozdział 6 — Azure RTOS z tolerancją błędów FileX

Ten rozdział zawiera opis modułu odporności na błędy systemu Azure RTOS FileX, który został zaprojektowany w celu zachowania integralności systemu plików w przypadku utraty zasilania lub wysunięcia nośnika w trakcie operacji zapisu pliku.

## <a name="filex-fault-tolerant-module-overview"></a>Omówienie modułu odporności na błędy FileX

Gdy aplikacja zapisuje dane w pliku, plik FileX aktualizuje zarówno klastry danych, jak i informacje o systemie. Te aktualizacje należy wykonać jako niepodzielną operację, aby zapewnić spójność informacji w systemie plików. Na przykład podczas dołączania danych do pliku plik FileX musi znaleźć dostępny klaster na nośniku, zaktualizować łańcuch FAT, zaktualizować długość pliku we wpisie katalogu i prawdopodobnie zaktualizować numer początkowego klastra we wpisie katalogu. Awaria zasilania lub wysunięcie nośnika może zakłócić sekwencję aktualizacji, co pozostawi system plików w niespójnym stanie. Jeśli niespójny stan nie zostanie poprawiony, aktualizowane dane mogą zostać utracone, a z powodu uszkodzenia informacji o systemie kolejne działanie systemu plików może uszkodzić inne pliki lub katalogi na nośniku.

Moduł tolerowania błędów FileX działa przez dzienniki kroków  wymaganych do zaktualizowania pliku przed zastosowaniem tych kroków do systemu plików. Jeśli aktualizacja pliku powiedzie się, te wpisy dziennika zostaną usunięte. Jeśli jednak aktualizacja pliku zostanie przerwana, wpisy dziennika będą przechowywane na nośniku. Następnym razem, gdy nośnik zostanie zainstalowany, plik FileX wykryje te wpisy dziennika z poprzedniej (niedokończonej) operacji zapisu. W takich przypadkach plik FileX może odzyskać dane po awarii, wywrócąc zmiany wprowadzone już w systemie plików lub ponownie zastosując wymagane zmiany w celu ukończenia poprzedniej operacji. W ten sposób moduł odporności na błędy FileX zachowuje integralność systemu plików, jeśli nośnik utraci zasilanie podczas operacji aktualizacji.

> [!IMPORTANT]
> *Moduł z tolerancją błędów FileX nie został zaprojektowany tak, aby zapobiegać uszkodzeniem systemu plików spowodowanym uszkodzeniem nośnika fizycznego i prawidłowymi danymi w nim.*

> [!IMPORTANT]
> *Gdy moduł z tolerancją błędów FileX chroni nośnik, nośnik nie może być zainstalowany przez coś innego niż PlikX z włączoną tolerancją błędów. Może to spowodować niespójność wpisów dziennika w systemie plików z informacjami o systemie na nośniku. Jeśli moduł z tolerancją błędów FileX spróbuje przetworzyć wpisy dziennika po zaktualizowaniu nośnika przez inny system plików, procedura odzyskiwania może się nie powieść, pozostawiając cały system plików w nieprzewidywalnym stanie.*

## <a name="use-of-the-fault-tolerant-module"></a>Korzystanie z modułu odporności na błędy

Funkcja tolerowania błędów FileX jest dostępna dla wszystkich systemów plików FAT obsługiwanych przez system FileX, w tym FAT12, FAT16, FAT32 i exFAT. Aby włączyć funkcję tolerancji błędów, plik FileX musi być zbudowany przy użyciu zdefiniowanego **FX_ENABLE_FAULT_TOLERANT** błędu. W czasie działania aplikacja uruchamia usługę tolerancji błędów, wywołując fx_fault_tolerant_enable _ natychmiast po ***wywołaniu*** funkcji _ fx_media_open . Po włączeniu odporności na uszkodzenia wszystkie operacje zapisu plików na wyznaczonym nośniku są chronione. Domyślnie moduł nie jest włączony.

> [!IMPORTANT]
> *Aplikacja musi upewnić się, że dostęp do systemu plików nie jest uzyskiwany przed **fx_fault_tolerant_enable** _ wywoływania. Jeśli aplikacja zapisuje dane w systemie plików przed włączeniem odporności na uszkodzenia, operacja zapisu może uszkodzić nośnik, jeśli wcześniejsze operacje zapisu nie zostały ukończone, a system plików nie został przywrócony przy użyciu funkcji dziennika entries._

## <a name="filex-fault-tolerant-module-log"></a>Dziennik modułu z tolerancją błędów FileX

Dziennik z tolerancją błędów FileX zajmuje jeden klaster logiczny w programie flash. Indeks do numeru początkowego klastra tego klastra jest rejestrowany w sektorze rozruchowym nośnika z przesunięciem określonym przez symbol **FX_FAULT_TOLERANT_BOOT_INDEX**. Domyślnie ten symbol jest zdefiniowany jako 116. Ta lokalizacja jest wybierana, ponieważ jest oznaczona jako zarezerwowana w specyfikacji FAT12/16/32 i exFAT.

Rysunek 5" Układ struktury dziennika przedstawia ogólny układ struktury dziennika. Struktura dziennika zawiera trzy sekcje: Nagłówek dziennika, Łańcuch FAT i Wpisy dziennika.

> [!IMPORTANT]
> *Wszystkie wartości wielo bajtów przechowywane we wpisach dziennika są w formacie Little Endian.*

![Układ struktury dziennika](./media/user-guide/log-structure-layout.png)

**Rysunek 5. Układ struktury dziennika**

Obszar Nagłówek dziennika zawiera informacje opisujące całą strukturę dziennika i szczegółowo objaśnia każde pole.

**TABELA 8. Obszar nagłówka dziennika**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
|ID (Identyfikator)|4|Identyfikuje strukturę dziennika z tolerancją błędów FileX. Struktura dziennika jest uznawana za nieprawidłową, jeśli wartość identyfikatora nie jest 0x46544C52.|
|Całkowity rozmiar|2|Wskazuje całkowity rozmiar (w bajtach) całej struktury dziennika.|
|Sumy kontrolne nagłówka|2|Sumy kontrolnej, która konwertuje obszar nagłówka dziennika. Struktura dziennika jest uważana za nieprawidłową, jeśli weryfikacja sumy kontrolnej w polach nagłówka nie powiedzie się.|
|Numer wersji|2|Numery wersji głównych i pomocniczych systemu FileX z tolerancją błędów.|
|Zarezerwowany|2|Na przyszłość.|

Po obszarze Nagłówek dziennika znajduje się obszar Dziennika łańcucha FAT. Rysunek 9 zawiera informacje opisujące sposób modyfikacji łańcucha FAT. Ten obszar dziennika zawiera informacje dotyczące klastrów przydzielanych do pliku, klastrów usuwanych z pliku oraz miejsce wstawiania/usuwania oraz opis każdego pola w obszarze dziennika łańcucha FAT.

**TABELA 9. Obszar dziennika łańcucha FAT**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
|Sumy kontrolne dziennika łańcucha FAT|2|Sumy kontrolne całego obszaru dziennika łańcucha FAT. Obszar dziennika łańcucha FAT jest uznawany za nieprawidłowy, jeśli weryfikacja sumy kontrolnej zakończy się niepowodzeniem.|
|Flaga|1|Prawidłowe wartości flag to:<br/>0x01 FAT Chain Valid (Prawidłowy łańcuch FAT)<br />0x02 BITMAP jest używana|
|Zarezerwowany|1|Zarezerwowane do użytku w przyszłości|
|Punkt wstawiania — przód|4|Klaster (należący do oryginalnego łańcucha FAT), do którego zostanie dołączony nowo utworzony łańcuch.|
|Klaster head nowego łańcucha FAT|4|Pierwszy klaster nowo utworzonego łańcucha FAT|
|Klaster head oryginalnego łańcucha FAT|4|Pierwszy klaster części oryginalnego łańcucha FAT, który ma zostać usunięty.|
|Punkt wstawiania — Wstecz|4|Oryginalny klaster, do którego łączy się nowo utworzony łańcuch FAT.|
|Następny punkt usuwania|4|To pole pomaga w procedurze oczyszczania łańcucha FAT.|

Obszar wpisów dziennika zawiera wpisy dziennika, które opisują zmiany wymagane do odzyskania danych po awarii. W module z tolerancją błędów FileX są obsługiwane trzy typy wpisów dziennika: wpis dziennika FAT; Wpis dziennika katalogu; i wpis dziennika mapy bitowej.

Te wpisy dziennika są szczegółowo opisane w trzech poniższych rysunkach i trzech tabelach.

![Wpis dziennika FAT](./media/user-guide/fat-log-entry.png)

**Rysunek 6. Wpis dziennika FAT**

**TABELA 10. Wpis dziennika FAT**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
Typ|2|Typ wpisu musi być FX_FAULT_TOLERANT_FAT_LOG_TYPE|
|Rozmiar|2|Rozmiar tego wpisu|
|Numer klastra|4|Numer klastra|
|Wartość|4|Wartość do zapisu we wpisie FAT|

![Wpis dziennika katalogu](./media/user-guide/directory-log-entry.png)

**Rysunek 7. Wpis dziennika katalogu**

**TABELA 11. Wpis dziennika katalogu**

|Pole|Size(w bajtach)|Opis|
|-----|--------------|-----------|
|Typ|2|Typ wpisu musi być FX_FAULT_TOLERANT_DIRECTORY_LOG_TYPE|
|Rozmiar|2|Rozmiar tego wpisu|
|Przesunięcie sektora|4|Przesunięcie (w bajtach) do sektora, w którym znajduje się ten katalog.|
|Sektor dziennika|4|Sektor, w którym znajduje się wpis katalogu|
|Dane dziennika|Zmienna|Zawartość wpisu katalogu|

![Wpis dziennika mapy bitowej](./media/user-guide/bitmap-log-entry.png)

**Rysunek 8. Wpis dziennika mapy bitowej**

**TABELA 12. Wpis dziennika mapy bitowej**

|Pole|Size(w bajtach)|Opis|
|-----|--------------|-----------|
|Typ|2|Typ wpisu musi być FX_FAULT_TOLERANT_BITMAP_LOG_TYPE|
|Rozmiar|2|Rozmiar tego wpisu|
|Numer klastra|4|Numer klastra|
|Wartość|4|Wartość do zapisu we wpisie FAT|

## <a name="fault-tolerant-protection"></a>Ochrona przed uszkodzeniami

Po uruchamianiu modułu odporności na błędy FileX najpierw wyszukuje na nośniku istniejący plik dziennika z tolerancją błędów. Jeśli nie można znaleźć prawidłowego pliku dziennika, plik FileX uzna nośnik za niechroniony. W takim przypadku plik FileX utworzy na nośniku plik dziennika z tolerancją błędów.

> [!IMPORTANT]
> *FileX nie może chronić systemu plików, jeśli został uszkodzony przed rozpoczęciem modułu odporności na uszkodzenia PlikuX. *

Jeśli znajduje się plik dziennika z tolerancją błędów, plik FileX sprawdza istniejące wpisy dziennika. Plik dziennika bez wpisu dziennika wskazuje, że poprzednia operacja na pliku powiodła się, a wszystkie wpisy dziennika zostały usunięte. W takim przypadku aplikacja może rozpocząć korzystanie z systemu plików z ochroną przed uszkodzeniami.

Jeśli jednak znajdują się wpisy dziennika, plik FileX musi zakończyć poprzednią operację na pliku lub cofnąć zmiany już zastosowane do systemu plików, cofnij zmiany. W obu przypadkach po zastosowaniu wpisów dziennika do systemu plików system plików jest przywracany do spójnego stanu, a aplikacja może ponownie rozpocząć korzystanie z systemu plików.

W przypadku nośników chronionych przez plik FileX podczas operacji aktualizacji pliku część danych jest zapisywana bezpośrednio na nośniku. PlikX zapisuje dane, rejestruje również wszelkie zmiany, które należy zastosować do wpisów katalogu, tabeli FAT. Te informacje są rejestrowane we wpisach dziennika z tolerancją pliku. Takie podejście gwarantuje, że aktualizacje systemu plików będą występować po napiseniu danych na nośniku. Jeśli nośnik zostanie wysucony w fazie zapisu danych, kluczowe informacje o systemie plików nie zostały jeszcze zmienione. W związku z tym na system plików nie ma wpływu przerwa.

Po pomyślnym zapisie wszystkich danych na nośniku plik FileX śledzi informacje we wpisach dziennika w celu wprowadzenia zmian w informacjach o systemie po jednym wpisie na raz. Po zatwierdzona na nośniku wszystkie informacje o systemie wpisy dziennika są usuwane z dziennika odporności na uszkodzenia. W tym momencie plik FileX kończy operację aktualizacji pliku.

Podczas operacji aktualizacji pliku pliki nie są aktualizowane na miejscu. Moduł z tolerancją błędów przydziela sektor danych do zapisu nowych danych, a następnie usuwa sektor zawierający dane do nadpisania, aktualizując powiązane wpisy FAT w celu połączenia nowego sektora z chianem. W sytuacjach, w których należy zmodyfikować częściowe dane w klastrze, plik FileX zawsze przydziela nowe klastry, zapisuje wszystkie dane ze starych klastrów ze zaktualizowanymi danymi do nowych klastrów, a następnie wydzieli stare klastry. Gwarantuje to, że jeśli aktualizacja pliku zostanie przerwana, oryginalny plik jest nienaruszony. Aplikacja musi mieć świadomość, że w obszarze Ochrona przed uszkodzeniami pliku FileX aktualizacja danych w pliku wymaga, aby nośnik miał wystarczająco dużo wolnego miejsca do przechowywania nowych danych, zanim będzie można zwolnić sektory ze starymi danymi. Jeśli nośnik nie ma wystarczającej ilości miejsca do przechowywania nowych danych, operacja aktualizacji kończy się niepowodzeniem.
