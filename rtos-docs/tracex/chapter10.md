---
title: Rozdział 10 — zdarzenia użytkownika dla klientów
description: Ten rozdział zawiera opis sposobu tworzenia zdarzeń zdefiniowanych przez użytkownika oraz niestandardowych ikon i pól informacji dla takich zdarzeń.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823509"
---
# <a name="chapter-10---customer-user-events"></a>Rozdział 10 — zdarzenia użytkownika dla klientów

Ten rozdział zawiera opis sposobu tworzenia zdarzeń zdefiniowanych przez użytkownika oraz niestandardowych ikon i pól informacji dla takich zdarzeń. Ten rozdział zawiera następujące sekcje: 

## <a name="inserting-user-defined-events"></a>Wstawianie zdarzeń User-Defined

ThreadX zapewnia deweloperom możliwość rejestrowania własnych zdarzeń zdefiniowanych przez użytkownika, co zapewnia jeszcze bardziej przydatne informacje, które mogą być wyświetlane graficznie przez TraceX. Zdefiniowane przez użytkownika numery zdarzeń z zakresu od

**TX_TRACE_USER_EVENT_START** (4096) do **TX_TRACE_USER_EVENT_END** (65535), włącznie. Umieszczanie zdarzeń w buforze śledzenia odbywa się za pośrednictwem ***tx_trace_user_event_insert*** zdefiniowanego w rozdziale 5. Poniższe przykładowe wywołania wstawiają dwa zdarzenia zdefiniowane przez użytkownika do bieżącego buforu śledzenia w miejscu docelowym, czyli zdarzenia zdefiniowanego przez użytkownika 4096 i zdarzenia 4098:

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>Domyślny sposób wyświetlania zdarzeń User-Defined

![Ikona zdarzenia zdefiniowanego przez użytkownika](./media/user-guide/tx-events/image0.png)

Domyślnie TraceX wyświetla wszystkie zdarzenia użytkownika z domyślną ikoną zdarzenia zdefiniowaną przez użytkownika, zgodnie z opisem w rozdziale 6. Rysunek 28 przedstawia domyślną ikonę zdarzenia zdefiniowaną przez użytkownika dla zdarzeń 452 i 453, które zostały umieszczone w buforze zdarzeń za pośrednictwem poprzednich przykładów ***tx_trace_user_event_insert*** .

![Zrzut ekranu przedstawiający domyślny sposób wyświetlania zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.1.png)
 **Rysunek 28**

Szczegółowe informacje są również dostępne dla zdarzeń zdefiniowanych przez użytkownika. Rysunek 28 przedstawia szczegółowe informacje o zdarzeniu dla zdarzenia 452, które ma numer zdarzenia 4096 i zawiera określone cztery pola informacji.

![Zrzut ekranu przedstawiający szczegółowy sposób wyświetlania zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.2.png)
 **Rysunek 29**

## <a name="defining-custom-user-defined-event-icons"></a>Definiowanie niestandardowych ikon zdarzeń User-Defined

TraceX udostępnia także użytkownikowi możliwość tworzenia niestandardowych ikon zdarzeń zdefiniowanych przez użytkownika i etykiet pól informacji niestandardowych. Tę możliwość uzyskuje się przez dodanie specyfikacji ikon zdarzeń do pliku konfiguracji ***tracex_custom. trxc** _. Ten plik znajduje się w podkatalogu _ *_CustomEvents_** katalogu instalacyjnego TraceX, który domyślnie jest C:\ Azure_RTOS \tracex. Przykład ścieżki do katalogu pokazano na rysunku 30.

![Zrzut ekranu przedstawiający przykład ścieżki katalogu. ](./media/user-guide/custom_events_folder.png)
 **Rysunek 30**

Plik konfiguracji niestandardowego zdarzenia ***tracex_custom. trxc*** to prosty plik tekstowy ASCII zawierający zero lub więcej niestandardowych definicji zdarzeń. Format pliku jest następujący:

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

Każdy wiersz między początkiem i końcem jest używany do definiowania pojedynczego zdarzenia niestandardowego. TraceX udostępnia wersję szablonu tego pliku bez zdefiniowanych zdarzeń niestandardowych (nie dotyczy etykiet "Start" i "End"). Format niestandardowej definicji zdarzenia jest następujący:

**Number, Name, skrót, top_color, bottom_color, Label1, etykiety 2, etykiety 2, Label4**

gdzie:

- Liczba: definiuje zdefiniowany przez użytkownika numer zdarzenia z zakresu od 4096 do 65535 włącznie.</th>
- Nazwa: Określa nazwę logiczną dla zdarzenia zdefiniowanego przez użytkownika.</td>
- skrót: definiuje dwuliterowy skrót zdarzenia zdefiniowany przez użytkownika.</td>
- top_color: definiuje wartość RGB dla górnej połowy ikony, która jest cyfrą w nawiasie. Niektóre typowe definicje RGB są
  - CZARNY = (0, 0, 0)       
  - BIAŁY = (255 255 255)
  - CZERWONY = (255, 0, 0)     
  - ZIELONY = (0255, 0)     
  - NIEBIESKI = (0, 0255)     
  - ŻÓŁTY = (255255, 0)   
  - BŁĘKITNY = (0255 255)   
  - AMARANTOWY = (255, 0255)   
  Użycie specyfikacji RBG umożliwia użytkownikowi szeroki zakres kolorów dla każdej ikony zdefiniowanej przez użytkownika. Aby uzyskać więcej informacji na temat definicji koloru RBG, zobacz: https://en.wikipedia.org/wiki/RGB#Digital_representations
- botton_color: definiuje wartość RGB dla dolnej połowy ikony, która jest liczbą składającą się z trzech cyfr w nawiasach.
- Label1: etykieta dla ***info_field_1** _, jak określono w wywołaniu _ *_tx_trace_user_event_insert_**.
- etykiety 2: etykieta dla ***info_field_2** _, jak określono w wywołaniu _ *_tx_trace_user_event_insert_**.
- etykiety 3: etykieta dla ***info_field_3** _, jak określono w wywołaniu _ *_tx_trace_user_event_insert_**.
- Label4: etykieta dla ***info_field_4** _, jak określono w wywołaniu _ *_tx_trace_user_event_insert_**.

Przykładowe definicje dla każdego z dwóch zdarzeń zdefiniowanych przez użytkownika użytych w tym rozdziale przedstawiono na rysunku 10,4. Pierwsza definicja dotyczy zdarzenia 4096 w wierszu 5 pliku ***tracex_custom. trxc** _. Ta definicja zawiera zdarzenie zdefiniowane przez użytkownika 4096 o nazwie _ * First_User_Event * *, określa dwuliterowy skrót **Fe**, powoduje, że górna część ikony czerwona, Dolna część ikony zielony i nazwy pól informacji jako **First_Info1**, **First_Info2**, **First_Info3** i **First_Info4**. Zdefiniowane przez użytkownika zdarzenie 4098 jest zdefiniowane w podobny sposób w wierszu 6 **_tracex_custom. trxc_**.

![Zrzut ekranu przedstawiający przykładowe definicje zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.4.png)
 **Rysunek 31**

Ponieważ plik ***tracex_custom. trxc** _ jest odczytywany przez tracex podczas inicjowania, tracex musi zostać zakończony i uruchomiony ponownie, zanim definicje ikon niestandardowych zaczną obowiązywać. Rysunek 32 przedstawia TraceX wyświetlania zdarzeń zdefiniowanych przez użytkownika 452 i 453 z niestandardowymi ikonami zdarzeń zdefiniowanymi w _ *_tracex_custom. trxc_* *.

![Zrzut ekranu przedstawiający wyświetlanie TraceX zdarzeń zdefiniowanych przez użytkownika z ikonami zdarzeń niestandardowych. ](./media/user-guide/10.5.png)
 **Rysunek 32**

Dodatkowe informacje w definicji zdarzenia niestandardowego są wyświetlane, gdy zdarzenie jest wybierane przy użyciu dwukrotnego kliknięcia, wskaźnika myszy lub kliknięcia przycisku bieżące zdarzenie. Rysunek 33 pokazuje zaznaczenie podwójnego kliknięcia dla zdarzenia 452. Pola Nazwa zdarzenia i informacje są zgodne z definicją przykładową, która została dodana do ***tracex_custom. trxc***.

![Zrzut ekranu przedstawiający zaznaczenie podwójnego kliknięcia na zdarzeniu. ](./media/user-guide/10.6.png)
 **Rysunek 33**
