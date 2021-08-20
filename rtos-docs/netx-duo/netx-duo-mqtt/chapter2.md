---
title: Rozdział 2 — Instalowanie i używanie klienta Azure RTOS NetX Duo MQTT
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika klienta NetX Duo MQTT.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4e27a6738456a90f3d708789f51b0471868c6f9e
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2021
ms.locfileid: "122601314"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a>Rozdział 2 — Instalowanie i używanie klienta Azure RTOS NetX Duo MQTT

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika klienta Azure RTOS NetX Duo MQTT.

## <a name="product-distribution"></a>Dystrybucja produktów

Klient MQTT dla netX Duo jest dostępny na stronie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe, jeden plik dołączany i plik zawierający ten dokument w następujący sposób:

- **nxd_mqtt_client.h** Plik nagłówkowy klienta MQTT dla NetX Duo
- **nxd_mqtt_client.c** Plik źródłowy języka C dla klienta MQTT dla NetX Duo
- **nxd_mqtt_client.pdf** Opis klienta MQTT dla netx duo
- **demo_mqtt_client.c** Pokaz netx duo MQTT

## <a name="mqtt-client-installation"></a>Instalacja klienta MQTT

Aby można było korzystać z klienta MQTT dla netX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo. Jeśli na przykład program NetX Duo jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu należy skopiować pliki *nxd_mqtt_client.h* i *nxd_mqtt_client.c* dla klienta NetX Duo MQTT.

## <a name="using-mqtt-client"></a>Korzystanie z klienta MQTT

Korzystanie z klienta MQTT dla netX Duo jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nxd_mqtt_client.h* po dojecheniu do plików *tx_api.h* i *nx_api.h,* aby można było używać odpowiednio funkcji ThreadX i NetX Duo. Gdy zostaną dołączone pliki nagłówkowe klienta MQTT, kod aplikacji będzie mógł korzystać z usług MQTT opisanych w dalszej części tego przewodnika. Aplikacja musi również *uwzględniać nxd_mqtt_client.c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z klienta NetX Duo MQTT.

## <a name="using-mqtt-client-with-netx-secure-tls"></a>Korzystanie z klienta MQTT z bezpiecznym TLS NetX

Aby można było korzystać z klienta MQTT z modułem NetX Secure TLS, aplikacja musi mieć zainstalowany moduł NetX Secure TLS z zainstalowanym modułem *nx_secure_tls_api.h* *i nx_crypto.h.* Biblioteka MQTT musi być zbudowana przy użyciu zdefiniowanego ***NX_SECURE_ENABLE*** symbolu.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia klienta MQTT dla netX Duo. Poniżej znajduje się lista wszystkich opcji, z których każda jest szczegółowo opisana. Zostaną wyświetlone wartości domyślne, ale można je ponownie zdefiniować przed dodaniem *nxd_mqtt_client.h.*

- **NX_DISABLE_ERROR_CHECKING:** zdefiniowana, ta opcja usuwa podstawowe sprawdzanie błędów klienta MQTT. Jest on zwykle używany po debugowaniu aplikacji.
- **NX_SECURE_ENABLE:** zdefiniowany klient MQTT jest zbudowany z obsługą TLS.
Zdefiniowanie tego symbolu wymaga zainstalowania modułu NetX Secure TLS.
*NX_SECURE_ENABLE* nie jest domyślnie włączona.**
- **NXD_MQTT_REQUIRE_TLS:** zdefiniowane, aplikacja musi używać TLS do nawiązywania połączenia z brokerem MQTT. Ta funkcja wymaga *NX_SECURE_ENABLE* zdefiniowanych. Domyślnie ten symbol nie jest zdefiniowany.
- **NXD_MQTT_MAXIMUM_TRANSMIT_QUEUE_DEPTH:** zdefiniowano, włączono głębokość kolejki przesyłania MQTT. Musi to być dodatnia liczba całkowita.
- **NXD_MQTT_MAX_TOPIC_NAME_LENGTH:** przestarzałe.
- **NXD_MQTT_MAX_MESSAGE_LENGTH:** przestarzałe.
- **NXD_MQTT_KEEPALIVE_TIMER_RATE:** definiuje szybkość czasomierza MQTT w taktach czasomierza ThreadX. Ten czasomierz służy do śledzenia czasu od ostatniego wysłania komunikatu sterującego MQTT i wysyła komunikat PINGREQ MQTT przed upływem czasu aktywności. Ten czasomierz jest aktywowany, jeśli klient łączy się z brokerem przy użyciu ustawionej wartości czasomierza keep-alive. Wartość domyślna to TX_TIMER_TICKS_PER_SECOND, która jest czasomierzem sekundy.
- **NXD_MQTT_PING_TIMEOUT_DELAY:** definiuje czas oczekiwania przez klienta MQTT na pingRESP z brokera po jego wysłanie pingREQ MQTT. Jeśli po tym opóźnieniu limitu czasu nie zostanie odebrany żaden pingRESP, klient traktuje brokera jako nie odpowiada i rozłącza się z brokerem. Domyślnym opóźnieniem limitu czasu polecenia PING jest TX_TIMER_TICKS_PER_SECOND, czyli jedna sekunda.
- **NXD_MQTT_SOCKET_TIMEOUT:** definiuje ujmowanie czasu w wywołaniu rozłączenia gniazda TCP podczas odłączania od serwera MQTT w taktach czasomierza. Wartość domyślna to NX_WAIT_FOREVER.

## <a name="sample-mqtt-program"></a>Przykładowy program MQTT

Poniższy program ilustruje prostą aplikację MQTT. Dla uproszczenia zakłada się, że kody powrotne są pomyślne, dlatego nie jest wykonywane żadne dalsze sprawdzanie błędów.

```c
#define LOCAL_SERVER_ADDRESS (IP_ADDRESS(192, 168, 1, 81))

/*******************************************************/
/* IOT MQTT Client Example                             */
/*******************************************************/
#define DEMO_STACK_SIZE 2048
#define CLIENT_ID_STRING "mytestclient"
#define MQTT_CLIENT_STACK_SIZE 4096
#define STRLEN(p) (sizeof(p) - 1)

/* Declare the MQTT thread stack space. */
static ULONG mqtt_client_stack[MQTT_CLIENT_STACK_SIZE / sizeof(ULONG)];

/* Declare the MQTT client control block. */
static NXD_MQTT_CLIENT mqtt_client;

/* Define the symbol for signaling a received message. */

/* Define the test threads. */

#define TOPIC_NAME "topic"

#define MESSAGE_STRING "This is a message. "

/* Define the priority of the MQTT internal thread. */
#define MQTT_THREAD_PRIORTY 2

/* Define the MQTT keep alive timer for 5 minutes */
#define MQTT_KEEP_ALIVE_TIMER 300
#define QOS0 0
#define QOS1 1

/* Declare event flag, which is used in this demo. */
TX_EVENT_FLAGS_GROUP mqtt_app_flag;
#define DEMO_MESSAGE_EVENT 1
#define DEMO_ALL_EVENTS 3

/* Declare buffers to hold message and topic. */
static UCHAR message_buffer[NXD_MQTT_MAX_MESSAGE_LENGTH];
static UCHAR topic_buffer[NXD_MQTT_MAX_TOPIC_NAME_LENGTH];

/* Declare the disconnect notify function. */
static VOID my_disconnect_func(NXD_MQTT_CLIENT *client_ptr)
{
    printf("client disconnected from server\n");
}

static VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr, UINT number_of_messages)
{
    tx_event_flags_set(&mqtt_app_flag, DEMO_MESSAGE_EVENT, TX_OR);
    return;
}

static ULONG error_counter;
void demo_mqtt_client_local(NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr)
{
    UINT status;
    NXD_ADDRESS server_ip;
    ULONG events;
    UINT topic_length, message_length;

    /* Create MQTT client instance. */
    nxd_mqtt_client_create(&mqtt_client, "my_client",
        CLIENT_ID_STRING, STRLEN(CLIENT_ID_STRING), ip_ptr, pool_ptr,
        (VOID*)mqtt_client_stack, sizeof(mqtt_client_stack),
        MQTT_THREAD_PRIORTY, NX_NULL, 0);

    /* Register the disconnect notification function. */
    nxd_mqtt_client_disconnect_notify_set(&mqtt_client, my_disconnect_func);

    /* Create an event flag for this demo. */
    status = tx_event_flags_create(&mqtt_app_flag, "my app event");
    server_ip.nxd_ip_version = 4;
    server_ip.nxd_ip_address.v4 = LOCAL_SERVER_ADDRESS;

    /* Start the connection to the server. */
    nxd_mqtt_client_connect(&mqtt_client, &server_ip, NXD_MQTT_PORT, 
        MQTT_KEEP_ALIVE_TIMER, 0, NX_WAIT_FOREVER);

    /* Subscribe to the topic with QoS level 0. */
    nxd_mqtt_client_subscribe(&mqtt_client, TOPIC_NAME, STRLEN(TOPIC_NAME),
        QOS0);

    /* Set the receive notify function. */
    nxd_mqtt_client_receive_notify_set(&mqtt_client, my_notify_func);

    /* Publish a message with QoS Level 1. */
    nxd_mqtt_client_publish(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME), (CHAR*)MESSAGE_STRING, 
        STRLEN(MESSAGE_STRING), 0, QOS1, NX_WAIT_FOREVER);

    /* Now wait for the broker to publish the message. */
    tx_event_flags_get(&mqtt_app_flag, DEMO_ALL_EVENTS,
        TX_OR_CLEAR, &events, TX_WAIT_FOREVER);

    if(events & DEMO_MESSAGE_EVENT)
    {
        nxd_mqtt_client_message_get(&mqtt_client, topic_buffer,
            sizeof(topic_buffer), &topic_length, message_buffer,
            sizeof(message_buffer), &message_length);

        topic_buffer[topic_length] = 0;

        message_buffer[message_length] = 0;

        printf("topic = %s, message = %s\n", topic_buffer, message_buffer);
    }

    /* Now unsubscribe the topic. */
    nxd_mqtt_client_unsubscribe(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME));

    /* Disconnect from the broker. */
    nxd_mqtt_client_disconnect(&mqtt_client);

    /* Delete the client instance, release all the resources. */
    nxd_mqtt_client_delete(&mqtt_client);
    return;
}
```
