---
title: Rozdział 2 . Instalowanie i używanie aplikacji Azure RTOS NetX Duo AutoIP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTOS NetX Duo AutoIP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56bd8cd3cc361bbe0ec435012251e751af8c1566d01e8d52ff38d2eb9c381bfd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790517"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>Rozdział 2 . Instalowanie i używanie aplikacji Azure RTOS NetX Duo AutoIP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTOS NetX Duo AutoIP.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS NetX AutoIP można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Pakiet zawiera trzy pliki źródłowe, jeden plik dołączany i plik PDF zawierający ten dokument w następujący sposób:

- **nx_auto_ip.h:** Plik nagłówka dla funkcji NetX AutoIP
- **nx_auto_ip.c:** plik źródłowy C dla funkcji NetX AutoIP
- **demo_netx_auto_ip.c:** Plik źródłowy języka C dla pokazu funkcji AutoIP netX
- **nx_auto_ip.pdf:** opis PDF funkcji NetX AutoIP

## <a name="autoip-installation"></a>Instalacja funkcji AutoIP

Aby można było korzystać z funkcji NetX AutoIP, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX. Jeśli na przykład netx jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nx_auto_ip.h*, *nx_auto_ip.c* i *demo_netx_auto_ip.c.*

## <a name="using-autoip"></a>Korzystanie z funkcji AutoIP

Korzystanie z funkcji NetX AutoIP jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_auto_ip.h* po dołączyć *tx_api.h* i *nx_api.h,* aby można było używać threadX i NetX. Po *nx_auto_ip.h* kod aplikacji może następnie wykonać wywołania funkcji AutoIP określone w dalszej części tego przewodnika. Aplikacja musi również *uwzględniać nx_auto_ip.c* w procesie kompilacji. Te pliki muszą zostać skompilowane w taki sam sposób, jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z funkcji NetX AutoIP.

> [!NOTE]
> Ze względu na to, że funkcja AutoIP korzysta  z usług ARP NetX, należy włączyć obsługę nx_arp_enable przed użyciem funkcji AutoIP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład łatwego korzystania z funkcji NetX AutoIP opisano na rysunku 1.1, który znajduje się poniżej. W tym przykładzie plik dołączania funkcji AutoIP *nx_auto_ip.h* jest przekierowyny w wierszu 002. Następnie wystąpienie netx autoIP jest tworzone w ciągu "*tx_application_define*" w wierszu 090. Zwróć uwagę, że blok sterowania NetX AutoIP "auto_ip_0" został wcześniej zdefiniowany jako zmienna globalna w wierszu 015. Po pomyślnym utworzeniu aplikacja NetX AutoIP jest uruchomiona w wierszu 098. Przetwarzanie funkcji wywołania zwrotnego zmiany adresu IP rozpoczyna się w wierszu 105, który jest używany do obsługi kolejnych konfliktów lub możliwego rozpoznawania adresów DHCP.

> [!NOTE]
> W poniższym przykładzie przyjęto założenie, że urządzenie hosta jest urządzeniem jednoademowym. W przypadku urządzenia wieloadresowego aplikacja hosta może używać zestawu nx_auto_ip_interface_ NetX AutoIP w celu określenia pomocniczego interfejsu sieciowego do sondowania adresu IP. Aby uzyskać więcej informacji na temat konfigurowania aplikacji wieloadresowych, zobacz NetX User Guide (Podręcznik użytkownika [netx).](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) Ponadto aplikacja hosta powinna używać interfejsu *API* NetX nx_status_ip_interface_check, aby sprawdzić, czy usługa AutoIP uzyskała adres IP.

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

Rysunek 1.1 Przykład użycia funkcji AutoIP z netX

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji tworzenia funkcji NetX AutoIP. Poniżej znajduje się lista wszystkich opcji, gdzie każda z nich jest szczegółowo opisana:

- **NX_DISABLE_ERROR_CHECKING:** zdefiniowana, ta opcja usuwa podstawowe sprawdzanie błędów funkcji AutoIP. Jest on zwykle używany po debugowaniu aplikacji.
- **NX_AUTO_IP_PROBE_WAIT:** liczba sekund oczekiwania przed wysłaniem pierwszej sondy. Domyślnie ta wartość jest zdefiniowana jako 1.
- **NX_AUTO_IP_PROBE_NUM:** liczba sond ARP do wysłania. Domyślnie ta wartość jest zdefiniowana jako 3.
- **NX_AUTO_IP_PROBE_MIN:** minimalna liczba sekund oczekiwania między wysyłaniem sond. Domyślnie ta wartość jest zdefiniowana jako 1.
- **NX_AUTO_IP_PROBE_MAX:** maksymalna liczba sekund oczekiwania między wysyłaniem sond. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_MAX_CONFLICTS:** Liczba konfliktów funkcji AutoIP przed zwiększeniem opóźnień przetwarzania. Domyślnie ta wartość jest zdefiniowana jako 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL:** liczba sekund, o które ma być wydłużony okres oczekiwania po przekroczeniu całkowitej liczby konfliktów. Domyślnie ta wartość jest zdefiniowana jako 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT:** liczba sekund oczekiwania przed wysłaniem powiadomienia. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_ANNOUNCE_NUM:** liczba ogłaszanych wiadomości ARP. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL:** liczba sekund oczekiwania między wysłaniem na głos. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_DEFEND_INTERVAL:** liczba sekund oczekiwania między głosami obrony. Domyślnie ta wartość jest zdefiniowana jako 10.
