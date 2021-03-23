---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo MQTT
description: Pakiet klienta NetX Duo MQTT wymaga zainstalowania programu NetX Duo (w wersji 5,10 lub nowszej), prawidłowej konfiguracji i utworzenia wystąpienia adresu IP.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e13b997f987e2fd82569bcb1904218908313d70
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821816"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo MQTT

## <a name="netx-duo-mqtt-requirements"></a>NetX Duo MQTT wymagania

Pakiet klienta platformy Azure RTO NetX Duo MQTT wymaga, aby NetX Duo (wersja 5,10 lub nowsza) była zainstalowana, prawidłowo skonfigurowana, a wystąpienie adresu IP zostało utworzone. W systemie musi być włączony moduł TCP. Ponadto, jeśli wymagane jest zabezpieczenie protokołu TLS, moduł bezpiecznego protokołu TLS NetX musi być skonfigurowany zgodnie z parametrem zabezpieczeń wymaganym przez brokera.

## <a name="netx-duo-mqtt-specification"></a>Specyfikacja NetX Duo MQTT

Implementacja klienta NetX Duo MQTT jest zgodna z języka Oasis MQTT wersja 3.1.1 KTZ 29<sup>th</sup> 2014. Specyfikację można znaleźć w:

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a>NetX Duo MQTT — operacja podstawowa

MQTT (transport telemetrii kolejki komunikatów) jest oparty na modelu subskrybentów wydawcy. Klient może publikować informacje na innych klientach za pośrednictwem brokera. Klient, Jeśli interesuje temat, może subskrybować temat za pośrednictwem brokera. Broker jest odpowiedzialny za dostarczanie opublikowanych komunikatów do klientów, którzy subskrybują ten temat. W tym modelu subskrybenta wydawcy, wielu klientów może publikować dane w tym samym temacie. Klient otrzyma komunikat publikowany, jeśli klient subskrybuje ten sam temat.

W zależności od przypadku użycia klient może wybrać jeden z trzech poziomów QoS podczas publikowania wiadomości:

- **Jakość** usług (QoS) 0: komunikat jest dostarczany najwyżej raz. Komunikaty wysyłane z użyciem QoS 0 mogą zostać utracone.
- **QoS 1**: komunikat jest dostarczany co najmniej raz. Komunikaty wysyłane za pomocą usługi QoS 1 mogą być dostarczane więcej niż raz.
- **Jakość** usług (QoS) 2: komunikat jest dostarczany dokładnie jeden raz. Komunikaty wysyłane z użyciem usługi QoS 2 są gwarantowane, bez duplikowania.

> [!NOTE]
> Ta implementacja klienta MQTT nie obsługuje komunikatów poziomu 2 usług QoS.

Ponieważ usługi QoS 1 i QoS 2 mają być dostarczone, Broker śledzi stan komunikatów QoS 1 i QoS 2 wysyłanych do każdego klienta. Jest to szczególnie ważne w przypadku klientów, którzy oczekują komunikatów QoS1 lub QoS 2. Klient może zostać odłączony od brokera (na przykład po ponownym uruchomieniu klienta lub łącze komunikacji). Broker musi przechowywać komunikaty QoS 1 i QoS 2, aby komunikaty mogły być dostarczane później po ponownym połączeniu klienta z brokerem. Jednak klient może zrezygnować z nieodebrania żadnych starych komunikatów z brokera po ponownej nawiązaniu połączenia. Klient może to zrobić przez zainicjowanie połączenia z flagą *clean_session* ustawioną na ***NX_TRUE** _. W takim przypadku po odebraniu komunikatu MQTT CONNECT Broker odrzuca wszystkie informacje o sesji skojarzone z tym klientem, w tym niedostarczone lub niepotwierdzone komunikaty QoS 1 lub QoS 2. Jeśli _flaga clean_session * ma wartość ***NX_FALSE**_, serwer wysyła ponownie komunikaty QoS 1 i QoS 2. Klient MQTT również ponownie wysyła wszystkie niepotwierdzone komunikaty, jeśli _clean_session * jest ustawiona na ***NX_TRUE *.** To potwierdzenie jest inne niż potwierdzenie warstwy protokołu TCP, chociaż taka sytuacja występuje również. Klient MQTT wysyła potwierdzenie do brokera.

Aplikacja tworzy wystąpienie klienta MQTT przez wywołanie ***nxd_mqtt_client_create ()** _. Po utworzeniu klienta aplikacja może połączyć się z brokerem, wywołując _*_nxd_mqtt_client_connect ()_*_. Po nawiązaniu połączenia z brokerem klient może subskrybować temat poprzez wywołanie _*_nxd_mqtt_client_subscribe ()_*_ lub opublikowanie tematu przez wywołanie _ *_nxd_mqtt_client_publish ()_* *.

Przychodzące komunikaty MQTT są przechowywane w kolejce odbierania w wystąpieniu klienta MQTT. Aplikacja pobiera te komunikaty, wywołując ***nxd_mqtt_client_message_get ()***. W przypadku komunikatów w kolejce odbierania pierwszy komunikat (np. najstarsze) z kolejki jest zwracany do obiektu wywołującego. Zwracany jest również ciąg tematu z komunikatu.

> [!NOTE]
> Funkcja ***nxd_mqtt_client_message_get ()** _ nie blokuje, jeśli kolejka odbierania MQTT klienta jest pusta. Funkcja wraca bezpośrednio z kodem powrotnym _ *_NXD_MQTT_NO_MESSAGE_* *. Aplikacja traktuje tę wartość zwracaną jako wskazanie, że kolejka odbierania jest pusta, a nie błędu.

Aby uniknąć sondowania kolejki odbierania dla wiadomości przychodzących, aplikacja może zarejestrować funkcję wywołania zwrotnego za pomocą klienta MQTT przez wywołanie ***nxd_mqtt_client_recieve_notify_set ()***. Funkcja wywołania zwrotnego jest zadeklarowana jako:

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

Gdy klient MQTT odbiera komunikaty z brokera, wywołuje funkcję wywołania zwrotnego, jeśli funkcja jest ustawiona. Funkcja wywołania zwrotnego przekazuje wskaźnik do bloku kontroli klienta i wartość liczby komunikatów. Wartość liczby komunikatów wskazuje liczbę komunikatów MQTT w kolejce odbierania. Należy zauważyć, że ta funkcja wywołania zwrotnego jest wykonywana w kontekście wątku klienta MQTT. W związku z tym funkcja wywołania zwrotnego nie powinna wykonywać żadnych procedur, które mogą blokować wątek klienta MQTT. Funkcja wywołania zwrotnego powinna wyzwolić wątek aplikacji, aby wywoływać ***nxd_mqtt_client_message_get ()*** w celu pobrania komunikatów.

Aby rozłączyć i zakończyć usługę klienta MQTT, aplikacja używa usługi ***nxd_mqtt_client_disconnect ()** _ i _*_nxd_mqtt_client_delete ()._*_ Wywołanie _*_nxd_mqtt_client_disconnect ()_*_ po prostu ROZŁĄCZA połączenie TCP z brokerem. Zwalnia komunikaty już odebrane i przechowywane w kolejce odbierania. Nie powoduje to jednak zwolnienia komunikatów poziomu 1 usługi QoS w kolejce transmisji. Komunikaty poziomu 1 usługi QoS są przesyłane ponownie po nawiązaniu połączenia, przy założeniu, że flaga _*_clean_session_*_ ma wartość _ *_NX_FALSE._**

Broker może także rozłączyć się z klientem. Gdy połączenie TCP między klientem i brokerem zostanie zakończone, aplikacja może zostać powiadomiona przez funkcję powiadamiania o rozłączeniu. Aby można było korzystać z mechanizmu powiadamiania, aplikacja instaluje funkcję odłączania powiadomienia przez wywołanie ***nxd_mqtt_client_disconnect_notify_set *.** Po rozłączeniu protokołu TCP i utworzeniu sesji MQTT zostaje wywołana funkcja powiadomień.

Wywołanie ***nxd_mqtt_client_delete ()*** zwalnia wszystkie bloki komunikatów w kolejce transmisji i w kolejce odbierania. Niepotwierdzone komunikaty poziomu 1 usługi QoS również są usuwane.

## <a name="secure-mqtt-connection"></a>Bezpieczne połączenie MQTT

Klient MQTT nawiązuje bezpieczne połączenie z brokerem przy użyciu modułu NetX Secure TLS. Domyślny numer portu dla MQTT z zabezpieczeniami TLS to 8883, zdefiniowany w ***NXD_MQTT_TLS_PORT***.

Aby można było utworzyć bezpieczne połączenie usługi MQTT z brokerem, należy wynegocjować sesję protokołu TLS po nawiązaniu połączenia TCP przed wysłaniem komunikatów MQTT CONNECT do brokera. Konfiguracja sesji TLS odbywa się przez wywołanie ***nxd_mqtt_client_secure_connect ()*** i przekazanie funkcji wywołania zwrotnego konfiguracji protokołu TLS zdefiniowanej przez użytkownika. W fazie połączenia usługi MQTT po nawiązaniu połączenia TCP klient wywołuje funkcję wywołania zwrotnego konfiguracji protokołu TLS w celu uruchomienia odpowiedniego procesu uzgadniania protokołu TLS. Po ustanowieniu sesji TLS klient kontynuuje komunikat MQTT CONNECT za pośrednictwem bezpiecznego kanału.

Funkcja wywołania zwrotnego zdefiniowanego przez użytkownika przyjmuje pięć wartości wejściowych i jest zadeklarowana jako:

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

Poniżej znajduje się opis parametrów wejściowych:

- **client_ptr**: wskaźnik do bloku kontroli klienta MQTT.
- **session_ptr**: wskaźnik do bloku sterowania sesją TLS.
- **certificate_ptr**: wskaźnik do bloku kontroli certyfikatu. Funkcja instalacji konfiguruje ten certyfikat przed wysłaniem go do brokera.
- **trusted_certificate_ptr**: wskaźnik do zaufanego certyfikatu. Funkcja konfiguracji protokołu TLS konfiguruje zaufany certyfikat w celu uwierzytelnienia serwera.

W funkcji konfiguracji protokołu TLS aplikacja jest odpowiedzialna za tworzenie sesji TLS i Konfigurowanie sesji przy użyciu odpowiedniego certyfikatu. Poniższy pseudo kod zawiera opis typowej procedury uruchamiania sesji TLS. Czytelnik odwołuje się do podręcznika użytkownika usługi NetX Secure TLS, aby uzyskać szczegółowe informacje na temat korzystania z interfejsów API protokołu TLS.

Poniżej znajduje się przykładowe wywołanie zwrotne konfiguracji protokołu TLS:

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

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a>Znane ograniczenia dotyczące klienta NetX Duo MQTT

- NetX Duo MQTT nie obsługuje wysyłania ani otrzymywania komunikatów poziomu 2 usług QoS.
- NetX Duo MQTT nie obsługuje pakietów łańcucha.
