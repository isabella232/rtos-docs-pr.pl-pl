---
title: Rozdział 3 — Opis Azure RTOS klienta DHCP NetX
description: Ten rozdział zawiera opis wszystkich usług DHCP Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50902d37f823302910b1b219658dcbf1a41406f480c14795ffceea6e733a0848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799544"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>Rozdział 3 — Opis Azure RTOS klienta DHCP NetX

Ten rozdział zawiera opis wszystkich usług DHCP Azure RTOS NetX (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_dhcp_create:** *tworzenie wystąpienia DHCP*

- **nx_dhcp_clear_broadcast_flag:** wyczyść flagę emisji w komunikatach klienta

- **nx_dhcp_delete:** usuwanie *wystąpienia DHCP*

- **nx_dhcp_decline:** Wyślij komunikat *o odmówienie na serwer*

- **nx_dhcp_force_renew:** Wyślij *wiadomość wymuś odnowienie*

- **nx_dhcp_packet_pool_set:** *ustawianie puli pakietów klienta DHCP*

- **nx_dhcp_release:** Wyślij *komunikat o wydaniu na serwer*

- **nx_dhcp_reinitialize:** wyczyść *parametry sieci klienta DHCP*

- **nx_dhcp_request_client_ip:** Określ *określony adres IP*

- **nx_dhcp_send_request:** wysyłanie *komunikatu DHCP do serwera*

- **nx_dhcp_server_address_get:** pobieranie adresu *serwera DHCP klienta DHCP*

- **nx_dhcp_set_interface_index:** określ *interfejs sieciowy klienta*

- **nx_dhcp_start:** *Uruchamianie przetwarzania DHCP*

- **nx_dhcp_state_change_notify:** *Powiadamianie o zmianie stanu protokołu DHCP*

- **nx_dhcp_stop:** *Zatrzymaj przetwarzanie DHCP*

- **nx_dhcp_user_option_retrieve:** opcja *Pobierania protokołu DHCP*

- **nx_dhcp_user_option_convert:** *przekonwertuj cztery bajty na ULONG*

Usługi klienta DHCP specyficzne dla interfejsu:

- **nx_dhcp_interface_clear_broadcast_flag:** wyczyść *flagę emisji w komunikatach klienta w określonym interfejsie*

- **nx_dhcp_interface_enable:** włącz *interfejs do uruchamiania protokołu DHCP na określonym interfejsie*

- **nx_dhcp_interface_disable:** wyłącz *interfejs, aby uruchamiać protokół DHCP na określonym interfejsie*

- **nx_dhcp_interface_decline:** *wyślij komunikat o odmówienie na serwer w określonym interfejsie*

- **nx_dhcp_interface_force_renew:** Wyślij *wiadomość o wymuś odnowienie w określonym interfejsie*

- **nx_dhcp_interface_reinitialize:** wyczyść *parametry sieci klienta DHCP w określonym interfejsie*

- **nx_dhcp_interface_release:** *wyślij komunikat o wydaniu do serwera w określonym interfejsie*

- **nx_dhcp_interface_request_client_ip:** Określ *określony adres IP w określonym interfejsie*

- **nx_dhcp_interface_send_request:** *wyślij komunikat DHCP do serwera w określonym interfejsie*

- **nx_dhcp_interface_server_address_get:** uzyskiwanie *adresu IP serwera DHCP w określonym interfejsie*

- **nx_dhcp_interface_start:** uruchom *przetwarzanie klienta DHCP w określonym interfejsie*

- **nx_dhcp_interface_stop:** *zatrzymaj przetwarzanie klienta DHCP w określonym interfejsie*

- **nx_dhcp_interface_state_change_notify:** *ustaw funkcję wywołania zwrotnego, gdy stan protokołu DHCP* zmieni się w określonym interfejsie

- **nx_dhcp_interface_user_option_retrieve:** *pobieranie określonej opcji DHCP w określonym interfejsie*

Usługi klienta DHCP, NX_DHCP_CLIENT_RESORE_STATE są zdefiniowane:

- **nx_dhcp_resume:** *Wznów wcześniej ustalony stan klienta DHCP*

- **nx_dhcp_suspend:** *wstrzymywanie przetwarzania stanu klienta DHCP*

- **nx_dhcp_client_get_record:** utwórz *rekord stanu klienta DHCP*

- **nx_dhcp_client_restore_record:** przywracanie *wcześniej zapisanego rekordu do klienta DHCP*

- **nx_dhcp_client_update_time_remaining:** *zaktualizuj czas pozostały w bieżącym stanie DHCP*

Usługi klienta DHCP specyficzne dla interfejsu, NX_DHCP_CLIENT_RESORE_STATE jest zdefiniowany:

- **nx_dhcp_client_interface_get_record:** utwórz *rekord stanu klienta DHCP w określonym interfejsie*

- **nx_dhcp_client_interface_restore_record:** przywracanie *wcześniej zapisanego rekordu do klienta DHCP w określonym interfejsie*

- **nx_dhcp_client_interface_update_time_remaining:** zaktualizuj czas pozostały w bieżącym *stanie DHCP w określonym interfejsie*

## <a name="nx_dhcp_create"></a>nx_dhcp_create

Tworzenie wystąpienia DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie protokołu DHCP dla wcześniej utworzonego wystąpienia adresu IP. Domyślnie podstawowy interfejs jest włączony do uruchamiania protokołu DHCP. Nazwa wejściowa, która nie jest używana w implementacji NetX klienta DHCP, musi spełniać kryteria RFC 1035 dotyczące nazw hostów. Całkowita długość nie może przekraczać 255 znaków, etykiety oddzielone kropkami muszą zaczynać się od litery i kończyć się literą lub liczbą i mogą zawierać łączniki, ale nie mogą zawierać znaków innych niż alfanumeryczne.

Jeśli aplikacja chce uruchomić protokół DHCP inny interfejs zarejestrowany w wystąpieniu adresu IP (przy użyciu usługi nx_ip_interface_attach), aplikacja może  wywołać usługę *nx_dhcp_set_interface_index,* aby uruchomić protokół DHCP tylko na tym interfejsie, lub nx_dhcp_interface_enable w celu uruchomienia protokołu DHCP w tym interfejsie.  Zobacz opis tych usług, aby uzyskać więcej szczegółów.

> [!NOTE]
> Aplikacja musi upewnić się, że ładunek puli pakietów klienta DHCP może obsługiwać minimalny rozmiar komunikatu DHCP określony przez sekcję 2 dokumentu RFC 2131 (548 bajtów danych komunikatów DHCP oraz nagłówki UDP, IP i fizycznej ramki sieci).

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.  
- **name_ptr** Wskaźnik do nazwy hosta dla wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie protokołu DHCP

- **NX_DHCP_INVALID_NAME** (0xA8) Nieprawidłowa nazwa hosta

- **NX_DHCP_INVALID_PAYLOAD** (0x9C) jest za mały dla komunikatu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

### <a name="allowed-from"></a>Dozwolone z

**Wątki,** Inicjowania

### <a name="example"></a>Przykład

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

Włącz określony interfejs, aby uruchomić protokół DHCP 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa umożliwia uruchomienie protokołu DHCP przez określony interfejs. Domyślnie interfejs podstawowy jest włączony dla klienta DHCP. W tym momencie protokół DHCP można uruchomić w tym interfejsie, wywołując protokół *nx_dhcp_interface_start* lub uruchamiając protokół DHCP we wszystkich włączonych *interfejsach nx_dhcp_start*.

Należy pamiętać, że aplikacja musi najpierw zarejestrować ten interfejs w wystąpieniu adresu IP przy użyciu *nx_ip_interface_attach.*

Ponadto musi być dostępny "rekord" interfejsu klienta DHCP, aby dodać ten interfejs do listy włączonych interfejsów. Domyślnie wartość NX_DHCP_CLIENT_MAX_RECORDS jest zdefiniowana na 1. Ustaw tę opcję na maksymalną liczbę interfejsów, które będą jednocześnie uruchamiać klienta DHCP. Zazwyczaj NX_DHCP_CLIENT_MAX_RECORDS będzie równa NX_MAX_PHYSICAL_INTERFACES; Jeśli jednak urządzenie ma więcej interfejsów fizycznych niż oczekuje uruchomienia klienta DHCP, może zaoszczędzić pamięć, ustawiając dla NX_DHCP_CLIENT_MAX_RECORDS mniejszą liczbę. Nie ma jednego mapowania interfejsów fizycznych z rekordami interfejsu klienta DHCP.

Różnica między tą usługą a usługą *nx_dhcp_set_interface_index* polega na tym, że ustawiany jest tylko jeden interfejs do uruchamiania protokołu DHCP, natomiast ta usługa po prostu dodaje określony interfejs do listy interfejsów klienta włączonych dla protokołu DHCP.

Aby wyłączyć interfejs protokołu DHCP, aplikacja może wywołać *usługę nx_dhcp_interface_disable* dhcp.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **interface_index** Indeks interfejsu umożliwiającego włączenie protokołu DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie protokołu DHCP

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) Brak dostępnych rekordów dla innego interfejsu, który ma być włączony dla protokołu DHCP

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Wyłączanie określonego interfejsu w celu uruchomienia protokołu DHCP 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa wyłącza określony interfejs do uruchamiania protokołu DHCP. Ponownie inicjalizuje klienta DHCP w tym interfejsie.

Aby ponownie uruchomić klienta DHCP, aplikacja musi ponownie włączyć interfejs przy użyciu nx_dhcp_interface_enable *i* ponownie uruchomić protokół DHCP, wywołując *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **interface_index** Indeks interfejsu do wyłączania protokołu DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie protokołu DHCP

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

Ustawianie flagi emisji DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Opis

Ta usługa ustawia lub czyszczy flagę emisji nagłówka komunikatu DHCP dla wszystkich interfejsów włączonych dla protokołu DHCP. W przypadku niektórych komunikatów DHCP (np. ODNAJDYWANIE) flaga emisji jest ustawiona na emisję, ponieważ klient nie ma adresu IP.

__clear_flag__


- **NX_TRUE** flaga emisji jest wyczyszowana (odpowiedź emisji pojedynczej żądania)

- **NX_FALSE** emisji jest ustawiona (żądanie odpowiedzi emisji)

Ta usługa jest przeznaczona dla klientów DHCP, którzy muszą przejść przez router, aby uzyskać dostęp do serwera DHCP, gdzie router odrzuca przekazywanie komunikatów emisji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP  

- **clear_flag** Wartość, na która należy ustawić flagę emisji

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zaktualizowano flagę emisji

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

Ustawianie lub wyczyszczenie flagi emisji w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji hosta klienta DHCP ustawienie lub wyczyszczenie flagi emisji w komunikatach klienta DHCP do serwera DHCP w określonym interfejsie. Aby uzyskać więcej informacji, zobacz **nx_dhcp_clear_broadcast_flag**

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP

- **interface_index** Indeks interfejsu do ustawienia flagi emisji  

- **clear_flag** Wartość, na która należy ustawić flagę emisji

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zaktualizowano flagę emisji

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Ta usługa usuwa utworzone wcześniej wystąpienie DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie protokołu DHCP.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

Wysyłanie wiadomości wymuś odnowienie 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji hosta wysyłanie wymuś odnowienie komunikatu we wszystkich interfejsach z włączoną obsługą protokołu DHCP. Klient DHCP musi być w stanie BOUND. Ta funkcja ustawia stan RENEW w taki sposób, że klient DHCP spróbuje odnowić przed upływem limitu czasu T1.

Aby wysłać wymuś odnowienie określonego interfejsu, gdy wiele interfejsów jest włączonych przy użyciu protokołu DHCP, użyj *nx_dhcp_interface_force_renew*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wysłano wymusz odnowienie.  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Wysyłanie wymuś odnowienie komunikatu na określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji hosta wysyłanie wymuś odnowienie komunikatu w interfejsie wejściowym, o ile ten interfejs został włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*). Klient DHCP w określonym interfejsie musi być w stanie BOUND. Ta funkcja ustawia stan RENEW w taki sposób, że klient DHCP spróbuje odnowić przed upływem limitu czasu T1.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wysłano wymusz odnowienie.  

- **NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

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

Ta usługa umożliwia aplikacji utworzenie puli pakietów klienta DHCP przez przekazanie wskaźnika do wcześniej utworzonej puli pakietów w tym wywołaniu usługi. Aby korzystać z tej funkcji, aplikacja hosta musi definiować NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL. W przypadku nx_dhcp_create *usługa* nie utworzy puli pakietów klienta. Należy pamiętać, że zaleca się używanie przez aplikację wartości domyślnych ładunku puli pakietów klienta DHCP zdefiniowanego jako NX_DHCP_PACKET_PAYLOAD w pliku *nx_dhcp.h* podczas tworzenia puli pakietów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **packet_pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) klienta DHCP jest ustawiona

- **NX_NOT_ENABLED** (0x14) nie jest włączona

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_DHCP_INVALID_PAYLOAD (0x9C) Ładunek jest za mały

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

Ustawianie żądanego adresu IP dla wystąpienia DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP na pierwszym interfejsie włączonym dla protokołu DHCP w rekordzie klienta DHCP. Jeśli *flaga skip_discover_message* ustawiona, klient DHCP pomija komunikat Odnajdywanie i wysyła komunikat Żądanie.

Aby ustawić żądanie określonego adresu IP dla komunikatów DHCP w określonym interfejsie, użyj *nx_dhcp_interface_request_client_ip* ip.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **client_ip_address** Adres IP do żądania z serwera DHCP

- **skip_discover_message** W przypadku wartości true klient DHCP wysyła komunikat żądania  
Jeśli wartość false, wysyła komunikat Odnajdywanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Ustawiono żądany adres IP.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

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

Ustawianie żądanego adresu IP dla wystąpienia DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP klienta DHCP na żądanie z serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*). Jeśli *flaga skip_discover_message* ustawiona, klient DHCP pomija komunikat Odnajdywanie i wysyła komunikat Żądanie.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **Interface_index** Indeks interfejsu do żądania adresu IP

- **client_ip_address** Adres IP do żądania z serwera DHCP

- **skip_discover_message** W przypadku wartości true klient DHCP wysyła komunikat Żądanie; w innym przypadku wysyła komunikat Odnajdywanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Ustawiono żądany adres IP.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik IP lub DHCP

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

Ta usługa wyczyści parametry sieci aplikacji hosta (adres IP, adres sieciowy i maskę sieci) i wyczyści stan klienta DHCP we wszystkich interfejsach włączonych dla protokołu DHCP. Jest on używany w połączeniu z *nx_dhcp_stop* i *nx_dhcp_start* do "ponownego uruchomienia" maszyny stanu DHCP: 

nx_dhcp_stop(&my_dhcp);  
nx_dhcp_reinitialize(&my_dhcp);  
nx_dhcp_start(&my_dhcp);


Aby ponownie zainicjować klienta DHCP na określonym interfejsie, gdy dla protokołu DHCP jest włączonych wiele interfejsów, użyj *nx_dhcp_interface_reinitialize* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) DHCP pomyślnie ponownie 

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

Wyczyść parametry sieci klienta DHCP dla określonego interfejsu 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa wyczyści parametry sieci (adres IP, adres sieciowy i maskę sieci) w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP (zobacz *nx_dhcp_interface_enable*). Zobacz *nx_dhcp_reinitialize,* aby uzyskać więcej informacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP

- **interface_index** Indeks interfejsu do ponownego zainicjowania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Interface successfully reinitialized

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Dzierżawiony adres IP wydania

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia adres IP uzyskany z serwera DHCP, wysyłając komunikat RELEASE do tego serwera. Następnie ponownie inicjalizuje klienta DHCP. Ta usługa jest stosowana do wszystkich interfejsów włączonych dla protokołu DHCP.

Aplikacja może ponownie uruchomić klienta DHCP, wywołując *nx_dhcp_start*.

Aby zwolnić adres z powrotem na serwerze DHCP w określonym interfejsie, użyj *nx_dhcp_interface_release* usługi

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wydanie protokołu DHCP.  

- **NX_DHCP_NOT_BOUND** (0x94) Adres IP nie został wydzierżawiony, dlatego nie można go zwolnić.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Ta usługa zwalnia adres IP uzyskany z serwera DHCP w określonym interfejsie i ponownie inicjalizuje klienta DHCP. Klienta DHCP można uruchomić ponownie, *wywołując* nx_dhcp_start .

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wydanie protokołu DHCP.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- **NX_DHCP_NOT_BOUND** (0x94) Adres IP nie został wydzierżawiony, dlatego nie można go zwolnić.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Ta usługa odrzuca adres IP dzierżawiony z serwera DHCP we wszystkich interfejsach włączonych dla protokołu DHCP. Jeśli NX_DHCP_CLIENT_ SEND_ ARP_PROBE jest zdefiniowany, klient DHCP wyśle komunikat ODRZUĆ, jeśli wykryje, że adres IP jest już w użyciu. Zobacz **Sondy ARP w** rozdziale 1, aby uzyskać więcej informacji na temat konfiguracji sondy ARP w kliencie DHCP NetX.

Aplikacja może użyć tej usługi, aby odrzucić swój adres IP, jeśli odkryje, że adres jest w użyciu w inny sposób.

Ta usługa ponownie inicjalizuje klienta DHCP, aby można go było uruchomić ponownie, wywołując *nx_dhcp_start*.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wysłano odrzuć  

- **NX_DHCP_NOT_STARTED** (0x96) Wystąpienie DHCP nie jest uruchomione

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę

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

Ta usługa wysyła komunikat ODRZUĆ do serwera, aby odrzucić adres IP przypisany przez serwer DHCP. Ponadto ponownie inicjalizuje klienta DHCP. Zobacz *nx_dhcp_decline,* aby uzyskać więcej szczegółów.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

- **Interface_index** Indeks interfejsu odrzucania adresu IP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) komunikat odrzucenia DHCP  

- **NX_DHCP_NOT_BOUND** klienta DHCP 0x94 (0x94)

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Wysyłanie komunikatu DHCP do serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>Opis

Ta usługa wysyła określony komunikat DHCP do serwera DHCP na pierwszym interfejsie włączonym dla protokołu DHCP znalezionego w rekordzie klienta DHCP. Aby wysłać komunikat RELEASE lub DECLINE, aplikacja musi używać usług *nx_dhcp[_interface]_release*() *lub nx_dhcp_interface_decline().*

Klient DHCP musi być uruchomiony do korzystania z tej usługi z wyjątkiem wysyłania INFORM_REQUEST typu komunikatu.

> [!NOTE] 
> Ta usługa nie jest przeznaczona dla aplikacji hosta do "dysku" komputera stanu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **dhcp_message_type** Żądanie komunikatu (zdefiniowane w *nx_dhcp.h*)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) protokołu DHCP  

- **NX_DHCP_NOT_STARTED** (0x96) Nieprawidłowy indeks interfejsu

- **NX_DHCP_INVALID_MESSAGE** (0x9B) Nieprawidłowy typ komunikatu do wysłania

- NX_PTR_ERROR (0x16) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

Wysyłanie komunikatu DHCP do serwera w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Opis

Ta usługa wysyła komunikat do serwera DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Aby wysłać komunikat RELEASE lub DECLINE, aplikacja musi używać usług *nx_dhcp[_interface]_release*() *lub nx_dhcp_interface_decline().*

Klient DHCP musi być uruchomiony do korzystania z tej usługi z wyjątkiem wysyłania DHCP INFORM REQUEST typ komunikatu.

Ta usługa nie jest przeznaczona dla aplikacji hosta do "dysku" komputera stanu klienta DHCP.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **Interface_index** Indeks interfejsu do wysyłania komunikatów  

- **dhcp_message_type** Żądanie komunikatu (zdefiniowane w *nx_dhcp.h*)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) DHCP  

- **NX_DHCP_NOT_STARTED** (0x96) Nieprawidłowy indeks interfejsu

- **NX_DHCP_INVALID_MESSAGE** (0x9B) Nieprawidłowy typ komunikatu do wysłania

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) nie jest włączony dla protokołu DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Uzyskiwanie adresu IP serwera DHCP klienta DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>Opis

Ta usługa pobiera adres IP serwera DHCP klienta DHCP w pierwszym interfejsie włączonym dla protokołu DHCP znalezionym w rekordzie klienta DHCP. Element wywołujący może używać tej usługi tylko wtedy, gdy klient DHCP jest powiązany z adresem IP przypisanym przez serwer DHCP. Aplikacja hosta może użyć usługi *nx_ip_status_check,* aby sprawdzić, czy adres IP został ustawiony, lub może użyć interfejsu *nx_dhcp_state_change_notify* i wysyłać zapytania o stan klienta DHCP NX_DHCP_STATE_BOUND. Zobacz *nx_dhcp_state_change_notify,* aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.

Aby znaleźć serwer DHCP w określonym interfejsie, gdy dla klienta DHCP jest włączonych wiele interfejsów, użyj *nx_dhcp_interface_server_address_get* usługi

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **server_address** Wskaźnik do adresu IP serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) zwracany jest adres serwera DHCP

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Uzyskiwanie adresu IP serwera DHCP klienta DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>Opis

Ta usługa pobiera adres IP serwera DHCP klienta DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Klient DHCP musi być w stanie Powiązana. Po uruchomieniu klienta DHCP w tym interfejsie aplikacja hosta może użyć usługi *nx_ip_status_check* do sprawdzenia, czy adres IP został ustawiony, lub użyć wywołania zwrotnego zmiany stanu klienta DHCP i zapytania o stan klienta DHCP jest NX_DHCP_STATE_BOUND. Zobacz *nx_dhcp_state_change_notify,* aby uzyskać więcej informacji na temat ustawiania funkcji wywołania zwrotnego zmiany stanu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.

- **Interface_index** Indeks interfejsu do uzyskiwania adresu IP  

- **server_address** Wskaźnik do adresu IP serwera

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) zwracany jest adres serwera DHCP

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Brak włączonych interfejsów dla protokołu DHCP

- **NX_DHCP_NOT_BOUND** klienta DHCP 0x94 (0x94)

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Ustawianie interfejsu sieciowego dla wystąpienia dhcp

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Opis

Ta usługa ustawia interfejs sieciowy dla wystąpienia DHCP w celu nawiązania połączenia z serwerem DHCP w programie podczas uruchamiania klienta DHCP skonfigurowanego dla jednego interfejsu sieciowego.

Domyślnie klient DHCP jest uruchamiany w interfejsie podstawowym. Aby uruchomić protokół DHCP w usłudze pomocniczej, użyj tej usługi, aby ustawić interfejs pomocniczy jako interfejs klienta DHCP. Aplikacja musi wcześniej zarejestrować określony interfejs w wystąpieniu adresu IP przy użyciu *nx_ip_interface_attach* usługi.

Należy pamiętać, że ta usługa jest przeznaczona dla aplikacji, które mają uruchamiać klienta DHCP tylko na jednym interfejsie. Aby uruchomić protokół DHCP na wielu interfejsach, *zobacz nx_dhcp_interface_enable* aby uzyskać więcej informacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do bloku sterowania DHCP.  

- **indeks** Indeks interfejsu sieciowego urządzenia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** interfejs (0x00) został pomyślnie ustawiony.

- **NX_INVALID_INTERFACE** (0x4C) Nieprawidłowy interfejs sieciowy

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) włączony dla protokołu DHCP

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) Brak dostępnego rekordu dla innego

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

Ta usługa rozpoczyna przetwarzanie DHCP na wszystkich interfejsach włączonych dla protokołu DHCP. Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*

Aby sprawdzić, kiedy wystąpienie adresu IP jest powiązane z  adresem IP w interfejsie klienta DHCP, użyj nx_ip_status_check , aby sprawdzić, czy adres IP jest prawidłowy.

Jeśli istnieją inne interfejsy, które już działają na serwerze DHCP, ta usługa nie wpłynie na nie.

Aby uruchomić protokół DHCP na określonym interfejsie, gdy jest włączonych wiele interfejsów, użyj *nx_dhcp_interface_start* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uruchomienie protokołu DHCP.  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP jest już uruchomiona.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

Uruchamianie przetwarzania DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa uruchamia przetwarzanie DHCP na określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Zobacz *nx_dhcp_interface_enable*(), aby uzyskać więcej informacji na temat włączania interfejsu dla protokołu DHCP. Domyślnie interfejs podstawowy jest włączony dla protokołu DHCP, gdy aplikacja wywołuje *nx_dhcp_create.*

Jeśli nie ma innych interfejsów z uruchomionym klientem DHCP, ta usługa uruchomi/wznowi wątek klienta DHCP i (ponownie) aktywuje czasomierz klienta DHCP.  
  
Aplikacja powinna użyć *nx_ip_status_check,* aby sprawdzić, czy adres IP został uzyskany.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

- **Interface_index** Indeks, na którym ma być uruchamiany klient DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uruchomienie protokołu DHCP.  

- **NX_DHCP_ALREADY_STARTED** (0x93) Wystąpienie DHCP zostało już uruchomione.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.

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

Ustawianie funkcji wywołania zwrotnego zmiany stanu PROTOKOŁU DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>Opis

Ta usługa rejestruje określoną funkcję wywołania zwrotnego dhcp_state_change_notify celu powiadamiania aplikacji o zmianach stanu DHCP. Funkcja wywołania zwrotnego dostarcza stan, do który przesunił się klient DHCP.

Poniżej przedstawiono wartości skojarzone z różnymi stanami DHCP:

| Stan                             | Wartość |
|-----------------------------------|-------|
| ROZRUCH \_ STANU DHCP NX \_ \_             | 1     |
| INIT STANU DHCP NX \_ \_ \_             | 2     |
| WYBIERANIE \_ STANU DHCP NX \_ \_        | 3     |
| ŻĄDANIE \_ STANU DHCP \_ NX \_       | 4     |
| WIĄZANIE \_ STANU DHCP \_ NX \_            | 5     |
| ODNAWIANIE \_ STANU DHCP \_ \_ NX         | 6     |
| PONOWNE \_ \_ POMIĘCIE STANU DHCP \_ NX        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| SONDOWANIE \_ \_ STANU \_ ADRESU DHCP NX \_ | 9     |


### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

- **dhcp_state_change_notify** Wskaźnik funkcji wywołania zwrotnego zmiany stanu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślnych wywołań zwrotnych.  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

### <a name="example"></a>Przykład

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

Ustawianie funkcji wywołania zwrotnego zmiany stanu DHCP w określonym interfejsie

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

Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu powiadamiania aplikacji o zmianach stanu DHCP. Argumenty wejściowe funciton wywołania zwrotnego są indeksem interfejsu i stanem, do który klient DHCP przesunieł się do tego interfejsu.

Aby uzyskać więcej informacji na temat funkcji zmiany stanu, *zobacz nx_dhcp_state_change_notify*().

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

- **dhcp_interface_state_change_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślnych wywołań zwrotnych.  

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

### <a name="allowed-from"></a>Dozwolone z

Wątki, inicjowanie

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

Zatrzymuje przetwarzanie DHCP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje przetwarzanie DHCP na wszystkich interfejsach, w których rozpoczęto przetwarzanie DHCP. Jeśli nie ma interfejsów przetwarzanych przez protokół DHCP, ta usługa wstrzyma wątek klienta DHCP i uaktywni czasomierz klienta DHCP.

Aby zatrzymać protokół DHCP dla określonego interfejsu, jeśli dla protokołu DHCP jest włączonych wiele interfejsów, użyj *nx_dhcp_interface_stop* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zatrzymanie protokołu DHCP

- **NX_DHCP_NOT_STARTED** (0x96) Wystąpienie DHCP nie jest uruchomione.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

Zatrzymywanie przetwarzania DHCP w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje przetwarzanie DHCP na określonym interfejsie, jeśli protokół DHCP jest już uruchomiony. Jeśli nie ma innych interfejsów z systemem DHCP, wątek DHCP i czasomierz są wstrzymane.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

- **Interface_index** Interfejs, na którym należy zatrzymać przetwarzanie DHCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne zatrzymanie protokołu DHCP

- **NX_DHCP_NOT_STARTED** (0x96) dhcp nie został uruchomiony.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.

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

Pobieranie opcji DHCP z ostatniej odpowiedzi serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera określoną opcję DHCP z buforu opcji DHCP dla pierwszego interfejsu włączonego dla protokołu DHCP znalezionego w rekordzie klienta DHCP. Jeśli to się powiedzie, dane opcji zostaną skopiowane do określonego buforu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.  

- **request_option** Opcja DHCP określona przez RFC. Zobacz opcję NX_DHCP_OPTION w *nx_dhcp.h.*

- **destination_ptr** Wskaźnik do miejsca docelowego ciągu odpowiedzi.  

- **destination_size** Wskaźnik do rozmiaru miejsca docelowego i na zwrot, miejsce docelowe, w którym ma być umieszczana liczba zwracanych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie opcji Powiodło się.  

- **NX_DHCP_NOT_BOUND** (0x94) klient DHCP nie jest powiązany.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Brak włączonych interfejsów dla protokołu DHCP

- **NX_DHCP_DEST_TO_SMALL** (0x95) Miejsce docelowe jest zbyt małe, aby można było przechowywać odpowiedź.

- **NX_DHCP_PARSE_ERROR** (0x97) DHCP nie można znaleźć w odpowiedzi serwera.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik wejściowy.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący tę usługę.

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

Pobieranie opcji DHCP z ostatniej odpowiedzi serwera w określonym interfejsie

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera określoną opcję DHCP z buforu opcji DHCP w określonym interfejsie, jeśli ten interfejs jest włączony dla protokołu DHCP. Jeśli to się powiedzie, dane opcji zostaną skopiowane do określonego buforu.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

- **Interface_index** Indeks, na którym ma zostać pobrana określona opcja  

- **request_option** Opcja DHCP określona przez RFC. Zobacz opcję NX_DHCP_OPTION w *nx_dhcp.h.*  

- **destination_ptr** Wskaźnik do miejsca docelowego ciągu odpowiedzi.  

- **destination_size** Wskaźnik do rozmiaru miejsca docelowego i na zwrot, miejsce docelowe, w którym ma być umieszczana liczba zwracanych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie opcji Powiodło się.  

- **NX_DHCP_NOT_BOUND** (0x94) adres IP nie jest przypisany

- **NX_DHCP_DEST_TO_SMALL** (0x95) jest za mały

- **NX_DHCP_PARSE_ERROR** (0x97) DHCP nie można znaleźć w odpowiedzi serwera.

- NX_PTR_ERROR (0x16) Nieprawidłowy wskaźnik DHCP.

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę.

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

Konwertowanie czterech bajtów na ULONG

### <a name="prototype"></a>Prototype

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>Opis

Ta usługa konwertuje cztery znaki wskazywane przez "option_string_ptr" na niepodpisaną wartość długą. Jest to szczególnie przydatne, gdy są obecne adresy IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **option_string_ptr** Wskaźnik do wcześniej pobranego ciągu opcji.

### <a name="return-values"></a>Wartości zwrócone

- **Wartość** Wartość pierwszych czterech bajtów.

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

Ustawianie funkcji wywołania zwrotnego w celu dodawania opcji podanych przez użytkownika

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

Ta usługa rejestruje określoną funkcję wywołania zwrotnego w celu dodania opcji podanych przez użytkownika.

Jeśli określona funkcja wywołania zwrotnego, aplikacje mogą dodać do pakietu opcje podane przez użytkownika, iface_index i message_type.

> [!NOTE]
> Zgodnie z procedurami użytkownika. Aplikacje muszą postępować zgodnie z formatem opcji DHCP podczas dodawania opcji podanych przez użytkownika. Łączny rozmiar opcji użytkownika musi być mniejszy lub równy user_option_length i aktualizować user_option_length jako rzeczywistą długość opcji. Jeśli NX_TRUE pomyślnie dodasz opcje, w innym przypadku zwróć NX_FALSE.

### <a name="input-parameters"></a>Parametry wejściowe

- **dhcp_ptr** Wskaźnik do wcześniej utworzonego wystąpienia DHCP.

- **dhcp_user_option_add** Wskaźnik do opcji użytkownika dodaj funkcję.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślnych wywołań zwrotnych.

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
