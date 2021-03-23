---
title: Rozdział 3 — Opis pamięci podręcznej usługi wewnętrznej
description: 'Moduł mDNS programu NetX Duo zarządza dwiema pamięciami podręcznymi usług wewnętrznych: lokalną pamięć podręczną usługi i równorzędną pamięć podręczną usługi.'
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 007f1080a076730cfbcdedc9f063ac0c427a414c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821817"
---
# <a name="chapter-3---description-of-internal-service-cache"></a>Rozdział 3 — Opis pamięci podręcznej usługi wewnętrznej

Moduł mDNS programu NetX Duo zarządza dwiema pamięciami podręcznymi usług wewnętrznych: lokalną pamięć podręczną usługi i równorzędną pamięć podręczną usługi. W pamięci podręcznej usługi lokalnej są przechowywane rekordy zasobów powiązane z usługami oferowanymi przez aplikacje działające w węźle. W przypadku zapytań przychodzących, jeśli pytanie pasuje do oferowanej usługi, odpowiedzi mDNS z odpowiedziami przechowywanymi w lokalnej pamięci podręcznej usługi. Aplikacje rejestrują usługi przez wywołanie interfejsu API *nx_mdns_service_add ()*. Aby usunąć usługi, aplikacje używają interfejsu API *nx_mdns_service_delete ()*, co spowoduje wysłanie komunikatów "pożegnania" przed usunięciem odpowiednich wpisów w lokalnej pamięci podręcznej usługi.

Po dodaniu usługi Usługa mDNS utrzymuje co najmniej 3 rekordy zasobów w lokalnej pamięci podręcznej usługi: SRV, PTR i TXT. Jeśli typ usługi zawiera podtyp, można dodać dodatkowy rekord zasobu PTR. Na przykład aplikacja rejestruje usługę:

```
*name*._*subtype*._sub._*type*._tcp.local,
```

dwa rekordy zasobów PTR są dodawane do lokalnej pamięci podręcznej usługi, jeden dla

```
“*_subtype._*sub*._type._*tcp.local *PTR name.type._*tcp*.*local”
```

i drugi dla

```
*“_type._*tcp*.*local *PTR name.type._*tcp*.*local”.
```

Pamięć podręczna usługi równorzędnej zawiera rekordy zasobów mDNS otrzymane z sąsiednich węzłów. Moduł mDNS zbiera rekordy zasobów anonsowane przez inne węzły w sieci i zapisuje otrzymane informacje w pamięci podręcznej usługi równorzędnej. Gdy aplikacja wysyła zapytania dotyczące informacji, takich jak hosty IPv4 lub IPv6, usługa mDNS przeszukuje pamięć podręczną usługi równorzędnej pod kątem lokalnie zbuforowanych odpowiedzi. Gdy zapytania aplikacji dotyczące usług oferowanych przez elementy równorzędne, usługa mDNS przeszukuje pamięć podręczną w poszukiwaniu powiązanych rekordów adresów PTR, SRV, TXT i IPv4/IPv6. Pamięć podręczna usługi równorzędnej przechowuje również zapytania wysyłane do węzła. Na przykład aplikacja może zażądać określonej usługi przez wywołanie *nx_mdns_service_one_shot_query.* Jeśli usługa nie zostanie znaleziona w pamięci podręcznej usługi peer, usługa mDNS tworzy pytania dotyczące zapytań (PTR, SRV i TXT) w pamięci podręcznej usługi równorzędnej. Te pytania dotyczące zapytań będą wysyłane do sieci okresowo aż do momentu rozwiązania usługi lub przeprowadzenia limitu czasu. Podobnie aplikacja może używać interfejsu API *nx_mdns_service_continous_query ()* , aby zażądać określonej usługi przez długi czas (aplikacja anuluje wcześniej wystawione ciągłe zapytanie przy użyciu interfejsu API *nx_mdns_service_query_stop ()* ). Aby wyszukać określoną usługę w pamięci podręcznej usługi równorzędnej bez wysyłania zapytań do sieci, aplikacje mogą używać interfejsu API *nx_mdns_serivce_lookup ().* Ten interfejs API przeszukuje rekordy zasobów tylko w pamięci podręcznej usługi równorzędnej.

Każdy rekord zasobu jest przechowywany w strukturze danych *NX_MDNS_RR* w pamięci podręcznej usługi. Ciągi w rekordach zasobów są o zmiennej długości, dlatego nie są przechowywane w strukturze *NX_MDNS_RR* . Rekord zasobu zawiera wskaźnik do rzeczywistej lokalizacji pamięci, w której jest przechowywany ciąg. Tabela ciągów i rekordy zasobów współużytkują pamięć podręczną usługi. Rekordy zasobów są przechowywane od początku pamięci podręcznej usługi i rosną do końca pamięci podręcznej. Tabela ciągów rozpoczyna się od końca pamięci podręcznej usługi i powiększa się do początku pamięci podręcznej. Każdy ciąg w tabeli ciągów ma pole długości i pole licznika. Gdy ciąg zostanie dodany do tabeli ciągów, jeśli ten sam ciąg już występuje w tabeli, wartość licznika jest zwiększana i nie jest przydzielono żadnej pamięci dla ciągu. Pamięć podręczna usługi jest traktowana jako pełna, jeśli do pamięci podręcznej usługi nie można dodać więcej rekordów zasobów lub nowych ciągów.

Istnieją dwa sposoby na znalezienie usług oferowanych w sieci lokalnej przez aplikację. Może wystawić konkretną usługę wyszukaną w ramach zapytania z jednym zdjęciem lub może zainicjować ciągłe zapytanie w celu "monitorowania" działań w sieci. W scenariuszu z jedną krótką kwerendą aplikacja musi określić typ usługi. Usługa mDNS wyszukuje za pomocą lokalnej pamięci podręcznej usługi i równorzędnej pamięci podręcznej usługi. W przypadku zlokalizowania wystąpień usługi zapytanie z jednym zdjęciem zwraca z informacjami znajdującymi się w rekordach zasobów. Jeśli w pamięci podręcznej usługi lokalnej lub w pamięci podręcznej usługi sieci równorzędnej nie ma żadnych rekordów, usługa mDNS wysyła komunikaty zapytań. Jeśli nazwa wystąpienia jest określona, *dowolnego* typu (kwerenda typu SRV i txt) o określonej nazwie wystąpienia w postaci "name. Type. local" jest wysyłana do sieci lokalnej. Jeśli nazwa wystąpienia nie zostanie określona, typ PTR zapytania jest wysyłany do sieci lokalnej. Pierwsza odebrana usługa została zwrócona do obiektu wywołującego.

Ciągłe zapytanie działa inaczej. Typowy przypadek użycia dla ciągłego zapytania polega na monitorowaniu sieci lokalnej dla określonej usługi (na przykład w celu ciągłego wyszukiwania usług drukowania w sieci lokalnej). W takim przypadku aplikacja wystawia zapytanie wyszukiwania (za pośrednictwem zapytania API *nx_mdns_service_continious_*) dla niektórych typów usług. Obiekt wywołujący zazwyczaj nie czeka na określoną odpowiedź. W przypadku zapytań przesyłanych w postaci ciągłego zapytania moduł mDNS przesyła zapytania okresowo przy użyciu wykładniczego wzrostu interwałów. Aby zatrzymać zapytanie, aplikacja musi używać interfejsu API *nx_mdns_service_query_stop* , aby zatrzymać wewnętrzny czasomierz w tych zapytaniach. Typ zapytania może mieć wartość NULL. w takim przypadku typ zapytania jest ustawiony na specjalny typ PTR "_services. _DNS-SD. _udp. local". Ten typ usługi jest definiowany przez mDNS jako sposób odnajdowania wszystkich usług dostępnych w sieci lokalnej. Jeśli zostanie podana nazwa wystąpienia, dowolny typ (zapytanie o typ SRV i TXT) o określonej nazwie wystąpienia "name. Type. local" jest wysyłany do sieci lokalnej. Jeśli nazwa wystąpienia ma wartość NULL, typ PTR zapytania jest wysyłany do sieci lokalnej,

Wszystkie odpowiedzi, w tym odpowiedzi z niezamówionych zapytań, są rejestrowane w pamięci podręcznej usługi równorzędnej. W późniejszym czasie aplikacja używa interfejsu API *nx_mdns_service_lookup* do pobierania określonej usługi z pamięci podręcznej usługi równorzędnej.

Specjalna Uwaga dotycząca fragmentacji: Każda struktura *NX_MDNS_RR* ma ustalony rozmiar i w związku z tym nie podlega fragmentacji, ponieważ program mDNS dodaje i usuwa rekordy zasobów. Ciągi są jednak o zmiennej długości. Po usunięciu ciągu miejsce stanie się dostępne i może być używane dla nowego ciągu, jeśli nowy ciąg może się zmieścić w. Jednak ta operacja powoduje fragmentację pamięci. Po dodaniu i usunięciu usług tabela ciągów może być pofragmentowana do punktu, w którym nie można dodać nowych ciągów, nawet jeśli pamięć podręczna usługi zawiera wystarczającą liczbę nieużywanych bajtów dla tego ciągu. Aplikacje lokalne są bardziej stabilne i przewidywalne. W związku z tym pamięć podręczna usługi lokalnej może być mniej istotna od fragmentacji. Pamięć podręczna usługi równorzędnej, z drugiej strony, ciągle dodaje rekordy zasobów, ponieważ usługi staną się dostępne, lub usuń rekordy zasobów, gdy usługi są usuwane przez węzły w sieci. Usługi w sieci są gotowe do użycia, co powoduje częstsze wykonywanie operacji przydzielania/usuwania w tabeli ciągów. W miarę możliwości tabela ciągów zostanie pofragmentowana. W takiej sytuacji proste rozwiązanie to opróżnianie całej pamięci podręcznej usługi peer Service. Można to zrobić, wywołując interfejs API *nx_mdns_peer_cache_clear ().* Należy zauważyć, że ten interfejs API automatycznie kończy wszystkie zaległe zapytania ciągłe.
