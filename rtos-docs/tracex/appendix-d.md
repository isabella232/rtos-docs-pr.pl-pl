---
title: Dodatek D — Bufor zrzucania i śledzenia
description: Zrzucanie buforu śledzenia utworzonego przez Azure RTOS ThreadX do pliku na komputerze-hoście odbywa się za pomocą poleceń i/lub narzędzi dostarczonych przez używane narzędzie programowe.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: afbbabbd04ac4c33a747bb0cce4a9f36ca2d197a819cb48d834429e29fe5572c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802399"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>Dodatek D — Bufor zrzucania i śledzenia

Zrzucanie buforu śledzenia utworzonego przez Azure RTOS ThreadX do pliku na komputerze-hoście odbywa się za pomocą poleceń i/lub narzędzi dostarczonych przez używane narzędzie programowe. Ten dodatek zawiera przykłady zrzucania buforu śledzenia do pliku hosta w niektórych z bardziej popularnych narzędzi deweloperskie używane z ThreadX. 

## <a name="benchx-tools"></a>Narzędzia BenchX

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi BenchX, wybierając przycisk ***** Zapisz pamięć do pliku _ w widoku pamięci __*,_ jak pokazano poniżej:

![Zrzut ekranu przedstawiający widok pamięci w narzędziach BenchX.](./media/user-guide/image642.jpg)

Na tym etapie określ adres buforu śledzenia, rozmiar, nazwę  pliku docelowego (w tym ścieżkę) i wybierz przycisk Zapisz, jak pokazano poniżej. Spowoduje to utworzenie binarnego pliku śledzenia do wyświetlania w obrębie traceX.

![Zrzut ekranu przedstawiający okno dialogowe zapisywania narzędzi BenchX.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>Narzędzia RealView

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi ARM RealView, wprowadzając następujące polecenie w wierszu polecenia w widoku RealView:

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

Po zakończeniu plik ***trace_file.trx*** będzie zawierać bufor śledzenia, który znajduje się od adresu 0x6860 i przechodzi do adresu 0xE560. Ten plik jest gotowy do wyświetlania przez traceX.

## <a name="iar-tools"></a>Narzędzia IAR

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi IAR, klikając prawym przyciskiem myszy w widoku pamięci i wybierając polecenie ***Zapisz pamięć...*** , jak pokazano poniżej.

![Zrzut ekranu przedstawiający opcję Zapisz pamięć w narzędziach IAR.](./media/user-guide/image0_311.jpg)

W wyniku tego zostanie wyświetlone okno dialogowe ***Zapisz** pamięć _. Wprowadź początkowy i końcowy adres oraz nazwę pliku śledzenia, a następnie wybierz _*_przycisk_*_ Zapisz. W poniższym przykładzie narzędzia IAR zapisują określony bufor śledzenia w rekordach Intel HEX w pliku _*_trace_file.hex_**.

![Zrzut ekranu przedstawiający okno dialogowe Zapisywanie pamięci w narzędziach IAR.](./media/user-guide/image648.jpg)

W tym momencie mamy bufor śledzenia zapisany w pliku ***trace_file.hex*** na hoście i jest gotowy do wyświetlania za pomocą traceX.

## <a name="codewarrior-tools"></a>CodeWarrior Tools

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi CodeWarrior, wprowadzając polecenie ***save** _ w oknie polecenia. W poniższym przykładzie _ *_zapisz_** polecenie zakłada, że bufor śledzenia rozpoczyna się od 0x102200 i kończy się na 0x109F00:

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

Powoduje to zapisanie buforu śledzenia w pliku ***trace_file.trx*** na hoście.

## <a name="mplab-tools"></a>Narzędzia MPLAB

Narzędzie MPLAB może utworzyć plik śledzenia zgodny z traceX za pomocą narzędzia eksportu tabeli, które umożliwia eksportowanie dowolnego zakresu pamięci do pliku hosta. Aby użyć tego narzędzia do utworzenia pliku śledzenia dla traceX, postępuj w następujący sposób:

**Krok 1** Otwórz okno pamięci, wybierając pozycję View -> Memory (Wyświetl > pamięci).

![Zrzut ekranu przedstawiający wybraną pozycję Pamięć w menu Widok.](./media/user-guide/image0_316.jpg)

**Krok 2** Kliknij prawym przyciskiem myszy w **widoku pamięci,** aby wyświetlić listę opcji. Określ **format wyświetlania -1 Bajt,** aby wybrać wyświetlanie bajtów.

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją Format wyświetlania.](./media/user-guide/image650.png)

![Zrzut ekranu przedstawiający okno dialogowe Przejdź do.](./media/user-guide/image651.jpg)

**Krok 3** Kliknij ponownie prawym przyciskiem myszy w oknie Widok pamięci **i** wybierz pozycję **Przejdź** do , co spowoduje otwarcie okna dialogowego, które umożliwia określenie adresu buforu zdarzeń. W tym **_przykładzie event_buffer_** wyświetlane.

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją Przejdź do.](./media/user-guide/image0_312.jpg)

![Zrzut ekranu przedstawiający przykład pokazujący event_buffer wyświetlane.](./media/user-guide/image653.png)

**Krok 4** To wyróżnia zawartość pierwszej lokalizacji buforu śledzenia, która jest zawsze ciągiem BTXT....

![Zrzut ekranu przedstawiający pierwszą lokalizację buforu śledzenia.](./media/user-guide/image0_313.jpg)

**Krok 5** Teraz kliknij ponownie prawym przyciskiem myszy, aby wyprowadzić menu opcji, a następnie wybierz pozycję **Eksportuj tabelę**.

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją Eksportuj tabelę.](./media/user-guide/image0_314.jpg)

**Krok 6** Zostanie wyświetlone okno dialogowe **Eksportowanie tabeli,** jak pokazano. Określ zakres adresów do wyeksportowania. W przypadku bufora śledzenia 8K, jak w tym przykładzie, określ zakres 0xA00006AC do 0xA00026AC i wprowadź nazwę pliku hosta, który ma zostać utworzony (w tym przykładzie demo_threadx.trx).

! [[Zrzut ekranu przedstawiający okno dialogowe Eksportowanie jako.](./media/user-guide/image656.jpg)

**Krok 7** Plik o **nazwie demo_threadx.trx** zostanie utworzony na hoście i plik ten może zostać otwarty przez traceX.

## <a name="ghs-tools"></a>GHS Tools

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi GHS, wprowadzając następujące polecenie w wierszu polecenia w oknie polecenia debugowania:

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

Po zakończeniu plik **demo_threadx.trx** będzie zawierać bufor śledzenia, który znajduje się w event_buffer o rozmiarze 32 768 bajtów i jest gotowy do wyświetlania przez traceX.

## <a name="renesas-hew"></a>Renesas HEW

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi HEW firmy Renasas, korzystając z poniższych trzech kroków (i kroków poniżej):

**Krok 1** Otwórz okno Pamięć.

! [[Zrzut ekranu przedstawiający okno pamięci.](./media/user-guide/image657.jpg)

**Krok 2** Umieść kursor w oknie pamięci i kliknij prawym przyciskiem myszy.

![Zrzut ekranu przedstawiający okno Pamięci z wybraną opcją Zapisz.](./media/user-guide/image0_315.jpg)

**Krok 3** Wybierz pozycję Zapisz, a następnie w oknie Zapisywanie pamięci jako wykonaj następujące czynności:

- Wybierz pozycję Format pliku: Binarny.
- Określ nazwę pliku: zgodnie z potrzebami
- Określ adres startowy: trace_buffer
- Określ końcowy adres: (trace_buffer+rozmiar)
- Określ rozmiar dostępu: 1
- Klikanie pozycji Zapisz.

![Zrzut ekranu przedstawiający okno dialogowe Zapisywanie pamięci jako.](./media/user-guide/image659.jpg)