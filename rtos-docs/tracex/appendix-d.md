---
title: Dodatek D — zrzucanie i bufor śledzenia
description: Zatopienie buforu śledzenia utworzonego przez usługę Azure RTO ThreadX do pliku na komputerze hosta odbywa się za pośrednictwem poleceń i/lub narzędzi dostarczonych przez określone narzędzie deweloperskie.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823628"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>Dodatek D — zrzucanie i bufor śledzenia

Zatopienie buforu śledzenia utworzonego przez usługę Azure RTO ThreadX do pliku na komputerze hosta odbywa się za pośrednictwem poleceń i/lub narzędzi dostarczonych przez określone narzędzie deweloperskie. Ten dodatek zawiera przykłady zatopienia buforu śledzenia do pliku hosta w niektórych najpopularniejszych narzędziach programistycznych używanych z programem ThreadX. 

## <a name="benchx-tools"></a>Narzędzia BenchX

Bufor śledzenia może być w łatwy sposób zrzucany do pliku hosta za pomocą narzędzi BenchX, wybierając przycisk ***przechowuj pamięć do pliku** _ w _widokach pamięci_* *, jak pokazano poniżej:

![Zrzut ekranu przedstawiający widok pamięci w narzędziach BenchX.](./media/user-guide/image642.jpg)

W tym momencie Określ adres bufora śledzenia, rozmiar, nazwę pliku docelowego (w tym ścieżkę), a następnie wybierz przycisk ***Zapisz*** , jak pokazano poniżej. Spowoduje to utworzenie binarnego pliku śledzenia do wyświetlania w TraceX.

![Zrzut ekranu przedstawiający okno dialogowe BenchX narzędzi do zapisywania.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>Narzędzia RealView

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi ARM RealView, wprowadzając następujące polecenie w wierszu polecenia w RealView:

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

Po zakończeniu plik ***trace_file. TRX*** będzie zawierać bufor śledzenia, który znajduje się na początku adresu 0x6860 i trafia do 0xE560. Ten plik jest gotowy do wyświetlania przez TraceX.

## <a name="iar-tools"></a>Narzędzia IAR

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi IAR, klikając prawym przyciskiem myszy w widoku pamięć i wybierając pozycję ***Zapisz pamięć...*** , jak pokazano poniżej.

![Zrzut ekranu opcji zapisywania pamięci w narzędziach IAR.](./media/user-guide/image0_311.jpg)

Spowoduje to wyświetlenie okna dialogowego ***Zapisz pamięć** _. Wprowadź adres początkowy i końcowy oraz nazwę pliku śledzenia, a następnie wybierz przycisk _*_Zapisz_*_ . W przykładzie pokazanym poniżej narzędzia IAR zapisują określony bufor śledzenia w rekordach SZESNASTKOWych Intel w pliku _ *_trace_file. hex_* *.

![Zrzut ekranu przedstawiający okno dialogowe zapisywania pamięci narzędzi IAR.](./media/user-guide/image648.jpg)

W tym momencie mamy bufor śledzenia zapisany w pliku ***trace_file. hex*** na hoście i jest gotowy do wyświetlania z TraceX.

## <a name="codewarrior-tools"></a>Narzędzia CodeWarrior

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi CodeWarrior, wprowadzając polecenie ***Save** _ w oknie poleceń. Poniższy przykład: _ *_Save_** polecenie zakłada, że bufor śledzenia zaczyna się od 0x102200 i kończą się o 0x109F00:

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

Powoduje to, że bufor śledzenia jest zapisywany w pliku ***trace_file. TRX*** na hoście.

## <a name="mplab-tools"></a>Narzędzia MPLAB

MPLAB może utworzyć plik śledzenia zgodny z TraceX za pomocą narzędzia do eksportowania tabeli, co umożliwia eksportowanie dowolnego zakresu pamięci do pliku hosta. Aby użyć tego narzędzia do tworzenia pliku śledzenia dla TraceX, wykonaj następujące czynności:

**Krok 1** Otwórz okno pamięci, wybierając polecenie Wyświetl > pamięć.

![Zrzut ekranu przedstawiający pamięć wybraną w menu Widok.](./media/user-guide/image0_316.jpg)

**Krok 2** Kliknij prawym przyciskiem myszy w **widoku pamięci** , aby wyświetlić listę opcji. Określ **Format wyświetlania — 1 bajt** , aby wybrać wyświetlanie bajtów.

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją format wyświetlania.](./media/user-guide/image650.png)

![Zrzut ekranu przedstawiający okno dialogowe Przejdź do.](./media/user-guide/image651.jpg)

**Krok 3** Kliknij ponownie prawym przyciskiem myszy w oknie **Widok pamięci** i wybierz pozycję **Przejdź do**, co spowoduje otwarcie okna dialogowego, w którym można określić adres buforu zdarzeń. Ten przykład pokazuje **_event_buffer_** wyświetlany.

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją przejdź do.](./media/user-guide/image0_312.jpg)

![Zrzut ekranu przedstawiający przykład pokazujący wyświetlaną event_buffer.](./media/user-guide/image653.png)

**Krok 4** Podświetla zawartość pierwszej lokalizacji buforu śledzenia, która jest zawsze ciągiem BTXT....

![Zrzut ekranu przedstawiający pierwszą lokalizację buforu śledzenia.](./media/user-guide/image0_313.jpg)

**Krok 5** Teraz ponownie kliknij prawym przyciskiem myszy, aby wyświetlić menu Opcje, a następnie wybierz pozycję **Eksportuj tabelę**.

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją Eksportuj tabelę.](./media/user-guide/image0_314.jpg)

**Krok 6** Spowoduje to wyświetlenie okna dialogowego **Eksportowanie tabeli** , jak pokazano. Określ zakres adresów do wyeksportowania. W przypadku bufora śledzenia 8K, podobnie jak w tym przykładzie, określ zakres 0xA00006AC do 0xA00026AC, a następnie wprowadź nazwę pliku hosta, który ma zostać utworzony (demo_threadx. TRX w tym przykładzie).

! [[Zrzut ekranu przedstawiający okno dialogowe Eksport jako.](./media/user-guide/image656.jpg)

**Krok 7** Na hoście zostanie utworzony plik o nazwie **demo_threadx. TRX** , a ten plik może być otwarty przez TraceX.

## <a name="ghs-tools"></a>Narzędzia GHS

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi GHS, wprowadzając następujące polecenie w wierszu polecenia w oknie polecenia debugowania:

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

Po zakończeniu plik **demo_threadx. TRX** będzie zawierać bufor śledzenia, który znajduje się w event_buffer o rozmiarze 32 768 bajtów i będzie gotowy do wyświetlania przez TraceX.

## <a name="renesas-hew"></a>Renesas HEW

Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi Renasas HEW, wykonując następujące trzy kroki (i podkroki) poniżej:

**Krok 1** Otwórz okno pamięci.

! [[Zrzut ekranu przedstawiający okno pamięci.](./media/user-guide/image657.jpg)

**Krok 2** Umieść kursor w oknie pamięci i kliknij prawym przyciskiem myszy.

![Zrzut ekranu okna pamięci z wybraną opcją Zapisz.](./media/user-guide/image0_315.jpg)

**Krok 3** Wybierz pozycję Zapisz, a następnie w oknie Zapisz pamięć jako wykonaj następujące czynności:

- Wybierz format pliku: dane binarne.
- Określ nazwę pliku: zgodnie z potrzebami
- Określ adres początkowy: trace_buffer
- Określ adres końcowy: (trace_buffer + rozmiar)
- Określ rozmiar dostępu: 1
- Klikanie pozycji Zapisz.

![Zrzut ekranu przedstawiający okno dialogowe Zapisywanie pamięci jako.](./media/user-guide/image659.jpg)