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
# <a name="chapter-10---customer-user-events"></a><span data-ttu-id="5b534-103">Rozdział 10 — zdarzenia użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="5b534-103">Chapter 10 - Customer user events</span></span>

<span data-ttu-id="5b534-104">Ten rozdział zawiera opis sposobu tworzenia zdarzeń zdefiniowanych przez użytkownika oraz niestandardowych ikon i pól informacji dla takich zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5b534-104">This chapter contains a description of how to create user-defined events and custom icons and information fields for such events.</span></span> <span data-ttu-id="5b534-105">Ten rozdział zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="5b534-105">This chapter includes the following sections:</span></span> 

## <a name="inserting-user-defined-events"></a><span data-ttu-id="5b534-106">Wstawianie zdarzeń User-Defined</span><span class="sxs-lookup"><span data-stu-id="5b534-106">Inserting User-Defined Events</span></span>

<span data-ttu-id="5b534-107">ThreadX zapewnia deweloperom możliwość rejestrowania własnych zdarzeń zdefiniowanych przez użytkownika, co zapewnia jeszcze bardziej przydatne informacje, które mogą być wyświetlane graficznie przez TraceX.</span><span class="sxs-lookup"><span data-stu-id="5b534-107">ThreadX provides the ability for developers to log their own user-defined events, providing even more useful information that can be viewed graphically by TraceX.</span></span> <span data-ttu-id="5b534-108">Zdefiniowane przez użytkownika numery zdarzeń z zakresu od</span><span class="sxs-lookup"><span data-stu-id="5b534-108">User-defined event numbers range from</span></span>

<span data-ttu-id="5b534-109">**TX_TRACE_USER_EVENT_START** (4096) do **TX_TRACE_USER_EVENT_END** (65535), włącznie.</span><span class="sxs-lookup"><span data-stu-id="5b534-109">**TX_TRACE_USER_EVENT_START** (4096) through **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span></span> <span data-ttu-id="5b534-110">Umieszczanie zdarzeń w buforze śledzenia odbywa się za pośrednictwem ***tx_trace_user_event_insert*** zdefiniowanego w rozdziale 5.</span><span class="sxs-lookup"><span data-stu-id="5b534-110">The placement of the events in the trace buffer is done via the ***tx_trace_user_event_insert***, defined in Chapter 5.</span></span> <span data-ttu-id="5b534-111">Poniższe przykładowe wywołania wstawiają dwa zdarzenia zdefiniowane przez użytkownika do bieżącego buforu śledzenia w miejscu docelowym, czyli zdarzenia zdefiniowanego przez użytkownika 4096 i zdarzenia 4098:</span><span class="sxs-lookup"><span data-stu-id="5b534-111">The following example calls insert two user-defined events into the current trace buffer on the target, namely user-defined event 4096 and event 4098:</span></span>

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a><span data-ttu-id="5b534-112">Domyślny sposób wyświetlania zdarzeń User-Defined</span><span class="sxs-lookup"><span data-stu-id="5b534-112">Default Display of User-Defined Events</span></span>

![Ikona zdarzenia zdefiniowanego przez użytkownika](./media/user-guide/tx-events/image0.png)

<span data-ttu-id="5b534-114">Domyślnie TraceX wyświetla wszystkie zdarzenia użytkownika z domyślną ikoną zdarzenia zdefiniowaną przez użytkownika, zgodnie z opisem w rozdziale 6.</span><span class="sxs-lookup"><span data-stu-id="5b534-114">By default, TraceX displays all user events with a default user-defined Event icon as described in Chapter 6.</span></span> <span data-ttu-id="5b534-115">Rysunek 28 przedstawia domyślną ikonę zdarzenia zdefiniowaną przez użytkownika dla zdarzeń 452 i 453, które zostały umieszczone w buforze zdarzeń za pośrednictwem poprzednich przykładów ***tx_trace_user_event_insert*** .</span><span class="sxs-lookup"><span data-stu-id="5b534-115">Figure 28 shows the default user-defined event icon for events 452 and 453, which were placed in the event buffer via the previous ***tx_trace_user_event_insert*** examples.</span></span>

<span data-ttu-id="5b534-116">![Zrzut ekranu przedstawiający domyślny sposób wyświetlania zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.1.png)
 **Rysunek 28**</span><span class="sxs-lookup"><span data-stu-id="5b534-116">![Screenshot of the default display of user-defined events.](./media/user-guide/10.1.png)
**FIGURE 28**</span></span>

<span data-ttu-id="5b534-117">Szczegółowe informacje są również dostępne dla zdarzeń zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5b534-117">Detailed information is also available for user-defined Events.</span></span> <span data-ttu-id="5b534-118">Rysunek 28 przedstawia szczegółowe informacje o zdarzeniu dla zdarzenia 452, które ma numer zdarzenia 4096 i zawiera określone cztery pola informacji.</span><span class="sxs-lookup"><span data-stu-id="5b534-118">Figure 28 shows the detailed event information for event 452, which has event number 4096 and shows the specified four information fields.</span></span>

<span data-ttu-id="5b534-119">![Zrzut ekranu przedstawiający szczegółowy sposób wyświetlania zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.2.png)
 **Rysunek 29**</span><span class="sxs-lookup"><span data-stu-id="5b534-119">![Screenshot of the detailed display of user-defined events.](./media/user-guide/10.2.png)
**FIGURE 29**</span></span>

## <a name="defining-custom-user-defined-event-icons"></a><span data-ttu-id="5b534-120">Definiowanie niestandardowych ikon zdarzeń User-Defined</span><span class="sxs-lookup"><span data-stu-id="5b534-120">Defining Custom User-Defined Event Icons</span></span>

<span data-ttu-id="5b534-121">TraceX udostępnia także użytkownikowi możliwość tworzenia niestandardowych ikon zdarzeń zdefiniowanych przez użytkownika i etykiet pól informacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5b534-121">TraceX also provides the user the ability to create custom user-defined event icons and custom information field labels.</span></span> <span data-ttu-id="5b534-122">Tę możliwość uzyskuje się przez dodanie specyfikacji ikon zdarzeń do pliku konfiguracji \***tracex_custom. trxc** _.</span><span class="sxs-lookup"><span data-stu-id="5b534-122">This capability is achieved by adding event icon specifications to the \***tracex_custom.trxc** _ configuration file.</span></span> <span data-ttu-id="5b534-123">Ten plik znajduje się w podkatalogu _ *_CustomEvents_*\* katalogu instalacyjnego TraceX, który domyślnie jest C:\ Azure_RTOS \tracex.</span><span class="sxs-lookup"><span data-stu-id="5b534-123">This file is located in the _ *_CustomEvents_*\* subdirectory of your user-defined TraceX installation directory, which defaults to c:\Azure_RTOS\TraceX.</span></span> <span data-ttu-id="5b534-124">Przykład ścieżki do katalogu pokazano na rysunku 30.</span><span class="sxs-lookup"><span data-stu-id="5b534-124">An example directory path is shown in Figure 30.</span></span>

<span data-ttu-id="5b534-125">![Zrzut ekranu przedstawiający przykład ścieżki katalogu. ](./media/user-guide/custom_events_folder.png)
 **Rysunek 30**</span><span class="sxs-lookup"><span data-stu-id="5b534-125">![Screenshot of an example directory path.](./media/user-guide/custom_events_folder.png)
**FIGURE 30**</span></span>

<span data-ttu-id="5b534-126">Plik konfiguracji niestandardowego zdarzenia ***tracex_custom. trxc*** to prosty plik tekstowy ASCII zawierający zero lub więcej niestandardowych definicji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5b534-126">The ***tracex_custom.trxc*** custom event configuration file is a simple ASCII text file containing zero or more custom event definitions.</span></span> <span data-ttu-id="5b534-127">Format pliku jest następujący:</span><span class="sxs-lookup"><span data-stu-id="5b534-127">The format of the file is as follows:</span></span>

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

<span data-ttu-id="5b534-128">Każdy wiersz między początkiem i końcem jest używany do definiowania pojedynczego zdarzenia niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="5b534-128">Each line between Start and End is used to define a single custom event.</span></span> <span data-ttu-id="5b534-129">TraceX udostępnia wersję szablonu tego pliku bez zdefiniowanych zdarzeń niestandardowych (nie dotyczy etykiet "Start" i "End").</span><span class="sxs-lookup"><span data-stu-id="5b534-129">TraceX provides a template version of this file with no custom events defined (nothing between the "Start" and "End" labels).</span></span> <span data-ttu-id="5b534-130">Format niestandardowej definicji zdarzenia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="5b534-130">The format of a custom event definition is as follows:</span></span>

<span data-ttu-id="5b534-131">**Number, Name, skrót, top_color, bottom_color, Label1, etykiety 2, etykiety 2, Label4**</span><span class="sxs-lookup"><span data-stu-id="5b534-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span></span>

<span data-ttu-id="5b534-132">gdzie:</span><span class="sxs-lookup"><span data-stu-id="5b534-132">where:</span></span>

- <span data-ttu-id="5b534-133">Liczba: definiuje zdefiniowany przez użytkownika numer zdarzenia z zakresu od 4096 do 65535 włącznie.</span><span class="sxs-lookup"><span data-stu-id="5b534-133">number: Defines the user-defined event number, between 4096 and 65535, inclusive.</span></span></th>
- <span data-ttu-id="5b534-134">Nazwa: Określa nazwę logiczną dla zdarzenia zdefiniowanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5b534-134">name: Defines the logical name for the user-defined event.</span></span></td>
- <span data-ttu-id="5b534-135">skrót: definiuje dwuliterowy skrót zdarzenia zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5b534-135">abbreviation: Defines the two-letter user-defined event abbreviation.</span></span></td>
- <span data-ttu-id="5b534-136">top_color: definiuje wartość RGB dla górnej połowy ikony, która jest cyfrą w nawiasie.</span><span class="sxs-lookup"><span data-stu-id="5b534-136">top_color: Defines the RGB value for the top-half of the icon, which is a three-digit number in parenthesis.</span></span> <span data-ttu-id="5b534-137">Niektóre typowe definicje RGB są</span><span class="sxs-lookup"><span data-stu-id="5b534-137">Some typical RGB definitions are</span></span>
  - <span data-ttu-id="5b534-138">CZARNY = (0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="5b534-138">BLACK = (0,0,0)</span></span>       
  - <span data-ttu-id="5b534-139">BIAŁY = (255 255 255)</span><span class="sxs-lookup"><span data-stu-id="5b534-139">WHITE = (255,255,255)</span></span>
  - <span data-ttu-id="5b534-140">CZERWONY = (255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="5b534-140">RED = (255,0,0)</span></span>     
  - <span data-ttu-id="5b534-141">ZIELONY = (0255, 0)</span><span class="sxs-lookup"><span data-stu-id="5b534-141">GREEN = (0,255,0)</span></span>     
  - <span data-ttu-id="5b534-142">NIEBIESKI = (0, 0255)</span><span class="sxs-lookup"><span data-stu-id="5b534-142">BLUE = (0,0,255)</span></span>     
  - <span data-ttu-id="5b534-143">ŻÓŁTY = (255255, 0)</span><span class="sxs-lookup"><span data-stu-id="5b534-143">YELLOW = (255,255,0)</span></span>   
  - <span data-ttu-id="5b534-144">BŁĘKITNY = (0255 255)</span><span class="sxs-lookup"><span data-stu-id="5b534-144">CYAN = (0,255,255)</span></span>   
  - <span data-ttu-id="5b534-145">AMARANTOWY = (255, 0255)</span><span class="sxs-lookup"><span data-stu-id="5b534-145">MAGENTA = (255,0,255)</span></span>   
  <span data-ttu-id="5b534-146">Użycie specyfikacji RBG umożliwia użytkownikowi szeroki zakres kolorów dla każdej ikony zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5b534-146">Using the RBG specification gives the user a broad range of colors for each user-defined icon.</span></span> <span data-ttu-id="5b534-147">Aby uzyskać więcej informacji na temat definicji koloru RBG, zobacz: https://en.wikipedia.org/wiki/RGB#Digital_representations</span><span class="sxs-lookup"><span data-stu-id="5b534-147">For more information on RBG color definition, see: https://en.wikipedia.org/wiki/RGB#Digital_representations</span></span>
- <span data-ttu-id="5b534-148">botton_color: definiuje wartość RGB dla dolnej połowy ikony, która jest liczbą składającą się z trzech cyfr w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5b534-148">botton_color: Defines the RGB value for the bottom half of the icon, which is a three-digit number in parenthesis.</span></span>
- <span data-ttu-id="5b534-149">Label1: etykieta dla \***info_field_1** _, jak określono w wywołaniu _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b534-149">label1: Label for ***info_field_1** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="5b534-150">etykiety 2: etykieta dla \***info_field_2** _, jak określono w wywołaniu _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b534-150">label2: Label for ***info_field_2** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="5b534-151">etykiety 3: etykieta dla \***info_field_3** _, jak określono w wywołaniu _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b534-151">label3: Label for ***info_field_3** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="5b534-152">Label4: etykieta dla \***info_field_4** _, jak określono w wywołaniu _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b534-152">label4: Label for ***info_field_4** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>

<span data-ttu-id="5b534-153">Przykładowe definicje dla każdego z dwóch zdarzeń zdefiniowanych przez użytkownika użytych w tym rozdziale przedstawiono na rysunku 10,4.</span><span class="sxs-lookup"><span data-stu-id="5b534-153">Example definitions for each of the two user-defined events used in this chapter are shown in Figure 10.4.</span></span> <span data-ttu-id="5b534-154">Pierwsza definicja dotyczy zdarzenia 4096 w wierszu 5 pliku \***tracex_custom. trxc** _.</span><span class="sxs-lookup"><span data-stu-id="5b534-154">The first definition is for event 4096 at line 5 of the \***tracex_custom.trxc** _ file.</span></span> <span data-ttu-id="5b534-155">Ta definicja zawiera zdarzenie zdefiniowane przez użytkownika 4096 o nazwie _ \* First_User_Event \* \*, określa dwuliterowy skrót **Fe**, powoduje, że górna część ikony czerwona, Dolna część ikony zielony i nazwy pól informacji jako **First_Info1**, **First_Info2**, **First_Info3** i **First_Info4**.</span><span class="sxs-lookup"><span data-stu-id="5b534-155">This definition gives user-defined event 4096 the name _\*First_User_Event\*\*, specifies a two-letter abbreviation of **FE**, makes the top portion of the icon red, the bottom portion of the icon green, and names the information fields as **First_Info1**, **First_Info2**, **First_Info3**, and **First_Info4**.</span></span> <span data-ttu-id="5b534-156">Zdefiniowane przez użytkownika zdarzenie 4098 jest zdefiniowane w podobny sposób w wierszu 6 **_tracex_custom. trxc_**.</span><span class="sxs-lookup"><span data-stu-id="5b534-156">User-defined event 4098 is defined similarly at line 6 of **_tracex_custom.trxc_**.</span></span>

<span data-ttu-id="5b534-157">![Zrzut ekranu przedstawiający przykładowe definicje zdarzeń zdefiniowanych przez użytkownika. ](./media/user-guide/10.4.png)
 **Rysunek 31**</span><span class="sxs-lookup"><span data-stu-id="5b534-157">![Screenshot of the example definitions for the user-defined events.](./media/user-guide/10.4.png)
**FIGURE 31**</span></span>

<span data-ttu-id="5b534-158">Ponieważ plik \***tracex_custom. trxc** _ jest odczytywany przez tracex podczas inicjowania, tracex musi zostać zakończony i uruchomiony ponownie, zanim definicje ikon niestandardowych zaczną obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="5b534-158">Since the \***tracex_custom.trxc** _ file is read by TraceX during initialization, TraceX must be exited and restarted before the custom icon definitions can take effect.</span></span> <span data-ttu-id="5b534-159">Rysunek 32 przedstawia TraceX wyświetlania zdarzeń zdefiniowanych przez użytkownika 452 i 453 z niestandardowymi ikonami zdarzeń zdefiniowanymi w _ *_tracex_custom. trxc_* \*.</span><span class="sxs-lookup"><span data-stu-id="5b534-159">Figure 32 shows the TraceX display of user-defined events 452 and 453 with the custom event icons defined in _\*_tracex_custom.trxc_\*\*.</span></span>

<span data-ttu-id="5b534-160">![Zrzut ekranu przedstawiający wyświetlanie TraceX zdarzeń zdefiniowanych przez użytkownika z ikonami zdarzeń niestandardowych. ](./media/user-guide/10.5.png)
 **Rysunek 32**</span><span class="sxs-lookup"><span data-stu-id="5b534-160">![Screenshot of the TraceX display of user defined events with the custom event icons.](./media/user-guide/10.5.png)
**FIGURE 32**</span></span>

<span data-ttu-id="5b534-161">Dodatkowe informacje w definicji zdarzenia niestandardowego są wyświetlane, gdy zdarzenie jest wybierane przy użyciu dwukrotnego kliknięcia, wskaźnika myszy lub kliknięcia przycisku bieżące zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="5b534-161">The additional information in the custom event definition is shown when the event you select using a double-click, mouse-over, or clicking the current event button.</span></span> <span data-ttu-id="5b534-162">Rysunek 33 pokazuje zaznaczenie podwójnego kliknięcia dla zdarzenia 452.</span><span class="sxs-lookup"><span data-stu-id="5b534-162">Figure 33 shows the double-click selection on event 452.</span></span> <span data-ttu-id="5b534-163">Pola Nazwa zdarzenia i informacje są zgodne z definicją przykładową, która została dodana do ***tracex_custom. trxc***.</span><span class="sxs-lookup"><span data-stu-id="5b534-163">The event name and information fields all match the sample definition that was added to ***tracex_custom.trxc***.</span></span>

<span data-ttu-id="5b534-164">![Zrzut ekranu przedstawiający zaznaczenie podwójnego kliknięcia na zdarzeniu. ](./media/user-guide/10.6.png)
 **Rysunek 33**</span><span class="sxs-lookup"><span data-stu-id="5b534-164">![Screenshot of the double-click selection on an event.](./media/user-guide/10.6.png)
**FIGURE 33**</span></span>
