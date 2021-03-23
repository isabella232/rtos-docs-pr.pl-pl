---
title: Rozdział 2 — Instalowanie i używanie klienta RTO NetX Duo LWM2M
description: W tym rozdziale wyjaśniono, jak zainstalować klienta programu RTO NetX Duo LWM2M i korzystać z niego.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 536225de30f54356157c222917fc904c6aa039fe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821853"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>Rozdział 2 Instalowanie i używanie klienta LWM2M

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta LWM2M.

## <a name="product-distribution"></a>Dystrybucja produktu

Klienta usługi Azure RTO LWM2M można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/) . Pakiet zawiera trzy pliki źródłowe, jeden plik dołączany w następujący sposób.

* plik nagłówkowy **NX \_ lwm2m \_ Client. h** dla klienta lwm2m

* plik źródłowy **NX \_ lwm2m \_ Client. c** c dla klienta lwm2m

* **Demonstracja \_ NetX \_ lwm2m \_ Client. c** c plik źródłowy dla pokazu klienta lwm2m

## <a name="lwm2m-client-installation"></a>Instalacja klienta LWM2M

Klient LWM2M jest częścią NetX Duo. W związku z tym po sklonowaniu NetX Duo z repozytorium GitHub LWM2M Źródło klienta można znaleźć w ***netxduo/dodatków/LWM2M***.

## <a name="using-lwm2m_client"></a>Korzystanie z \_ klienta LWM2M

Korzystanie z klienta LWM2M jest proste. Zasadniczo kod aplikacji musi zawierać polecenie ***NX \_ lwm2m \_ Client. h **_ po* dołączeniu _ _API TX \_ . h_*_ i _*_NX \_ API. h_*_, aby można było użyć ThreadX i NetX. Gdy _*_\_ lwm2m \_ Client. h_*_ jest dołączony, kod aplikacji może następnie wprowadzić wywołania funkcji klienta lwm2m określone w dalszej części tego przewodnika. Aplikacja musi również zaimportować _* _Nx \_ lwm2m \_ Client \_ . \**** Files do biblioteki NetX.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki klienta LWM2M i aplikacji przy użyciu klienta LWM2M istnieje kilka opcji konfiguracji. Opcje konfiguracji można definiować w źródle aplikacji w wierszu polecenia, o ile nie określono inaczej.

| &nbsp;Opcja konfiguracji | Opis |
| --- | --- |
| **\_ \_ Jednostka MTU LWM2M klienta NX \_** | Określa maksymalny rozmiar komunikatu CoAP, w tym nagłówki IP i UDP. Wartość domyślna to 1280. |
| **\_LWM2My \_ klienta w usłudze \_ NX \_** | Typ usługi wymaganej przez protokół UDP LwM2M. Domyślnie ta wartość jest definiowana jako \_ zwykły adres IP NX \_ w celu wskazania normalnej usługi pakietów IP. |
| **\_ \_ \_ Czas wygaśnięcia gniazda klienta NX LWM2M \_** | Określa liczbę routerów, które ten pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80. |
| **\_ \_ \_ \_ Maksymalna liczba kolejek gniazda klienta NX LWM2M \_** | Określa liczbę maksymalnych głębokości kolejki odbierania. Wartość domyślna to 4. |
| **\_ \_ \_ \_ \_ Ścieżka identyfikatora URI LWM2M klienta NX \_ COAP** | Określa liczbę maksymalnych długości opcji Uri-Path CoAP. Wartość domyślna to 32. |
| **\_ \_ \_ Maksymalna liczba \_ błędów urządzenia dla klienta NX LWM2M \_** | Określa maksymalną liczbę kodów błędów przechowywanych przez obiekt urządzenia. Wartość domyślna to 8. |
| **\_ \_ \_ Maksymalna liczba \_ \_ wystąpień zabezpieczeń NX LWM2M klienta** | Określa maksymalną liczbę wystąpień obiektu zabezpieczeń. Wartość domyślna to 2 dla obsługi serwera Bootstrap i serwera standardowego. |
| **\_ \_ \_ Maksymalna liczba \_ wystąpień serwera klienta NX LWM2M \_** | Określa maksymalną liczbę wystąpień obiektów serwera. Wartość domyślna to 1 w przypadku obsługi pojedynczego serwera w warstwie Standardowa. |
| **\_ \_ \_ Maksymalna liczba \_ \_ wystąpień kontroli dostępu dla \_ klienta NX LWM2M** | Określa maksymalną liczbę wystąpień Access Control. Wartość domyślna to 0, co powoduje wyłączenie kontroli dostępu. Jeśli aplikacja obsługuje więcej niż jeden serwer LWM2M, Maksymalna liczba wystąpień Access Control musi być ustawiona na maksymalną liczbę wystąpień obiektów obsługiwanych przez klienta LWM2M, ponieważ należy utworzyć jedno wystąpienie Access Control dla każdego wystąpienia obiektu (z wyjątkiem wystąpień obiektu zabezpieczeń). |
| **\_ \_ \_ Maksymalna liczba \_ \_ list ACL kontroli dostępu \_ klienta NX LWM2M** | Określa maksymalną liczbę zasobów listy ACL na wystąpienie Access Control. Wartość domyślna to 4. |
| **\_ \_ \_ Maksymalne powiadomienia dotyczące klienta NX LWM2M \_** | Określa maksymalną liczbę powiadomień, które będą obsługiwane przez klienta LWM2M. Serwer LWM2M może ustawiać powiadomienia dotyczące obiektów, wystąpień obiektów i zasobów. Wartość domyślna to 8. |
| **\_ \_ \_ Maksymalna liczba zasobów klienta NX LWM2M \_** | Określa maksymalną liczbę zasobów na obiekt. Wartość domyślna to 32. |
| **\_Klient NX LWM2M z maksymalną liczbą \_ \_ \_ \_ zasobów** | Określa maksymalną liczbę wystąpień zasobów dla wielu zasobów. Wartość domyślna to 8. |
| **\_ \_ \_ \_ Czasomierz bezczynności Bootstrap klienta NX LWM2M \_** | Określa maksymalny czas oczekiwania na żądania serwera ładowania początkowego, gdy sesja ładowania początkowego zostanie zainicjowana przed przerwaniem sesji. Wartość domyślna to 60 sekund. |
| **\_ \_ \_ \_ Limit czasu uruchamiania klienta NX LWM2M DTLS \_** | Określa maksymalny czas oczekiwania na zakończenie uzgadniania DTLS. Wartość domyślna to 30 sekund. |
| **\_ \_ \_ \_ Limit czasu zakończenia DTLS klienta NX LWM2M \_** | Określa maksymalny czas oczekiwania na zakończenie zamykania DTLS. Wartość domyślna to 5 sekund. |
| **\_ \_ \_ \_ Maksymalny \_ \_ Identyfikator URI serwera zabezpieczeń NX LWM2M klienta** | Określa maksymalną długość identyfikatora URI serwera, w tym kończący znak null. Wartość domyślna to 128. |
| **\_ \_ \_ \_ Maksymalny \_ \_ klucz publiczny \_ lub \_ tożsamość klienta NX LWM2M** | Określa maksymalną długość klucza publicznego lub tożsamości dla DTLS. Wartość domyślna to 128. |
| **\_ \_ \_ \_ \_ \_ Klucz publiczny serwera zabezpieczeń \_ NX LWM2M klienta** | Określa maksymalną długość klucza publicznego serwera dla DTLS. Wartość domyślna to 128. |
| **\_ \_ \_ \_ Maksymalny \_ klucz tajny zabezpieczeń NX LWM2M klienta \_** | Określa maksymalną długość klucza tajnego dla DTLS. Wartość domyślna to 128. |
| **\_ \_ \_ Wstrzymano klienta NX \_ LWM2M** | Określa liczbę sekund oczekiwania przed inicjacją ładowania początkowego. Wartość domyślna to 1 sekunda. |
| **\_ \_ \_ Czas życia klienta NX \_ LWM2M** | Określa liczbę sekund okresu istnienia rejestracji. Wartość domyślna to 600 sekund. |
