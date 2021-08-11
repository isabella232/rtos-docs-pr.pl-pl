---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS NetX PPPoE Server
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS NetX PPPoE Server.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5e93d783299448301c4e79a324ccec01473dbcce3fb96d25d7be352384d4fa53
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796331"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS NetX PPPoE Server

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS NetX PPPoE Server.

## <a name="product-distribution"></a>Dystrybucja produktów

Serwer PPPoE dla NetX jest dostępny na stronie [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Pakiet zawiera dwa pliki źródłowe i plik PDF zawierający ten dokument w następujący sposób:

- **nx_pppoe_server.h:** plik nagłówka dla serwera PPPoE dla NetX
- **nx_pppoe_server.c:** plik źródłowy języka C dla serwera PPPoE dla NetX
- **nx_pppoe_server.pdf:** opis PDF serwera PPPoE dla netx
- **demo_netx_pppoe_server.c:** Pokaz serwera NetX PPPoE

## <a name="pppoe-server-installation"></a>Instalacja serwera PPPoE

Aby można było używać serwera PPPoE dla netx, cała dystrybucja, o której wspomniano wcześniej, powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano platformę NetX. Jeśli na przykład netx jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nx_pppoe_server.h* i *nx_pppoe_server.c.*

## <a name="using-pppoe-server"></a>Korzystanie z serwera PPPoE

Korzystanie z serwera PPPoE dla netx jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_pppoe_server.h* po dojecheniu do plików *tx_api.h* i *nx_api.h,* aby można było używać odpowiednio threadX i NetX. Po *nx_pppoe_server.h* kod aplikacji może następnie wykonać wywołania funkcji serwera PPPoE określone w dalszej części tego przewodnika. Aplikacja musi również uwzględniać *nx_pppoe_server.c* w procesie kompilacji. Ten plik musi zostać skompilowany w taki sam sposób, jak inne pliki aplikacji, a jego formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z serwera NetX PPPoE.

## <a name="small-example-system"></a>Mały przykładowy system

Poniżej przedstawiono przykład, który ilustruje sposób korzystania z serwera NetX PPPoE, opisano na rysunku 1.1. W tym przykładzie serwer PPPoE zawiera plik *nx_pppoe_server.h* jest w wierszu 50. Następnie serwer PPPoE jest tworzony w ciągu *"thread_0_entry"* w wierszu 248. Należy pamiętać, że serwer PPPoE powinien zostać utworzony po utworzeniu wystąpienia adresu IP. Wystąpienie adresu IP zostanie utworzone i zainicjowane wiersz165. Blok sterowania serwera PPPoE "*pppoe_server*" został wcześniej zdefiniowany jako zmienna globalna w wierszu 79. Funkcje powiadamiania są ustawiane w wierszu 257. Należy pamiętać pppoe_session_data_receive należy ustawić funkcję notify. Po pomyślnym utworzeniu serwera IP i PPPoE, proces serwera PPPoE ustanawiania sesji PPPoE w wywołaniu nx_pppoe_server_enable wierszu 272.

Ogólnie rzecz biorąc, moduł PPPoE powinien być używany z modułem PPP. W tym przykładzie plik dołączania serwera PPP *nx_ppp.h* jest dołączany w wierszu 49. Następnie serwer PPP jest tworzony w wierszu 174. Wiersz 182 skonfiguruje funkcję do wysyłania pakietu PPP. Wiersz 188-200 skonfiguruj adresy IP i zdefiniuj protokół PAP. Wiersz 115-139 skonfiguruj nazwę użytkownika i hasło dla protokołu PAP.

Po nawiązyniu sesji PPPoE. Aplikacja może wywołać nx_pppoe_server_session_get, aby uzyskać informacje o sesji (adres MAC klienta i identyfikator sesji) w wierszu 281.

Gdy aplikacja nie będzie już przetwarzać ruchu PPP, aplikacja PppCloseInd lub nx_pppoe_server_session_terminate zakończy sesję PPPoE.

> [!NOTE]
> W tym przykładzie serwer PPPoE działa ze zwykłym stosem adresów IP w tym samym czasie i współużytkuje jeden sterownik Ethernet. Przekaż ten sam sterownik Ethernet dla normalnego wystąpienia adresu IP w wierszu 165 i w wystąpieniu serwera PPPoE w wierszu 248.

> [!NOTE]
> Funkcje są udostępniane przez implementację ppPoE do wywoływania przez oprogramowanie w ramach zdefiniowanych NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.

Jeśli jest zdefiniowana, włącza funkcję, która kontroluje sesję PPPoE.

Serwer PPPoE nie będzie automatycznie odpowiedzią na żądanie, dopóki aplikacja nie wywoła określonego interfejsu API, jeśli nie zostanie zdefiniowany, serwer PPPoE automatycznie odezwą na żądanie. Domyślnie włącza on w programie nx_pppoe_server.h.

Pamiętaj, że zmień **NX_PHYSICAL_HEADER** na 24, aby zapewnić wystarczającą ilość miejsca do wypełnienia nagłówka fizycznego. Nagłówek fizyczny:14 (nagłówek Ethernet) + 6 (nagłówek PPPoE) + 2 (nagłówek PPP) + 2 (kwalifikowanie z czterema bajtami).

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

Rysunek 1.1 Przykład użycia serwera PPPoE z netx

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji tworzenia serwera PPPoE dla netx. Na poniższej liście szczegółowo opisano poszczególne z nich:

- **NX_DISABLE_ERROR_CHECKING:** zdefiniowana, ta opcja usuwa podstawowe sprawdzanie błędów serwera PPPoE. Jest on zwykle używany po debugowaniu aplikacji.

- **NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE:** jeśli jest zdefiniowana, włącza funkcję, która kontroluje sesję PPPoE. Serwer PPPoE nie będzie automatycznie odpowiedzią na żądanie, dopóki aplikacja nie wywoła określonego interfejsu API.

- **NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE:** jeśli ta opcja jest zdefiniowana, umożliwia funkcji inicjowanie sterownika Ethernet w module PPPoE. Domyślnie jest ona wyłączana.

- **NX_PPPOE_SERVER_THREAD_TIME_SLICE:** opcja fragmentatora czasu dla wątku serwera PPPoE. Domyślnie ta wartość jest TX_NO_TIME_SLICE.

- **NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER:** definiuje maksymalną liczbę współbieżnych sesji klientów. Domyślnie ta wartość to 10.

- **NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE:** określa maksymalny rozmiar hosta Uniq. Domyślnie ta wartość to 32.

- **NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE:** określa maksymalny rozmiar identyfikatora sesji przekaźnika. Domyślnie ta wartość to 12.

- **NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE:** określa minimalny rozmiar ładunku pakietu dla serwera PPPoE. Jeśli rozmiar ładunku pakietu jest większy niż ta wartość, można uniknąć łańcucha pakietów. Domyślnie ta wartość to 1520 (maksymalny rozmiar ładunku Ethernet 1500, nagłówek Ethernet 14, CRC 2 i wyrównanie 4 bajtów).

- **NX_PPPOE_SERVER_PACKET_TIMEOUT:** Definiuje to potion oczekiwania (w taktach czasomierza) do przydzielania pakietów lub dołączania danych do pakietów. Domyślnie ta wartość to **NX_IP_PERIODIC_RATE** (100 takt).

- **NX_PPPOE_SERVER_START_SESSION_ID:** definiuje identyfikator sesji uruchamiania do przypisania do sesji PPPoE. Domyślnie ta wartość to 0X4944(wartość ASCII identyfikatora).