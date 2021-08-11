---
title: Rozdział 3 — Opis wewnętrznej pamięci podręcznej usług
description: 'Moduł mDNS NetX Duo zarządza dwiema pamięciami podręcznmi usług wewnętrznych: lokalną pamięcią podręczną usługi i pamięcią podręczną usługi równorzędnej.'
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: edf52cb2d7df293a4606d6c5b5b63075969933fb1a093a1d83b91b2709c08f0c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791724"
---
# <a name="chapter-3---description-of-internal-service-cache"></a>Rozdział 3 — Opis wewnętrznej pamięci podręcznej usług

Moduł mDNS NetX Duo zarządza dwiema pamięciami podręcznmi usług wewnętrznych: lokalną pamięcią podręczną usługi i pamięcią podręczną usługi równorzędnej. Lokalna pamięć podręczna usługi przechowuje rekordy zasobów związane z usługami oferowanymi przez aplikacje działające w węźle. W przypadku zapytań przychodzących, jeśli pytanie pasuje do oferowanej usługi, odpowiedzi mDNS z odpowiedziami przechowywanymi w lokalnej pamięci podręcznej usługi. Aplikacje rejestrują usługi, wywołując interfejs API *nx_mdns_service_add()*. Aby usunąć usługi, aplikacje używają interfejsu API *nx_mdns_service_delete(),* który z kolei będzie wysyłać komunikaty "do odszukania" przed usunięciem odpowiednich wpisów w lokalnej pamięci podręcznej usługi.

Po dodaniu usługi mDNS przechowuje co najmniej 3 rekordy zasobów w lokalnej pamięci podręcznej usługi: SRV, PTR i TXT. Jeśli typ usługi zawiera podtyp, może zostać dodany dodatkowy rekord zasobu PTR. Na przykład aplikacja rejestruje usługę:

```
*name*._*subtype*._sub._*type*._tcp.local,
```

Dwa rekordy zasobów PTR są dodawane do lokalnej pamięci podręcznej usługi, jeden dla

```
“*_subtype._*sub*._type._*tcp.local *PTR name.type._*tcp*.*local”
```

i drugi dla

```
*“_type._*tcp*.*local *PTR name.type._*tcp*.*local”.
```

Pamięć podręczna usługi równorzędnej zawiera rekordy zasobów mDNS odebrane z sąsiednich węzłów. Moduł mDNS zbiera rekordy zasobów anonsowane przez inne węzły w sieci i zapisuje odebrane informacje w pamięci podręcznej usługi równorzędnej. Gdy aplikacja wysyła zapytanie o informacje, takie jak adresy IPv4 lub IPv6 hosta, usługa mDNS wyszukuje odpowiedzi lokalnie buforowane w pamięci podręcznej w pamięci podręcznej równorzędnej. Gdy aplikacja wykonuje zapytania dotyczące usług oferowanych przez sieci równorzędne, mDNS wyszukuje w pamięci podręcznej powiązane rekordy adresów PTR, SRV, TXT i IPv4/IPv6. Pamięć podręczna usługi równorzędnej przechowuje również zapytania wysyłane do węzła. Na przykład aplikacja może zażądać określonej usługi, wywołując *nx_mdns_service_one_shot_query.* Jeśli usługa nie zostanie znaleziona w pamięci podręcznej usługi równorzędnej, usługa mDNS tworzy pytania dotyczące zapytań (PTR, SRV i TXT) w pamięci podręcznej usługi równorzędnej. Te pytania dotyczące zapytań będą okresowo wysyłane do sieci do momentu rozwiązania usługi lub przeoowania jej czasu. Podobnie aplikacja może używać interfejsu API *nx_mdns_service_continous_query()* do żądania określonej usługi przez długi czas (aplikacja anuluje wcześniej wystawione ciągłe zapytanie przy użyciu interfejsu API *nx_mdns_service_query_stop()* ). Aby wyszukać określoną usługę w pamięci podręcznej usługi równorzędnej bez wysyłania zapytań do sieci, aplikacje mogą używać interfejsu API *nx_mdns_serivce_lookup().* Ten interfejs API przeszukuje tylko rekordy zasobów w pamięci podręcznej usługi równorzędnej.

Każdy rekord zasobu jest przechowywany w strukturze danych *NX_MDNS_RR* w pamięciach podręcznych usługi. Ciągi w rekordach zasobów mają zmienną długość, dlatego nie są przechowywane w *NX_MDNS_RR* zasobów. Rekord zasobu zawiera wskaźnik do rzeczywistej lokalizacji pamięci, w której jest przechowywany ciąg. Tabela ciągów i rekordy zasobów współdzielą pamięć podręczną usługi. Rekordy zasobów są przechowywane od początku pamięci podręcznej usługi i rosną do końca pamięci podręcznej. Tabela ciągów zaczyna się od końca pamięci podręcznej usługi i rozwija się do początku pamięci podręcznej. Każdy ciąg w tabeli ciągów ma pole długości i pole licznika. Gdy ciąg jest dodawany do tabeli ciągów, jeśli ten sam ciąg jest już obecny w tabeli, wartość licznika jest zwiększana i nie jest przydzielana pamięć dla ciągu. Pamięć podręczna usługi jest uważana za zapełnianą, jeśli do pamięci podręcznej usługi nie można dodać żadnych dodatkowych rekordów zasobów lub nowych ciągów.

Istnieją dwa sposoby, aby aplikacja znalazła usługi oferowane w sieci lokalnej. Może ona wydać konkretną usługę podczas wyszukiwania za pomocą zapytania jednostrzałowego lub może zainicjować ciągłe zapytanie w celu "monitorowania" działań w sieci. W scenariuszu z jednym zapytaniem aplikacja musi określić typ usługi. Usługa mDNS przeszukuje lokalną pamięć podręczną usługi i pamięć podręczną usługi równorzędnej. Jeśli znajduje się wystąpienie usługi, jednozdniowe zapytanie zwraca informacje znajdujące się w rekordach zasobów. Jeśli w lokalnej pamięci podręcznej usługi lub pamięci podręcznej usługi równorzędnej nie ma żadnych rekordów, usługa mDNS wysyła komunikaty zapytania. Jeśli zostanie określona nazwa wystąpienia, typ *ANY* (zapytanie typu SRV i TXT) o określonej nazwie wystąpienia w postaci "name.type.local" jest wysyłany do sieci lokalnej. Jeśli nazwa wystąpienia nie zostanie określona, typ PTR zapytania jest wysyłany do sieci lokalnej. Pierwsza kompletna odebrana usługa jest zwracana do wywołującego.

Zapytanie ciągłe działa inaczej. Typowym zastosowaniem zapytania ciągłego jest monitorowanie sieci lokalnej pod zakresie określonej usługi (na przykład w celu ciągłego wyszukiwania usług drukowania w sieci lokalnej). W takim przypadku aplikacja wydaje zapytanie wyszukiwania (za pośrednictwem zapytania interfejsu API *nx_mdns_service_continious_)* dla określonego typu usług. Wywołujący zazwyczaj nie czeka na określonej odpowiedzi. W przypadku zapytań przesyłanych jako zapytania ciągłe moduł mDNS okresowo przesyła zapytania z wykładniczo rosnącymi interwałami. Aby zatrzymać zapytanie, aplikacja musi użyć interfejsu API *nx_mdns_service_query_stop,* aby zatrzymać wewnętrzny czasomierz w tych zapytaniach. Typ zapytania może mieć wartość NULL. W takim przypadku typ zapytania jest ustawiony na specjalny typ PTR "_services._dns-sd._udp.local". Ten typ usługi jest definiowany przez sieci mDNS jako sposób odnajdywania wszystkich usług dostępnych w sieci lokalnej. Jeśli nazwa wystąpienia jest podany, dowolny typ (zapytanie typu SRV i TXT) o określonej nazwie wystąpienia "name.type.local" jest wysyłany do sieci lokalnej. Jeśli nazwa wystąpienia ma wartość NULL, typ PTR zapytania jest wysyłany do sieci lokalnej,

Wszystkie odpowiedzi, w tym odpowiedzi z niezamówionych zapytań, są rejestrowane w pamięci podręcznej usługi równorzędnej. W późniejszym czasie aplikacja używa interfejsu API *nx_mdns_service_lookup* do pobrania określonej usługi z pamięci podręcznej usługi równorzędnej.

Specjalna uwaga na temat fragmentacji: każda *struktura NX_MDNS_RR* jest stała i dlatego nie podlega fragmentacji, ponieważ mDNS dodaje i usuwa rRs. Jednak ciągi mają zmienną długość. Po usunięciu ciągu miejsce staje się dostępne i może być używane dla nowego ciągu, jeśli nowy ciąg jest w stanie zmieścić. Jednak ta operacja powoduje fragmentacji pamięci. Po dodaniu i usunięciu usług tabela ciągów może być podzielona na fragmenty do punktu, w którym nie można dodać nowych ciągów, mimo że pamięć podręczna usługi zawiera wystarczającą ilość nieużywanych bajtów dla ciągu. Aplikacje lokalne są zwykle bardziej stabilne i przewidywalne. W związku z tym istnieje mniejsze prawdopodobieństwo, że fragmentacja lokalnej pamięci podręcznej usługi będzie mniej niosła ze względu na fragmentację. Z kolei pamięć podręczna usługi równorzędnej stale dodaje rrs w przypadku, gdy usługi stają się dostępne, lub usuwają rrs, gdy usługi są usuwane przez węzły w sieci. Usługi w sieci przychodzą i odchodzą, co powoduje częstsze operacje przydzielania/usuwania w tabeli ciągów. W miarę możliwości tabela ciągów staje się pofragmentowana. W takiej sytuacji prostym rozwiązaniem jest opróżnienie całej pamięci podręcznej usługi równorzędnej. Można to zrobić, wywołując interfejs API *nx_mdns_peer_cache_clear().* Należy pamiętać, że ten interfejs API automatycznie kończy wszystkie zaległe ciągłe zapytania.
