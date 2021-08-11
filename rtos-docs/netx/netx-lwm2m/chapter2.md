---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS NetX CELUM2M
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS NetX CELUM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ad8963c342e907201074559929f3a7a2d70c9f13e135cd95c9a2e9b224e17cf
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791231"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS NetX CELUM2M

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS NetX CELUM2M.

## <a name="product-distribution"></a>Dystrybucja produktów

NetX CELUM2M jest dostępny na stronie [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Pakiet zawiera trzy pliki źródłowe, jeden plik dołączany i plik PDF zawierający ten dokument w następujący sposób:

- **nx_lwm2m_client.h:** plik nagłówkowy klienta NETX CSVM2M

- **nx_lwm2m_*.c/h:** pliki źródłowe C/H dla NetX MARKSM2M

- **demo_netx_lwm2m_client.c:** Plik źródłowy języka C dla pokazu klienta NETX CSVM2M

- **NetX_LWM2M_User_Guide.pdf:** opis PDF produktu NetX CELUM2M

## <a name="netx-lwm2m-installation"></a>Instalacja systemu NetX MARKSM2M

Aby można było korzystać z systemu NetX LISTM2M, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX. Jeśli na przykład netx jest zainstalowany w katalogu *\\ "threadx \\ arm7 \\ green",* pliki *nx_lwm2m&#42;.&#42;* powinny zostać skopiowane do tego katalogu.

## <a name="using-netx-lwm2m"></a>Korzystanie z NetX MARKSM2M

Korzystanie z systemu NetX MARKSM2M jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_lwm2m_client.h,* gdy zawiera on elementy *tx_api.h* i *nx_api.h,* aby można było używać threadX i NetX. Po *nx_lwm2m_client.h* kod aplikacji może następnie wykonać wywołania funkcji NetX QRM2M określone w dalszej części tego przewodnika. Aplikacja musi również zaimportować *pliki nx_lwm2m&#42;.&#42;* do biblioteki NetX.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki klienta KLASTRA 2M i aplikacji przy użyciu klienta THEM2M. Opcje konfiguracji można zdefiniować w źródle aplikacji w wierszu polecenia, chyba że określono inaczej.

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

Zdefiniowano , usuwa podstawowy interfejs API sprawdzania błędów klienta PODCZASM2M i zwiększa wydajność. Kody powrotne interfejsu API, na które nie ma wpływu wyłączenie sprawdzania błędów, są wyświetlane pogrubioną czcionką w definicji interfejsu API.

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

Zdefiniowano , usuwa obsługę wartości liczb zmiennoprzecinków. Po wyłączeniu klient THEM2M nie może obsługiwać zasobów z typem danych Float.

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

Zdefiniowano , usuwa obsługę 64-bitowych wartości liczb zmiennoprzecinków. Klient THEM2M może nadal odbierać komunikaty TLV zawierające 64-bitowe liczby zmiennoprzecinające, ale wartości są konwertowane na 32-bitowy zmiennoprzecinek do przetwarzania.

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

Określa priorytet wątku klienta THEM2M. Domyślnie ta wartość jest zdefiniowana jako 16, aby określić priorytet 16.

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

Określa maksymalną liczbę kodów błędów przechowywanych przez obiekt urządzenia. Wartość domyślna to 8.

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

Określa maksymalną liczbę wystąpień obiektów zabezpieczeń. Wartość domyślna to 2 dla obsługi serwera Bootstrap i standardowego serwera.

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

Określa maksymalną liczbę wystąpień obiektów serwera. Wartość domyślna to 1 do obsługi jednego serwera standardowego.

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

Określa maksymalną długość serwera URI, łącznie z zakończeniem zero znaku. Wartość domyślna to 128.

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

Określa maksymalną liczbę wystąpień Access Control Wystąpienia. Wartość domyślna to 0, co wyłącza kontrolę dostępu. Jeśli aplikacja obsługuje więcej niż jeden serwer THEM2M, maksymalna liczba wystąpień Access Control musi być ustawiona na maksymalną liczbę wystąpień obiektów, które będzie obsługiwać klient DSM2M, ponieważ dla każdego wystąpienia obiektu należy utworzyć jedno wystąpienie Access Control (z wyjątkiem wystąpień obiektów zabezpieczeń).

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

Określa maksymalną liczbę zasobów listy ACL na wystąpienie Access Control ACL. Wartość domyślna to 4.

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

Określa maksymalną liczbę powiadomień, które będzie obsługiwać klient THEM2M. Serwer DHCPM2M może ustawiać powiadomienia dotyczące obiektów, wystąpień obiektów i zasobów. Wartość domyślna to 8.

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

Określa maksymalną liczbę zasobów na obiekt. Wartość domyślna to 32.

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

Określa maksymalny czas oczekiwania na żądania serwera ładowania początkowego, gdy sesja bootstrap jest inicjowana przed przerwaniem sesji. Wartość domyślna to 60 sekund.

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

Określa maksymalny czas oczekiwania na ukończenie procesu uściślania dtls. Wartość domyślna to 30 sekund.

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

Określa maksymalny czas oczekiwania na ukończenie zamykania usługi DTLS. Wartość domyślna to 5 sekund.
