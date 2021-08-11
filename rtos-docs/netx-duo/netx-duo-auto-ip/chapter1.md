---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo AutoIP
description: Protokół AutoIP to protokół przeznaczony do dynamicznego konfigurowania adresów IPv4 w sieci lokalnej. Aby zapewnić prawidłowe działanie, pakiet Azure RTOS NetX Duo AutoIP wymaga, aby wystąpienie adresu IP NetX zostało już utworzone.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24fb514b71f7812266de23ec6d485dca9769a2bef491fc773a90f9945885f3df
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784907"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-autoip"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo AutoIP

Protokół AutoIP to protokół przeznaczony do dynamicznego konfigurowania adresów IPv4 w sieci lokalnej. AutoIP to prosty protokół, który wykorzystuje możliwości ARP do wykonywania funkcji automatycznego przypisywania adresów IP. Funkcja AutoIP przydziela adresy z zakresu od 169.254.1.0 do 169.254.254.255.

## <a name="autoip-requirements"></a>Wymagania funkcji AutoIP

Aby zapewnić prawidłowe działanie, pakiet Azure RTOS NetX Duo AutoIP wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto protokół ARP musi być włączony w tym samym wystąpieniu adresu IP. Pakiet NetX AutoIP nie ma dodatkowych wymagań.

## <a name="autoip-constraints"></a>Ograniczenia funkcji AutoIP

Protokół NetX AutoIP implementuje wymagania standardu RFC3927. Istnieją jednak następujące ograniczenia:

1. Jeśli jest używany protokół DHCP NetX, wątek DHCP musi być utworzony z wyższym priorytetem niż wątek wystąpienia adresu IP NetX i wątek autoIP.

1. Funkcja NetX AutoIP nie zapewnia mechanizmu dalszego dalszego działania starych adresów IP.

1. Po zmianie adresu IP aplikacja jest odpowiedzialna za odjęcie wszystkich istniejących połączeń TCP i ponowne ustanowienie ich na nowym adresie IP.

## <a name="autoip-protocol-implementation"></a>Implementacja protokołu AutoIP

Protokół NetX AutoIP najpierw wybiera losowy adres w zakresie adresów IPv4 funkcji AutoIP od 169.254.1.0 do 169.254.254.255. Alternatywnie aplikacja może wymusić początkowy adres IP, podając go do ***nx_auto_ip_start*** funkcji. Jest to przydatne w sytuacjach, gdy adres AutoIP został pomyślnie użyty w wcześniejszym uruchomieniu.

Po wybraniu adresu autoIP funkcja NetX AutoIP wysyła serię sond ARP dla wybranego adresu. Sonda ARP składa się z komunikatu żądania ARP z adresem nadawcy ustawionym na 0.0.0.0, a adres docelowy ustawiony na żądany adres autoIP. Wysyłana jest seria tych sond ARP (rzeczywista liczba jest określana przez definicję NX_AUTO_IP_PROBE_NUM). Jeśli inny węzeł sieci odpowiada na tę sondę lub wysyła identyczną sondę dla tego samego adresu, nowy adres funkcji AutoIP jest wybierany losowo w zakresie adresów IPv4 funkcji AutoIP, a przetwarzanie sondy jest powtarzane.

Jeśli NX_AUTO_IP_PROBE_NUM są wysyłane bez żadnych odpowiedzi, funkcja NetX AutoIP wysyła serię anonsów ARP dla wybranego adresu. Anons ARP składa się z komunikatu żądania ARP z adresem nadawcy i adresu docelowego w komunikacie ARP ustawionym na wybrany adres autoIP. Wysyłana jest seria komunikatów anonsów ARP odpowiadających definicjom NX_AUTO_IP_ANNOUNCE_NUM. Jeśli inny węzeł sieci odpowiada na komunikat z ogłoszeniem lub wysyła identyczne anons dla tego samego adresu, nowy adres AutoIP jest losowo wybierany w zakresie adresów IPv4 funkcji AutoIP i rozpocznie się przetwarzanie sondy.

Po zakończeniu sondowania i anonsu bez żadnych wykrytych konfliktów wybrany adres autoIP jest uznawany za prawidłowy, a skojarzone wystąpienie adresu IP jest konfigurowe przy użyciu tego adresu.

## <a name="autoip-address-change"></a>Zmiana adresu automatycznego adresu IP

Jak wspomniano wcześniej, funkcja NetX AutoIP zmienia adres wystąpienia IP po pomyślnym przetworzeniu sondy i anonsu. Monitorowanie w tym przypadku nie jest bardzo ważne. Jednak w przyszłości adres autoip może ulec zmianie. Potencjalne przyczyny obejmują przyszłe konflikty adresów AutoIP, a także rozpoznawania adresów DHCP. Aby prawidłowo przetworzyć te potencjalne sytuacje, aplikacja powinna użyć następującego interfejsu API NetX, aby ostrzec ją o wszelkich zmianach adresów IP:

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
            VOID *additional_info);
```

Przetwarzanie w dostarczonej funkcji *ip_address_change_notify* musi ponownie uruchomić procesor NetX AutoIP lub wyłączyć go, jeśli protokół DHCP rozpozna następnie adres IP. Aby uzyskać informacje na temat *przetwarzania przykładów,* zapoznaj się z sekcją Small Example System (Mały przykładowy system).

## <a name="autoip-rfcs"></a>Automatyczne RFC

Funkcja NetX AutoIP jest zgodna ze specyfikacją RFC3927 i powiązanymi RFC.