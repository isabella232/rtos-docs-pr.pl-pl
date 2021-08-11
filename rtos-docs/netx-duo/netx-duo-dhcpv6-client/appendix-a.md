---
title: Dodatek A — opis funkcji przywracania stanu dla klienta AZURE RTOS NetX Duo DHCPv6
description: Opcja Azure RTOS konfiguracji klienta DHDPv6 NetX Duo NX_DHCPV6_CLIENT_RESTORE_STATE umożliwia systemowi przywrócenie wcześniej utworzonego klienta DHCP w stanie powiązaną między ponownym uruchomieniem systemu.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6840f89e66d713b1839ac84427b73273b3f9601d4b6d9d39cd94908ac77a77ca
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791333"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a>Dodatek A — opis funkcji przywracania stanu dla klienta AZURE RTOS NetX Duo DHCPv6

Opcja Azure RTOS konfiguracji klienta DHDPv6 NetX Duo NX_DHCPV6_CLIENT_RESTORE_STATE umożliwia systemowi przywrócenie wcześniej utworzonego klienta DHCP w stanie powiązaną między ponownym uruchomieniem systemu.

Ta opcja umożliwia również aplikacji wstrzymanie wątku klienta DHCPv6 i wznowienie go, zaktualizowanego o czas, który upłynął między wstrzymaniem i wznowieniem wątku bez wyłączenia.

## <a name="restoring-the-dhcpv6-client-between-reboots"></a>Przywracanie klienta DHCPv6 między ponownymi rozruchami

Aby przywrócić klienta DHCPv6 między ponownymi uruchomieniami, aplikacja DHCPv6 tworzy wystąpienie klienta DHCPv6, a następnie uzyskuje dzierżawę adresu IP przy użyciu normalnego protokołu DHCPv6 i wywołując nx_dhcpv6_start *.* Następnie aplikacja DHCPv6 czeka na ukończenie protokołu. Jeśli wszystko pójdzie dobrze, urządzenie osiągnie stan BOUND przy użyciu przypisanego prawidłowego adresu IP z serwera DHCPv6. Zanim zostanie wyzwoloną, aplikacja klienczka DHCPv6 zapisuje bieżące wystąpienie klienta DHCPv6 w rekordzie klienta DHCPv6, który jest następnie przechowywany w pamięci trwałej. Niezależny "strażnik czasu" w innym miejscu w systemie śledzi czas, który upłynął podczas tego stanu od zasilania. W przypadku zasilania aplikacja tworzy nowe wystąpienie klienta DHCPv6, a następnie aktualizuje je przy użyciu utworzonego wcześniej rekordu klienta DHCPv6. Czas, który upłynął, jest uzyskiwany od "strażnika czasu", a następnie stosowany do czasu pozostałego w dzierżawie klienta DHCP clientv6. W tym momencie aplikacja może wznowić działanie klienta DHCPv6.

Jeśli czas, który upłynął podczas zasilania, ustawia stan klienta DHCPv6 w stanie RENEW lub REBIND, klient DHCPv6 automatycznie zainicjuje komunikaty DHCPv6 z żądaniem odnowienia lub ponownego wiązania dzierżawy adresu IP. Jeśli adres IP wygasł, klient DHCPv6 automatycznie wyczyści adres IP wystąpienia adresu IP i rozpocznie proces DHCPv6 od stanu INIT, żądając nowego adresu IP.

W ten sposób klient DHCPv6 może działać między ponownymi uruchomieniami, tak jakby nie został przerwany.

Poniżej przedstawiono ilustrację tej funkcji.

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a>nx_dhcpv6_client_get_record

Utwórz rekord bieżącego stanu klienta DHCPv6

### <a name="prototype"></a>Prototype

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Opis

Ta usługa zapisuje klienta DHCPv6 w rekordzie wskazywanym przez record_ptr. Umożliwia to aplikacji klienckiej DHCPv6 przywrócenie stanu klienta DHCPv6 po na przykład przy zasilaniu i ponownym uruchomieniu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do klienta DHCPv6

- **record_ptr** Wskaźnik do rekordu klienta DHCPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS (0x0)** Utworzono prawidłowy rekord klienta

- **NX_DHCPV6_NOT_BOUND** (0xE94) Klient nie jest w stanie powiązanym, dlatego nie ma przypisanego prawidłowego adresu IP

- **NX_PTR_ERROR** (0x16) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_client_restore_record

## <a name="nx_dhcpv6_client_restore_record"></a>nx_dhcpv6_client_restore_record

Przywracanie stanu klienta DHCPv6 z zapisanego rekordu

### <a name="prototype"></a>Prototype

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji DHCPv6 ponowne utworzenie stanu klienta DHCPv6 z poprzedniej sesji przez zaktualizowanie klienta DHCPv6 przy użyciu rekordu klienta DHCPv6 wskazywanego przez usługę record_ptr i zaktualizowanie czasu pozostałego w dzierżawie klienta DHCPv6 przy użyciu danych time_elapsed danych wejściowych. Dzięki temu aplikacja klienczka DHCPv6 może ponownie utworzyć klienta DHCPv6, na przykład po zakończeniu zasilania. Wymaga to, aby aplikacja klienczka DHCPv6 utworzyła rekord klienta DHCPv6 przed jego zasilaniem i zapisała ten rekord w pamięci trwałej.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcpv6_ptr** Wskaźnik do klienta DHCPv6

- **record_ptr** Wskaźnik do rekordu klienta DHCPv6

- **time_elapsed** Czas odejmowania od czasu dzierżawy pozostałego w wejściowym rekordzie klienta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS (0x0)** Przywrócony rekord klienta

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a>Zobacz też

- nx_dhcpv6_client_get_record