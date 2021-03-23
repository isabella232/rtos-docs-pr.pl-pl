---
title: Rozdział 6 — moduł odporny na błędy usługi Azure RTO FileX
description: Ten rozdział zawiera opis modułu odpornego na błędy usługi Azure RTO FileX, który został zaprojektowany z myślą o utrzymaniu integralności systemu plików, jeśli nośnik utraci energię lub zostanie wysunięty w trakcie operacji zapisu pliku.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 68a24f0345a2c4d3e824270699b00a2daab32f8e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822410"
---
# <a name="chapter-6---azure-rtos-filex-fault-tolerant-module"></a>Rozdział 6 — moduł odporny na błędy usługi Azure RTO FileX

Ten rozdział zawiera opis modułu odpornego na błędy usługi Azure RTO FileX, który został zaprojektowany z myślą o utrzymaniu integralności systemu plików, jeśli nośnik utraci energię lub zostanie wysunięty w trakcie operacji zapisu pliku.

## <a name="filex-fault-tolerant-module-overview"></a>Przegląd modułu odpornego na błędy FileX

Gdy aplikacja zapisuje dane do pliku, FileX aktualizuje zarówno klastry danych, jak i informacje o systemie. Te aktualizacje należy wykonać jako niepodzielną operację, aby zachować spójność informacji w systemie plików. Na przykład podczas dołączania danych do pliku FileX musi znaleźć dostępny klaster na nośniku, zaktualizować łańcuch systemu plików FAT, zaktualizować długość wpisu w katalogu i ewentualnie zaktualizować początkowy numer klastra w pozycji katalog. Awaria lub wysuwanie nośnika może przerwać sekwencję aktualizacji, co spowoduje pozostawienie systemu plików w stanie niespójnym. Jeśli niespójny stan nie zostanie poprawiony, aktualizowane dane mogą zostać utracone i z powodu uszkodzenia informacji o systemie kolejna operacja systemu plików może uszkodzić inne pliki lub katalogi na nośniku.

Moduł odporny na uszkodzenia FileX działa zgodnie z instrukcjami rejestrowania wymaganymi do zaktualizowania pliku *przed* zastosowaniem tych kroków do systemu plików. Jeśli aktualizacja pliku zakończyła się pomyślnie, te wpisy dziennika zostaną usunięte. Jeśli jednak Aktualizacja pliku zostanie przerwana, wpisy dziennika są przechowywane na nośniku. Podczas następnego montowania nośnika FileX wykrywa te wpisy dziennika z poprzedniej (nieukończonej) operacji zapisu. W takich przypadkach FileX może odzyskać sprawność po awarii przez wycofanie zmian już wprowadzonych w systemie plików lub przez ponowne zastosowanie wymaganych zmian w celu ukończenia poprzedniej operacji. W ten sposób moduł odporny na uszkodzenia FileX zachowuje integralność systemu plików, jeśli nośnik utraci moc podczas operacji aktualizacji.

> [!IMPORTANT]
> *Moduł odporny na uszkodzenia FileX nie został zaprojektowany, aby zapobiec uszkodzeniu systemu plików spowodowanym uszkodzeniem nośnika fizycznego z prawidłowymi danymi.*

> [!IMPORTANT]
> *Gdy moduł odporny na uszkodzenia FileX chroni nośnik, nośnik nie może być instalowany przez coś innego niż FileX z włączonym odpornością na uszkodzenia. Wykonanie tej operacji może spowodować niespójność wpisów dziennika w systemie plików z informacjami o systemie na nośniku. Jeśli moduł odporny na uszkodzenia FileX próbuje przetworzyć wpisy dziennika po zaktualizowaniu nośnika przez inny system plików, procedura odzyskiwania może zakończyć się niepowodzeniem, pozostawiając cały system plików w stanie nieprzewidywalnym.*

## <a name="use-of-the-fault-tolerant-module"></a>Korzystanie z modułu odpornego na uszkodzenia

Funkcja odporna na uszkodzenia FileX jest dostępna dla wszystkich systemów plików FAT obsługiwanych przez FileX, w tym FAT12, FAT16, FAT32 i exFAT. Aby włączyć funkcję odporną na uszkodzenia, FileX musi być skompilowana przy użyciu zdefiniowanego symbolu **FX_ENABLE_FAULT_TOLERANT** . W czasie wykonywania aplikacja uruchamia usługę odporną na uszkodzenia, wywołując **_fx_fault_tolerant_enable_*_ bezpośrednio po wywołaniu _*_fx_media_open_**. Po włączeniu odporności na uszkodzenia wszystkie operacje zapisu plików na wydzielonym nośniku są chronione. Domyślnie moduł odporny na uszkodzenia nie jest włączony.

> [!IMPORTANT]
> * Aplikacja musi upewnić się, że nie można uzyskać dostępu do systemu plików przed ***fx_fault_tolerant_enable** _. Jeśli aplikacja zapisuje dane w systemie plików przed włączeniem odporności na uszkodzenia, operacja zapisu może uszkodzić nośnik, jeśli wcześniejsze operacje zapisu nie zostały ukończone i system plików nie został przywrócony przy użyciu dziennika odpornego na błędy entries._

## <a name="filex-fault-tolerant-module-log"></a>Dziennik modułu odporny na błędy FileX

Dziennik odporny na błędy FileX w programie Flash zajmuje jeden klaster logiczny. Indeks początkowego numeru klastra tego klastra jest rejestrowany w sektorze rozruchowym nośnika, z przesunięciem określonym przez symbol **FX_FAULT_TOLERANT_BOOT_INDEX**. Domyślnie ten symbol jest zdefiniowany jako 116. Ta lokalizacja jest wybierana, ponieważ jest oznaczona jako zastrzeżona w specyfikacji FAT12/16/32 i exFAT.

Rysunek 5 "układ struktury dziennika" pokazuje ogólny układ struktury dziennika. Struktura dziennika zawiera trzy sekcje: nagłówek dziennika, łańcuch tłuszczu i wpisy dziennika.

> [!IMPORTANT]
> *Wszystkie wartości wielobajtowe przechowywane w wpisach dziennika są w formacie little-endian.*

![Układ struktury dziennika](./media/user-guide/log-structure-layout.png)

**Rysunek 5. Układ struktury dziennika**

Obszar nagłówka dziennika zawiera informacje opisujące całą strukturę dziennika i szczegółowo objaśnia każde pole.

**TABELA 8. Obszar nagłówka dziennika**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
|ID (Identyfikator)|4|Identyfikuje strukturę dziennika odpornego na błędy FileX. Struktura dziennika jest uważana za nieprawidłową, jeśli wartość identyfikatora nie jest 0x46544C52.|
|Łączny rozmiar|2|Wskazuje łączny rozmiar (w bajtach) całej struktury dziennika.|
|Suma kontrolna nagłówka|2|Suma kontrolna, która konwertuje obszar nagłówka dziennika. Struktura dziennika jest uważana za nieprawidłową, jeśli pola nagłówka nie powiodą się weryfikacja sumy kontrolnej.|
|Numer wersji|2|FileX odporne na uszkodzenia i wersje główne i pomocnicze.|
|Zarezerwowany|2|Do przyszłego rozwinięcia.|

Po zakończeniu obszaru nagłówka dziennika następuje obszar dziennika łańcucha FAT. Rysunek 9 zawiera informacje opisujące sposób modyfikacji łańcucha FAT. Ten obszar dziennika zawiera informacje dotyczące klastrów przypisywanych do pliku, klastrów usuwanych z pliku oraz miejsca, w których należy wstawić/usunąć, i opis poszczególnych pól w obszarze dziennika łańcucha FAT.

**TABELA 9. Obszar dziennika łańcucha FAT**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
|Suma kontrolna dziennika łańcucha FAT|2|Suma kontrolna całego obszaru dziennika łańcucha FAT. Obszar dziennika łańcucha FAT jest uznawany za nieprawidłowy, jeśli nie powiedzie się weryfikacja sumy kontrolnej.|
|Flaga|1|Prawidłowe wartości flag to:<br/>Prawidłowy łańcuch systemu plików FAT 0x01<br />0x02 Mapa bitowa jest używana|
|Zarezerwowany|1|Zarezerwowane do użytku w przyszłości|
|Punkt wstawiania — przód|4|Klaster (należący do oryginalnego łańcucha FAT), w którym ma zostać dołączony nowo utworzony łańcuch.|
|Klaster główny nowego łańcucha FAT|4|Pierwszy klaster nowo utworzonego łańcucha FAT|
|Główny klaster oryginalnego łańcucha FAT|4|Pierwszy klaster części oryginalnego łańcucha FAT, który ma zostać usunięty.|
|Punkt wstawiania — wstecz|4|Oryginalny klaster, w którym jest przyłączany nowo utworzony łańcuch systemu plików FAT.|
|Następny punkt usuwania|4|To pole ułatwia procedurę oczyszczania łańcucha FAT.|

Obszar wpisy dziennika zawiera wpisy dziennika opisujące zmiany, które są konieczne do odzyskania po awarii. W module odporny na błędy FileX są obsługiwane trzy typy wpisów dziennika: wpis dziennika FAT; Wpis dziennika katalogu; i wpis dziennika mapy bitowej.

Poniższe trzy ilustracje i trzy tabele opisują te wpisy dziennika szczegółowo.

![Wpis dziennika FAT](./media/user-guide/fat-log-entry.png)

**Rysunek 6. Wpis dziennika FAT**

**TABELA 10. Wpis dziennika FAT**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
Typ|2|Typ wpisu musi być FX_FAULT_TOLERANT_FAT_LOG_TYPE|
|Rozmiar|2|Rozmiar tego wpisu|
|Numer klastra|4|Numer klastra|
|Wartość|4|Wartość, która ma być zapisywana we wpisie systemu FAT|

![Wpis dziennika katalogu](./media/user-guide/directory-log-entry.png)

**Rysunek 7. Wpis dziennika katalogu**

**TABELA 11. Wpis dziennika katalogu**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
|Typ|2|Typ wpisu musi być FX_FAULT_TOLERANT_DIRECTORY_LOG_TYPE|
|Rozmiar|2|Rozmiar tego wpisu|
|Przesunięcie sektora|4|Przesunięcie (w bajtach) do sektora, w którym znajduje się ten katalog.|
|Sektor dziennika|4|Sektor, w którym znajduje się wpis katalogu|
|Dane dziennika|Zmienna|Zawartość wpisu katalogu|

![Wpis dziennika mapy bitowej](./media/user-guide/bitmap-log-entry.png)

**Rysunek 8. Wpis dziennika mapy bitowej**

**TABELA 12. Wpis dziennika mapy bitowej**

|Pole|Rozmiar (w bajtach)|Opis|
|-----|--------------|-----------|
|Typ|2|Typ wpisu musi być FX_FAULT_TOLERANT_BITMAP_LOG_TYPE|
|Rozmiar|2|Rozmiar tego wpisu|
|Numer klastra|4|Numer klastra|
|Wartość|4|Wartość, która ma być zapisywana we wpisie systemu FAT|

## <a name="fault-tolerant-protection"></a>Ochrona odporna na uszkodzenia

Po uruchomieniu modułu odpornego na błędy FileX najpierw szuka istniejącego pliku dziennika odpornego na błędy na nośniku. Jeśli nie można znaleźć prawidłowego pliku dziennika, FileX traktuje nośnik bez ochrony. W takim przypadku FileX utworzy plik dziennika odporny na uszkodzenia na nośniku.

> [!IMPORTANT]
> * FileX nie jest w stanie chronić systemu plików, jeśli został uszkodzony przed uruchomieniem modułu odpornego na błędy FileX. *

Jeśli zlokalizowany jest plik dziennika odporny na błędy, FileX sprawdza obecność istniejących wpisów dziennika. Plik dziennika bez wpisu dziennika wskazuje, że wcześniejsza operacja pliku zakończyła się pomyślnie, a wszystkie wpisy dziennika zostały usunięte. W takim przypadku aplikacja może zacząć korzystać z systemu plików z ochroną odporną na błędy.

Jeśli jednak znajdują się wpisy dziennika, FileX musi wykonać poprzednią operację pliku lub przywrócić zmiany, które zostały już zastosowane do systemu plików, skutecznie cofnąć zmiany. W obu przypadkach po zastosowaniu wpisów dziennika do systemu plików system plików jest przywracany w spójny stan, a aplikacja może ponownie rozpocząć korzystanie z systemu plików.

W przypadku multimediów chronionych przez FileX podczas operacji aktualizowania pliku część danych jest zapisywana bezpośrednio na nośniku. Ponieważ FileX zapisuje dane, rejestruje także wszelkie zmiany, które trzeba zastosować do wpisów w katalogu, tabeli FAT. Te informacje są rejestrowane w dziennikach odpornych na pliki. To podejście gwarantuje, że aktualizacje systemu plików są wykonywane po zapisaniu danych na nośniku. Jeśli nośnik zostanie wysunięty w fazie zapisu danych, podstawowe informacje o systemie plików nie zostały jeszcze zmienione. W związku z tym system plików nie ma wpływ na przerwy.

Po pomyślnym zapisaniu wszystkich danych na nośniku FileX następnie postępuj zgodnie z informacjami w wpisach dziennika, aby zastosować zmiany do informacji o systemie, po jednym wpisie. Po zatwierdzeniu wszystkich informacji o systemie na nośniku wpisy dziennika są usuwane z dziennika odpornego na błędy. W tym momencie FileX wykonuje operację aktualizacji pliku.

Podczas operacji aktualizowania pliku pliki nie są aktualizowane na miejscu. Moduł odporny na uszkodzenia przydziela sektora danych, aby zapisać nowe dane w, a następnie usunąć sektor zawierający dane przeznaczone do zastąpienia, aktualizując powiązane wpisy systemu FAT w celu połączenia nowego sektora z Chian. W sytuacjach, w których należy zmodyfikować częściowe dane w klastrze, FileX zawsze przydziela nowe klastry, zapisuje wszystkie dane ze starych klastrów ze zaktualizowanymi danymi w nowych klastrach, a następnie zwalnia stare klastry. Gwarantuje to, że jeśli aktualizacja pliku zostanie przerwana, oryginalny plik jest nienaruszony. Aplikacja musi mieć świadomość, że w obszarze Ochrona odporna na uszkodzenia FileX aktualizacja danych w pliku wymaga, aby nośnik miał wystarczającą ilość wolnego miejsca do przechowywania nowych danych przed udostępnieniem sektorów ze starymi danymi. Jeśli nośnik nie ma wystarczającej ilości miejsca do przechowywania nowych danych, operacja aktualizacji zakończy się niepowodzeniem.
