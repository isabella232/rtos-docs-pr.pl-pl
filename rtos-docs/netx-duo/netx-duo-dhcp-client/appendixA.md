---
title: Dodatek A — opis funkcji przywracania stanu dla usług klienta DHCP w systemie Azure RTO NetX Duo
description: Ten rozdział zawiera opis funkcji przywracania stanu dla usług klienta DHCP platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 008ca6fb0052339e188e0240cc38a81d3a6b40e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822050"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a>Dodatek A: Opis funkcji przywracania stanu dla usług klienta DHCP w systemie Azure RTO NetX Duo

NX_DHCP_CLIENT_RESTORE_STATE opcja konfiguracji klienta NetX Duo DHDP umożliwia systemowi przywrócenie wcześniej utworzonego rekordu klienta DHCP w stanie związanym między ponownymi uruchomieniami systemu.

Gdy ta opcja jest włączona, aplikacja może wstrzymywać i wznawiać wątek klienta DHCP. Istnieje również usługa do aktualizowania klienta DHCP z upływem czasu między wstrzymaniem i wznowieniem wątku.

## <a name="restoring-the-dhcp-client-between-reboots"></a>Przywracanie klienta DHCP między ponownymi uruchomieniami

Przed przystąpieniem do przywracania klienta DHCP po ponownym uruchomieniu komputera został wcześniej utworzony klient DHCP, który musi dotrzeć do powiązanego stanu i ma przypisany adres IP z serwera DHCP. Zanim będzie to możliwe, aplikacja DHCP musi zapisać bieżący rekord klienta DHCP w pamięci nieulotnej. W systemie musi być również niezależny opiekun czasowy, aby śledzić czas, który upłynął podczas tego stanu zasilania. W przypadku włączania aplikacji tworzy nowe wystąpienie klienta DHCP, a następnie aktualizuje je przy użyciu utworzonego wcześniej rekordu klienta DHCP. Czas, który upłynął, jest uzyskiwany z "czasu opiekuna", a następnie stosowany do pozostałego czasu dzierżawy klienta DHCP. Należy zauważyć, że może to spowodować zmianę Stanów przez klienta DHCP, np. z powiązanym z ODNAWIAniem. W tym momencie aplikacja może wznowić działanie klienta DHCP.

Jeśli czas, który upłynął podczas włączania usługi, powoduje, że stan klienta DHCP w stanie ODNOWIENIa lub ponownego powiązania, klient DHCP automatycznie inicjuje komunikaty DHCP żądające odnowienia lub ponownego powiązania dzierżawy adresu IP. Jeśli adres IP wygasł, klient DHCP automatycznie wyczyści adres IP w wystąpieniu IP i rozpocznie proces DHCP ze stanu INIT, żądając nowego adresu IP.

W ten sposób klient DHCP może działać między ponownymi uruchomieniami tak, jakby nie został przerwany.

Poniżej znajduje się ilustracja tej funkcji. To zakłada, że klient DHCP działa tylko w interfejsie podstawowym.

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
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>Wznawianie wątku klienta DHCP po zawieszeniu 

Aby wstrzymać wątek klienta DHCP bez wyłączania, aplikacja wywołuje *nx_dhcp_suspend* na kliencie DHCP, który osiągnął stan powiązany i ma prawidłowy adres IP. Gdy jest gotowy do wznowienia klienta DHCP, najpierw wywołuje *nx_dhcp_client_update_time_remaining* , aby zaktualizować pozostały czas w dzierżawie adresu DHCP (Uzyskiwanie czasu od niezależnego opiekuna). Następnie wywołuje *nx_dhcp_resume* , aby wznowić wątek klienta DHCP.

W przypadku przełączenia stanu klienta DHCP w stanie ODNOWIENIa lub ponownego powiązania klient DHCP automatycznie inicjuje komunikaty DHCP żądające odnowienia lub ponownego powiązania dzierżawy adresu IP. Jeśli adres IP wygasł, klient DHCP automatycznie wyczyści adres IP i rozpocznie proces DHCP ze stanu INIT, żądając nowego adresu IP.

Poniżej znajduje się ilustracja przedstawiająca korzystanie z tej funkcji.

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
Poniżej znajduje się lista usług służących do przywracania stanu klienta DHCP z pamięci oraz do wstrzymywania i wznawiania klienta DHCP.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

Utwórz rekord bieżącego stanu klienta DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia zapisanie klienta DHCP uruchomionego na pierwszym interfejsie z włączonym protokołem DHCP, który znajduje się w wystąpieniu klienta DHCP, do rekordu wskazywanego przez record_ptr. Dzięki temu aplikacja kliencka DHCP przywraca swój stan klienta DHCP po wystąpieniu programu, na przykład o wyłączeniu i ponownym uruchomieniu.

Aby zapisać rekord klienta DHCP w określonym interfejsie, jeśli dla usługi DHCP jest włączony więcej niż jeden interfejs, Użyj usługi *nx_dhcp_interface_client_get_record* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP
- **record_ptr**: wskaźnik do rekordu klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS (0x0)**: utworzony rekord klienta
- **NX_DHCP_NOT_BOUND**: klient (0x94) nie znajduje się w Stanach powiązanych
- **NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) brak włączonych interfejsów dla protokołu DHCP
- NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika

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

Utwórz rekord bieżącego stanu klienta DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia zapisanie klienta DHCP działającego w określonym interfejsie do rekordu wskazywanego przez record_ptr. Dzięki temu aplikacja kliencka DHCP przywraca swój stan klienta DHCP po wystąpieniu programu, na przykład o wyłączeniu i ponownym uruchomieniu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP
- **interface_index**: indeks, w którym ma zostać pobrany rekord
- **record_ptr**: wskaźnik do rekordu klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS (0x0)**: utworzony rekord klienta
- **NX_DHCP_NOT_BOUND**: klient (0x94) **nie jest powiązany**
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0X9A) Nieprawidłowy indeks interfejsu
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

Przywróć klienta DHCP z wcześniej zapisanego rekordu

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji przywrócenie klienta DHCP z poprzedniej sesji przy użyciu rekordu klienta DHCP wskazywanego przez record_ptr. Dane wejściowe time_elapsed są stosowane do pozostałego czasu dzierżawy klienta DHCP.

Wymaga to, aby aplikacja klienta DHCP utworzyła rekord klienta DHCP przed wyłączeniem i zapisała ten rekord w pamięci nieulotnej.

Jeśli dla klienta DHCP jest włączony więcej niż jeden interfejs, ta usługa zostanie zastosowana do pierwszego prawidłowego interfejsu znalezionego w wystąpieniu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP
- **record_ptr**: wskaźnik do rekordu klienta DHCP 
- **time_elapsed**: czas odejmowania od pozostałego czasu dzierżawy w rekordzie klienta wejściowego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x0) rekord klienta został przywrócony
- **NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) Brak interfejsów z uruchomionym protokołem DHCP
- NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika

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

Przywróć klienta DHCP z wcześniej zapisanego rekordu w określonym interfejsie

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji przywrócenie klienta DHCP w określonym interfejsie przy użyciu rekordu klienta DHCP wskazywanego przez record_ptr. Dane wejściowe time_elapsed są stosowane do pozostałego czasu dzierżawy klienta DHCP.

Wymaga to, aby aplikacja klienta DHCP utworzyła rekord klienta DHCP przed wyłączeniem i zapisała ten rekord w pamięci nieulotnej.

Jeśli dla klienta DHCP jest włączony więcej niż jeden interfejs, ta usługa zostanie zastosowana do pierwszego prawidłowego interfejsu znalezionego w wystąpieniu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP
- **record_ptr**: wskaźnik do rekordu klienta DHCP 
- **time_elapsed**: czas odejmowania od pozostałego czasu dzierżawy w rekordzie klienta wejściowego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x0) rekord klienta został przywrócony
- **NX_DHCP_NOT_BOUND**: klient (0x94) nie jest powiązany z adresem IP
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0X9A) Nieprawidłowy indeks interfejsu
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

Aktualizowanie pozostałego czasu na dzierżawie klienta DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Opis

Ta usługa aktualizuje pozostały czas w dzierżawie adresu IP klienta DHCP przy użyciu time_elapsed danych wejściowych pierwszego interfejsu włączonego dla protokołu DHCP w wystąpieniu klienta DHCP. Aplikacja musi wstrzymać wątek klienta DHCP przed użyciem tej usługi przy użyciu *nx_dhcp_suspend*. Po wywołaniu tej usługi aplikacja może wznowić wątek klienta DHCP, wywołując *nx_dhcp_resume*.

Jest to przeznaczone dla aplikacji klienckich DHCP, które muszą wstrzymać wątek klienta DHCP przez pewien czas, a następnie zaktualizować pozostały czas dzierżawy adresu IP.

Uwaga: Ta usługa nie jest przeznaczona do użycia z *nx_dhcp_client_get_record* i *nx_dhcp_client_restore_record* opisanymi wcześniej). Te usługi zostały opisane wcześniej w tej sekcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP 
- **time_elapsed**: czas odejmowania od pozostałego czasu w dzierżawie adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x0) aktualizacja dzierżawy adresu IP klienta
- **NX_DHCP_NO_INTERFACES_ENABLED**: (0XA5) brak włączonych interfejsów dla protokołu DHCP
- NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika

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

Zaktualizuj pozostały czas w dzierżawie klienta DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a>Opis

Ta usługa aktualizuje pozostały czas w dzierżawie adresu IP klienta DHCP przy użyciu time_elapsed danych wejściowych w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Aplikacja musi wstrzymać wątek klienta DHCP przed użyciem tej usługi przy użyciu *nx_dhcp_suspend*. Po wywołaniu tej usługi aplikacja może wznowić wątek klienta DHCP, wywołując *nx_dhcp_resume*. Zwróć uwagę, że Wstrzymywanie i wznawianie wątku klienta DHCP ma zastosowanie do wszystkich interfejsów włączonych dla protokołu DHCP.

Jest to przeznaczone dla aplikacji klienckich DHCP, które muszą wstrzymać wątek klienta DHCP przez pewien czas, a następnie zaktualizować pozostały czas dzierżawy adresu IP.

Uwaga: Ta usługa nie jest przeznaczona do użycia z *nx_dhcp_client_get_record* i *nx_dhcp_client_restore_record* opisanymi wcześniej). Te usługi zostały opisane wcześniej w tej sekcji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP
- **interface_index**: indeks do interfejsu do zastosowania, który upłynął czas
- **time_elapsed**: czas odejmowania od pozostałego czasu w dzierżawie adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x0) aktualizacja dzierżawy adresu IP klienta
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0X9A) Nieprawidłowy indeks interfejsu
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

Ta usługa wstrzymuje bieżący wątek klienta DHCP. Należy pamiętać, że w przeciwieństwie do *nx_dhcp_stop* nie ma zmiany stanu klienta DHCP, gdy ta usługa jest wywoływana.

Ta usługa zawiesza serwer DHCP działa na wszystkich interfejsach włączonych dla protokołu DHCP.

Aby zaktualizować stan klienta DHCP z upływem czasu, który upłynął podczas wstrzymania klienta DHCP, zobacz *nx_dhcp_client_update_time_remaining* opisany wcześniej. Aby wznowić wstrzymany wątek klienta DHCP, aplikacja powinna wywołać *nx_dhcp_resume*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x0) wątek klienta jest zawieszony
- NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

Wznów zawieszony wątek klienta DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa wznawia zawieszony wątek klienta DHCP. Należy pamiętać, że po wznowieniu wątku klienta nie ma zmiany rzeczywistego stanu klienta DHCP. Aby zaktualizować pozostały czas dla dzierżawy adresu IP klienta DHCP z upływem czasu przed wywołaniem *nx_dhcp_resume*, zobacz *nx_dhcp_client_update_time_remaining* opisany wcześniej.

Ta usługa wznawia działanie protokołu DHCP na wszystkich interfejsach włączonych dla protokołu DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr**: wskaźnik do klienta DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x0) wątek klienta został wznowiony
- NX_PTR_ERROR: (0x16) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```