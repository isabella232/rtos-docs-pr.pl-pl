---
title: Rozdział 2 — Instalowanie i korzystanie z klienta POP3 usługi Azure RTO NetX
description: Klient POP3 NetX zawiera jeden plik źródłowy, jeden plik nagłówkowy i plik demonstracyjny. Istnieją dwa dodatkowe pliki dla usług MD5 Digest.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24de396c69d458866f9423fd995bcb8d905f29c8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822567"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a>Rozdział 2 — Instalowanie i korzystanie z klienta POP3 usługi Azure RTO NetX

Klient POP3 NetX zawiera jeden plik źródłowy, jeden plik nagłówkowy i plik demonstracyjny. Istnieją dwa dodatkowe pliki dla usług MD5 Digest. Istnieje również plik PDF podręcznika użytkownika (ten dokument).

- plik źródłowy **nx_pop3_client. c**: c dla interfejsu API klienta POP3 NetX
- **nx_pop3_client. h**: plik nagłówkowy języka C dla interfejsu API klienta NetX POP3
- **demo_netxduo_pop3_client. c**: plik demonstracyjny dotyczący tworzenia klienta POP3 i inicjowania sesji
- plik źródłowy **nx_md5. c**: c Definiowanie usług MD5 Digest
- **nx_md5. h**: plik nagłówkowy C definiujący usługi MD5 Digest
- **nx_pop3_client.pdf**: Podręcznik użytkownika klienta POP3 NetX

Aby można było korzystać z klienta POP3 NetX, cała wymieniona wyżej dystrybucja może zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowany w katalogu "*\threadx\mcf5272\green*", wówczas pliki *nx_md5. h*, *nx_md5. c,* *nx_pop3_client. h i nx_pop3_client. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-netx-pop3-client"></a>Korzystanie z klienta POP3 NetX

Aby można było korzystać z usługi klienta POP3 NetX, aplikacja musi dodać *nx_pop3_client. c* do projektu kompilacji. Kod aplikacji musi zawierać *nx_md5. h, nx_pop3. h i nx_pop3_client. h* po *tx_api. h* i *nx_api. h*, aby można było korzystać z ThreadX i NetX.

Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i kod obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z klienta POP3 NetX.

## <a name="small-example-of-the-netx-pop3-client"></a>Niewielki przykład klienta POP3 NetX

Przykład korzystania z usług klienta POP3 NetX został opisany na rysunku 1, który pojawia się poniżej. Ten pokaz konfiguruje dwa wywołania zwrotne w celu powiadomienia o pobraniach poczty i zakończeniu sesji w wierszach 37 i 38. Pula pakietów klienta POP3 jest tworzona w wierszu 76. Zadanie wątku IP jest tworzone w wierszu 88. Należy zauważyć, że ta pula pakietów jest również używana dla puli pakietów klienta POP3. Protokół TCP jest włączony w zadaniu IP w wierszu 107.

Klient POP3 jest tworzony w wierszu 133 wewnątrz funkcji wprowadzania wątku aplikacji, *demo_thread_entry*. Wynika to z faktu, że usługa *nx_pop3_client_create* próbuje nawiązać połączenie TCP z serwerem POP3. Jeśli to się powiedzie, aplikacja wysyła zapytanie do serwera POP3 o liczbę elementów w maildrop w wierszu 149 przy użyciu usługi *nx_pop3_client_mail_items_get* .

Jeśli istnieje co najmniej jeden element, aplikacja iteruje przez pętlę while dla każdego elementu poczty, aby pobrać wiadomość e-mail. Żądanie RETR jest wykonywane w wierszu 149 w wywołaniu *nx_pop3_client_mail_item_get* . Jeśli to się powiedzie, aplikacja pobiera pakiety przy użyciu usługi *nx_pop3_client_mail_item_message_get* w wierszu 177 do czasu, aż wykryje ostatni pakiet w komunikacie w wierszu 196. Na koniec aplikacja usuwa element poczty, przy założeniu, że w wierszu 199 w wywołaniu *nx_pop3_client_mail_item_delete* nastąpiło pomyślne pobranie. W dokumencie RFC 1939 zaleca się, aby klienci POP3 instruują serwer, aby usunął pobrane elementy poczty, aby zapobiec wysyłaniu poczty w maildrop klienta. Serwer może to zrobić automatycznie.

Po pobraniu wszystkich elementów poczty lub niepowodzeniu wywołania usługi klienta POP3 aplikacja kończy działanie pętli i usuwa klienta POP3 w wierszu 217 przy użyciu usługi *nx_pop3_client_delete* .

```c
/*
    demo_netxduo_pop3.c

    This is a small demo of POP3 Client on the NetX TCP/IP stack.
    This demo relies on Thread, NetX and POP3 Client API to conduct
    a POP3 mail session.
*/

#include "tx_api.h"
#include "nx_api.h"
#include "nx_pop3_client.h"

#define DEMO_STACK_SIZE        4096
#define CLIENT_ADDRESS         IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS         IP_ADDRESS(192,2,2,89)
#define SERVER_PORT            110

/* Replace the 'ram' driver with your own Ethernet driver. */
void _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client. */

TX_THREAD          demo_client_thread;
NX_POP3_CLIENT     demo_client;
NX_PACKET_POOL     client_packet_pool;
NX_IP              client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void     demo_thread_entry(ULONG info);

/* Shared secret is the same as password. */

#define LOCALHOST              "recipient@domain.com"
#define LOCALHOST_PASSWORD     "testpwd"

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *free_memory_pointer;

    /* Setup the working pointer. */
    free_memory_pointer = first_unused_memory;

    /* Create a client thread. */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                    free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer = free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* The demo client username and password is the authentication
    data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status = nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                        PAYLOAD_SIZE, free_memory_pointer, (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);

    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                            CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                            _nx_ram_network_driver, free_memory_pointer,
                            2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}

/* Define the application thread entry function. */

void demo_thread_entry(ULONG info)
{

UINT          status;
UINT          mail_item, number_mail_items;
UINT          bytes_downloaded = 0;
UINT          final_packet = NX_FALSE;
ULONG         total_size, mail_item_size, bytes_retrieved;
NX_PACKET     *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);

    /* Create a NetX POP3 Client instance with no byte or block memory pools.
    Note that it uses its password for its APOP shared secret. */
    status = nx_pop3_client_create(&demo_client,
                        NX_TRUE,
                        &client_ip, &client_packet_pool, SERVER_ADDRESS,
                        SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox. */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items, &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {
        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items. */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {

        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item, &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely downloaded. */

        while((final_packet == NX_FALSE) && (status == NX_SUCCESS))
        {
            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {
                break;
            }

            if (bytes_retrieved != 0)
            {

            printf("Received %d bytes of data for item %d: %s\n",
                    packet_ptr -> nx_packet_length,
                    mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);
    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client. This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

Rysunek 1. Przykład aplikacji klienckiej NetX POP3

## <a name="pop3-client-configuration-options"></a>Opcje konfiguracji klienta POP3

Istnieje kilka opcji konfiguracji dla klienta POP3 NetX. Poniżej znajduje się lista wszystkich opcji opisanych szczegółowo:

- **NX_POP3_CLIENT_PACKET_TIMEOUT**: definiuje opcję oczekiwania w sekundach dla klienta POP3 do przydzielenia pakietu. Wartość domyślna to 1 sekunda.

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT**: definiuje opcję oczekiwania w sekundach dla klienta POP3 do nawiązywania połączenia z serwerem POP3. Wartość domyślna to 30 sekund.

- **NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: określa opcję oczekiwania w sekundach, przez którą klient POP3 ma rozłączyć się z serwerem POP3. Wartość domyślna to 2 sekundy.

- **NX_POP3_TCP_SOCKET_SEND_WAIT**: Ta opcja ustawia opcję oczekiwania w sekundach w przypadku wywołań usługi *nx_tcp_socket_send* . Wartość domyślna to 2 sekundy.

- **NX_POP3_SERVER_REPLY_TIMEOUT**: Ta opcja ustawia opcję oczekiwania w *nx_tcp_socket_receive* wywołania usługi dla odpowiedzi serwera na żądanie klienta. Wartość domyślna to 10 sekund.

- **NX_POP3_CLIENT_TCP_WINDOW_SIZE**: Ta opcja ustawia rozmiar okna odbierania protokołu TCP klienta. Ta wartość powinna być równa rozmiarowi jednostki MTU wystąpienia IP pomniejszonej o adres IP i nagłówek TCP. Wartość domyślna to 1460.

- **NX_POP3_MAX_USERNAME**: Ta opcja ustawia rozmiar buforu nazwy użytkownika klienta POP3. Wartość domyślna to 40 bajtów.

- **NX_POP3_MAX_PASSWORD**: Ta opcja ustawia rozmiar buforu hasła klienta POP3. Wartość domyślna to 20 bajtów.