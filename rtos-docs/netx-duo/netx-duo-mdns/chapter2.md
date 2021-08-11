---
title: Rozdział 2 — Instalowanie i używanie sieci mDNS
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfigurowaniem i użyciem modułu NetX Duo mDNS.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b27671f82c100db4e6a70a568e8a68f14b3ab45e3a33f46dd1f2e1852010f500
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796433"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>Rozdział 2 — Instalowanie i używanie sieci mDNS

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfigurowaniem i użyciem modułu NetX Duo mDNS.

## <a name="product-distribution"></a>Dystrybucja produktów

Sieć mDNS NetX Duo jest dostępna pod witrynie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe i plik PDF zawierający ten dokument w następujący sposób:

- **nxd_mdns.h** Plik nagłówkowy modułu mDNS NetX Duo
- **nxd_mdns.c** Plik źródłowy języka C dla modułu mDNS NetX Duo
- **nxd_mdns.pdf** Opis w formacie PDF mDNS for NetX Duo
- **demo_netxduo_mdns.c** Prosty program demonstracyjny, który ilustruje usługi udostępniane przez sieci mDNS.

## <a name="netx-duo-mdns-installation"></a>Instalacja sieci mDNS NetX Duo

Aby można było korzystać z interfejsów API mDNS NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo. Jeśli na przykład netX Duo jest zainstalowany w katalogu *"c:\netxduo",* to do tego katalogu powinny zostać skopiowane pliki *nxd_mdns.h* i *nxd_mdns.c.*

## <a name="using-netx-duo-mdns"></a>Korzystanie z sieci mDNS NetX Duo

Korzystanie z modułu mDNS NetX Duo jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nxd_mdns.h* po dołączyć elementy *tx_api.h* i *nx_api.h*, aby można było używać odpowiednio threadX i NetX Duo. Projekt kompilacji musi zawierać kod źródłowy mDNS i plik aplikacji oraz oczywiście pliki bibliotek ThreadX i NetX. To wszystko, co jest wymagane do korzystania z sieci mDNS NetX Duo.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia modułu mDNS NetX Duo. Zostaną wyświetlone wartości domyślne, ale każda z nich może zostać ustawiona przez aplikację przed dodaniem określonego pliku nagłówkowego mDNS NetX Duo. Na poniższej liście szczegółowo opisano poszczególne z nich:

- **NX_MDNS_DISABLE_SERVER** Wyłącza funkcjonalność serwera mDNS/DNS-SD. Bez funkcjonalności serwera moduł mDNS/DNS-SD nie ogłasza usług dostarczanych przez hosta lokalnego ani nie odpowiada na błędy mDNS. Ten symbol nie jest zdefiniowany domyślnie.
- **NX_MDNS_DISABLE_CLIENT** Wyłącza funkcjonalność klienta mDNS/DNS-SD. Bez funkcjonalności klienta mDNS/DNS-SD nie wysyła zapytań ani nie obsługuje odpowiedzi na zapytania mDNS odebranych za pośrednictwem sieci.
- **NX_MDNS_ENABLE_ADDRESS_CHECK** Zdefiniowany moduł mDNS sprawdza poprawność adresów (adres źródłowy, adres docelowy i numery portów) z odebranych komunikatów mDNS. Ten symbol jest zdefiniowany domyślnie.
- **NX_MDNS_ENABLE_CLIENT_POOF** Zdefiniowany moduł mDNS wykonuje pasywną obserwację awarii. Klient mDNS /DNS_SD (querier) obserwuje zapytania multiemisji wydane przez inne hosty w sieci. Ten symbol jest zdefiniowany domyślnie.
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES** Zdefiniowane, serwer mDNS /DNS-SD (responder) generuje negatywne odpowiedzi na zapytania, dla których ma prawo własności. Ten symbol jest zdefiniowany domyślnie.
- **NX_MDNS_ENABLE_IPV6** Zdefiniowano komunikat mDNS/DNS-SD wysyłania/przetwarzania mDNS za pośrednictwem adresu IPv6. Ten symbol nie jest zdefiniowany domyślnie.
- **NX_MDNS_IPV6_ADDRESS_COUNT** Maksymalna liczba adresów IPv6 hosta. Wartość domyślna to 2.
- **NX_MDNS_HOST_NAME_MAX** Maksymalny rozmiar ciągu dla nazwy hosta. Wartość domyślna to 64. Nie zawiera terminatora NULL.
- **NX_MDNS_SERVICE_NAME_MAX** Maksymalny rozmiar ciągu dla nazwy usługi. Wartość domyślna to 64. Nie zawiera terminatora NULL.
- **NX_MDNS_DOMAIN_NAME_MAX** Maksymalny rozmiar ciągu dla nazwy domeny. Wartość domyślna to 16. Nie zawiera terminatora NULL.
- **NX_MDNS_CONFLICT_COUNT** Maksymalna liczba konfliktów dla nazwy hosta lub nazwy usługi. Wartość domyślna to 8.
- **NX_MDNS_RR_TTL_HOST** Wartość TTL rekordów zasobów z nazwą hosta w sekundach. Wartość domyślna to 120 dla 120.
- **NX_MDNS_RR_TTL_OTHER** Wartość TTL dla innych rekordów zasobów, w sekundach. Wartość domyślna to 4500 przez 75 minut.
- **NX_MDNS_PROBING_TIMER_COUNT** Przedział czasu, w taktach, między komunikatami sondowania mDNS. Wartość domyślna to 25 takt dla 250 min.
- **NX_MDNS_ANNOUNCING_TIMER_COUNT** Przedział czasu, w taktach, między komunikatami anonsów mDNS. Wartość domyślna to 25 takt dla 250 min.
- **NX_MDNS_GOODBYE_TIMER_COUNT** Przedział czasu, w taktach, między powtórzonymi komunikatami "do widzenia". Wartość domyślna to 25 takt dla 250 min.
- **NX_MDNS_QUERY_MIN_TIMER_COUNT** Minimalny interwał czasu, w taktach, między dwoma zapytaniami. Wartość domyślna to 100 takt dla 1 sekundy.
- **NX_MDNS_QUERY_MAX_TIMER_COUNT** Maksymalny interwał czasu, w taktach, między dwoma zapytaniami. Wartość domyślna to 360000 przez 60 sekund.
- **NX_MDNS_QUERY_DELAY_MIN** Minimalne opóźnienie wysyłania pierwszego zapytania, w taktach. Wartość domyślna to 2 takty dla 20ms.
- **NX_MDNS_QUERY_DELAY_RANGE** Zakres opóźnień dla wysyłania pierwszego zapytania, w taktach. Wartość domyślna to 10 takt dla 100ms.
- **NX_MDNS_RESPONSE_INTERVAL** Przedział czasu, w taktach, w odpowiadaniu na zapytanie w celu zapewnienia interwału co najmniej 1s od czasu ostatniego multiemisji rekordu. Wartość domyślna to 100 takt.
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT** Interwał czasu odpowiedzi na zapytania sondy w celu zapewnienia interwału co najmniej 250ms od czasu ostatniego multiemisji rekordu. Wartość domyślna to 25 takt.
- **NX_MDNS_RESPONSE_UNIQUE_DELAY** Opóźnienie w taktach w odpowiadaniu na zapytanie do usługi, która jest unikatowa dla sieci lokalnej. Wartość domyślna to 1 znacznik dla 10ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN** Minimalne opóźnienie, w taktach, w odpowiadaniu na zapytanie do udostępnionego zasobu. Wartość domyślna to 2 takty dla 20ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE** Zakres opóźnień, w taktach, w odpowiedzi na zapytanie do udostępnionego zasobu. Wartość domyślna to 10 takt dla 100ms.
- **NX_MDNS_RESPONSE_TC_DELAY_MIN** Minimalne opóźnienie w taktach w odpowiadaniu na zapytanie za pomocą bitu TC. Wartość domyślna to 40 takt dla 400ms.
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE** Zakres opóźnień, w taktach, w odpowiadaniu na zapytanie za pomocą bitu TC. Wartość domyślna to 10 takt dla 100ms.
- **NX_MDNS_TIMER_COUNT_RANGE** Podczas wysyłania odpowiedzi mDNS pakiet zawiera odpowiedzi, które w przeciwnym razie byłyby wysyłane w tym zakresie licznika czasomierza. Zakres liczby czasomierzy jest wyrażony w taktach. Wartość domyślna to 12 dla 120ms. Ta wartość umożliwia dołącznie odpowiedzi do komunikatów, które zostaną wysłane w ciągu następnych 120ms zakres, jeśli każdy znacznik jest 10ms.
- **NX_MDNS_PROBING_RETRANSMIT_COUNT** Liczba ponownie emitowanych komunikatów sondowania. Wartość domyślna to 3.
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT** Liczba ponownie emitowanych komunikatów "do widzenia". Wartość domyślna to 1.
- **NX_MDNS_POOF_MIN_COUNT** Liczba zapytań, które nie odpowiedzi multiemisji, a następnie hosta może przyjąć jako wskazanie, że rekord może już nie być prawidłowy. Wartość domyślna to 2.
- **NX_MDNS_POOF_TIME_COUNT** Przedział czasu w taktach podczas usuwania rekordu z pamięci podręcznej po zobaczeniu co najmniej dwóch z tych zapytań i bez odpowiedzi multiemisji zawierającej oczekiwaną odpowiedź. Wartość domyślna to 1000 taktów przez 10 sekund.
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT** Opóźnienie usuwania rekordu zasobu, gdy czas wygaśnięcia tego rekordu wynosi zero, w taktach wartość domyślna to 100 takt przez 1 sekundę.
