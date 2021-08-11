---
title: Rozdział 10 — Zdarzenia użytkownika klienta
description: Ten rozdział zawiera opis sposobu tworzenia zdarzeń zdefiniowanych przez użytkownika oraz niestandardowych ikon i pól informacji dla takich zdarzeń.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: b287436fb7f61df846bb0c84d910f5c095bc1f8f6635305e97c9e8b7aab64655
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790435"
---
# <a name="chapter-10---customer-user-events"></a>Rozdział 10 — Zdarzenia użytkownika klienta

Ten rozdział zawiera opis sposobu tworzenia zdarzeń zdefiniowanych przez użytkownika oraz niestandardowych ikon i pól informacji dla takich zdarzeń. Ten rozdział zawiera następujące sekcje: 

## <a name="inserting-user-defined-events"></a>Wstawianie User-Defined zdarzeń

ThreadX umożliwia deweloperom rejestrowanie własnych zdarzeń zdefiniowanych przez użytkownika, zapewniając jeszcze więcej przydatnych informacji, które mogą być wyświetlane graficznie przez narzędzie TraceX. Zdefiniowane przez użytkownika numery zdarzeń mogą być różne od

**TX_TRACE_USER_EVENT_START** (4096) do **TX_TRACE_USER_EVENT_END** (65535), włącznie. Umieszczanie zdarzeń w buforze śledzenia odbywa się za pośrednictwem tx_trace_user_event_insert ***zdefiniowanej*** w rozdziale 5. W poniższym przykładzie wywołania wstaw dwa zdarzenia zdefiniowane przez użytkownika do bieżącego buforu śledzenia na obiekt docelowy, to znaczy zdarzenia zdefiniowane przez użytkownika 4096 i zdarzenia 4098:

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>Domyślne wyświetlanie User-Defined zdarzeń

![Ikona zdarzenia zdefiniowanego przez użytkownika](./media/user-guide/tx-events/image0.png)

Domyślnie traceX wyświetla wszystkie zdarzenia użytkownika z domyślną ikoną zdarzenia zdefiniowaną przez użytkownika zgodnie z opisem w rozdziale 6. Rysunek 28 przedstawia domyślną ikonę zdarzenia zdefiniowaną przez użytkownika dla zdarzeń 452 i 453, które zostały umieszczone w buforze zdarzeń za pośrednictwem ***poprzednich tx_trace_user_event_insert*** przykładów.

![Zrzut ekranu przedstawiający domyślne wyświetlanie zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.1.png)
 **RYSUNEK 28**

Dostępne są również szczegółowe informacje dotyczące zdarzeń zdefiniowanych przez użytkownika. Rysunek 28 przedstawia szczegółowe informacje o zdarzeniu 452, które ma numer zdarzenia 4096 i zawiera określone cztery pola informacji.

![Zrzut ekranu przedstawiający szczegółowy ekran zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.2.png)
 **RYSUNEK 29**

## <a name="defining-custom-user-defined-event-icons"></a>Definiowanie niestandardowych User-Defined zdarzeń

TraceX zapewnia również użytkownikowi możliwość tworzenia niestandardowych ikon zdarzeń zdefiniowanych przez użytkownika i niestandardowych etykiet pól informacji. Ta możliwość jest osiągana przez dodanie specyfikacji ikon zdarzeń do pliku konfiguracji ***tracex_custom.trxc_.** Ten plik znajduje się w podkatalogu _ *_CustomEvents_** katalogu instalacyjnego TraceX zdefiniowanego przez użytkownika, który domyślnie ma wartość c:\Azure_RTOS\TraceX. Przykładowa ścieżka katalogu jest pokazana na rysunku 30.

![Zrzut ekranu przedstawiający przykładową ścieżkę katalogu. ](./media/user-guide/custom_events_folder.png)
 **RYSUNEK 30**

Plik ***tracex_custom.trxc*** niestandardowej konfiguracji zdarzeń to prosty plik tekstowy ASCII zawierający zero lub więcej niestandardowych definicji zdarzeń. Format pliku jest następujący:

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

Każdy wiersz między wartościami Start i End służy do definiowania pojedynczego zdarzenia niestandardowego. TraceX udostępnia wersję szablonu tego pliku bez zdefiniowanych zdarzeń niestandardowych (nic między etykietami "Start&quot; i &quot;End"). Format niestandardowej definicji zdarzenia jest następujący:

**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**

gdzie:

- number: definiuje zdefiniowany przez użytkownika numer zdarzenia z zakresów od 4096 do 65535 włącznie.</th>
- name: definiuje nazwę logiczną zdarzenia zdefiniowanego przez użytkownika.</td>
- abbreviation: definiuje dwuliterowy skrót zdarzeń zdefiniowany przez użytkownika.</td>
- top_color: definiuje wartość RGB dla górnej połowy ikony, czyli trzycyfrową liczbę w nawiasie. Niektóre typowe definicje RGB to:
  - BLACK = (0,0,0)       
  - WHITE = (255 255 255)
  - RED = (255,0,0)     
  - GREEN = (0,255,0)     
  - BLUE = (0,0,255)     
  - YELLOW = (255 255,0)   
  - = (0 255 255)   
  - MAGENTA = (255,0,255)   
  Użycie specyfikacji RBG zapewnia użytkownikowi szeroki zakres kolorów dla każdej ikony zdefiniowanej przez użytkownika. Aby uzyskać więcej informacji na temat definicji koloru RBG, zobacz: https://en.wikipedia.org/wiki/RGB#Digital_representations
- botton_color: definiuje wartość RGB dla dolnej połowy ikony, która jest liczbą trzycyfrową w nawiasie.
- label1: etykieta dla ***info_field_1** _, jak określono w wywołaniu _ *_tx_trace_user_event_insert_**.
- label2: etykieta ***info_field_2** _, określona w wywołaniu _ *_tx_trace_user_event_insert_**.
- label3: etykieta ***info_field_3** _, jak określono w wywołaniu _ *_tx_trace_user_event_insert_**.
- label4: etykieta ***info_field_4** _, jak określono w wywołaniu _ *_tx_trace_user_event_insert_**.

Na rysunku 10.4 przedstawiono przykładowe definicje dla każdego z dwóch zdarzeń zdefiniowanych przez użytkownika użytych w tym rozdziale. Pierwsza definicja dotyczy zdarzenia 4096 w wierszu 5 pliku ***tracex_custom.trxc_.** Ta definicja nadaje zdefiniowanej przez użytkownika 4096 nazwie _*First_User_Event**, określa dwuliterowy skrót **fe,** sprawia, że górna część ikony jest czerwona, dolna część ikony jest zielona, a pola informacji są nazwane jako **First_Info1,** **First_Info2,** **First_Info3** i **First_Info4.** Zdarzenie zdefiniowane przez użytkownika 4098 jest zdefiniowane podobnie w wierszu 6 **_tracex_custom.trxc_**.

![Zrzut ekranu przedstawiający przykładowe definicje zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.4.png)
 **RYSUNEK 31**

Ponieważ plik ***tracex_custom.trxc** _ jest odczytywany przez traceX podczas inicjowania, należy zamknąć i ponownie uruchomić plik TraceX, zanim definicje ikon niestandardowych zajdą w życie. Rysunek 32 przedstawia ekran TraceX zdarzeń zdefiniowanych przez użytkownika 452 i 453 z niestandardowymi ikonami zdarzeń zdefiniowanymi w _*_tracex_custom.trxc_**.

![Zrzut ekranu przedstawiający ekran TraceX zdarzeń zdefiniowanych przez użytkownika z ikonami zdarzeń niestandardowych. ](./media/user-guide/10.5.png)
 **RYSUNEK 32**

Dodatkowe informacje w definicji zdarzenia niestandardowego są wyświetlane po wybraniu zdarzenia za pomocą dwukrotnego kliknięcia lub kliknięcia przycisku bieżącego zdarzenia. Rysunek 33 przedstawia wybór dwukrotnego kliknięcia zdarzenia 452. Wszystkie pola nazwy zdarzenia i informacji są zgodne z przykładową definicją, która została dodana ***do tracex_custom.trxc***.

![Zrzut ekranu przedstawiający dwukrotne kliknięcie zdarzenia. ](./media/user-guide/10.6.png)
 **RYSUNEK 33**
