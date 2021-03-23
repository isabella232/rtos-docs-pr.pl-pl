---
title: Rozdział 3 — Opis usługi Azure RTO NetX Duo MQTT Client Services
description: Ten rozdział zawiera opis wszystkich usług klienta NetX Duo MQTT (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821799"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>Rozdział 3 — Opis usługi Azure RTO NetX Duo MQTT Client Services

Ten rozdział zawiera opis wszystkich usług klienta Azure RTO NetX Duo MQTT (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nxd_mqtt_client_create** *utworzyć wystąpienia klienta MQTT*
- **nxd_mqtt_client_will_message_set** *ustawić komunikat będzie*
- **nxd_mqtt_client_client_login_set** *ustawić nazwy użytkownika i hasła logowania klienta MQTT*
- **nxd_mqtt_client_connect** *łączenie z klientem programu MQTT z brokerem*
- **nxd_mqtt_client_secure_connect** *łączenie klienta z klientem przy użyciu zabezpieczeń TLS*
- **nxd_mqtt_client_publish** *opublikować komunikat za pośrednictwem brokera.*
- **nxd_mqtt_client_subscribe** *subskrybować tematu*
- **nxd_mqtt_client_unsubscribe** *Anulowanie subskrypcji tematu*
- **nxd_mqtt_client_receive_notify_set** *Ustaw funkcję wywołania zwrotnego powiadomienia o OTRZYMAniu komunikatu MQTT*
- **nxd_mqtt_client_message_get** *pobrać komunikatu z brokera*
- **nxd_mqtt_client_disconnect_notify_set** *Ustaw funkcję wywołania zwrotnego powiadomienia o rozłączeniu komunikatu MQTT*
- **nxd_mqtt_client_disconnect** *rozłączyć klienta MQTT z brokera*
- **nxd_mqtt_client_delete** *usunąć wystąpienia klienta MQTT*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

Utwórz wystąpienie klienta MQTT

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

Ta usługa tworzy wystąpienie klienta MQTT na określonym wystąpieniu IP. Ciąg *client_id* jest przesyłany do serwera podczas fazy połączenia MQTT jako *Identyfikator klienta (ClientId)*. Tworzy również niezbędne zasoby ThreadX (wątek zadania klienta MQTT, mutex, grupę flag zdarzeń i gniazdo TCP).

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **CLIENT_NAME** Ciąg nazwy klienta.
- **client_id** Ciąg identyfikatora klienta używany podczas fazy połączenia. Broker MQTT używa tego client_id do unikatowego identyfikowania klienta.
- **client_id_length** Długość ciągu identyfikatora klienta w bajtach.
- **ip_ptr** Wskaźnik na wystąpienie adresu IP.
- **pool_ptr** Wskaźnik do puli pakietów MQTT przez klienta do jego działania.
- **stack_ptr** Obszar stosu dla wątku klienta MQTT.
- **stack_size** Rozmiar obszaru stosu w bajtach.
- **mqtt_thread_priority** Priorytet wątku MQTT.
- **memory_ptr** Przestarzałe. Nie jest już używane.
- **memory_size** Przestarzałe. Nie jest już używane.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie UTWORZYŁ klienta MQTT.
- Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)
- NX_PTR_ERROR (0x07) nieprawidłowy MQTT bloku sterowania, ip_ptr lub puli pakietów.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowa wartość ciągu tematu, will_retrain_flag lub will_QoS.

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

Ustawia komunikat będzie

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

Ta usługa ustawia opcjonalny temat i zostanie wyświetlony komunikat, zanim klient nawiąże połączenie z serwerem. Temat musi być ciągiem zakodowanym w formacie UTF-8.

Jeśli zestaw zostanie wysłany do brokera w ramach komunikatu CONNECT, zostanie wyświetlony komunikat. W związku z tym aplikacja, której zamierzasz używać, będzie musiał używać tej usługi przed nawiązaniem połączenia MQTT.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **will_topic** Kodowanie UTF-8 będzie ciąg tematu. Sekcja musi być obecna. Obiekt wywołujący musi utrzymywać poprawność ciągu will_topic, aż do wywołania *nx_mqtt_client_connect* .
- **will_topic_length** Liczba bajtów w ciągu tematu
- **will_message** Zdefiniowana aplikacja będzie komunikatem. Jeśli komunikat nie jest wymagany, aplikacja może ustawić to pole na *NX_NULL.*
- **will_message_length** Liczba bajtów w ciągu komunikatu. Jeśli will_message ma wartość NULL, will_message_length musi być ustawiona na 0.
- **will_retain_flag** Czy serwer publikuje komunikat w postaci wiadomości przechowywanej. Prawidłowe wartości to *NX_TRUE* lub *NX_FALSE.*
- **will_QoS** Wartość QoS używana przez serwer podczas wysyłania zostanie wyświetlony komunikat. Prawidłowe wartości to 0 lub 1.  

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawia komunikat o błędzie.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) jakość komunikatów poziomu 2 nie są obsługiwane.
- NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowa wartość ciągu tematu, will_retrain_flag lub will_QoS.

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

Ta usługa ustawia nazwę użytkownika i hasło, które są używane podczas fazy połączenia MQTT na potrzeby logowania w celu uwierzytelnienia.

Identyfikator logowania klienta MQTT z nazwą użytkownika i hasłem jest opcjonalny. W sytuacjach, gdy serwer wymaga nazwy użytkownika i hasła, przed nawiązaniem połączenia należy ustawić nazwę użytkownika i hasło.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **Nazwa użytkownika** Zakodowany ciąg nazwy użytkownika w formacie UTF-8. Obiekt wywołujący musi utrzymywać prawidłowy ciąg nazwy użytkownika, aż do wywołania *nx_mqtt_client_connect* .
- **username_length** Liczba bajtów w ciągu nazwy użytkownika
- **hasło** Ciąg hasła. Jeśli hasło nie jest wymagane, to pole może mieć wartość NX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawia komunikat o błędzie.
- NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowa nazwa użytkownika lub ciąg hasła.

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

Łączenie klienta MQTT z brokerem

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Opis

Ta usługa inicjuje połączenie z brokerem. Najpierw wiąże się z gniazdem TCP, a następnie nawiązuje połączenie TCP. Przy założeniu, że program zakończy się pomyślnie, tworzy czasomierz, jeśli funkcja utrzymywania aktywności MQTT jest włączona. Następnie łączy się z serwerem MQTT (brokerem).

Należy zauważyć, że ta usługa tworzy połączenie MQTT bez ochrony TLS. Aby można było utworzyć bezpieczne połączenie MQTT, aplikacja używa usługi ***nxd_mqtt_client_secure_connect ().***

Jeśli klient ustawi *clean_session* na NX_FALSE, klient będzie ponownie przesyłał wszystkie zapisane komunikaty, które nie zostały jeszcze potwierdzone.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **server_IP** Adres IP brokera.
- **SERVER_PORT** Numer portu brokera. Domyślny port dla MQTT jest zdefiniowany jako **_NXD_MQTT_PORT_** (1883).
- **keep_alive** Wartość utrzymywania aktywności (w sekundach), która ma być używana podczas sesji. Wartość wskazuje maksymalny czas między dwoma komunikatami sterującymi MQTT wysyłanymi do brokera, zanim Broker przekroczy ten klient. Wartość 0 wyłącza funkcję Keep-Alive.
- **clean_session** Czy serwer rozpoczyna czyszczenie tej sesji. Prawidłowe opcje to **_NX_TRUE_*_ lub _*_NX_FALSE._**
- **WAIT_OPTION** Czas oczekiwania na połączenie.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie MQTT połączenie
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) klient jest już połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX 
- Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) nie może nawiązać połączenia z brokerem.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.
- Serwer **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) odpowiedział z błędem
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085)
- NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów

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

Podłączanie klienta MQTT do brokera z zabezpieczeniami TLS

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

Ta usługa jest taka sama jak ***nxd_mqtt_client_connect*** , z tą różnicą, że połączenie przechodzi przez warstwę TLS zamiast TCP. W związku z tym komunikacja między klientem i brokerem jest zabezpieczona.

*Tls_setup* zdefiniowane przez użytkownika to funkcja wywołania zwrotnego, która jest stosowana przez klienta MQTT przed nawiązaniem połączenia z klientem MQTT. Aplikacja inicjuje NetX Secure TLS, konfiguruje parametry zabezpieczeń i ładuje odpowiednie certyfikaty do użycia podczas uzgadniania protokołu TLS. Rzeczywista uzgadnianie protokołu TLS następuje po ustanowieniu połączenia TCP na porcie MQTT TLS brokera (domyślny port TCP 8883). Po pomyślnym przeprowadzeniu uzgadniania TLS pakiet MQTT CONNECT Control zostanie wysłany za pośrednictwem protokołu TLS.

Aby zapewnić bezpieczne połączenia, musi być dostępna Biblioteka NetX Secure TLS, a klient NetX Duo MQTT musi być skompilowany przy użyciu zdefiniowanych ***NX_SECURE_ENABLE*** .

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **server_IP** Adres IP brokera.
- **SERVER_PORT** Numer portu brokera. Domyślny port dla MQTT IsDefined jako **_NXD_MQTT_TLS_PORT_** (8883).
- **tls_setup** Funkcja wywołania zwrotnego konfiguracji protokołu TLS dostarczonej przez użytkownika. Ta funkcja wywołania zwrotnego jest wywoływana w celu skonfigurowania parametrów połączenia klienta protokołu TLS.
- **keep_alive** Wartość Keep-Alive, która ma być używana podczas sesji. Wartość 0 wyłącza funkcję Keep-Alive.
- **clean_session** Bez względu na to, czy serwer rozpoczyna czyszczenie tej sesji. Prawidłowe opcje to **_NX_TRUE_*_ lub _*_NX_FALSE._**
- **WAIT_OPTION** Czas oczekiwania na połączenie.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie MQTT połączenie z klientem za pośrednictwem protokołu TLS.
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) klient jest już połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX 
- Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) nie może nawiązać połączenia z brokerem.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.
- Serwer **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) odpowiedział na komunikat o błędzie.
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084)
- Kod odpowiedzi serwera **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085)
- NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT lub struktura adresów serwera.
- Port serwera NX_INVALID_PORT (0x46) nie może mieć wartości 0.
- Błąd parametru wejściowego NXD_MQTT_INVALID_PARAMETER (0x10009)
- Nie rozpoczęto jeszcze działania NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT.

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

Publikowanie wiadomości za pośrednictwem brokera

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>Opis

Ta usługa publikuje komunikat za pośrednictwem brokera. Publikowanie komunikatów poziomu 2 usług QoS nie jest jeszcze obsługiwane.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **topic_name** Temat do opublikowania.
- **topic_name_length** Długość tematu w bajtach.
- **komunikat** Wskaźnik do buforu komunikatów.
- **message_length** Rozmiar wiadomości (w bajtach)
- **Zachowaj** Określa, czy ten komunikat jest przechowywany przez brokera.
- **Jakość** usług (QoS) Wymagana wartość QoS: 0 lub 1.
- **limit czasu** Wartość limitu czasu

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślne utworzenie klienta MQTT
- Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004).
- **NXD_MQTT_PACKET_POOL_FAILURE** (0X10006) nie może uzyskać pakietu z puli pakietów.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może nawiązać komunikacji z brokerem.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) jakość komunikatów poziomu 2 nie są obsługiwane.
- NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów
- Błąd parametru wejściowego NXD_MQTT_INVALID_PARAMETER (0x10009)

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

Ta usługa subskrybuje określony temat. Subskrybowanie komunikatów poziomu 2 usługi QoS nie jest jeszcze obsługiwane.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **topic_name** Temat do opublikowania.
- **topic_name_length** Długość tematu w bajtach.
- **Jakość usług QoS żądany poziom jakości usług:** 0 lub 1.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie subskrybuje temat.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) klient nie jest połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX
- Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) poziom QoS 2messages nie są obsługiwane.
- NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów
- Nie ustawiono topic_name NXD_MQTT_INVALID_PARAMETER (0x10009) lub topic_name_length jest równa zero lub wartość ustawienia QoS jest nieprawidłowa.

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

Ta usługa anuluje subskrypcję z tematu.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **topic_name** Temat anulowania subskrypcji.
- **topic_name_length** Długość tematu w bajtach.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie anulował subskrypcję tematu.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) klient nie jest połączony z brokerem.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX.
- Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.
- NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik bloku sterowania MQTT
- Nie ustawiono topic_name NXD_MQTT_INVALID_PARAMETER (0x10009) lub topic_name_length wynosi zero.

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

Ustaw funkcję wywołania zwrotnego powiadomienia o otrzymaniu komunikatu MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego za pomocą klienta MQTT. Po odebraniu komunikatu opublikowanego przez brokera klient MQTT przechowuje komunikat w kolejce odbierania. Jeśli funkcja wywołania zwrotnego jest ustawiona, wywoływana jest funkcja wywołania zwrotnego w celu powiadomienia aplikacji o gotowości do pobrania. Funkcja odbierania powiadomień przyjmuje wskaźnik do bloku kontroli klienta MQTT, a *message_count* wskazujący liczbę komunikatów dostępnych w kolejce odbierania. Należy pamiętać, że liczba może ulec zmianie między powiadomieniem dotyczącym odebrania a pobraniem tych komunikatów przez aplikację, ponieważ w interwale mogły zostać odebrane nowe komunikaty.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **receive_notify** Funkcja wywołania zwrotnego podanego przez użytkownika ma być wywoływana podczas otrzymywania komunikatu.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawił funkcję Odbierz powiadomienie.
- NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.

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

Ta usługa pobiera komunikat opublikowany przez brokera. Wszystkie komunikaty przychodzące są przechowywane w kolejce odbierania. Aplikacja używa tej usługi do pobierania tych komunikatów. To wywołanie nie blokuje się. Jeśli kolejka odbierania jest pusta, ta usługa zwraca ***NXD_MQTT_NO_MESSAGE** _. Aplikacja, która chce otrzymywać powiadomienia o przychodzących komunikatach, może wywołać usługę _ *_nxd_mqtt_client_receive_notify_set_**, aby zarejestrować funkcję wywołania zwrotnego.

Obiekt wywołujący musi podać miejsce w pamięci dla ciągu tematu i treści komunikatu. Rozmiary tych dwóch buforów są przesyłane przy użyciu *topic_buffer_size* i *message_buffer_size*. Rzeczywista liczba bajtów w ciągu tematu i treść komunikatu są zwracane w *actual_topic_length* i *actual_message_length*. Jeśli długość tematu lub długość Massage jest większa niż podana ilość miejsca w buforze, ta usługa zwróci kod błędu *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.

Aplikacja przydzieli większy bufor i spróbuj ponownie.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **topic_buffer** Wskaźnik do lokalizacji pamięci, w której jest kopiowany ciąg tematu.
- **topic_buffer_size** Rozmiar buforu tematu.
- **actual_topic_length** Wskaźnik do lokalizacji pamięci, w której jest zwracana rzeczywista długość tematu.
- **message_buffer** Wskaźnik do lokalizacji pamięci, w której jest kopiowany ciąg wiadomości.
- **message_buffer_size** Rozmiar buforu komunikatów.
- **actual_message_length** Wskaźnik do lokalizacji pamięci, w której zostanie zwrócona długość wiadomości.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie pobrał komunikat.
- Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)
- **NXD_MQTT_NO_MESSAGE** (0x1000A) Kolejka odbierania jest pusta.
- Bufor tematu (0x1000D) lub bufor komunikatów jest za mały dla tematu lub wiadomości. **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE**
- NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów
- NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer lub topic_buffer wskaźnik ma wartość NULL

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

Ustaw funkcję wywołania zwrotnego powiadomienia o rozłączeniu komunikatu MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego za pomocą klienta MQTT. Gdy MQTT wykrywa połączenie z brokerem, wywołuje tę funkcję powiadamiania o alercie do aplikacji. W związku z tym aplikacja może używać tej funkcji wywołania zwrotnego do wykrywania utraconych połączeń i w celu ponownego nawiązania połączenia z brokerem.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.
- **disconnect_notify** Funkcja wywołania zwrotnego, która ma zostać wywołana, gdy MQTT wykrywa połączenie z brokerem, zostanie utracona.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawił funkcję powiadamiania o rozłączeniu.
- NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.

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

Ta usługa rozłącza klienta od brokera. Zwróć uwagę na to, że komunikaty w kolejce odbierania są wydane. Komunikaty z funkcją QoS 1 w kolejce transmisji nie są wydane. Po ponownym nawiązaniu połączenia klienta z serwerem można przetworzyć komunikaty QoS 1, chyba że klient ponownie nawiąże połączenie z serwerem z flagą *clean_session* ustawioną na ***NX_TRUE***.

Jeśli połączenie zostało nawiązane z ochroną zabezpieczeń TLS, ta usługa zamknie sesję TLS przed odłączeniem połączenia TCP.

Rzeczywiste wywołanie rozłączenia gniazda TCP jest zdefiniowane przez NXD_MQTT_SOCKET_TIMEOUT (Takty czasomierza). Wartość domyślna to NX_WAIT_FOREVER. Aby uniknąć nieograniczonego zawieszenia w przypadku utraty połączenia sieciowego lub braku odpowiedzi serwera, ustaw tę opcję na wartość skończoną.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) zostało pomyślnie rozłączone z brokerem
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX.
- NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT

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

Ta usługa usuwa wystąpienie klienta MQTT i zwalnia zasoby wewnętrzne. Ta usługa automatycznie rozłącza klienta z brokera, jeśli jest nadal połączony. Komunikaty, które nie zostały jeszcze przesłane lub nie zostały potwierdzone, są wydawane. Komunikaty odebrane, ale nie pobrane przez aplikację są również wydane.

Jeśli nastąpiło połączenie z ochroną zabezpieczeń TLS, ta usługa zamyka sesję protokołu TLS przed odłączeniem połączenia TCP.

Po usunięciu klienta aplikacja, która chce korzystać z usługi MQTT, musi utworzyć nowe wystąpienie.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do MQTT bloku sterowania klientem.

### <a name="return-values"></a>Wartości zwrócone

- **NXD_MQTT_SUCCESS** (0X00) pomyślnie usunął klienta MQTT.
- NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
