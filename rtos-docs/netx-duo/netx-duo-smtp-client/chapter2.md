---
title: Rozdział 2 — Instalowanie i korzystanie z klienta SMTP NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta SMTP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821690"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>Rozdział 2 — Instalowanie i korzystanie z klienta SMTP NetX Duo

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta SMTP NetX Duo.

## <a name="netx-duo-smtp-client-installation"></a>Instalacja klienta SMTP NetX Duo

Klient SMTP NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera następujące pliki:

- **nxd_smtp_client. c** Plik źródłowy języka C dla interfejsu API klienta SMTP NetX Duo
- **nxd_smtp_client. h** Plik nagłówkowy języka C dla interfejsu API klienta SMTP NetX Duo
- **demo_netxduo_smtp_client. c** Demonstracja dla klienta SMTP NetX Duo
- **Podręcznik użytkownikanxd_smtp_client.pdf** Interfejs API klienta SMTP NetX Duo

Aby użyć interfejsu API klienta SMTP NetX Duo, cała wymieniona wyżej dystrybucja może zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "c:*\myproject*", wówczas pliki *nxd_smtp_client. h i nxd_smtp_client. c* powinny być skopiowane do tego katalogu.

## <a name="using-netx-duo-smtp-client"></a>Korzystanie z klienta SMTP NetX Duo

Aby utworzyć aplikację kliencką SMTP NetX Duo, należy najpierw skompilować biblioteki ThreadX i NetX Duo oraz uwzględnić je w projekcie kompilacji. Aplikacja musi następnie uwzględnić TX *_api. h* i *nx_api. h w kodzie źródłowym aplikacji*. Spowoduje to włączenie usług ThreadX i NetX Duo. Musi on również zawierać *nxd_smtp_client. c* i *nxd_smtp_client. h* po *tx_api. h* i *Nx_api. h do korzystania z usług klienta SMTP.*

Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i kod obiektu muszą być połączone wraz z plikami aplikacji. Jest to wszystko wymagane do utworzenia aplikacji klienckiej SMTP NetX Duo.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład korzystania z klienta SMTP NetX Duo został opisany na rysunku 1, który pojawia się poniżej. Pula pakietów dla wystąpienia IP jest tworzona przy użyciu usługi nx_packet_pool_create w wierszu 68 i ma bardzo mały ładunek pakietu. Wynika to z faktu, że wystąpienie IP wysyła tylko pakiety sterujące, które nie wymagają dużo ładunku. Pula pakietów klienta SMTP utworzona w wierszu 84 i służy do przesyłania komunikatów klienta SMTP do danych serwera i komunikatów. Jego ładunek pakietu jest dużo większy. Wystąpienie protokołu IP jest tworzone w wierszu 118 przy użyciu tej samej puli pakietów. Protokół TCP, wymagany dla protokołu SMTP, jest włączony w wystąpieniu protokołu IP w wierszu 130.

W wątku aplikacji klient SMTP jest tworzony przy użyciu usługi *nxd_smtp_client_create* w wierszu 170. Usługa *nxd_smtp_client_create* obsługuje połączenia z serwerem SMTP IPv4 i IPv6, chociaż ten przykład jest ograniczony do protokołu IPv4. Następnie wiadomość e-mail zostanie przesłana do klienta SMTP w celu transmisji w wierszu 184 przy użyciu usługi *nx_smtp_mail_send* . Należy pamiętać, że wiersz tematu z nagłówkiem zawartości poczty jest tworzony niezależnie od treści komunikatu. Należy również zauważyć, że żądanie wysłania poczty akceptuje tylko jeden adres e-mail adresata, który jest traktowany pod kątem poprawności składniowej.

Następnie aplikacja kończy działanie klienta SMTP w wierszu 200. Usługa *nx_smtp_client_delete* sprawdza, czy połączenie gniazda zostało zamknięte i czy port jest niepowiązany. Należy pamiętać, że do aplikacji klienckiej SMTP należy usunąć pulę pakietów, jeśli nie ma już jej użycia.

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

**Rysunek 1. Przykład użycia klienta SMTP z NetX Duo**

## <a name="client-configuration-options"></a>Opcje konfiguracji klienta

Istnieje kilka opcji konfiguracji z interfejsem API klienta SMTP NetX Duo. Poniżej znajduje się lista wszystkich opcji opisanych szczegółowo:

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE** Ta opcja ustawia rozmiar okna odbierania klienta TCP. Ta wartość powinna być mniejsza niż rozmiar jednostki MTU podstawowego sprzętu sieci Ethernet i umożliwia miejsce dla nagłówków IP i TCP. Domyślny rozmiar okna klienta SMTP w programie NetX Duo to 1460.
- **NX_SMTP_CLIENT_PACKET_TIMEOUT** Ta opcja ustawia limit czasu dla alokacji pakietu NetX. Domyślny limit czasu pakietu klienta SMTP w programie NetX Duo wynosi 2 sekundy.
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT** Ta opcja ustawia limit czasu połączenia gniazda TCP klienta. Domyślny limit czasu połączenia klienta SMTP w programie NetX Duo wynosi 10 sekund.
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** Ta opcja ustawia limit czasu rozłączenia gniazda TCP klienta. Domyślny limit czasu rozłączenia klienta SMTP w programie NetX Duo wynosi 5 sekund *. Należy pamiętać, że jeśli klient SMTP napotka błąd wewnętrzny, taki jak zerwane połączenie, może przerwać połączenie z upływem limitu czasu oczekiwania na zero.
- **NX_SMTP_GREETING_TIMEOUT** Ta opcja określa limit czasu, przez który klient otrzymuje odpowiedź serwera na jego powitanie. Wartość domyślna klienta SMTP NetX Duo to 10 sekund.
- **NX_SMTP_ENVELOPE_TIMEOUT** Ta opcja określa limit czasu, przez który klient otrzymuje odpowiedź serwera na polecenie klienta. Wartość domyślna klienta SMTP NetX Duo to 10 sekund.
- **NX_SMTP_MESSAGE_TIMEOUT** Ta opcja określa limit czasu, przez który klient otrzymuje odpowiedź serwera w celu odebrania danych wiadomości e-mail. Wartość domyślna klienta SMTP NetX Duo to 30 sekund.
- **NX_SMTP_CLIENT_SEND_TIMEOUT** Ta opcja definiuje opcję oczekiwania buforu do przechowywania hasła użytkownika podczas uwierzytelniania SMTP na serwerze. Wartość domyślna to 20 bajtów.
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING** Ta opcja określa rozmiar buforu dla wyodrębniania wezwania serwera podczas uwierzytelniania SMTP. Wartość domyślna to 200 bajtów. W przypadku logowania i ZWYKŁEgo uwierzytelniania klient SMTP prawdopodobnie może użyć mniejszego buforu.
- **NX_SMTP_CLIENT_MAX_PASSWORD** Ta opcja określa rozmiar buforu do przechowywania hasła użytkownika podczas uwierzytelniania przy użyciu protokołu SMTP na serwerze programu. Wartość domyślna to 20 bajtów. 
- **NX_SMTP_CLIENT_MAX_USERNAME** Ta opcja określa rozmiar buforu do przechowywania nazwy użytkownika hosta podczas uwierzytelniania przy użyciu protokołu SMTP na serwerze programu. Wartość domyślna to 40 bajtów. 
