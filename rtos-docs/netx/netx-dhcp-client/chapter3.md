---
title: Rozdział 3 — Opis usług klienta DHCP w usłudze Azure RTO NetX
description: Ten rozdział zawiera opis wszystkich usług DHCP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822699"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>Rozdział 3 — Opis usług klienta DHCP w usłudze Azure RTO NetX

Ten rozdział zawiera opis wszystkich usług DHCP usługi Azure RTO NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_dhcp_create**: *Tworzenie wystąpienia DHCP*

- **nx_dhcp_clear_broadcast_flag**: Wyczyść flagę emisji na komunikatach klienta

- **nx_dhcp_delete**: *usuwanie wystąpienia DHCP*

- **nx_dhcp_decline**: Wyślij *komunikat odrzucania do serwera*

- **nx_dhcp_force_renew**: *Wyślij komunikat odnowienia Force*

- **nx_dhcp_packet_pool_set**: *Ustaw pulę pakietów klienta DHCP*

- **nx_dhcp_release**: Wyślij *komunikat o zwolnieniu do serwera*

- **nx_dhcp_reinitialize**: *Wyczyść parametry sieciowe klienta DHCP*

- **nx_dhcp_request_client_ip**: *Określ konkretny adres IP*

- **nx_dhcp_send_request**: *Wyślij komunikat DHCP do serwera*

- **nx_dhcp_server_address_get**: *pobieranie adresu serwera DHCP klienta DHCP*

- **nx_dhcp_set_interface_index**: *Określ interfejs sieciowy klienta*

- **nx_dhcp_start**: *Uruchamianie przetwarzania DHCP*

- **nx_dhcp_state_change_notify**: *powiadamianie o zmianie stanu protokołu DHCP*

- **nx_dhcp_stop**: *ZAtrzymywanie przetwarzania DHCP*

- **nx_dhcp_user_option_retrieve**: *pobieranie opcji DHCP*

- **nx_dhcp_user_option_convert**: *przekonwertuj cztery BAJTy na ULONG*

Usługi klienta DHCP specyficzne dla interfejsu:

- **nx_dhcp_interface_clear_broadcast_flag**: *Wyczyść flagę emisji na komunikatach klienta w określonym interfejsie*

- **nx_dhcp_interface_enable**: *Włącz interfejs do uruchamiania protokołu DHCP w określonym interfejsie*

- **nx_dhcp_interface_disable**: *Wyłącz interfejs do uruchamiania protokołu DHCP w określonym interfejsie*

- **nx_dhcp_interface_decline**: *Wyślij komunikat odrzucania do serwera w określonym interfejsie*

- **nx_dhcp_interface_force_renew**: *Wyślij komunikat wymuszania odnowienia w określonym interfejsie*

- **nx_dhcp_interface_reinitialize**: *Wyczyść parametry sieciowe klienta DHCP w określonym interfejsie*

- **nx_dhcp_interface_release**: *wysyła komunikat o zwolnieniu do serwera w określonym interfejsie*

- **nx_dhcp_interface_request_client_ip**: *Określ konkretny adres IP w określonym interfejsie*

- **nx_dhcp_interface_send_request**: *Wyślij komunikat DHCP do serwera w określonym interfejsie*

- **nx_dhcp_interface_server_address_get**: *Pobierz adres IP serwera DHCP w określonym interfejsie*

- **nx_dhcp_interface_start**: *Uruchamianie przetwarzania klienta DHCP w określonym interfejsie*

- **nx_dhcp_interface_stop**: *Zatrzymywanie przetwarzania klienta DHCP w określonym interfejsie*

- **nx_dhcp_interface_state_change_notify**: *Ustaw funkcję wywołania zwrotnego, gdy stan DHCP zostanie zmieniony w określonym interfejsie*

- **nx_dhcp_interface_user_option_retrieve**: *Pobierz określoną opcję DHCP w określonym interfejsie*

Usługi klienta DHCP, jeśli NX_DHCP_CLIENT_RESORE_STATE jest zdefiniowany:

- **nx_dhcp_resume**: *Wznów poprzednio ustanowiony stan klienta DHCP*

- **nx_dhcp_suspend**: *wstrzymywanie przetwarzania stanu klienta DHCP*

- **nx_dhcp_client_get_record**: *Utwórz rekord stanu klienta DHCP*

- **nx_dhcp_client_restore_record**: *przywracanie wcześniej zapisanego rekordu do klienta DHCP*

- **nx_dhcp_client_update_time_remaining**: *zaktualizuj pozostały czas w bieżącym stanie DHCP*

Specyficzne dla interfejsu usługi klienta DHCP, jeśli NX_DHCP_CLIENT_RESORE_STATE jest zdefiniowany:

- **nx_dhcp_client_interface_get_record**: *Utwórz rekord stanu klienta DHCP w określonym interfejsie*

- **nx_dhcp_client_interface_restore_record**: *przywracanie wcześniej zapisanego rekordu do klienta DHCP w określonym interfejsie*

- **nx_dhcp_client_interface_update_time_remaining**: *zaktualizuj pozostały czas w bieżącym stanie DHCP w określonym interfejsie*

## <a name="nx_dhcp_create"></a>nx_dhcp_create

Tworzenie wystąpienia DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie DHCP dla utworzonego wcześniej wystąpienia adresu IP. Domyślnie interfejs podstawowy jest włączony do uruchamiania protokołu DHCP. Nazwy wejściowe, które nie są używane w implementacji NetX klienta DHCP, muszą być zgodne z kryteriami RFC 1035 dla nazw hostów. Łączna długość nie może przekraczać 255 znaków, etykiety oddzielone kropkami muszą zaczynać się literą i kończyć literą lub cyfrą i mogą zawierać łączniki, ale nie inny znak inny niż alfanumeryczny.

Jeśli aplikacja ma uruchamiać inne interfejsy zarejestrowane przy użyciu wystąpienia protokołu IP (przy użyciu *nx_ip_interface_attach*), aplikacja może wywoływać *nx_dhcp_set_interface_index* , aby uruchomić usługę DHCP tylko na tym interfejsie, lub *nx_dhcp_interface_enable* do uruchamiania protokołu DHCP również w tym interfejsie. Aby uzyskać więcej informacji, zobacz opis tych usług.

> [!NOTE]
> Aplikacja musi upewnić się, że ładunek puli pakietów klienta DHCP może obsługiwać minimalny rozmiar komunikatu DHCP określony w sekcji RFC 2131 (548 bajtów danych komunikatów DHCP oraz nagłówków protokołu UDP, adresu IP i ramki sieci fizycznej).

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.  
- **name_ptr** Wskaźnik na nazwę hosta dla wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie protokołu DHCP

- **NX_DHCP_INVALID_NAME** (0XA8) Nieprawidłowa nazwa hosta

- Ładunek **NX_DHCP_INVALID_PAYLOAD** (0x9C) jest za mały dla komunikatu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

### <a name="allowed-from"></a>Dozwolone z

**Wątki,** Zainicjować

### <a name="example"></a>Przykład

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

Włącz określony interfejs do uruchamiania protokołu DHCP 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa umożliwia określony interfejs do uruchamiania protokołu DHCP. Domyślnie interfejs podstawowy jest włączony dla klienta DHCP. W tym momencie można uruchomić protokół DHCP w tym interfejsie przez wywołanie *nx_dhcp_interface_start* lub uruchomienie protokołu DHCP we wszystkich włączonych interfejsach *nx_dhcp_start*.

Zwróć uwagę, że aplikacja musi najpierw zarejestrować ten interfejs z wystąpieniem IP przy użyciu *nx_ip_interface_attach.*

Ponadto w celu dodania tego interfejsu do listy włączonych interfejsów musi istnieć dostępny interfejs klienta DHCP "rekord". Domyślnie NX_DHCP_CLIENT_MAX_RECORDS jest zdefiniowana na 1. Ustaw tę opcję na maksymalną liczbę interfejsów oczekiwanych na równoczesne uruchomienie klienta DHCP. Zwykle NX_DHCP_CLIENT_MAX_RECORDS będzie równa NX_MAX_PHYSICAL_INTERFACES; Jeśli jednak urządzenie ma więcej interfejsów fizycznych niż oczekuje na uruchomienie klienta DHCP, może zaoszczędzić pamięć przez ustawienie NX_DHCP_CLIENT_MAX_RECORDS na mniejszą niż ten numer. Nie istnieje jeden do jednego mapowanie interfejsów fizycznych z rekordami interfejsu klienta DHCP.

Różnica między tą usługą a *nx_dhcp_set_interface_index* to ta, która powoduje, że tylko jeden interfejs do uruchamiania protokołu DHCP, podczas gdy ta usługa po prostu dodaje określony interfejs do listy interfejsów klienta włączonych dla protokołu DHCP.

Aby wyłączyć interfejs dla protokołu DHCP, aplikacja może wywołać usługę *nx_dhcp_interface_disable* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **interface_index** Indeks interfejsu umożliwiającego włączenie protokołu DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie protokołu DHCP

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) Brak dostępnego rekordu dla innego interfejsu, który ma zostać włączony dla protokołu DHCP

- Interfejs **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) z włączonym protokołem DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a>nx_dhcp_interface_disable

Wyłączenie określonego interfejsu w celu uruchomienia protokołu DHCP 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa wyłącza określony interfejs na potrzeby uruchamiania protokołu DHCP. Ponownie inicjuje klienta DHCP w tym interfejsie.

Aby ponownie uruchomić klienta DHCP, aplikacja musi ponownie włączyć interfejs przy użyciu *nx_dhcp_interface_enable* i ponownie uruchomić usługę DHCP, wywołując *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **interface_index** Indeks interfejsu w celu wyłączenia protokołu DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie protokołu DHCP

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

Ustaw flagę emisji DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Opis

Ta usługa ustawia lub czyści flagę emisji w nagłówku komunikatu DHCP dla wszystkich interfejsów włączonych dla protokołu DHCP. W przypadku niektórych komunikatów DHCP (np. DISCOVER) flaga emisji jest ustawiona na emisję, ponieważ klient nie ma adresu IP.

__clear_flag__


- Flaga emisji **NX_TRUE** jest wyczyszczona (Żądaj odpowiedzi emisji pojedynczej)

- Ustawiono flagę emisji **NX_FALSE** (odpowiedź na żądanie emisji)

Ta usługa jest przeznaczona dla klientów DHCP, którzy muszą przejść przez router, aby uzyskać dostęp do serwera DHCP, gdzie router odrzuca komunikaty emisji przesyłania dalej.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP  

- **clear_flag** Wartość, dla której ma zostać ustawiona flaga emisji

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zaktualizował flagę emisji

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

Ustaw lub wyczyść flagę emisji w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji hosta klienta DHCP Ustawianie lub czyszczenie flagi emisji w komunikatach klienta DHCP na serwerze DHCP w określonym interfejsie. Aby uzyskać więcej informacji, zobacz **nx_dhcp_clear_broadcast_flag**

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP

- **interface_index** Indeks interfejsu służący do ustawiania flagi emisji  

- **clear_flag** Wartość, dla której ma zostać ustawiona flaga emisji

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zaktualizował flagę emisji

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a>nx_dhcp_delete

Usuwanie wystąpienia DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie usługi DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie protokołu DHCP.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

Wyślij komunikat Force o odnowieniu 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji hosta wysyłanie komunikatów Force w celu odnowienia na wszystkich interfejsach włączonych dla protokołu DHCP. Klient DHCP musi być w stanie powiązanym. Ta funkcja ustawia stan do ODNOWIENIa, aby klient DHCP próbował odnowić działanie przed upływem limitu czasu T1.

Aby wysłać Force w określonym interfejsie, gdy jest włączona obsługa protokołu DHCP w wielu interfejsach, użyj *nx_dhcp_interface_force_renew*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał wymuszenie odnowienia.  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

Wyślij komunikat Wymuś odnowienie w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji hosta wysyłanie komunikatów Force (Wymuś odnowienie) w interfejsie wejściowym, o ile ten interfejs został włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*). Klient DHCP w określonym interfejsie musi być w stanie powiązanym. Ta funkcja ustawia stan do ODNOWIENIa, aby klient DHCP próbował odnowić działanie przed upływem limitu czasu T1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłał wymuszenie odnowienia.  

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

Ustawianie puli pakietów klienta DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji utworzenie puli pakietów klienta DHCP, przekazując wskaźnik do wcześniej utworzonej puli pakietów w ramach tego wywołania usługi. Aby można było użyć tej funkcji, aplikacja hosta musi definiować NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL. Po zdefiniowaniu usługa *nx_dhcp_create* nie utworzy puli pakietów klienta. Należy pamiętać, że aplikacja zaleca się użycie wartości domyślnych dla ładunku puli pakietów klienta DHCP zdefiniowanego jako NX_DHCP_PACKET_PAYLOAD w *nx_dhcp. h* podczas tworzenia puli pakietów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **packet_pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pula pakietów klienta DHCP jest ustawiona

- Usługa **NX_NOT_ENABLED** (0x14) nie jest włączona

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- Ładunek NX_DHCP_INVALID_PAYLOAD (0x9C) jest za mały

### <a name="allowed-from"></a>Dozwolone z

Kod aplikacji

### <a name="example"></a>Przykład

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a>nx_dhcp_request_client_ip

Ustaw żądany adres IP dla wystąpienia DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP przy pierwszym interfejsie włączonym dla protokołu DHCP w rekordzie klienta DHCP. Jeśli flaga *skip_discover_message* jest ustawiona, klient DHCP pomija komunikat odnajdywania i wysyła komunikat żądania.

Aby ustawić żądanie dla określonego adresu IP dla komunikatów DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_request_client_ip* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **client_ip_address** Adres IP do żądania z serwera DHCP

- **skip_discover_message** W przypadku wartości true klient DHCP wysyła komunikat żądania  
W przypadku wartości false wysyła komunikat odnajdywania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) wybrano żądany adres IP.

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy
 
### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

Ustaw żądany adres IP dla wystąpienia DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*). Jeśli flaga *skip_discover_message* jest ustawiona, klient DHCP pomija komunikat odnajdywania i wysyła komunikat żądania.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **Interface_index** Indeks interfejsu do żądania adresu IP

- **client_ip_address** Adres IP do żądania z serwera DHCP

- **skip_discover_message** W przypadku wartości true klient DHCP wysyła komunikat żądania; w przeciwnym razie zostanie wysłany komunikat odnajdywania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) wybrano żądany adres IP.

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik adresu IP lub protokołu DHCP

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

Wyczyść parametry sieci klienta DHCP 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyści parametry sieciowe aplikacji hosta (adres IP, adres sieciowy i maska sieci), a następnie czyści stan klienta DHCP we wszystkich interfejsach włączonych dla protokołu DHCP. Jest on używany w połączeniu z *nx_dhcp_stop* i *nx_dhcp_start* do "ponownego uruchomienia" komputera stanu DHCP: 

nx_dhcp_stop (&my_dhcp);  
nx_dhcp_reinitialize (&my_dhcp);  
nx_dhcp_start (&my_dhcp);


Aby ponownie zainicjować klienta DHCP w określonym interfejsie, gdy na serwerze DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_reinitialize* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) protokół DHCP został pomyślnie zainicjowany ponownie 

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

Wyczyść parametry sieciowe klienta DHCP w określonym interfejsie 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa czyści parametry sieci (adres IP, adres sieciowy i maska sieci) w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*). Aby uzyskać więcej informacji, zobacz *nx_dhcp_reinitialize* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia usługi DHCP

- **interface_index** Indeks interfejsu, który ma zostać ponownie zainicjowany.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie zainicjowano Interfejs **NX_SUCCESS** (0x00)

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

Zwolnij adres IP dzierżawy

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia adres IP uzyskany z serwera DHCP, wysyłając do niego komunikat o wersji. Następnie ponownie inicjuje klienta DHCP. Ta usługa jest stosowana do wszystkich interfejsów włączonych dla protokołu DHCP.

Aplikacja może ponownie uruchomić klienta DHCP, wywołując *nx_dhcp_start*.

Aby zwolnić adres z powrotem do serwera DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_release*

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wydanie protokołu DHCP.  

- **NX_DHCP_NOT_BOUND** (0x94) adres IP nie został wydzierżawiony, więc nie można go zwolnić.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

Zwolnij adres IP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa zwalnia adres IP uzyskany z serwera DHCP w określonym interfejsie i ponownie inicjuje klienta DHCP. Klienta DHCP można uruchomić ponownie, wywołując *nx_dhcp_start*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wydanie protokołu DHCP.

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- **NX_DHCP_NOT_BOUND** (0x94) adres IP nie został wydzierżawiony, więc nie można go zwolnić.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a>nx_dhcp_decline

Odrzuć adres IP z serwera DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa odrzuca adres IP dzierżawiony z serwera DHCP na wszystkich interfejsach włączonych dla protokołu DHCP. W przypadku zdefiniowania NX_DHCP_CLIENT_ SEND_ ARP_PROBE klient DHCP wyśle komunikat o ODRZUCENIu, jeśli wykryje, że adres IP jest już używany. Zobacz **sondy protokołu ARP** w rozdziale 1, aby uzyskać więcej informacji na temat konfiguracji sondowania ARP w kliencie DHCP NetX.

Aplikacja może korzystać z tej usługi, aby odrzucić swój adres IP, jeśli odnajdzie adres jest używany w inny sposób.

Ta usługa ponownie inicjalizuje klienta DHCP, aby mógł on zostać oduruchamiany przez wywołanie *nx_dhcp_start*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- Odrzucanie **NX_SUCCESS** (0x00) zostało pomyślnie wysłane  

- **NX_DHCP_NOT_STARTED** (0x96) wystąpienie DHCP nie zostało uruchomione

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

Odrzuć adres IP z serwera DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa wysyła do serwera komunikat o ODRZUCENIu, aby odrzucić adres IP przypisany przez serwer DHCP. Powoduje również ponowne zainicjowanie klienta DHCP. Aby uzyskać więcej informacji, zobacz *nx_dhcp_decline* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

- **Interface_index** Indeks interfejsu do odrzucania adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) wysłano komunikat o ODRZUCENIu DHCP  

- Klient DHCP **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

Wyślij komunikat DHCP do serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>Opis

Ta usługa wysyła określony komunikat DHCP do serwera DHCP przy pierwszym interfejsie z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP. Aby wysłać wiadomość wydania lub odrzucić, aplikacja musi odpowiednio używać *nx_dhcp [_interface] _release*() lub *nx_dhcp_interface_decline ()* .

Aby można było używać tej usługi, należy uruchomić klienta DHCP, z wyjątkiem wysyłania komunikatu INFORM_REQUEST typu.

> [!NOTE] 
> Ta usługa nie jest przeznaczona dla aplikacji hosta na dysk, na którym znajduje się komputer stanu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **dhcp_message_type** Żądanie komunikatu (zdefiniowane w *nx_dhcp. h*)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) wysłano komunikat DHCP  

- **NX_DHCP_NOT_STARTED** (0X96) Nieprawidłowy indeks interfejsu

- **NX_DHCP_INVALID_MESSAGE** (0X9B) Nieprawidłowy typ komunikatu do wysłania

- NX_PTR_ERROR (0x16) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

Wyślij komunikat DHCP do serwera w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat do serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Aby wysłać wiadomość wydania lub odrzucić, aplikacja musi odpowiednio używać *nx_dhcp [_interface] _release*() lub *nx_dhcp_interface_decline ()* .

Aby korzystać z tej usługi, należy uruchomić klienta DHCP, z wyjątkiem wysyłania komunikatu żądania INFORM protokołu DHCP.

Ta usługa nie jest przeznaczona dla aplikacji hosta na dysk, na którym znajduje się komputer stanu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **Interface_index** Indeks interfejsu, na którym ma zostać wysłany komunikat  

- **dhcp_message_type** Żądanie komunikatu (zdefiniowane w *nx_dhcp. h*)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) wysłano komunikat DHCP  

- **NX_DHCP_NOT_STARTED** (0X96) Nieprawidłowy indeks interfejsu

- **NX_DHCP_INVALID_MESSAGE** (0X9B) Nieprawidłowy typ komunikatu do wysłania

- Interfejs **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

Pobierz adres IP serwera DHCP klienta DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>Opis

Ta usługa Pobiera adres IP serwera DHCP klienta DHCP na pierwszym interfejsie z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP. Obiekt wywołujący może korzystać tylko z tej usługi po powiązaniu klienta DHCP z adresem IP przydzielonym przez serwer DHCP. Aplikacja hosta może użyć usługi *nx_ip_status_check* , aby sprawdzić, czy adres IP jest ustawiony, lub użyć *nx_dhcp_state_change_notify* i zbadać stan klienta DHCP, NX_DHCP_STATE_BOUND. Zobacz *nx_dhcp_state_change_notify* , aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.

Aby znaleźć serwer DHCP w określonym interfejsie, gdy dla klienta DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_server_address_get*

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **server_address** Wskaźnik na adres IP serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) zwrócony adres serwera DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a>nx_dhcp_interface_server_address_get

Pobierz adres IP serwera DHCP klienta DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>Opis

Ta usługa Pobiera adres IP serwera DHCP klienta DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Klient DHCP musi znajdować się w stanie związanym. Po uruchomieniu klienta DHCP w tym interfejsie aplikacja hosta może użyć usługi *nx_ip_status_check* do sprawdzenia, czy adres IP jest ustawiony, lub może użyć wywołania zwrotnego zmiany stanu klienta DHCP i wysłać zapytanie o stan klienta dhcp, NX_DHCP_STATE_BOUND. Zobacz *nx_dhcp_state_change_notify* , aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **Interface_index** Indeks interfejsu w celu uzyskania adresu IP  

- **server_address** Wskaźnik na adres IP serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) zwrócony adres serwera DHCP

- **NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) brak włączonych interfejsów dla protokołu DHCP

- Klient DHCP **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a>nx_dhcp_set_interface_index

Ustaw interfejs sieciowy dla wystąpienia DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Opis

Ta usługa ustawia interfejs sieciowy dla wystąpienia DHCP, aby połączyć się z serwerem DHCP w przypadku uruchamiania klienta DHCP skonfigurowanego dla jednego interfejsu sieciowego.

Domyślnie klient DHCP jest uruchamiany w interfejsie podstawowym. Aby uruchomić protokół DHCP w usłudze dodatkowej, Użyj tej usługi, aby ustawić interfejs pomocniczy jako interfejs klienta DHCP. Aplikacja musi wcześniej zarejestrować określony interfejs w wystąpieniu IP przy użyciu usługi *nx_ip_interface_attach* .

Należy zauważyć, że ta usługa jest przeznaczona dla aplikacji, które zamierzają uruchamiać klienta DHCP tylko na jednym interfejsie. Aby uruchomić protokół DHCP na wielu interfejsach, zobacz *nx_dhcp_interface_enable* , aby uzyskać więcej szczegółów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **indeks** Indeks interfejsu sieciowego urządzenia

### <a name="return-values"></a>Wartości zwrócone

- Interfejs **NX_SUCCESS** (0x00) został pomyślnie ustawiony.

- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy interfejs sieciowy

- Interfejs **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) z włączonym protokołem DHCP

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) Brak dostępnego rekordu dla innego

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a>nx_dhcp_start

Uruchamianie przetwarzania DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia przetwarzanie DHCP na wszystkich interfejsach włączonych dla protokołu DHCP. Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*

Aby sprawdzić, kiedy wystąpienie protokołu IP jest powiązane z adresem IP w interfejsie klienta DHCP, należy użyć *nx_ip_status_check* , aby sprawdzić, czy adres IP jest prawidłowy.

Jeśli istnieją inne interfejsy, na których jest już uruchomiony protokół DHCP, ta usługa nie będzie mieć na nie wpływu.

Aby uruchomić protokół DHCP w określonym interfejsie, jeśli włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_start* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne uruchomienie usługi DHCP.  

- **NX_DHCP_ALREADY_STARTED** (0X93) DHCP jest już uruchomiony.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

Uruchom przetwarzanie DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa uruchamia przetwarzanie DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Aby uzyskać więcej informacji na temat włączania interfejsu protokołu DHCP, zobacz *nx_dhcp_interface_enable*(). Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*

Jeśli nie ma innych interfejsów z uruchomionym klientem DHCP, ta usługa uruchomi/wznowi wątek klienta DHCP i (ponownie) uaktywni czasomierz klienta DHCP.  
  
Aplikacja powinna używać *nx_ip_status_check* , aby sprawdzić, czy uzyskano adres IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

- **Interface_index** Indeks, na którym ma zostać uruchomiony klient DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne uruchomienie usługi DHCP.  

- **NX_DHCP_ALREADY_STARTED** (0x93) wystąpienie usługi DHCP zostało już uruchomione.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

Ustawianie funkcji wywołania zwrotnego zmiany stanu protokołu DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>Opis

Ta usługa rejestruje określoną funkcję wywołania zwrotnego dhcp_state_change_notify w celu powiadomienia aplikacji o zmianach stanu protokołu DHCP. Funkcja wywołania zwrotnego dostarcza stan, do którego przeszedł klient DHCP.

Poniżej przedstawiono wartości skojarzone z różnymi stanami DHCP:

| Stan                             | Wartość |
|-----------------------------------|-------|
| \_rozruch stanu protokołu DHCP NX \_ \_             | 1     |
| \_ \_ init stanu DHCP \_ NX             | 2     |
| \_wybór stanu protokołu DHCP NX \_ \_        | 3     |
| \_ \_ żądanie stanu DHCP \_ NX       | 4     |
| \_ \_ powiązano stan DHCP \_ NX            | 5     |
| \_ \_ odnawianie stanu protokołu DHCP NX \_         | 6     |
| ponowne \_ \_ wiązanie stanu \_ DHCP NX        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| \_ \_ \_ sondowanie adresu stanu protokołu DHCP NX \_ | 9     |


### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

- **dhcp_state_change_notify** Wskaźnik funkcji wywołania zwrotnego zmiany stanu

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna konfiguracja wywołania zwrotnego **NX_SUCCESS** (0x00).  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

Ustaw funkcję wywołania zwrotnego zmiany stanu DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a>Opis

Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu powiadomienia aplikacji o zmianach stanu protokołu DHCP. Argumenty wejściowe ATANH wywołania zwrotnego są indeksem interfejsu i stanem, w którym klient DHCP przeszedł w tym interfejsie.

Aby uzyskać więcej informacji na temat funkcji zmiany stanu, zobacz *nx_dhcp_state_change_notify*().

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

- **dhcp_interface_state_change_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna konfiguracja wywołania zwrotnego **NX_SUCCESS** (0x00).  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

### <a name="allowed-from"></a>Dozwolone z

Wątki, Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a>nx_dhcp_stop

Powoduje zatrzymanie przetwarzania protokołu DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa powoduje zatrzymanie przetwarzania protokołu DHCP na wszystkich interfejsach, które uruchomiły przetwarzanie DHCP. Jeśli nie ma żadnych interfejsów przetwarzających protokół DHCP, ta usługa zawiesza wątek klienta DHCP i dezaktywuje czasomierz klienta DHCP.

Aby zatrzymać usługę DHCP w określonym interfejsie, jeśli dla usługi DHCP włączono wiele interfejsów, Użyj usługi *nx_dhcp_interface_stop* .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) POMYŚLNE zatrzymanie DHCP

- **NX_DHCP_NOT_STARTED** (0x96) wystąpienie DHCP nie zostało uruchomione.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

Zatrzymaj przetwarzanie DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa powoduje zatrzymanie przetwarzania DHCP w określonym interfejsie, jeśli usługa DHCP jest już uruchomiona. Jeśli nie ma innych interfejsów z uruchomionym protokołem DHCP, wątek i czasomierz DHCP są wstrzymywane.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

- **Interface_index** Interfejs, na którym ma zostać zatrzymane przetwarzanie DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) POMYŚLNE zatrzymanie DHCP

- **NX_DHCP_NOT_STARTED** (0X96) DHCP nie został uruchomiony.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

Pobierz opcję DHCP z ostatniej odpowiedzi serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera określoną opcję DHCP z bufora opcji DHCP pierwszego interfejsu z włączonym protokołem DHCP znalezionym w rekordzie klienta DHCP. Jeśli to się powiedzie, dane opcji są kopiowane do określonego buforu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.  

- **request_option** Opcja DHCP określona przez specyfikacje RFC. Zobacz opcję NX_DHCP_OPTION w *nx_dhcp. h*.

- **destination_ptr** Wskaźnik do miejsca docelowego dla ciągu odpowiedzi.  

- **destination_size** Wskaźnik na rozmiar lokalizacji docelowej i w przypadku powrotu, miejsce docelowe, do którego zostanie umieszczona liczba zwracanych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne pobranie opcji.  

- Klient DHCP **NX_DHCP_NOT_BOUND** (0x94) nie jest powiązany.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) brak włączonych interfejsów dla protokołu DHCP

- Miejsce docelowe **NX_DHCP_DEST_TO_SMALL** (0x95) jest za małe, aby można było przetrzymać odpowiedź.

- W odpowiedzi serwera nie znaleziono opcji DHCP **NX_DHCP_PARSE_ERROR** (0x97).

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a>nx_dhcp_interface_user_option_retrieve

Pobierz opcję DHCP z ostatniej odpowiedzi serwera w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera określoną opcję DHCP z bufora opcji DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Jeśli to się powiedzie, dane opcji są kopiowane do określonego buforu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

- **Interface_index** Indeks, na którym ma zostać pobrana określona opcja  

- **request_option** Opcja DHCP określona przez specyfikacje RFC. Zobacz opcję NX_DHCP_OPTION w *nx_dhcp. h*.  

- **destination_ptr** Wskaźnik do miejsca docelowego dla ciągu odpowiedzi.  

- **destination_size** Wskaźnik na rozmiar lokalizacji docelowej i w przypadku powrotu, miejsce docelowe, do którego zostanie umieszczona liczba zwracanych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne pobranie opcji.  

- Adres IP **NX_DHCP_NOT_BOUND** (0x94) nie jest przypisany

- Bufor **NX_DHCP_DEST_TO_SMALL** (0x95) jest za mały

- W odpowiedzi serwera nie znaleziono opcji DHCP **NX_DHCP_PARSE_ERROR** (0x97).

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi.

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a>nx_dhcp_user_option_convert

Konwertuj cztery bajty na ULONG

### <a name="prototype"></a>Prototype

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>Opis

Ta usługa konwertuje cztery znaki wskazywane przez "option_string_ptr" na wartość długą bez znaku. Jest to szczególnie przydatne w przypadku obecności adresów IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **option_string_ptr** Wskaźnik do wcześniej pobranego ciągu opcji.

### <a name="return-values"></a>Wartości zwrócone

- **Wartość** Wartość czterech pierwszych bajtów.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a>nx_dhcp_user_option_add_callback_set

Ustaw funkcję wywołania zwrotnego w celu dodania opcji dostarczonych przez użytkownika

### <a name="prototype"></a>Prototype

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a>Opis

Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu dodania opcji dostarczonych przez użytkownika.

Jeśli określono funkcję wywołania zwrotnego, aplikacje mogą dodać opcje dostarczone przez użytkownika do pakietu, iface_index i message_type.

> [!NOTE]
> W procedurze użytkownika. W przypadku dodawania opcji dostarczonych przez użytkownika aplikacje muszą być zgodne z formatem opcji DHCP. Łączny rozmiar opcji użytkownika musi być mniejszy lub równy user_option_length i aktualizować user_option_length jako rzeczywistą długość opcji. Zwróć NX_TRUE w przypadku pomyślnego dodania opcji, w przeciwnym razie Zwróć NX_FALSE.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia serwera DHCP.

- **dhcp_user_option_add** Wskaźnik do opcji użytkownika Dodaj funkcję.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna konfiguracja wywołania zwrotnego **NX_SUCCESS** (0x00).

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
