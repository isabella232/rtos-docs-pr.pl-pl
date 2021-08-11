---
title: Rozdział 2 — Instalacja i korzystanie z klienta RTOS NetX DUOM2M
description: W tym rozdziale opisano sposób instalowania i używania klienta RTOS NetX Duo ZM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f804ae59dd639ca05d1b8f5251cf8b878e78bb9ad2575e08c21d43b14e727a19
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796518"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>Rozdział 2 Instalacja i korzystanie z klienta SIECIOWAM2M

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika klienta THEM2M.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS klienta ZM2M można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie [https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/) . Pakiet zawiera trzy pliki źródłowe, jeden plik dołączany w następujący sposób.

* **Plik \_ nagłówkowy NXm2m \_ client.h** dla klienta CSVM2M

* **Nx \_ folderm2m \_ client.c** Pliki źródłowe języka C dla klienta ZMIM2M

* **demonstracyjny \_ plik źródłowy \_ netx marksm2m \_ client.c** języka C dla pokazu klienta CSVM2M

## <a name="lwm2m-client-installation"></a>Instalacja klienta SIECIOWA 2M

Klient ZM2M jest częścią usługi NetX Duo. W związku z tym po sklonowaniu aplikacji NetX Duo z repozytorium GitHub źródło klienta JESTM2M można znaleźć na stronie ***netxduo/addons/systemm2m.***

## <a name="using-lwm2m_client"></a>Korzystanie z klienta KOMPUTERA \_ 2M

Korzystanie z klienta KOMPUTERA 2M jest proste. W celu użycia funkcji ThreadX i NetX kod aplikacji musi zawierać ***wartość \_ nxplikaplikacyjm2m client.h* _ po dojściu do niego \_ plików *_*_tx \_ api.h_*_* i _ nx _\_ api.h_*_. Po*_\_ doliciu pliku _nxplikatora \_ nxm2m client.h_ _ kod aplikacji może następnie wykonać wywołania funkcji klienta URZĄDZENIA 2M określone w dalszej części *tego przewodnika. Aplikacja musi również zaimportować pliki .* _nx _ \_ _nx do \_ \_ \**** biblioteki NetX.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki klienta z programem THEM2M i aplikacji przy użyciu klienta THEM2M. Opcje konfiguracji można zdefiniować w źródle aplikacji w wierszu polecenia, chyba że określono inaczej.

| Opcja &nbsp; konfiguracji | Opis |
| --- | --- |
| **MTU KLIENTA \_ NX MIĘDZY \_ JEDNOSTKAMI \_ MTU** | Określa maksymalny rozmiar komunikatu CoAP, w tym nagłówków IP i UDP. Wartość domyślna to 1280. |
| **NX \_ DOSTĘP DO GNIAZDA KLIENTA Z \_ \_ PROCESOREM NXM2M \_** | Typ usługi wymaganej dla dostawcy UDP w programie OdadM2M. Domyślnie ta wartość jest zdefiniowana jako NX \_ IP \_ NORMAL, aby wskazać normalną usługę pakietów IP. |
| **NX \_ PODCZAS ŁADOWANIA GNIAZDA \_ \_ KLIENTA NXM2M \_** | Określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80. |
| **\_NXIZMM2M \_ CLIENT SOCKET QUEUE \_ \_ \_ MAX** | Określa maksymalną głębokość kolejki odbierania. Wartość domyślna to 4. |
| **MAKSYMALNA \_ ŚCIEŻKA \_ \_ \_ \_ URI COAP \_ KLIENTA NXRAPM2M** | Określa liczbę maksymalnych długości opcji Uri-Path CoAP. Wartość domyślna to 32. |
| **BŁĘDY URZĄDZEŃ Z \_ \_ MAKSYMALNYM ROZMIAREM KLIENTA NX NXM2M \_ \_ \_** | Określa maksymalną liczbę kodów błędów przechowywanych przez obiekt urządzenia. Wartość domyślna to 8. |
| **MAKSYMALNA LICZBA WYSTĄPIEŃ ZABEZPIECZEŃ KLIENTA NX \_ POM2M \_ \_ \_ \_** | Określa maksymalną liczbę wystąpień obiektów zabezpieczeń. Wartość domyślna to 2 do obsługi serwera Bootstrap i standardowego serwera. |
| **MAKSYMALNA LICZBA WYSTĄPIEŃ SERWERA \_ KLIENTA NX POM2M \_ \_ \_ \_** | Określa maksymalną liczbę wystąpień obiektów serwera. Wartość domyślna to 1 do obsługi pojedynczego serwera standardowego. |
| **MAKSYMALNA LICZBA WYSTĄPIEŃ KONTROLI DOSTĘPU KLIENTA NX \_ POM2M \_ \_ \_ \_ \_** | Określa maksymalną liczbę Access Control wystąpień. Wartość domyślna to 0, co powoduje wyłączenie kontroli dostępu. Jeśli aplikacja obsługuje więcej niż jeden serwer ZM2M, maksymalną liczbę wystąpień Access Control należy ustawić na maksymalną liczbę wystąpień obiektów, które będzie obsługiwać klient ZMIM2M, ponieważ dla każdego wystąpienia obiektu należy utworzyć jedno wystąpienie Access Control (z wyjątkiem wystąpień obiektów zabezpieczeń). |
| **MAKSYMALNA LICZBA LIST KONTROLI DOSTĘPU KLIENTA NX \_ POM2M \_ \_ \_ \_ \_** | Określa maksymalną liczbę zasobów listy ACL na Access Control Wystąpienie. Wartość domyślna to 4. |
| **MAKSYMALNA \_ LICZBA POWIADOMIEŃ KLIENTA NXŁĄCZYĆ 2M \_ \_ \_** | Określa maksymalną liczbę powiadomień, które będzie obsługiwać klient ZMIM2M. SerwerOWIEM2M może ustawiać powiadomienia dotyczące obiektów, wystąpień obiektów i zasobów. Wartość domyślna to 8. |
| **MAKSYMALNA \_ LICZBA ZASOBÓW KLIENTA NX POM2M \_ \_ \_** | Określa maksymalną liczbę zasobów na obiekt. Wartość domyślna to 32. |
| **MAKSYMALNA \_ LICZBA ZASOBÓW KLIENTA NX POM2M \_ \_ \_ \_** | Określa maksymalną liczbę wystąpień zasobów dla wielu zasobów. Wartość domyślna to 8. |
| **CZASOMIERZ BEZCZYNNY KLIENTA NX \_ PODCZAS \_ ŁADOWANIA \_ \_ \_ POCZĄTKOWEGO** | Określa maksymalny czas oczekiwania na żądania serwera ładowania początkowego, gdy sesja ładowania początkowego jest inicjowana przed przerwaniem sesji. Wartość domyślna to 60 sekund. |
| **LIMIT \_ CZASU ROZPOCZĘCIA USŁUGI DTLS KLIENTA NX \_ \_ \_ \_ POM2M** | Określa maksymalny czas oczekiwania na zakończenie uściślania usługi DTLS. Wartość domyślna to 30 sekund. |
| **LIMIT \_ CZASU ZAKOŃCZENIA DLA USŁUGI DTLS KLIENTA NX PODCZAS \_ \_ \_ \_ 2.02.02** | Określa maksymalny czas oczekiwania na zakończenie zamykania usługi DTLS. Wartość domyślna to 5 sekund. |
| **MAKSYMALNY ROZMIAR URI SERWERA ZABEZPIECZEŃ KLIENTA NX \_ \_ \_ \_ \_ \_ POM2M** | Określa maksymalną długość serwera URI, łącznie z zakończeniem znak null. Wartość domyślna to 128. |
| **MAKSYMALNA LICZBA KLUCZY PUBLICZNYCH LUB TOŻSAMOŚCI ZABEZPIECZEŃ KLIENTA NX \_ MIĘDZY \_ \_ \_ \_ \_ \_ KLUCZEM I \_ TOŻSAMOŚCIĄ KLIENTA NX** | Określa maksymalną długość klucza publicznego lub tożsamości dla usługi DTLS. Wartość domyślna to 128. |
| **MAKSYMALNY KLUCZ PUBLICZNY SERWERA ZABEZPIECZEŃ KLIENTA NX \_ POM2M \_ \_ \_ \_ \_ \_** | Określa maksymalną długość klucza publicznego serwera dla usługi DTLS. Wartość domyślna to 128. |
| **MAKSYMALNA WARTOŚĆ KLUCZA TAJNEGO ZABEZPIECZEŃ KLIENTA NX MIĘDZY KLUCZEM TAJNYM I \_ \_ \_ \_ \_ KLUCZEM \_ ZABEZPIECZEŃ KLIENTA NX** | Określa maksymalną długość klucza tajnego dla usługi DTLS. Wartość domyślna to 128. |
| **KLIENT \_ NX POM2M \_ JEST \_ \_ WSTRZYMYWANY** | Określa liczbę sekund oczekiwania przed zainicjowanie ładowania początkowego. Wartość domyślna to 1 sekunda. |
| **CZAS ŻYCIA KLIENTA \_ NX POM2M \_ \_ \_** | Określa liczbę sekund okresu istnienia rejestracji. Wartość domyślna to 600 sekund. |
