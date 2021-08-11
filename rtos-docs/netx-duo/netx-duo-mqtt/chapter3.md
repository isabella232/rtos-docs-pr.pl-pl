---
title: Rozdział 3 — opis Azure RTOS klienta NetX Duo MQTT
description: Ten rozdział zawiera opis wszystkich usług klienta NetX Duo MQTT (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cc08f7c0dceb84d5843e25384275557d2871e3546d90579aab006119a2d9980c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797521"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>Rozdział 3 — Opis Azure RTOS klienta NetX Duo MQTT

Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX Duo MQTT (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nxd_mqtt_client_create** *tworzenie wystąpienia klienta MQTT*
- **nxd_mqtt_client_will_message_set** *ustawić komunikat will*
- **nxd_mqtt_client_client_login_set** *ustawić nazwę użytkownika i hasło logowania klienta MQTT*
- **nxd_mqtt_client_connect** *Połączenie klienta MQTT do brokera*
- **nxd_mqtt_client_secure_connect** *Połączenie MQTT do brokera z zabezpieczeniami TLS*
- **nxd_mqtt_client_publish** *publikowanie komunikatu za pośrednictwem brokera.*
- **nxd_mqtt_client_subscribe** *Subskrybowanie tematu*
- **nxd_mqtt_client_unsubscribe** *anuluj subskrypcję tematu*
- **nxd_mqtt_client_receive_notify_set** ustawić funkcję wywołania zwrotnego powiadomienia o odbierania *komunikatu MQTT*
- **nxd_mqtt_client_message_get** *pobieranie komunikatu z brokera*
- **nxd_mqtt_client_disconnect_notify_set** ustawić funkcję wywołania zwrotnego powiadomienia o rozłączeniu *komunikatu MQTT*
- **nxd_mqtt_client_disconnect** *odłącz klienta MQTT od brokera*
- **nxd_mqtt_client_delete** *usuwanie wystąpienia klienta MQTT*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

Tworzenie wystąpienia klienta MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta MQTT w określonym wystąpieniu adresu IP. Ciąg *client_id* jest przekazywany do serwera w fazie połączenia MQTT jako *identyfikator klienta (ClientId).* Tworzy również niezbędne zasoby ThreadX (wątek zadania klienta MQTT, mutex, grupa flag zdarzeń i gniazdo TCP).

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **client_name** Ciąg nazwy klienta.
- **client_id** Ciąg identyfikatora klienta używany podczas fazy połączenia. Broker MQTT używa tego client_id do unikatowego identyfikowania klienta.
- **client_id_length** Długość ciągu identyfikatora klienta w bajtach.
- **ip_ptr** Wskaźnik do wystąpienia adresu IP.
- **pool_ptr** Wskaźnik do puli pakietów używany przez klienta MQTT do jego działania.
- **stack_ptr** Obszar stosu dla wątku klienta MQTT.
- **stack_size** Rozmiar obszaru stosu w bajtach.
- **mqtt_thread_priority** Priorytet wątku MQTT.
- **memory_ptr** Przestarzałe. Nie jest już używany.
- **memory_size** Przestarzałe. Nie jest już używany.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie utworzono klienta MQTT.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Wewnętrzny błąd logiki
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik puli pakietów, blok ip_ptr MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowy ciąg tematu, will_retrain_flag lub will_QoS tematu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a>nxd_mqtt_client_will_message_set

Ustawia komunikat Will

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a>Opis

Ta usługa ustawia opcjonalny temat will i będzie wysyłać komunikat, zanim klient połączy się z serwerem. Temat Will musi być ciągiem zakodowanym w formacie UTF-8.

Komunikat będzie, jeśli zostanie ustawiony, jest przesyłany do brokera jako część komunikatu CONNECT. W związku z tym aplikacja, która chce użyć usługi , musi użyć tej usługi przed nawiązaniu połączenia MQTT.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **will_topic** Kodowanie UTF-8 spowoduje ciąg tematu. Temat Will musi być obecny. Wywołujący musi zachować will_topic prawidłowy do momentu nx_mqtt_client_connect *wywołania.*
- **will_topic_length** Liczba bajtów w ciągu tematu will
- **will_message** Komunikat zostanie wyświetlony przez zdefiniowaną przez aplikację. Jeśli komunikat będzie nie jest wymagany, aplikacja może ustawić to pole *na wartość NX_NULL.*
- **will_message_length** Liczba bajtów w ciągu komunikatu will. Jeśli will_message ustawiono wartość NULL, will_message_length musi być ustawiona na 0.
- **will_retain_flag** Określa, czy serwer publikuje komunikat będzie wyświetlany jako zachowany komunikat. Prawidłowe wartości to *NX_TRUE* lub *NX_FALSE.*
- **will_QoS** Wartość QoS używana przez serwer podczas wysyłania komunikatu będzie. Prawidłowe wartości to 0 lub 1.  

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie ustawia komunikat will.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) komunikatów QoS poziom 2 nie są obsługiwane.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok kontrolek MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowy ciąg tematu, will_retrain_flag lub will_QoS tematu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a>nxd_mqtt_client_login_set

Ustawia nazwę użytkownika i hasło logowania klienta MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>Opis

Ta usługa ustawia nazwę użytkownika i hasło, które są używane podczas fazy połączenia MQTT na potrzeby uwierzytelniania logowania.

Identyfikator logowania klienta MQTT z nazwą użytkownika i hasłem jest opcjonalny. W sytuacjach, gdy serwer wymaga nazwy użytkownika i hasła, przed nawiązaniu połączenia należy ustawić nazwę użytkownika i hasło.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **nazwa użytkownika** Ciąg nazwy użytkownika zakodowany w formacie UTF-8. Wywołujący musi zachować prawidłowy ciąg nazwy użytkownika do *nx_mqtt_client_connect* wywołania.
- **username_length** Liczba bajtów w ciągu nazwy użytkownika
- **hasło** Ciąg hasła. Jeśli hasło nie jest wymagane, to pole może być ustawione na NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie ustawia komunikat will.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok kontrolek MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowy ciąg nazwy użytkownika lub ciąg hasła.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a>nxd_mqtt_client_connect

Połączenie Klient MQTT do brokera

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Opis

Ta usługa inicjuje połączenie z brokerem. Najpierw wiąże gniazdo TCP, a następnie tworzy połączenie TCP. Przy założeniu, że to się powiedzie, program utworzy czasomierz, jeśli funkcja utrzymania aktywności MQTT jest włączona. Następnie nawiązuje połączenie z serwerem MQTT (brokerem).

Należy pamiętać, że ta usługa tworzy połączenie MQTT bez ochrony TLS. Aby utworzyć bezpieczne połączenie MQTT, aplikacja musi używać usługi ***nxd_mqtt_client_secure_connect().***

Po nawiązaniu połączenia, jeśli  klient clean_session na NX_FALSE, klient ponownie przetransmituje wszystkie przechowywane komunikaty, które nie zostały jeszcze potwierdzone.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **server_ip** Adres IP brokera.
- **server_port** Numer portu brokera. Domyślny port dla MQTT jest zdefiniowany jako **_NXD_MQTT_PORT_** (1883).
- **keep_alive** Wartość keep alive (podtrzymanie aktywności) w sekundach, która ma być używana podczas sesji. Wartość wskazuje maksymalny czas między dwoma komunikatami sterującymi MQTT wysyłanymi do brokera, zanim broker przejmie limit czasu tego klienta. Wartość 0 powoduje wyłączenie funkcji utrzymania aktywności.
- **clean_session** Czy serwer powinien uruchomić tę sesję czyste. Prawidłowe opcje to **_NX_TRUE_*_ lub _*_NX_FALSE._**
- **wait_option** Czas oczekiwania na połączenie.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślne połączenie MQTT
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) Klient jest już połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Nie można uzyskać obiektu mutex MQTT 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Wewnętrzny błąd logiki
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) Nie można nawiązać połączenia z brokerem.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Nie można wysyłać komunikatów do brokera.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Serwer odpowiedział z błędem
- NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL (0x10081) Server response code (Kod odpowiedzi serwera programu **0x10081)**
- NXD_MQTT_ERROR_IDENTIFYIER_REJECTED (0x10082) Server response code (Kod odpowiedzi serwera programu **0x10082)**
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code (Kod odpowiedzi serwera NXD_MQTT_ERROR_SERVER_UNAVAILABLE (0x10083)
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code (Kod odpowiedzi serwera 0x10084)
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code (Kod odpowiedzi serwera NXD_MQTT_ERROR_NOT_AUTHORIZED (0x10085)
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik puli pakietów, blok ip_ptr MQTT

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a>nxd_mqtt_client_secure_connect

Połączenie Klient MQTT do brokera z zabezpieczeniami TLS

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Opis

Ta usługa jest taka sama ***jak nxd_mqtt_client_connect*** z tą różnicą, że połączenie przechodzi przez warstwę TLS zamiast protokołu TCP. W związku z tym komunikacja między klientem a brokerem jest zabezpieczona.

Zdefiniowane przez użytkownika *tls_setup* jest funkcją wywołania zwrotnego używaną przez klienta MQTT przed nawiązaniu połączenia klienta MQTT. Aplikacja powinna zainicjować zabezpieczenia NetX Secure TLS, skonfigurować parametry zabezpieczeń i załadować odpowiednie certyfikaty, które mają być używane podczas ugody TLS. Rzeczywiste uściślicie protokołu TLS ma miejsce po nawiązaniu połączenia TCP na porcie TLS protokołu MQTT brokera (domyślny port TCP 8883). Po pomyślnym zakończeniu połączenia TLS pakiet kontrolny MQTT CONNECT jest wysyłany za pośrednictwem protokołu TLS.

Aby można było bezpiecznego połączenia, biblioteka NetX Secure TLS musi ***być*** dostępna, a klient NetX Duo MQTT musi być NX_SECURE_ENABLE zdefiniowany.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **server_ip** Adres IP brokera.
- **server_port** Numer portu brokera. Domyślny port dla MQTT jestokreślony jako **_NXD_MQTT_TLS_PORT_** (8883).
- **tls_setup** Funkcja wywołania zwrotnego Instalatora TLS dostarczana przez użytkownika. Ta funkcja wywołania zwrotnego jest wywoływana w celu skonfigurowania parametrów połączenia klienta TLS.
- **keep_alive** Wartość keep-alive, która ma być używana podczas sesji. Wartość 0 powoduje wyłączenie funkcji utrzymania aktywności.
- **clean_session** Czy serwer powinien uruchomić tę sesję czyste. Prawidłowe opcje to **_NX_TRUE_*_ lub _*_NX_FALSE._**
- **wait_option** Czas oczekiwania na połączenie.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślne połączenie klienta MQTT nawiązane za pośrednictwem TLS.
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) Klient jest już połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Nie można uzyskać obiektu mutex MQTT 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Wewnętrzny błąd logiki
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) Nie można nawiązać połączenia z brokerem.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Nie można wysyłać komunikatów do brokera.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Serwer odpowiedział z komunikatem o błędzie.
- NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL (0x10081) Server response code (Kod odpowiedzi serwera programu **0x10081)**
- NXD_MQTT_ERROR_IDENTIFYIER_REJECTED (0x10082) Server response code (Kod odpowiedzi serwera programu **0x10082)**
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code (Kod odpowiedzi serwera NXD_MQTT_ERROR_SERVER_UNAVAILABLE (0x10083)
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code (Kod odpowiedzi serwera 0x10084)
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code (Kod odpowiedzi serwera NXD_MQTT_ERROR_NOT_AUTHORIZED (0x10085)
- NX_PTR_ERROR (0x07) Nieprawidłowa struktura adresu lub bloku kontrolki MQTT.
- NX_INVALID_PORT (0x46) Server port nie może być 0.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Błąd parametru wejściowego
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) wątek MQTT nie został jeszcze uruchomiony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a>nxd_mqtt_client_publish

Publikowanie komunikatu za pośrednictwem brokera

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>Opis

Ta usługa publikuje komunikat za pośrednictwem brokera. Publikowanie komunikatów QoS poziomu 2 nie jest jeszcze obsługiwane.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **topic_name** Temat do opublikowania.
- **topic_name_length** Długość tematu w bajtach.
- **komunikat** Wskaźnik do buforu komunikatów.
- **message_length** Rozmiar komunikatu w bajtach
- **zachowaj** Określa, czy broker powinien zachować komunikat.
- **QoS** Żądana wartość QoS: 0 lub 1.
- **limit czasu** Wartość limitu czasu

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślne utworzenie klienta MQTT
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Wewnętrzny błąd logiki.
- **NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Nie można uzyskać pakietu z puli pakietów.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Nie można nawiązywała komunikacji z brokerem.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 nie są obsługiwane.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok sterowania MQTT, ip_ptr lub wskaźnik puli pakietów
- NXD_MQTT_INVALID_PARAMETER (0x10009) Błąd parametru wejściowego

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a>nxd_mqtt_client_subscribe

Subskrybowanie tematu

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a>Opis

Ta usługa subskrybuje określony temat. Subskrybowanie komunikatów QoS na poziomie 2 nie jest jeszcze obsługiwane.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **topic_name** Temat do opublikowania.
- **topic_name_length** Długość tematu w bajtach.
- **QoS Żądany poziom QoS:** 0 lub 1.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie subskrybowanie tematu.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) Klient nie jest połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Nie można uzyskać obiektu mutex MQTT
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Wewnętrzny błąd logiki
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Nie można wysyłać komunikatów do brokera.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages nie są obsługiwane.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok sterowania MQTT, ip_ptr lub wskaźnik puli pakietów
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name jest ustawiona lub topic_name_length jest równa zero lub QoS to wartość jest nieprawidłowa.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a>nxd_mqtt_client_unsubscribe

Anulowanie subskrypcji tematu

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a>Opis

Ta usługa anuluje subskrypcję tematu.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **topic_name** Temat do anulowania subskrypcji.
- **topic_name_length** Długość tematu w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie anulowano subskrypcję tematu.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) Klient nie jest połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Nie można uzyskać obiektu mutex MQTT.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Wewnętrzny błąd logiki
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Nie można wysyłać komunikatów do brokera.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik bloku sterowania MQTT
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name jest ustawiona lub topic_name_length jest równa zero.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a>nxd_mqtt_client_receive_notify_set

Ustawianie funkcji wywołania zwrotnego powiadomienia o odbierania komunikatu MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego przy użyciu klienta MQTT. Po otrzymaniu komunikatu opublikowanego przez brokera klient MQTT przechowuje komunikat w kolejce odbierania. Jeśli funkcja wywołania zwrotnego jest ustawiona, wywoływana jest funkcja wywołania zwrotnego, aby powiadomić aplikację, że komunikat jest gotowy do pobrania. Funkcja receive notify przyjmuje wskaźnik do bloku sterowania klienta  MQTT i message_count wskazującą liczbę komunikatów dostępnych w kolejce odbierania. Należy pamiętać, że liczba może ulec zmianie między powiadomieniem odbioru a pobraniem tych komunikatów przez aplikację, ponieważ w interwale mogą pojawić się nowe komunikaty.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **receive_notify** Funkcja wywołania zwrotnego dostarczona przez użytkownika, która ma być wywoływana po otrzymaniu komunikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie ustaw funkcję powiadomienia o odbierania.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok kontrolek MQTT.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a>nxd_mqtt_client_message_get

Pobieranie komunikatu z brokera

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>Opis

Ta usługa pobiera komunikat opublikowany przez brokera. Wszystkie komunikaty przychodzące są przechowywane w kolejce odbierania. Aplikacja używa tej usługi do pobierania tych komunikatów. To wywołanie nie jest blokujące. Jeśli kolejka odbierania jest pusta, ta usługa zwraca wartość ***NXD_MQTT_NO_MESSAGE** _. Aplikacja, która ma być powiadamiana o komunikacie przychodzącym, może wywołać usługę _ *_nxd_mqtt_client_receive_notify_set_** w celu zarejestrowania funkcji odbierania wywołania zwrotnego.

Wywołujący musi zapewnić miejsce w pamięci dla ciągu tematu i treści komunikatu. Rozmiary tych dwóch buforów są przekazywane przy użyciu topic_buffer_size *i* *message_buffer_size*. Rzeczywista liczba bajtów w ciągu tematu i treści  komunikatu są zwracane w ciągu actual_topic_length i *actual_message_length*. Jeśli długość tematu lub długość odstępu jest większa niż ilość miejsca w buforze, ta usługa zwraca kod *błędu NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.

Aplikacja musi przydzielić większy bufor i spróbować ponownie.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **topic_buffer** Wskaźnik do lokalizacji pamięci, do której jest kopiowany ciąg tematu.
- **topic_buffer_size** Rozmiar buforu tematu.
- **actual_topic_length** Wskaźnik do lokalizacji pamięci, w której jest zwracana rzeczywista długość tematu.
- **message_buffer** Wskaźnik do lokalizacji pamięci, do której jest kopiowany ciąg komunikatu.
- **message_buffer_size** Rozmiar buforu komunikatów.
- **actual_message_length** Wskaźnik do lokalizacji pamięci, w której jest zwracana długość komunikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie pobrano komunikat.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Wewnętrzny błąd logiki
- **NXD_MQTT_NO_MESSAGE** (0x1000A) Kolejka odbierania jest pusta.
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Bufor tematu lub bufor komunikatów jest zbyt mały dla tematu lub komunikatu.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok sterowania MQTT, ip_ptr lub wskaźnik puli pakietów
- NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer lub topic_buffer ma wartość NULL

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a>nxd_mqtt_client_disconnect_notify_set

Ustawianie funkcji powiadamiania zwrotnego o rozłączeniu komunikatu MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego przy użyciu klienta MQTT. Gdy MQTT wykryje, że połączenie z brokerem zostanie utracone, wywołuje tę funkcję powiadamiania, aby ostrzec aplikację. W związku z tym aplikacja może używać tej funkcji wywołania zwrotnego do wykrywania utraconego połączenia i ponownego nawiązywania połączenia z brokerem.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.
- **disconnect_notify** Funkcja wywołania zwrotnego dostarczona przez użytkownika, która ma być wywoływana, gdy program MQTT wykryje, że połączenie z brokerem zostanie utracone.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie ustaw funkcję powiadamiania o rozłączeniu.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok kontrolek MQTT.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a>nxd_mqtt_client_disconnect

Odłączanie klienta MQTT od brokera

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa odłącza klienta od brokera. Należy pamiętać, że komunikaty w kolejce odbierania są zwalniane. Komunikaty z QoS 1 w kolejce przesyłania nie są zwalniane. Po ponownym nawiązaniu połączenia z serwerem można przetwarzać komunikaty QoS 1, chyba że klient ponownie nawiąży połączenie z serwerem za pomocą flagi *clean_session* ustawionej na ***NX_TRUE***.

Jeśli połączenie zostało nawiązaniu przy użyciu zabezpieczeń protokołu TLS, ta usługa zamknie sesję protokołu TLS przed odłączeniem połączenia TCP.

Rzeczywiste wywołanie rozłączenia gniazda TCP ma opcję oczekiwania zdefiniowaną przez NXD_MQTT_SOCKET_TIMEOUT (takty czasomierza). Wartość domyślna to NX_WAIT_FOREVER. Aby uniknąć zawieszenia na czas nieokreślony w przypadku, gdy połączenie sieciowe zostanie utracone lub serwer nie odpowiada, ustaw tę opcję na wartość skończoną.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie odłączony od brokera
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Nie można uzyskać obiektu mutex MQTT.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok kontrolek MQTT

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

Usuwanie wystąpienia klienta MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie klienta MQTT i zwalnia zasoby wewnętrzne. Ta usługa automatycznie rozłącza klienta z brokerem, jeśli jest nadal połączony. Komunikaty, które nie zostały jeszcze przesłane lub nie zostały potwierdzone, są zwalniane. Komunikaty odebrane, ale nie pobrane przez aplikację również są zwalniane.

Jeśli połączenie zostało nawiązaniu przy użyciu zabezpieczeń protokołu TLS, ta usługa zamyka sesję protokołu TLS przed odłączeniem połączenia TCP.

Po usunięciu klienta aplikacja, która chce korzystać z usługi MQTT, musi utworzyć nowe wystąpienie.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta MQTT.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0x00) Pomyślnie usunięto klienta MQTT.
- NX_PTR_ERROR (0x07) Nieprawidłowy blok kontrolek MQTT

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
