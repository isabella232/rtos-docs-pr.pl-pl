---
title: Dodatek A — opis funkcji przywracania stanu dla usług klienta DHCP Azure RTOS NetX Duo
description: Ten rozdział zawiera opis funkcji przywracania stanu dla usług klienta DHCP Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b6d01930abdf7dd9d91ebe2e60eaac69ac73d2663a10263f07380e5c2895551
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788460"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a>Dodatek A: Opis funkcji przywracania stanu dla usług klienckich DHCP Azure RTOS NetX Duo

Opcja konfiguracji klienta NetX Duo DHDP, NX_DHCP_CLIENT_RESTORE_STATE, umożliwia systemowi przywrócenie wcześniej utworzonego rekordu klienta DHCP w stanie Powiązana między ponownym uruchomieniem systemu.

Po włączeniu tej opcji aplikacja może wstrzymać i wznowić wątek klienta DHCP. Istnieje również usługa aktualizowania klienta DHCP o czas, który upłynął między wstrzymaniem i wznowienie wątku.

## <a name="restoring-the-dhcp-client-between-reboots"></a>Przywracanie klienta DHCP między ponownymi uruchomieniami

Przed przywróceniem klienta DHCP po ponownym uruchomieniu, wcześniej utworzony klient DHCP, który musi osiągnąć stan Powiązana i ma przypisany adres IP z serwera DHCP. Zanim aplikacja DHCP zostanie wyzjemnia, musi zapisać bieżący rekord klienta DHCP w pamięci trwałej. Musi być również niezależny "strażnik czasu" w innym miejscu w systemie, aby śledzić czas, który upłynął podczas tego stanu wyłączonych zasilania. W przypadku zasilania aplikacja tworzy nowe wystąpienie klienta DHCP, a następnie aktualizuje je przy użyciu wcześniej utworzonego rekordu klienta DHCP. Upłynął czas uzyskany od "strażnika czasu", a następnie zastosowany do czasu pozostałego w dzierżawie klienta DHCP. Należy pamiętać, że może to spowodować, że klient DHCP zmieni stany, np. z POWIĄZANA na ODNAWIANIE. W tym momencie aplikacja może wznowić działanie klienta DHCP.

Jeśli czas, który upłynął podczas zasilania, ustawia stan klienta DHCP w stanie RENEW lub REBIND, klient DHCP automatycznie zainicjuje komunikaty DHCP żądające odnowienia lub ponownego połączenia dzierżawy adresu IP. Jeśli adres IP wygasł, klient DHCP automatycznie wyczyści adres IP w wystąpieniu adresu IP i rozpocznie proces DHCP od stanu INIT, żądając nowego adresu IP.

W ten sposób klient DHCP może działać między ponownymi uruchomieniami, tak jakby był nieprzerwany.

Poniżej przedstawiono ilustrację tej funkcji. Przyjęto założenie, że klient DHCP jest uruchomiony tylko w interfejsie podstawowym.

```c
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{
    /* No previously saved Client record. Start the DHCP Client in the INIT state.  */
    status =  nx_dhcp_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    do
    {
        /* Wait for DHCP to assign the IP address.  */
    } while (status != NX_SUCCESS);

    /* We have a valid IP address. */
    /* At some point decide we power down the system. */
    /* Save the Client state data which we will subsequently need to restore the DHCP    
       Client. */
    status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);               

    /* Copy this memory to non-volatile memory (not shown). */
    /* Delete the IP and DHCP Client instances before powering down. */
    nx_dhcp_delete(&dhcp_0);

    nx_ip_delete(&ip_0);
    /* Ready to power down, having released other resources as necessary. */

}
else
{

    /* The application has determined there is a previously saved record. We will 
        restore it to the current DHCP Client instance.  */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
        update the IP instance with IP address, mask etc. */
    status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

    if (status != NX_SUCCESS)
        return;

    /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
    status = nx_dhcp_resume(&dhcp_0);

    if (status != NX_SUCCESS)
        return;

}
```
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>Wznawianie wątku klienta DHCP po wstrzymaniu 

Aby wstrzymać wątek klienta DHCP bez zasilania, aplikacja wywołuje nx_dhcp_suspend klienta DHCP, który osiągnął stan BOUND i który ma prawidłowy adres IP.  Gdy klient DHCP jest gotowy do wznowienia, najpierw wywołuje usługę *nx_dhcp_client_update_time_remaining* w celu zaktualizowania czasu pozostałego na dzierżawie adresu DHCP (uzyskanie czasu, który upłynął od niezależnego strażnika czasu). Następnie wywołuje on *nx_dhcp_resume,* aby wznowić wątek klienta DHCP.

Jeśli upłynął czas, w którym stan klienta DHCP jest ustawiany w stanie RENEW lub REBIND, klient DHCP automatycznie zainicjuje komunikaty DHCP żądające odnowienia lub ponownego połączenia dzierżawy adresu IP. Jeśli adres IP wygasł, klient DHCP automatycznie wyczyści adres IP i rozpocznie proces DHCP ze stanu INIT, żądając nowego adresu IP.

Poniżej przedstawiono ilustrację użycia tej funkcji.

```c
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client.  */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   /* Wait for DHCP to obtain an IP address.  */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the network...  */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the elapsed      
     time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}

```
Poniżej znajduje się lista usług do przywracania stanu klienta DHCP z pamięci oraz do zawieszania i wznawiania klienta DHCP.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

Tworzenie rekordu bieżącego stanu klienta DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Opis

Ta usługa zapisuje klienta DHCP uruchomionego na pierwszym interfejsie włączonym dla protokołu DHCP znalezionego w wystąpieniu klienta DHCP w rekordzie wskazywanym przez record_ptr. Dzięki temu aplikacja klienta DHCP może przywrócić swój stan klienta DHCP po na przykład przy zasilaniu i ponownym uruchomieniu.

Aby zapisać rekord klienta DHCP w określonym interfejsie, jeśli dla protokołu DHCP jest włączony więcej niż *jeden interfejs,* użyj nx_dhcp_interface_client_get_record usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP
- **record_ptr:** wskaźnik do rekordu klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS (0x0) :** utworzony rekord klienta
- **NX_DHCP_NOT_BOUND:**(0x94) Klient nie jest w powiązanych stanach
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Brak włączonych interfejsów dla protokołu DHCP
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

Tworzenie rekordu bieżącego stanu klienta DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Opis

Ta usługa zapisuje klienta DHCP uruchomionego w określonym interfejsie w rekordzie wskazywanym przez record_ptr. Dzięki temu aplikacja klienta DHCP może przywrócić swój stan klienta DHCP po na przykład przy zasilaniu i ponownym uruchomieniu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP
- **interface_index:** indeks, na którym ma być rejestrowany rekord
- **record_ptr:** wskaźnik do rekordu klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS (0x0) :** utworzony rekord klienta
- **NX_DHCP_NOT_BOUND:**(0x94) Klient nie **jest w stanie Powiązana**
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Nieprawidłowy indeks interfejsu
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.
- NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a>nx_dhcp_ client_restore_record

Przywracanie klienta DHCP z wcześniej zapisanego rekordu

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji przywrócenie klienta DHCP z poprzedniej sesji przy użyciu rekordu klienta DHCP wskazywanego przez record_ptr. Dane time_elapsed są stosowane do czasu pozostałego w dzierżawie klienta DHCP.

Wymaga to, aby aplikacja klienta DHCP utworzyła rekord klienta DHCP przed jego zasilaniem i zapisała ten rekord w pamięci nieulotnej.

Jeśli dla klienta DHCP jest włączony więcej niż jeden interfejs, ta usługa jest stosowana do pierwszego prawidłowego interfejsu znalezionego w wystąpieniu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP
- **record_ptr:** wskaźnik do rekordu klienta DHCP 
- **time_elapsed:** czas do odjęcia od czasu dzierżawy pozostałego w wejściowym rekordzie klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x0) Przywrócono rekord klienta
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Brak interfejsów z uruchomionym serwerem DHCP
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a>nx_dhcp_interace_client_restore_record

Przywracanie klienta DHCP z wcześniej zapisanego rekordu w określonym interfejsie

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji przywrócenie klienta DHCP w określonym interfejsie przy użyciu rekordu klienta DHCP wskazywanego przez record_ptr. Dane time_elapsed są stosowane do czasu pozostałego w dzierżawie klienta DHCP.

Wymaga to, aby aplikacja klienta DHCP utworzyła rekord klienta DHCP przed jego zasilaniem i zapisała ten rekord w pamięci nieulotnej.

Jeśli dla klienta DHCP jest włączony więcej niż jeden interfejs, ta usługa jest stosowana do pierwszego prawidłowego interfejsu znalezionego w wystąpieniu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP
- **record_ptr:** wskaźnik do rekordu klienta DHCP 
- **time_elapsed:** czas do odjęcia od czasu dzierżawy pozostałego w wejściowym rekordzie klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x0) Przywrócono rekord klienta
- **NX_DHCP_NOT_BOUND:**(0x94) Klient nie jest powiązany z adresem IP
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Nieprawidłowy indeks interfejsu
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.
- NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a>nx_dhcp_ client_update_time_remaining

Aktualizowanie czasu pozostałego w dzierżawie klienta DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Opis

Ta usługa aktualizuje czas pozostały w dzierżawie adresu IP klienta DHCP przy użyciu danych wejściowych time_elapsed pierwszego interfejsu włączonego dla protokołu DHCP znalezionego w wystąpieniu klienta DHCP. Aplikacja musi wstrzymać wątek klienta DHCP przed użyciem tej usługi przy użyciu *nx_dhcp_suspend*. Po wywołaniu tej usługi aplikacja może wznowić wątek klienta DHCP, wywołując *nx_dhcp_resume*.

Jest to przeznaczone dla aplikacji klienckich DHCP, które muszą zawiesić wątek klienta DHCP na okres czasu, a następnie zaktualizować pozostały czas dzierżawy adresu IP.

Uwaga: Ta usługa nie jest przeznaczona do nx_dhcp_client_get_record *i* *nx_dhcp_client_restore_record* opisanych wcześniej). Te usługi zostały wcześniej opisane w tej sekcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP 
- **time_elapsed:** czas do odjęcia od czasu pozostałego w dzierżawie adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x0) Zaktualizowano dzierżawę adresu IP klienta
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Brak włączonych interfejsów dla protokołu DHCP
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a>nx_dhcp_interface_client_update_time_remaining

Aktualizowanie czasu pozostałego na dzierżawie klienta DHCP dla określonego interfejsu

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a>Opis

Ta usługa aktualizuje czas pozostały w dzierżawie adresu IP klienta DHCP przy użyciu time_elapsed danych wejściowych na określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Aplikacja musi wstrzymać wątek klienta DHCP przed użyciem tej usługi przy użyciu *nx_dhcp_suspend*. Po wywołaniu tej usługi aplikacja może wznowić wątek klienta DHCP, wywołując *nx_dhcp_resume*. Należy pamiętać, że wstrzymanie i wznowienie wątku klienta DHCP ma zastosowanie do wszystkich interfejsów włączonych dla protokołu DHCP.

Jest to przeznaczone dla aplikacji klienckich DHCP, które muszą zawiesić wątek klienta DHCP na okres czasu, a następnie zaktualizować pozostały czas dzierżawy adresu IP.

Uwaga: Ta usługa nie jest przeznaczona do nx_dhcp_client_get_record *i* *nx_dhcp_client_restore_record* opisanych wcześniej). Te usługi zostały wcześniej opisane w tej sekcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP
- **interface_index:** Indeksowanie do interfejsu w celu zastosowania czasu, do
- **time_elapsed:** czas do odjęcia od czasu pozostałego w dzierżawie adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x0) Zaktualizowano dzierżawę adresu IP klienta
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Nieprawidłowy indeks interfejsu
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik DHCP.
- NX_INVALID_INTERFACE: (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a>nx_dhcp_suspend

Wstrzymywanie wątku klienta DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa wstrzymuje bieżący wątek klienta DHCP. Należy *pamiętać, nx_dhcp_stop*, nie ma żadnych zmian stanu klienta DHCP, gdy ta usługa jest wywoływana.

Ta usługa wstrzymuje działanie protokołu DHCP na wszystkich interfejsach z włączoną obsługą protokołu DHCP.

Aby zaktualizować stan klienta DHCP z upływem czasu, gdy klient DHCP jest wstrzymany, zobacz *nx_dhcp_client_update_time_remaining* wcześniej. Aby wznowić wstrzymany wątek klienta DHCP, aplikacja powinna *wywołać* nx_dhcp_resume .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x0) Wątek klienta jest zawieszony
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

Wznawianie zawieszonego wątku klienta DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa wznawia zawieszony wątek klienta DHCP. Należy pamiętać, że po wznowieniu wątku klienta nie ma zmian rzeczywistego stanu klienta DHCP. Aby zaktualizować czas pozostały w dzierżawie adresu IP klienta DHCP o czas, który upłynął *przed* wywołaniem nx_dhcp_resume , zobacz *nx_dhcp_client_update_time_remaining* wcześniej.

Ta usługa wznawia działanie protokołu DHCP we wszystkich interfejsach włączonych dla protokołu DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr:** wskaźnik do klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x0) Wątek klienta jest wznawiany
- NX_PTR_ERROR: (0x16) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```