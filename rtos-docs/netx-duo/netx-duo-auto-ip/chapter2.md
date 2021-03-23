---
title: Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo AutoIP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo AutoIP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822074"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo AutoIP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo AutoIP.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO NetX AutoIP można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Pakiet zawiera trzy pliki źródłowe, jedno dołączane pliki i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nx_auto_ip. h**: plik nagłówkowy dla NetX AutoIP
- plik źródłowy **nx_auto_ip. c**: c dla NetX AutoIP
- plik źródłowy **demo_netx_auto_ip. c**: c dla demonstracji NetX AutoIP
- **nx_auto_ip.pdf**: Opis pliku PDF NetX AutoIP

## <a name="autoip-installation"></a>Instalacja AutoIP

Aby można było korzystać z programu NetX AutoIP, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_auto_ip. h*, *nx_auto_ip. c* i *demo_netx_auto_ip. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-autoip"></a>Korzystanie z AutoIP

Korzystanie z programu NetX AutoIP jest proste. W zasadzie kod aplikacji musi zawierać *nx_auto_ip. h* po zawiera *tx_api. h* i *nx_api. h*, aby można było użyć ThreadX i NetX. Po dołączeniu *nx_auto_ip. h* kod aplikacji jest następnie w stanie umożliwić wywoływanie funkcji AutoIP w dalszej części tego przewodnika. Aplikacja musi również zawierać *nx_auto_ip. c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z NetX AutoIP.

> [!NOTE]
> Ponieważ AutoIP korzysta z usług NetX ARP, należy włączyć protokół ARP z wywołaniem *nx_arp_enable* przed użyciem AutoIP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład, jak łatwo jest używać NetX AutoIP jest opisany na rysunku 1,1, który jest widoczny poniżej. W tym przykładzie AutoIP dołączenia pliku *nx_auto_ip. h* jest w wierszu 002. Następnie wystąpienie NetX AutoIP jest tworzone w lokalizacji "*tx_application_define*" w wierszu 090. Należy zauważyć, że blok sterujący NetX AutoIP "auto_ip_0" został wcześniej zdefiniowany jako zmienna globalna w wierszu 015. Po pomyślnym utworzeniu NetX AutoIP jest uruchamiany w wierszu 098. Przetwarzanie funkcji wywołania zwrotnego zmiany adresu IP zaczyna się w wierszu 105, który jest używany do obsługi kolejnych konfliktów lub rozpoznawania adresów DHCP.

> [!NOTE]
> W poniższym przykładzie przyjęto założenie, że urządzenie hosta jest urządzeniem pojedynczym. W przypadku urządzenia wieloadresowego aplikacja hosta może korzystać z *nx_auto_ip_interface_* usługi NetX AutoIP, aby określić pomocniczy interfejs sieciowy do sondowania adresu IP. Więcej informacji na temat konfigurowania aplikacji wieloadresowych można znaleźć w [podręczniku użytkownika NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) . Zwróć uwagę na to, że aplikacja hosta powinna używać interfejsu API NetX *nx_status_ip_interface_check* , aby zweryfikować, że AutoIP uzyskała adres IP.

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

Rysunek 1,1 przykład użycia AutoIP z NetX

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania NetX AutoIP. Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:

- **NX_DISABLE_ERROR_CHECKING**: zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów AutoIP. Jest on zazwyczaj używany po debugowaniu aplikacji.
- **NX_AUTO_IP_PROBE_WAIT**: liczba sekund oczekiwania przed wysłaniem pierwszej sondy. Domyślnie ta wartość jest definiowana jako 1.
- **NX_AUTO_IP_PROBE_NUM**: liczba sond protokołu ARP do wysłania. Domyślnie ta wartość jest definiowana jako 3.
- **NX_AUTO_IP_PROBE_MIN**: minimalna liczba sekund oczekiwania między wysłaniem sond. Domyślnie ta wartość jest definiowana jako 1.
- **NX_AUTO_IP_PROBE_MAX**: Maksymalna liczba sekund oczekiwania między wysłaniem sond. Domyślnie ta wartość jest definiowana jako 2.
- **NX_AUTO_IP_MAX_CONFLICTS**: liczba konfliktów AutoIP przed zwiększeniem opóźnień przetwarzania. Domyślnie ta wartość jest definiowana jako 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: liczba sekund określająca czas oczekiwania w przypadku przekroczenia całkowitej liczby konfliktów. Domyślnie ta wartość jest definiowana jako 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: liczba sekund oczekiwania przed wysłaniem anonsu. Domyślnie ta wartość jest definiowana jako 2.
- **NX_AUTO_IP_ANNOUNCE_NUM**: liczba ANONSÓW protokołu ARP do wysłania. Domyślnie ta wartość jest definiowana jako 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: liczba sekund oczekiwania między wysłaniem ogłaszania. Domyślnie ta wartość jest definiowana jako 2.
- **NX_AUTO_IP_DEFEND_INTERVAL**: liczba sekund oczekiwania między podwyższeniem poziomu zabezpieczeń. Domyślnie ta wartość jest definiowana jako 10.
