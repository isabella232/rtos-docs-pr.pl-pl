---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Duo MQTT Client
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta NetX Duo MQTT.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cde19a0e84f369f1199ea4027fa09e6bd038e837
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821811"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Duo MQTT Client

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta platformy Azure RTO NetX Duo MQTT.

## <a name="product-distribution"></a>Dystrybucja produktu

MQTT Client for NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe, jeden plik dołączany i plik, który zawiera ten dokument, w następujący sposób:

- **nxd_mqtt_client. h** Plik nagłówkowy dla klienta MQTT dla NetX Duo
- **nxd_mqtt_client. c** Plik źródłowy języka C dla klienta MQTT dla programu NetX Duo
- **nxd_mqtt_client.pdf** Opis klienta MQTT dla programu NetX Duo
- **demo_mqtt_client. c** Demonstracja NetX Duo MQTT

## <a name="mqtt-client-installation"></a>Instalacja klienta MQTT

Aby można było używać klienta MQTT do NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", następnie należy skopiować do tego katalogu klienta *nxd_mqtt_client. h* i *Nxd_mqtt_client. c* dla NetX Duo MQTT.

## <a name="using-mqtt-client"></a>Korzystanie z klienta MQTT

Korzystanie z programu MQTT Client for NetX Duo jest proste. W zasadzie kod aplikacji musi zawierać *nxd_mqtt_client. h* , po uwzględnieniu *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo. Po dołączeniu plików nagłówkowych klienta MQTT kod aplikacji może korzystać z usług MQTT opisanych w dalszej części tego przewodnika. Aplikacja musi również zawierać *nxd_mqtt_client. c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z programu NetX Duo MQTT Client.

## <a name="using-mqtt-client-with-netx-secure-tls"></a>Korzystanie z MQTT Client with NetX Secure TLS

Aby można było używać klienta MQTT z modułem Secure TLS NetX, aplikacja musi mieć zainstalowany moduł NetX Secure TLS i zawierać *nx_secure_tls_api. h* i *nx_crypto. h*. Biblioteka MQTT musi być skompilowana przy użyciu zdefiniowanego symbolu ***NX_SECURE_ENABLE*** .

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania klienta MQTT dla NetX Duo. Poniżej znajduje się lista wszystkich opcji, w których poszczególne są szczegółowo opisane. Wartości domyślne są wyświetlane, ale można je zdefiniować ponownie przed włączeniem *nxd_mqtt_client. h.*

- **NX_DISABLE_ERROR_CHECKING**: zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów klienta MQTT. Jest on zazwyczaj używany po debugowaniu aplikacji.
- **NX_SECURE_ENABLE**: zdefiniowany klient MQTT jest oparty na obsłudze protokołu TLS.
Zdefiniowanie tego symbolu wymaga zainstalowania bezpiecznego modułu protokołu TLS NetX.
*NX_SECURE_ENABLE* nie jest domyślnie włączona. * *
- **NXD_MQTT_REQUIRE_TLS**: zdefiniowane, aplikacja musi używać protokołu TLS do łączenia się z brokerem MQTT. Ta funkcja wymaga zdefiniowania *NX_SECURE_ENABLE* . Domyślnie ten symbol nie jest zdefiniowany.
- **NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: przestarzałe.
- **NXD_MQTT_MAX_MESSAGE_LENGTH**: przestarzałe.
- **NXD_MQTT_KEEPALIVE_TIMER_RATE**: określa szybkość czasomierza MQTT w taktach czasomierza ThreadX. Ten czasomierz służy do śledzenia czasu od momentu wysłania ostatniej wiadomości sterującej MQTT i wysłania komunikatu MQTT PINGREQ przed upływem czasu utrzymywania aktywności. Ten czasomierz jest uaktywniany, jeśli klient nawiązuje połączenie z brokerem z ustawioną wartością czasomierza Keep-Alive. Wartość domyślna to TX_TIMER_TICKS_PER_SECOND, która jest czasomierzem jednosekundowym.
- **NXD_MQTT_PING_TIMEOUT_DELAY**: określa czas oczekiwania klienta MQTT na PINGRESP z brokera po wysłaniu przez niego MQTT PINGREQ. Jeśli nie otrzymasz PINGRESP po upływie tego limitu czasu, klient traktuje brokera jako nieodpowiadający i rozłącza się z brokerem. Domyślne opóźnienie limitu czasu polecenia PING to TX_TIMER_TICKS_PER_SECOND, co jest jedną sekundą.
- **NXD_MQTT_SOCKET_TIMEOUT**: określa limit czasu w wywołaniu połączenia gniazda TCP podczas rozłączania z serwerem MQTT w taktach czasomierza. Wartość domyślna to NX_WAIT_FOREVER.

## <a name="sample-mqtt-program"></a>Przykładowy program MQTT

Poniższy program ilustruje prostą aplikację MQTT. W celu uproszczenia kody powrotne są uznawane za pomyślne, dlatego nie jest wykonywane żadne dalsze sprawdzanie błędów.

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
