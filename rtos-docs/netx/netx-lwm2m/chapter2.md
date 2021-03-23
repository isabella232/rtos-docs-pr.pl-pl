---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX LWM2M
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika LWM2M usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822603"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX LWM2M

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika LWM2M usługi Azure RTO NetX.

## <a name="product-distribution"></a>Dystrybucja produktu

NetX LWM2M jest dostępny pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Pakiet zawiera trzy pliki źródłowe, jedno dołączane pliki i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nx_lwm2m_client. h**: plik nagłówkowy dla klienta NetX lwm2m

- **nx_lwm2m_ *. c/h**: pliki źródłowe c/h dla NetX lwm2m

- plik źródłowy **demo_netx_lwm2m_client. c**: c dla pokazu klienta NetX lwm2m

- **NetX_LWM2M_User_Guide.pdf**: Opis PDF NetX produktu LWM2M

## <a name="netx-lwm2m-installation"></a>Instalacja LWM2M NetX

Aby można było korzystać z programu NetX LWM2M, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\\ ThreadX \\ ARM7 \\ zielony*", wówczas *&#42; nx_lwm2m. pliki &#42;* powinny zostać skopiowane do tego katalogu.

## <a name="using-netx-lwm2m"></a>Korzystanie z NetX LWM2M

Korzystanie z programu NetX LWM2M jest proste. W zasadzie kod aplikacji musi zawierać *nx_lwm2m_client. h* po zawiera *tx_api. h* i *nx_api. h*, aby można było użyć ThreadX i NetX. Po dołączeniu *nx_lwm2m_client. h* kod aplikacji może następnie wprowadzić wywołania funkcji NetX lwm2m w dalszej części tego przewodnika. Aplikacja musi również zaimportować pliki *nx_lwm2m&#42;. &#42;* do biblioteki NetX.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki klienta LWM2M i aplikacji przy użyciu klienta LWM2M istnieje kilka opcji konfiguracji. Opcje konfiguracji można definiować w źródle aplikacji w wierszu polecenia, o ile nie określono inaczej.

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

Zdefiniowane, usuwa interfejs API podstawowego sprawdzania błędów klienta LWM2M i zwiększa wydajność. Kody powrotne interfejsu API, których nie dotyczy wyłączenie sprawdzania błędów, są wymienione w pogrubionym kroju pisma w definicji interfejsu API.

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

Zdefiniowane, usuwa obsługę liczb zmiennoprzecinkowych. Po wyłączeniu klient LWM2M nie może obsługiwać zasobów z typem danych zmiennoprzecinkowych.

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

Zdefiniowane, usuwa obsługę 64-bitowych liczb zmiennoprzecinkowych. Klient LWM2M nadal może odbierać komunikaty TLV zawierające 64-bitowe liczby zmiennoprzecinkowe, ale wartości są konwertowane na 32-bitowe zmiennoprzecinkowe do przetwarzania.

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

Określa priorytet wątku klienta LWM2M. Domyślnie ta wartość jest definiowana jako 16, aby określić priorytet 16.

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

Określa maksymalną liczbę kodów błędów przechowywanych przez obiekt urządzenia. Wartość domyślna to 8.

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

Określa maksymalną liczbę wystąpień obiektu zabezpieczeń. Wartość domyślna to 2 dla obsługi serwera Bootstrap i serwera standardowego.

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

Określa maksymalną liczbę wystąpień obiektów serwera. Wartość domyślna to 1 w przypadku obsługi pojedynczego serwera w warstwie Standardowa.

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

Określa maksymalną długość identyfikatora URI serwera, włącznie z przerwaniem znaku Nil. Wartość domyślna to 128.

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

Określa maksymalną liczbę wystąpień Access Control. Wartość domyślna to 0, co powoduje wyłączenie kontroli dostępu. Jeśli aplikacja obsługuje więcej niż jeden serwer LWM2M, Maksymalna liczba wystąpień Access Control musi być ustawiona na maksymalną liczbę wystąpień obiektów obsługiwanych przez klienta LWM2M, ponieważ należy utworzyć jedno wystąpienie Access Control dla każdego wystąpienia obiektu (z wyjątkiem wystąpień obiektu zabezpieczeń).

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

Określa maksymalną liczbę zasobów listy ACL na wystąpienie Access Control. Wartość domyślna to 4.

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

Określa maksymalną liczbę powiadomień, które będą obsługiwane przez klienta LWM2M. Serwer LWM2M może ustawiać powiadomienia dotyczące obiektów, wystąpień obiektów i zasobów. Wartość domyślna to 8.

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

Określa maksymalną liczbę zasobów na obiekt. Wartość domyślna to 32.

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

Określa maksymalny czas oczekiwania na żądania serwera ładowania początkowego, gdy sesja ładowania początkowego zostanie zainicjowana przed przerwaniem sesji. Wartość domyślna to 60 sekund.

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

Określa maksymalny czas oczekiwania na zakończenie uzgadniania DTLS. Wartość domyślna to 30 sekund.

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

Określa maksymalny czas oczekiwania na zakończenie zamykania DTLS. Wartość domyślna to 5 sekund.
