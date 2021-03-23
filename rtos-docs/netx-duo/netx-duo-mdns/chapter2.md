---
title: Rozdział 2 — Instalowanie i korzystanie z programu mDNS
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfigurowaniem i użyciem modułu mDNS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6f9e3d023f1bdbde4546a94da1bc1ccb48578d0e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821823"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>Rozdział 2 — Instalowanie i korzystanie z programu mDNS

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfigurowaniem i użyciem modułu mDNS NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktu

NetX Duo — mDNS jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nxd_mdns. h** Plik nagłówka dla modułu mDNS programu NetX Duo
- **nxd_mdns. c** Plik źródłowy języka C dla modułu mDNS programu NetX Duo
- **nxd_mdns.pdf** Opis pliku PDF dotyczący programu mDNS dla NetX Duo
- **demo_netxduo_mdns. c** Prosty program demonstracyjny, który ilustruje usługi udostępniane przez usługę mDNS.

## <a name="netx-duo-mdns-installation"></a>NetX Duo — instalacja mDNS

Aby można było korzystać z interfejsów API usługi mDNS NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*c:\netxduo*", wówczas należy skopiować *nxd_mdns. h* i *nxd_mdns. c* do tego katalogu.

## <a name="using-netx-duo-mdns"></a>Korzystanie z NetX Duo mDNS

Korzystanie z modułu mDNS NetX Duo jest proste. W zasadzie kod aplikacji musi zawierać *nxd_mdns. h* , po uwzględnieniu *tx_api. h i* *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo. Projekt kompilacji musi zawierać kod źródłowy mDNS i plik aplikacji oraz oczywiście pliki biblioteki ThreadX i NetX. To wszystko, co jest wymagane do korzystania z NetX Duo mDNS.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania modułu mDNS NetX Duo. Wartości domyślne są wyświetlane, ale poszczególne definicje mogą być ustawiane przez aplikację przed włączeniem określonego pliku nagłówka mDNS NetX Duo. Poniższa lista zawiera szczegółowy opis:

- **NX_MDNS_DISABLE_SERVER** Wyłącza funkcję serwera mDNS/DNS-SD. Bez funkcjonalności serwera moduł mDNS/DNS-SD nie ogłasza usług udostępnianych przez hosta lokalnego ani nie odpowiada na zapytania mDNS. Ten symbol nie jest domyślnie zdefiniowany.
- **NX_MDNS_DISABLE_CLIENT** Wyłącza funkcję klienta mDNS/DNS-SD. Bez funkcji klienta usługa mDNS/DNS-SD nie wysyła zapytań ani nie utrzymuje odpowiedzi na zapytania mDNS odebrane przez sieć.
- **NX_MDNS_ENABLE_ADDRESS_CHECK** Zdefiniowany moduł mDNS sprawdza poprawność adresów (adres źródłowy, adres docelowy i numery portów) z odebranych komunikatów usługi mDNS. Ten symbol jest definiowany domyślnie.
- **NX_MDNS_ENABLE_CLIENT_POOF** Zdefiniowany moduł mDNS przeprowadzi pasywną obserwację błędów, a klient mDNS/DNS_SD (bada) obserwować zapytania multiemisji wystawione przez inne hosty w sieci. Ten symbol jest definiowany domyślnie.
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES** Zdefiniowany serwer mDNS (responder/DNS-SD) generuje negatywne odpowiedzi na zapytania, dla których ma legalną własność. Ten symbol jest definiowany domyślnie.
- **NX_MDNS_ENABLE_IPV6** Zdefiniowane, usługa mDNS/DNS-SD wysyła/przetwarza komunikat mDNS za pośrednictwem adresu IPv6. Ten symbol nie jest domyślnie zdefiniowany.
- **NX_MDNS_IPV6_ADDRESS_COUNT** Maksymalna liczba adresów IPv6 hosta. Wartość domyślna to 2.
- **NX_MDNS_HOST_NAME_MAX** Maksymalny rozmiar ciągu dla nazwy hosta. Wartość domyślna to 64. Nie zawiera terminatora o wartości NULL.
- **NX_MDNS_SERVICE_NAME_MAX** Maksymalny rozmiar ciągu dla nazwy usługi. Wartość domyślna to 64. Nie zawiera terminatora o wartości NULL.
- **NX_MDNS_DOMAIN_NAME_MAX** Maksymalny rozmiar ciągu dla nazwy domeny. Wartość domyślna to 16. Nie zawiera terminatora o wartości NULL.
- **NX_MDNS_CONFLICT_COUNT** Maksymalna liczba konfliktów dla nazwy hosta lub nazwy usługi. Wartość domyślna to 8.
- **NX_MDNS_RR_TTL_HOST** Wartość czasu wygaśnięcia dla rekordów zasobów o nazwie hosta w drugim. Wartość domyślna to 120 dla 120s.
- **NX_MDNS_RR_TTL_OTHER** Wartość czasu wygaśnięcia dla innych rekordów zasobów w drugim. Wartość domyślna to 4500 75 w minutach.
- **NX_MDNS_PROBING_TIMER_COUNT** Przedział czasu (w taktach) między wiadomościami usługi mDNS. Wartość domyślna to 25 taktów dla 250ms.
- **NX_MDNS_ANNOUNCING_TIMER_COUNT** Przedział czasu (w taktach) między komunikatami anonsu mDNS. Wartość domyślna to 25 taktów dla 250ms.
- **NX_MDNS_GOODBYE_TIMER_COUNT** Przedział czasu (w taktach) między powtarzanymi komunikatami "pożegnania". Wartość domyślna to 25 taktów dla 250ms.
- **NX_MDNS_QUERY_MIN_TIMER_COUNT** Minimalny przedział czasu (w taktach) między dwoma zapytaniami. Wartość domyślna to 100 Takty dla 1 sekundy.
- **NX_MDNS_QUERY_MAX_TIMER_COUNT** Maksymalny przedział czasu (w taktach) między dwoma zapytaniami. Wartość domyślna to 360000 przez 60 sekund.
- **NX_MDNS_QUERY_DELAY_MIN** Minimalne opóźnienie wysyłania pierwszego zapytania w taktach. Wartość domyślna to 2 Takty dla 20ms.
- **NX_MDNS_QUERY_DELAY_RANGE** Zakres opóźnienia wysyłania pierwszego zapytania w taktach. Wartość domyślna to 10 taktów dla 100 ms.
- **NX_MDNS_RESPONSE_INTERVAL** Przedział czasu (w taktach) odpowiadający na zapytanie, aby zapewnić interwał co najmniej 1, od ostatniego rekordu multiemisji. Wartość domyślna to 100 taktów.
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT** Przedział czasu (w taktach) odpowiadający na zapytania sondy w celu zapewnienia interwału co najmniej 250ms od ostatniego rekordu multiemisji. Wartość domyślna to 25 taktów.
- **NX_MDNS_RESPONSE_UNIQUE_DELAY** Opóźnienie w taktach w odpowiedzi na zapytanie do usługi, która jest unikatowa dla sieci lokalnej. Wartość domyślna to 1 takt dla 10 ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN** Minimalne opóźnienie w taktach w odpowiedzi na zapytanie do zasobu udostępnionego. Wartość domyślna to 2 Takty dla 20ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE** Zakres opóźnień w taktach w odpowiedzi na zapytanie do zasobu udostępnionego. Wartość domyślna to 10 taktów dla 100 ms.
- **NX_MDNS_RESPONSE_TC_DELAY_MIN** Minimalne opóźnienie w taktach w odpowiedzi na zapytanie z bitem TC. Wartość domyślna to 40 Takty dla 400ms.
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE** Zakres opóźnienia (w taktach) w odpowiedzi na zapytanie z bitem TC. Wartość domyślna to 10 taktów dla 100 ms.
- **NX_MDNS_TIMER_COUNT_RANGE** W przypadku wysyłania odpowiedzi mDNS pakiet zawiera odpowiedzi, które w przeciwnym razie byłyby wysyłane w ramach tego zakresu licznika czasomierza. Zakres liczby czasomierzy jest wyrażony w taktach. Wartość domyślna to 12 dla 120ms. Ta wartość umożliwia odpowiedzi na dołączenie komunikatów, które byłyby wysyłane w ramach następnego zakresu 120ms, jeśli każdy takt jest 10 ms.
- **NX_MDNS_PROBING_RETRANSMIT_COUNT** Liczba przetransmitowanych komunikatów sondy. Wartość domyślna to 3.
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT** Liczba przetransmitowanych komunikatów "pożegnania". Wartość domyślna to 1.
- **NX_MDNS_POOF_MIN_COUNT** Liczba zapytań, które nie odpowiadają na multiemisję, a następnie host może to zrobić jako wskazanie, że rekord nie może być już prawidłowy. Wartość domyślna to 2.
- **NX_MDNS_POOF_TIME_COUNT** Przedział czasu (w taktach) podczas usuwania rekordu z pamięci podręcznej po wyświetleniu dwóch lub więcej z tych zapytań, bez odpowiedzi multiemisji zawierającej oczekiwaną odpowiedź. Wartość domyślna to 1000 Takty przez 10 sekund.
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT** Opóźnienie usuwania rekordu zasobu, gdy czas wygaśnięcia tego rekordu wynosi zero, w taktach wartość domyślna to 100 Takty dla 1 sekundy.
