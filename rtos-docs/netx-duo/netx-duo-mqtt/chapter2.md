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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a><span data-ttu-id="b49df-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Duo MQTT Client</span><span class="sxs-lookup"><span data-stu-id="b49df-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo MQTT client</span></span>

<span data-ttu-id="b49df-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta platformy Azure RTO NetX Duo MQTT.</span><span class="sxs-lookup"><span data-stu-id="b49df-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo MQTT client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="b49df-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="b49df-105">Product Distribution</span></span>

<span data-ttu-id="b49df-106">MQTT Client for NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="b49df-106">MQTT Client for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="b49df-107">Pakiet zawiera dwa pliki źródłowe, jeden plik dołączany i plik, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b49df-107">The package includes two source files, one include file, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="b49df-108">**nxd_mqtt_client. h** Plik nagłówkowy dla klienta MQTT dla NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b49df-108">**nxd_mqtt_client.h** Header file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="b49df-109">**nxd_mqtt_client. c** Plik źródłowy języka C dla klienta MQTT dla programu NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b49df-109">**nxd_mqtt_client.c** C Source file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="b49df-110">**nxd_mqtt_client.pdf** Opis klienta MQTT dla programu NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b49df-110">**nxd_mqtt_client.pdf** Description of MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="b49df-111">**demo_mqtt_client. c** Demonstracja NetX Duo MQTT</span><span class="sxs-lookup"><span data-stu-id="b49df-111">**demo_mqtt_client.c** NetX Duo MQTT demonstration</span></span>

## <a name="mqtt-client-installation"></a><span data-ttu-id="b49df-112">Instalacja klienta MQTT</span><span class="sxs-lookup"><span data-stu-id="b49df-112">MQTT Client Installation</span></span>

<span data-ttu-id="b49df-113">Aby można było używać klienta MQTT do NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b49df-113">In order to use MQTT Client for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="b49df-114">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", następnie należy skopiować do tego katalogu klienta *nxd_mqtt_client. h* i *Nxd_mqtt_client. c* dla NetX Duo MQTT.</span><span class="sxs-lookup"><span data-stu-id="b49df-114">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_mqtt_client.h* and *nxd_mqtt_client.c* for NetX Duo MQTT Client need to be copied into this directory.</span></span>

## <a name="using-mqtt-client"></a><span data-ttu-id="b49df-115">Korzystanie z klienta MQTT</span><span class="sxs-lookup"><span data-stu-id="b49df-115">Using MQTT Client</span></span>

<span data-ttu-id="b49df-116">Korzystanie z programu MQTT Client for NetX Duo jest proste.</span><span class="sxs-lookup"><span data-stu-id="b49df-116">Using MQTT Client for NetX Duo is easy.</span></span> <span data-ttu-id="b49df-117">W zasadzie kod aplikacji musi zawierać *nxd_mqtt_client. h* , po uwzględnieniu *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b49df-117">Basically, the application code must include *nxd_mqtt_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX, and NetX Duo, respectively.</span></span> <span data-ttu-id="b49df-118">Po dołączeniu plików nagłówkowych klienta MQTT kod aplikacji może korzystać z usług MQTT opisanych w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b49df-118">Once the MQTT Client header files are included, the application code is then able to use the MQTT services described later in this guide.</span></span> <span data-ttu-id="b49df-119">Aplikacja musi również zawierać *nxd_mqtt_client. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b49df-119">The application must also include *nxd_mqtt_client.c* in the build process.</span></span> <span data-ttu-id="b49df-120">Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b49df-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="b49df-121">To wszystko, co jest wymagane do korzystania z programu NetX Duo MQTT Client.</span><span class="sxs-lookup"><span data-stu-id="b49df-121">This is all that is required to use NetX Duo MQTT Client.</span></span>

## <a name="using-mqtt-client-with-netx-secure-tls"></a><span data-ttu-id="b49df-122">Korzystanie z MQTT Client with NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="b49df-122">Using MQTT Client with NetX Secure TLS</span></span>

<span data-ttu-id="b49df-123">Aby można było używać klienta MQTT z modułem Secure TLS NetX, aplikacja musi mieć zainstalowany moduł NetX Secure TLS i zawierać *nx_secure_tls_api. h* i *nx_crypto. h*.</span><span class="sxs-lookup"><span data-stu-id="b49df-123">To use MQTT client with NetX Secure TLS module, application must have NetX Secure TLS module installed, and include *nx_secure_tls_api.h* and *nx_crypto.h*.</span></span> <span data-ttu-id="b49df-124">Biblioteka MQTT musi być skompilowana przy użyciu zdefiniowanego symbolu ***NX_SECURE_ENABLE*** .</span><span class="sxs-lookup"><span data-stu-id="b49df-124">The MQTT library must be built with the symbol ***NX_SECURE_ENABLE*** defined.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="b49df-125">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b49df-125">Configuration Options</span></span>

<span data-ttu-id="b49df-126">Istnieje kilka opcji konfiguracji do kompilowania klienta MQTT dla NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b49df-126">There are several configuration options for building MQTT client for NetX Duo.</span></span> <span data-ttu-id="b49df-127">Poniżej znajduje się lista wszystkich opcji, w których poszczególne są szczegółowo opisane.</span><span class="sxs-lookup"><span data-stu-id="b49df-127">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="b49df-128">Wartości domyślne są wyświetlane, ale można je zdefiniować ponownie przed włączeniem *nxd_mqtt_client. h.*</span><span class="sxs-lookup"><span data-stu-id="b49df-128">The default values are listed, but can be redefined prior to inclusion of *nxd_mqtt_client.h.*</span></span>

- <span data-ttu-id="b49df-129">**NX_DISABLE_ERROR_CHECKING**: zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów klienta MQTT.</span><span class="sxs-lookup"><span data-stu-id="b49df-129">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic MQTT client error checking.</span></span> <span data-ttu-id="b49df-130">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b49df-130">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="b49df-131">**NX_SECURE_ENABLE**: zdefiniowany klient MQTT jest oparty na obsłudze protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="b49df-131">**NX_SECURE_ENABLE**: Defined, MQTT Client is built with TLS support.</span></span>
<span data-ttu-id="b49df-132">Zdefiniowanie tego symbolu wymaga zainstalowania bezpiecznego modułu protokołu TLS NetX.</span><span class="sxs-lookup"><span data-stu-id="b49df-132">Defining this symbol requires NetX Secure TLS module to be installed.</span></span>
<span data-ttu-id="b49df-133">*NX_SECURE_ENABLE* nie jest domyślnie włączona. \* \*</span><span class="sxs-lookup"><span data-stu-id="b49df-133">*NX_SECURE_ENABLE* is not enabled by default.\*\*</span></span>
- <span data-ttu-id="b49df-134">**NXD_MQTT_REQUIRE_TLS**: zdefiniowane, aplikacja musi używać protokołu TLS do łączenia się z brokerem MQTT.</span><span class="sxs-lookup"><span data-stu-id="b49df-134">**NXD_MQTT_REQUIRE_TLS**: Defined, application must use TLS to connect to MQTT broker.</span></span> <span data-ttu-id="b49df-135">Ta funkcja wymaga zdefiniowania *NX_SECURE_ENABLE* .</span><span class="sxs-lookup"><span data-stu-id="b49df-135">This feature requires *NX_SECURE_ENABLE* defined.</span></span> <span data-ttu-id="b49df-136">Domyślnie ten symbol nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="b49df-136">By default, this symbol is not defined.</span></span>
- <span data-ttu-id="b49df-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="b49df-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="b49df-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="b49df-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="b49df-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: określa szybkość czasomierza MQTT w taktach czasomierza ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b49df-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: Defines the MQTT timer rate, in ThreadX timer ticks.</span></span> <span data-ttu-id="b49df-140">Ten czasomierz służy do śledzenia czasu od momentu wysłania ostatniej wiadomości sterującej MQTT i wysłania komunikatu MQTT PINGREQ przed upływem czasu utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="b49df-140">This timer is used to keep track of the time since last MQTT control message was sent, and sends out an MQTT PINGREQ message before the keep-alive time expires.</span></span> <span data-ttu-id="b49df-141">Ten czasomierz jest uaktywniany, jeśli klient nawiązuje połączenie z brokerem z ustawioną wartością czasomierza Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="b49df-141">This timer is activated if the client connects to the broker with a keep-alive timer value set.</span></span> <span data-ttu-id="b49df-142">Wartość domyślna to TX_TIMER_TICKS_PER_SECOND, która jest czasomierzem jednosekundowym.</span><span class="sxs-lookup"><span data-stu-id="b49df-142">The default value is TX_TIMER_TICKS_PER_SECOND, which is a one-second timer.</span></span>
- <span data-ttu-id="b49df-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: określa czas oczekiwania klienta MQTT na PINGRESP z brokera po wysłaniu przez niego MQTT PINGREQ.</span><span class="sxs-lookup"><span data-stu-id="b49df-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: Defines the time the MQTT client waits for PINGRESP from the broker after it sends out MQTT PINGREQ.</span></span> <span data-ttu-id="b49df-144">Jeśli nie otrzymasz PINGRESP po upływie tego limitu czasu, klient traktuje brokera jako nieodpowiadający i rozłącza się z brokerem.</span><span class="sxs-lookup"><span data-stu-id="b49df-144">If no PINGRESP is received after this timeout delay, the client treats the broker as non-responsive and disconnects itself from the broker.</span></span> <span data-ttu-id="b49df-145">Domyślne opóźnienie limitu czasu polecenia PING to TX_TIMER_TICKS_PER_SECOND, co jest jedną sekundą.</span><span class="sxs-lookup"><span data-stu-id="b49df-145">The default PING timeout delay is TX_TIMER_TICKS_PER_SECOND, which is one second.</span></span>
- <span data-ttu-id="b49df-146">**NXD_MQTT_SOCKET_TIMEOUT**: określa limit czasu w wywołaniu połączenia gniazda TCP podczas rozłączania z serwerem MQTT w taktach czasomierza.</span><span class="sxs-lookup"><span data-stu-id="b49df-146">**NXD_MQTT_SOCKET_TIMEOUT**: Defines the time out in the TCP socket disconnect call when disconnecting from the MQTT server in timer ticks.</span></span> <span data-ttu-id="b49df-147">Wartość domyślna to NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="b49df-147">The default value is NX_WAIT_FOREVER.</span></span>

## <a name="sample-mqtt-program"></a><span data-ttu-id="b49df-148">Przykładowy program MQTT</span><span class="sxs-lookup"><span data-stu-id="b49df-148">Sample MQTT program</span></span>

<span data-ttu-id="b49df-149">Poniższy program ilustruje prostą aplikację MQTT.</span><span class="sxs-lookup"><span data-stu-id="b49df-149">The following program illustrates a simple MQTT application.</span></span> <span data-ttu-id="b49df-150">W celu uproszczenia kody powrotne są uznawane za pomyślne, dlatego nie jest wykonywane żadne dalsze sprawdzanie błędów.</span><span class="sxs-lookup"><span data-stu-id="b49df-150">For simplicity, the return codes are assumed to be successful, therefore no further error checking is done.</span></span>

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
