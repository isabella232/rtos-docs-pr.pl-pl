---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo MQTT
description: Pakiet klienta NetX Duo MQTT wymaga zainstalowania, prawidłowego skonfigurowania i utworzenia wystąpienia adresu IP netx Duo (w wersji 5.10 lub nowszej).
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be650186b233d0f1202beecc22f4bd8bc0af4dbe0f677704d09df057fcbc34fc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797742"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo MQTT

## <a name="netx-duo-mqtt-requirements"></a>NetX Duo MQTT Requirements

Pakiet Azure RTOS NetX Duo MQTT wymaga zainstalowania, prawidłowego skonfigurowania i utworzenia wystąpienia ip netx duo (w wersji 5.10 lub nowszej). Moduł TCP musi być włączony w systemie. Ponadto jeśli wymagane są zabezpieczenia TLS, moduł NetX Secure TLS musi być skonfigurowany zgodnie z parametrem zabezpieczeń wymaganym przez brokera.

## <a name="netx-duo-mqtt-specification"></a>Specyfikacja NetX Duo MQTT

Implementacja klienta NetX Duo MQTT jest zgodna z wersją 3.1.1 systemu PIPE MQTT z<sup>29</sup> października 2014 r. Specyfikację można znaleźć w:

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a>Podstawowa operacja NetX Duo MQTT

MQTT (Message Queue Telemetry Transport) jest oparty na modelu wydawca-subskrybent. Klient może publikować informacje dla innych klientów za pośrednictwem brokera. Klient, jeśli interesuje się tematem, może zasubskrybować temat za pośrednictwem brokera. Broker jest odpowiedzialny za dostarczanie opublikowanych komunikatów do swoich klientów, którzy subskrybują temat. W tym modelu wydawcy i subskrybenta wielu klientów może publikować dane z tego samego tematu. Klient otrzyma komunikat, który publikuje, jeśli klient subskrybuje ten sam temat.

W zależności od przypadku użycia klient może wybrać jeden z trzech poziomów QoS podczas publikowania komunikatu:

- **QoS 0:** komunikat jest dostarczany co najwyżej raz. Komunikaty wysyłane z QoS 0 mogą zostać utracone.
- **QoS 1:** komunikat jest dostarczany co najmniej raz. Komunikaty wysyłane za pomocą QoS 1 mogą być dostarczane więcej niż raz.
- **QoS 2:** Komunikat jest dostarczany dokładnie jeden raz. Gwarantuje się, że komunikaty wysyłane za pomocą QoS 2 będą dostarczane bez duplikowania.

> [!NOTE]
> Ta implementacja klienta MQTT nie obsługuje komunikatów QoS poziom 2.

Ponieważ gwarantowane jest zapewnianie jakości usług (QoS 1) i QoS 2, broker śledzi stan komunikatów QoS 1 i QoS 2 wysyłanych do każdego klienta. Jest to szczególnie ważne w przypadku klientów, którzy oczekują komunikatów QoS1 lub QoS 2. Klient może zostać odłączony od brokera (na przykład po ponownym uruchomieniu klienta lub tymczasowej utracie linku komunikacyjnego). Broker musi przechowywać komunikaty QoS 1 i QoS 2, aby komunikaty można było dostarczyć później po ponownym połączeniu klienta z brokerem. Jednak klient może zdecydować, aby nie odbierać żadnych nieaktualnych komunikatów od brokera po ponownym nawiązaniu połączenia. Klient może to zrobić, inicjując połączenie z flagą *clean_session* ustawioną na ***NX_TRUE** _. W takim przypadku po otrzymaniu komunikatu MQTT CONNECT broker odrzuca wszystkie informacje o sesji skojarzone z tym klientem, w tym niezweryfikowane lub niepotwierdzone komunikaty QoS 1 lub QoS 2. Jeśli _flaga clean_session*_ to * NX_FALSE , serwer musi ponownie wysłać komunikaty QoS 1 i QoS 2. Klient MQTT wysyła również ponownie wszystkie nieprzyznane komunikaty, jeśli _clean_session* jest ustawiony na ***NX_TRUE*.** To potwierdzenie różni się od ACK warstwy TCP, chociaż dzieje się tak również. Klient MQTT wysyła potwierdzenie do brokera.

Aplikacja tworzy wystąpienie klienta MQTT przez wywołanie funkcji ***nxd_mqtt_client_create()** _. Po utworzeniu klienta aplikacja może połączyć się z brokerem, wywołując _*_nxd_mqtt_client_connect()._*_ Po nałączeniu się do brokera klient może zasubskrybować temat, wywołując _*_nxd_mqtt_client_subscribe()_*_ lub opublikować temat, wywołując wywołanie _*_nxd_mqtt_client_publish()_**.

Przychodzące komunikaty MQTT są przechowywane w kolejce odbierania w wystąpieniu klienta MQTT. Aplikacja pobiera ten komunikat, wywołując ***nxd_mqtt_client_message_get()***. Jeśli w kolejce odbierania znajdują się komunikaty, pierwszy komunikat (np. najstarszy) z kolejki jest zwracany do wywołującego. Zwracany jest również ciąg tematu z komunikatu.

> [!NOTE]
> Funkcja ***nxd_mqtt_client_message_get()** _ nie blokuje, jeśli kolejka odbioru klienta MQTT jest pusta. Funkcja zwraca natychmiast z kodem powrotu _*_NXD_MQTT_NO_MESSAGE_**. Aplikacja powinna traktować tę wartość zwracaną jako wskazanie, że kolejka odbioru jest pusta, a nie jako błąd.

Aby uniknąć sondowania kolejki odbierania komunikatów przychodzących, aplikacja może zarejestrować funkcję wywołania zwrotnego za pomocą klienta MQTT, wywołując ***funkcję nxd_mqtt_client_recieve_notify_set()***. Funkcja wywołania zwrotnego jest zadeklarowana jako:

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

Gdy klient MQTT odbiera komunikaty z brokera, wywołuje funkcję wywołania zwrotnego, jeśli funkcja jest ustawiona. Funkcja wywołania zwrotnego przekazuje wskaźnik do bloku sterowania klienta i wartość liczby komunikatów. Wartość liczby komunikatów wskazuje liczbę komunikatów MQTT w kolejce odbierania. Należy pamiętać, że ta funkcja wywołania zwrotnego jest wykonywana w kontekście wątku klienta MQTT. W związku z tym funkcja wywołania zwrotnego nie powinna wykonywać żadnych procedur, które mogą blokować wątek klienta MQTT. Funkcja wywołania zwrotnego powinna wyzwalać wątek aplikacji w celu wywołania ***nxd_mqtt_client_message_get() w*** celu pobrania komunikatów.

Aby odłączyć i zakończyć działanie usługi klienta MQTT, aplikacja musi używać usług ***nxd_mqtt_client_disconnect()** _ _*_i nxd_mqtt_client_delete()._*_ Wywołanie _*_nxd_mqtt_client_disconnect()_*_ po prostu rozłącza połączenie TCP z brokerem. Zwalnia komunikaty, które zostały już odebrane i zapisane w kolejce odbierania. Nie zwalnia jednak komunikatów QoS poziomu 1 w kolejce przesyłania. Komunikaty QoS poziomu 1 są ponownie emitowane podczas połączenia przy założeniu, _*_clean_session_*_ flaga usługi jest ustawiona na _ *_NX_FALSE._**

Broker może również rozłączyć się z klientem. Po zakończeniu połączenia TCP między klientem a brokerem aplikacja może zostać powiadomiona przez funkcję powiadamiania o rozłączeniu. Aby użyć mechanizmu powiadomień, aplikacja instaluje funkcję powiadamiania o rozłączeniu, wywołując funkcję ***nxd_mqtt_client_disconnect_notify_set*.** Po zaobserwowaniu rozłączenia protokołu TCP i utworzeniu sesji MQTT wywoływana jest funkcja powiadomień.

Wywołanie ***nxd_mqtt_client_delete()*** zwalnia wszystkie bloki komunikatów w kolejce przesyłania i kolejce odbierania. Usuwane są również nieświadome komunikaty QoS poziomu 1.

## <a name="secure-mqtt-connection"></a>Bezpieczne połączenie MQTT

Klient MQTT umożliwia bezpieczne połączenie z brokerem przy użyciu modułu NetX Secure TLS. Domyślny numer portu dla MQTT z zabezpieczeniami TLS to 8883, zdefiniowany w ***NXD_MQTT_TLS_PORT***.

Aby utworzyć bezpieczne połączenie MQTT z brokerem, należy negocjować sesję protokołu TLS po nawiązaniu połączenia TCP, zanim komunikaty MQTT CONNECT będą wysyłane do brokera. Konfigurowanie sesji TLS jest realizowane przez wywołanie ***nxd_mqtt_client_secure_connect()*** i przekazanie zdefiniowanej przez użytkownika funkcji wywołania zwrotnego konfiguracji TLS. Podczas fazy połączenia protokołu MQTT po nawiązaniu połączenia TCP klient wywołuje funkcję wywołania zwrotnego konfiguracji protokołu TLS w celu uruchomienia odpowiedniego procesu uściśniania protokołu TLS. Po nawiązyniu sesji TLS klient kontynuuje komunikat MQTT CONNECT za pośrednictwem bezpiecznego kanału.

Funkcja wywołania zwrotnego zdefiniowana przez użytkownika przyjmuje pięć wartości wejściowych i jest zadeklarowana jako:

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

Poniżej znajduje się opis parametrów wejściowych:

- **client_ptr:** wskaźnik do bloku sterowania klienta MQTT.
- **session_ptr:** wskaźnik do bloku kontroli sesji TLS.
- **certificate_ptr:** wskaźnik do bloku kontroli certyfikatu. Funkcja konfiguracji konfiguruje ten certyfikat przed wysłaniem go do brokera.
- **trusted_certificate_ptr:** wskaźnik do zaufanego certyfikatu. Funkcja konfiguracji TLS konfiguruje zaufany certyfikat do uwierzytelniania serwera.

W funkcji konfiguracji TLS aplikacja jest odpowiedzialna za tworzenie sesji TLS i konfigurowanie sesji przy użyciu odpowiedniego certyfikatu. Poniższy kod przykładowy przedstawia typową procedurę uruchamiania sesji TLS. Czytelnik jest określany w Podręczniku użytkownika bezpiecznego TLS NetX, aby uzyskać szczegółowe informacje na temat korzystania z interfejsów API TLS.

Poniżej znajduje się przykład wywołania zwrotnego konfiguracji TLS:

```c
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_pt
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certrifcate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate_ptr)
{
    /* Initialize TLS module */
    nx_secure_tls_initialize();

    /* Create a TLS session */
    nx_secure_tls_session_create(session_ptr, …);

    /* Need to allocate space for the certificate coming in from the broker. */
    memset(certificate_ptr), 0, sizeof(NX_SECURE_TLS_CERTIFICATE));

    nx_secure_tls_remote_certificate_allocate(session_ptr, certificate_ptr);

    /* Add a CA Certificate to our trusted store for verifying incomingserver certificates. */
    nx_secure_tls_certificate_initialize(
        trusted_certificate_ptr,
        ca_cert_der,
        ca_cert_der_len, NULL, 0);
    nx_secure_tls_trusted_certificate_add(session_ptr,
        trusted_certificate));
}
```

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a>Znane ograniczenia klienta NetX Duo MQTT

- NetX Duo MQTT nie obsługuje wysyłania ani odbierania komunikatów QoS poziomu 2.
- NetX Duo MQTT nie obsługuje pakietów łańcuchowych.
