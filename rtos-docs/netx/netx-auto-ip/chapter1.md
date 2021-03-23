---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX AutoIP
description: Protokół Azure RTO NetX AutoIP jest protokołem przeznaczonym do dynamicznego konfigurowania adresów IPv4 w sieci lokalnej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c26b4112814bb586e056246d68c2597d56df6085
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822753"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-autoip"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX AutoIP
  
Protokół Azure RTO NetX AutoIP jest protokołem przeznaczonym do dynamicznego konfigurowania adresów IPv4 w sieci lokalnej. AutoIP to prosty protokół, który wykorzystuje funkcje ARP do wykonywania funkcji automatycznego przypisywania adresów IP. AutoIP przydziela adresy z zakresu od 169.254.1.0 do 169.254.254.255.

## <a name="autoip-requirements"></a>Wymagania AutoIP

Aby zapewnić prawidłowe działanie, pakiet NetX AutoIP wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto należy włączyć protokół ARP dla tego samego wystąpienia IP. Pakiet AutoIP NetX nie ma żadnych dalszych wymagań.

## <a name="autoip-constraints"></a>Ograniczenia AutoIP 

Protokół NetX AutoIP implementuje wymagania standardu RFC3927. Istnieją jednak następujące ograniczenia:

1. Jeśli używany jest protokół DHCP NetX, należy utworzyć wątek DHCP z wyższym priorytetem niż zarówno wątek wystąpienia adresu IP NetX, jak i wątek AutoIP.
1. NetX AutoIP nie zapewnia mechanizmu dla starych adresów IP do dalszego użycia.
1. Gdy adres IP ulegnie zmianie, aplikacja jest odpowiedzialna za rozbicie istniejących połączeń TCP i ponowne ich ustanowienie na nowym adresie IP.

## <a name="autoip-protocol-implementation"></a>Implementacja protokołu AutoIP

Protokół NetX AutoIP najpierw wybiera adres losowy w zakresie adresów IPv4 AutoIP 169.254.1.0 za pomocą 169.254.254.255. Alternatywnie aplikacja może wymusić początkowy adres IP, dostarczając go do funkcji ***nx_auto_ip_start*** . Jest to przydatne w sytuacjach, gdy adres AutoIP został pomyślnie użyty w poprzednim uruchomieniu.

Po wybraniu adresu AutoIP, NetX AutoIP wysyła serię sond ARP dla wybranego adresu. Sonda ARP składa się z komunikatu żądania ARP z adresem nadawcy ustawionym na wartość 0.0.0.0 i adresem docelowym ustawionym na żądany adres AutoIP. Są wysyłane serie tych sond ARP (rzeczywista liczba jest określana przez Definiuj NX_AUTO_IP_PROBE_NUM). Jeśli inny węzeł sieci odpowiada na tę sondę lub wysyła identyczną sondę dla tego samego adresu, nowy adres AutoIP jest losowo wybierany w ramach zakresu adresów IPv4 AutoIP i powtarzające się przetwarzanie sondy.

Jeśli NX_AUTO_IP_PROBE_NUM sondy są wysyłane bez odpowiedzi, NetX AutoIP wystawia listę anonsów ARP dla wybranego adresu. Anons protokołu ARP składa się z komunikatu żądania ARP z adresem nadawcy i docelowym w wiadomości ARP ustawionym na wybrany adres AutoIP. Zostanie wysłany szereg komunikatów anonsu ARP odpowiadających Definiuj NX_AUTO_IP_ANNOUNCE_NUM. Jeśli inny węzeł sieci odpowiada na wiadomość anonsu lub wysyła identyczny anons dla tego samego adresu, nowy adres AutoIP jest losowo wybierany w ramach zakresu adresów IPv4 AutoIP, a przetwarzanie sondy zaczyna się od początku.

Gdy sonda i powiadomienie zakończą się bez wykrytych konfliktów, wybrany adres AutoIP jest uznawany za prawidłowy, a skojarzone wystąpienie adresu IP jest skonfigurowane z tym adresem.

## <a name="autoip-address-change"></a>Zmiana adresu AutoIP

Jak wspomniano wcześniej, NetX AutoIP zmienia adres wystąpienia adresu IP po pomyślnym przeprowadzeniu sondowania i przetworzeniu anonsu. Monitorowanie w tym przypadku nie jest poważny ważne. Jednak w przyszłości można zmienić adres AutoIP. Potencjalnymi przyczynami są konflikty w przyszłości, a także rozpoznawanie adresów DHCP. Aby prawidłowo przetwarzać te potencjalne sytuacje, aplikacja powinna używać następującego interfejsu API NetX w celu wysyłania alertów o wszelkich zmianach adresu IP i wszystkich:

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
                            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
                            VOID *additional_info);
```

W przypadku przetwarzania w podanej funkcji *ip_address_change_notify* należy ponownie uruchomić procesor NetX AutoIP lub go wyłączyć, jeśli protokół DHCP następnie rozpoznał adres IP. Przykład przetwarzania przykładowego zapoznaj się z małą sekcją *systemu* .

## <a name="autoip-rfcs"></a>AutoIP specyfikacje RFC

NetX AutoIP jest zgodny z RFC3927 i pokrewnymi specyfikacjami RFC.