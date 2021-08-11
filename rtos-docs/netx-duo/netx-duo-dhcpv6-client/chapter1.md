---
title: Rozdział 1 — Wprowadzenie do klienta AZURE RTOS NetX Duo DHCPv6
description: W sieciach IPv6 protokół DHCPv6 zastępuje protokół DHCP dla dynamicznego globalnego przypisywania adresów IP z serwera DHCPv6 i oferuje większość tych samych funkcji, a także wiele ulepszeń.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f938be404c121f3080cfed1a81aa356f698538c4f557387009d951df40496a6d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791316"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>Rozdział 1 — Wprowadzenie do klienta AZURE RTOS NetX Duo DHCPv6

W sieciach IPv6 protokół DHCPv6 zastępuje protokół DHCP dla dynamicznego globalnego przypisywania adresów IP z serwera DHCPv6 i oferuje większość tych samych funkcji, a także wiele ulepszeń. W tym dokumencie szczegółowo wyjaśniono, jak interfejs API klienta Azure RTOS NetX Duo DHCPv6 jest używany do uzyskiwania adresów IPv6.

## <a name="dhcpv6-communication"></a>Komunikacja DHCPv6

Protokół DHCPv6 używa protokołu UDP. Klient używa portu 546, a serwer używa portu 547 do wymiany komunikatów DHCPv6. Klient używa swojego lokalnego adresu linku dla adresu źródłowego do inicjowania żądań DHCPv6 do dostępnych serwerów DHCPv6. Gdy klient wysyła komunikaty przeznaczone dla wszystkich serwerów DHCPv6 w sieci używa adresu *All_DHCP_Relay_Agents_and_Servers* multiemisji *FF02::01:02.* Jest to zastrzeżony adres multiemisji o zakresie łącza.

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>Proces DHCPv6 żądania adresu IPv6

Aby rozpocząć proces żądania globalnego przypisania adresu IPv6, klient najpierw wysyła komunikat SOLICIT przy użyciu *nx_dhcpv6_send_solicit* usługi:

**UINT nx_dhcpv6_request_solicit(NX_DHCPV6 \* dhcpv6_ptr)**

Ten komunikat jest wysyłany do wszystkich serwerów przy użyciu *All_DHCP_Relay_Agents_and_Servers* adresu. W żądaniu SOLICIT Klient może zażądać przypisania określonych adresów IPv6 jako wskazówek do serwera. Może również żądać innych informacji o konfiguracji sieci z serwera, takich jak serwer DNS, serwer NTP i inne opcje w żądaniu opcji w komunikacie SOLICIT.

Serwer DHCPv6, który może przesiecić żądanie klienta, odpowiada komunikatem ANONS zawierającym adres(y) IPv6, które można przypisać do klienta, czas dzierżawy adresu IPv6 i wszelkie dodatkowe informacje żądane przez klienta. Protokół klienta DHCPv6 wymaga od klienta oczekiwania przez okres czasu na odbieranie komunikatów ANONS ZE wszystkich serwerów DHCPv6 w sieci. Wstępnie przetwarza każdy komunikat ANONS jako prawidłowy komunikat i skanuje dane opcji dla różnych parametrów DHCPv6. Sprawdza również wartość preferencji w opcji preferencji, jeśli jest dostarczany przez serwer. Jeśli zostanie odebrany więcej niż jeden komunikat ANONS, klient DHCPv6 NetX wybierze serwer z najwyższą wartością preferencji odebraną na koniec okresu oczekiwania.

Wyjątek występuje, jeśli klient odbiera komunikat ANONS Z wartością preferencji 255. Natychmiast akceptuje ten komunikat i odrzuca wszystkie kolejne komunikaty ANONS.

Okres oczekiwania jest zdefiniowany jako okres retransmisji, który klient DHCPv6 czeka przed wysłaniem kolejnego komunikatu SOLICIT, jeśli nie otrzymał odpowiedzi z żadnego serwera. Początkowy limit czasu retransmisji w stanie SOLICIT jest definiowany przez protokół DHCPv6 opisany w dokumencie RFC 3315 jako 1 sekundę. Kolejne interwały retransmisji, jeśli klient DHCPv6 nie odbierze prawidłowej odpowiedzi serwera, zostaną podwojone do maksymalnie 120 sekund.

Po wybraniu serwera klient wyodrębnia dane z komunikatu ADVERTISE i wysyła komunikat REQUEST z powrotem do serwera, aby zaakceptować informacje o przypisanym adresie i czasy dzierżawy. Serwer odpowiada komunikatem REPLY w celu potwierdzenia, że adres(y) IPv6 klienta są zarejestrowane na serwerze jako przypisane do klienta.

Klient DHCPv6 rejestruje przypisane adresy IPv6 w wystąpieniu adresu IP (np. NetX Duo). Jeśli skonfigurowano protokół wykrywania zduplikowanych adresów (TCP, Duplicate Address Detection) (domyślnie włączony), program NetX Duo będzie automatycznie wysyłać wiadomości sąsiadujące w celu sprawdzenia, czy przypisane adres(y) są unikatowe w sieci. Jeśli tak, powiadamia klienta DHCPv6, gdy każdy przypisany adres zostanie podniesieny z WARTOŚCIOWY DO PRAWIDŁOWY. Poziom klienta DHCPv6 jest podyowany do stanu BOUND, a urządzenie może używać tego adresu IPv6 do wysyłania i przesyłania komunikatów. Jeśli protokół DHCP ulegnie awarii, NetX Duo powiadamia klienta DHCPv6, a klient DHCPv6 wysyła komunikat ODRZUCENIA dla adresów IPv6 przypisanych z powrotem do serwera i resetuje stan klienta DHCPv6 do stanu INIT.

### <a name="notification-of-successful-address-assignment-and-validation"></a>Powiadomienie o pomyślnym przypisaniu adresu i weryfikacji

Aplikacja może określić wynik żądania adresu klienta DHCPv6 ze zmian stanu, jeśli klient DHCPv6 jest skonfigurowany przy użyciu wywołania zwrotnego zmiany stanu w nx_dhcpv6_client_create *usługi.* Jeśli nie otrzyma odpowiedzi z serwera, zaobserwowana zmiana stanu pochodzi z SOLICIT na INIT. Jeśli serwer odebrał odpowiedź z serwera, ale nie może przypisać adresu, aplikacja zostanie powiadomiona przez wywołanie zwrotne błędu serwera klienta DHCPv6, jeśli zostanie skonfigurowane za pomocą jednego z nich (również w *nx_dhcpv6_client_create).* Jeśli klient osiągnął stan BOUND, ale następnie nie powiódł się podczas sprawdzania STANU, zobaczy zmianę stanu z BOUND na INIT. Należy pamiętać, że aplikacja, która jest włączona dla funkcji NOTC, musi po rozpoczęciu procesu żądania wymagać czasu na sprawdzenie w trybie THE. Zwykle jest to około 400–500 takt (w większości przypadków 4–5 sekund).

### <a name="relinquishing-an-ipv6-address"></a>Relinquishing an IPv6 Address

Jeśli i kiedy klient musi zwolnić przypisany adres IPv6, informuje on serwer DHCPv6, wywołując *usługę nx_dhcpv6_request_release* usługę:

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release(NX_DHCPV6 \* dhcpv6_ptr)

Klient DHCPv6 wysyła komunikat RELEASE emisji pojedynczej zawierający przypisane adresy do serwera, który przypisał adres, i czeka na odpowiedź z potwierdzeniem, że serwer odebrał komunikat.

Uwaga: Istnieje inny proces dla klienta, który jest wyzwolony, ale planuje dalsze używanie przypisanych adresów IPv6 po ponownym uruchomieniu. Nie wysyła ona komunikatu RELEASE przy zasilaniu, chyba że planuje zażądać nowego adresu podczas zasilania. Aby uzyskać wyjaśnienie tej sytuacji, zobacz "Wymagania dotyczące pamięci trwałej".

### <a name="dhcpv6-lease-timeouts"></a>Limity czasu dzierżawy DHCPv6

Dzierżawa IPv6 przypisana przez serwer zawiera dwa parametry limitu czasu T1 i T2 w każdym bloku Identity Association — Non Temporary Addresses (IANA). IANA jest opisana w innym miejscu tego Podręcznika użytkownika. Jeśli czas, który upłynął od momentu, gdy klient DHCPv6 został powiązany z przypisanym adresem IPv6, jest równy T1, klient DHCPv6 automatycznie rozpoczyna odnawianie adresu IPv6, wysyłając komunikat RENEW. Jeśli upłynął czas T2, klient DHCPv6 automatycznie wysyła komunikat REBIND, jeśli nie otrzymał odpowiedzi na żądania RENEW.

Dwa inne parametry dzierżawy IPv6 , preferowany i prawidłowy okres istnienia, są przypisywane do każdego bloku skojarzenia tożsamości (IA) zawartego w bloku IANA. Preferowanymi i prawidłowymi okresami istnienia są, odpowiednio, gdy przypisany adres IPv6 jest przestarzały lub nieprawidłowy. T1 musi być krótszy niż preferowany okres istnienia. T2 musi być krótszy niż prawidłowy okres istnienia.

### <a name="ip-thread-task-requirements"></a>Wymagania dotyczące zadań wątku IP

Klient NetX Duo DHCPv6 wymaga utworzenia wystąpienia adresu IP NetX Duo przed utworzeniem klienta DHCPv6 w celu korzystania z usług klienta DHCPv6.

Protokół UDP, IPv6 i ICMPv6 muszą być włączone w wystąpieniu adresu IP przed użyciem klienta DHCPv6.

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>Wymagania dotyczące puli pakietów

Tworzenie klienta DHCPv6 netX Duo wymaga wcześniej utworzonej puli pakietów do wysyłania komunikatów DHCPv6. Rozmiar puli pakietów pod względem ładunku pakietu i liczby dostępnych pakietów jest konfigurowalny przez użytkownika i zależy od przewidywanej ilości komunikatów DHCPv6 i innych transmisji, które będzie wysyłać aplikacja.

Typowy komunikat DHCPv6 to około 200 bajtów w zależności od liczby adresów IA i opcji protokołu DHCPv6 żądanych przez klienta.

### <a name="network-requirements"></a>Wymagania dotyczące sieci

Klient NetX Duo DHCPv6 wymaga utworzenia gniazda UDP powiązanego z portem 546. Gniazdo jest tworzone podczas tworzenia zadania klienta DHCPv6.

### <a name="non-volatile-memory-requirements"></a>Wymagania dotyczące pamięci trwałej

Jeśli klient DHCPv6 zwalnia dzierżawę IPv6 z serwerem DHCPv6 podczas uruchamiania i żąda nowych adresów IPv6 przy ponownym uruchomieniu, nie jest wymagany nietrwały magazyn pamięci. Jeśli klient chce nadal korzystać z przypisanej dzierżawy, musi przechowywać pewne informacje o kliencie DHCPv6 w trwałej pamięci podczas ponownych rozruchów.

Wymagania dotyczące pamięci trwałej i interfejs API klienta DHCPv6 zostały omówione w dalszej części tematu Korzystanie z klienta **DHCPv6 NetX Duo** w rozdziale 2.

### <a name="netx-duo-dhcpv6-client-limitations"></a>NetX Duo DHCPv6 Client Limitations

Bieżąca wersja klienta NETX Duo DHCPv6 ma następujące ograniczenia:

  - Klient NetX Duo DHCPv6 nie obsługuje opcji emisji pojedynczej serwera w celu wysyłania komunikatów DHCPv6 emisji pojedynczej do serwera DHCPv6, nawet jeśli serwer wskazuje, że jest to dozwolone.

  - Klient NetX Duo DHCPv6 nie obsługuje żądania ponownego konfigurowania, w którym serwer inicjuje zmiany adresów IPv6 w klientach w sieci.

  - Klient NetX Duo DHCPv6 nie obsługuje formatu Enterprise dla bloku sterowania unikatowym identyfikatorem DHCPv6. Obsługuje tylko warstwy łącza i warstwy łącza plus format czasu.

  - Klient NetX Duo DHCPv6 nie obsługuje żądań adresów tymczasowego skojarzenia(TA), ale obsługuje żądania opcji non temporary (IANA).

## <a name="multihome-and-multiple-address-support"></a>Obsługa wieloadresowych i wieloadresowych adresów

Klient DHCPv6 obsługuje wiele interfejsów i wiele adresów na interfejs. Usługa klienta DHCPv6, *nx_dhcpv6_client_set_interface* umożliwia aplikacji klienckiej ustawienie interfejsu sieciowego, na którym aplikacja będzie komunikować się z serwerem DHCPv6. Domyślnie klient DHCPv6 jest interfejsem podstawowym (indeks zero).

W przypadku wielu adresów na interfejs klient DHCPv6 przechowuje wewnętrzną listę adresów rozpoczynającą się od indeksu 0. Należy pamiętać, że ten sam adres zarejestrowany za pomocą klienta DHCPv6 nie musi być umieszczony w tym samym indeksie w tabeli ADRESÓW IP adresów interfejsu.

W przypadku usług klienta DHCPv6, które pobierają informacje o dzierżawie adresu IPv6 klienta, niektóre wymagają określonego indeksu adresów. Poniżej przedstawiono przykład uzyskiwania preferowanych i prawidłowych okresów istnienia:

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

Aplikacja kliency może również pobrać liczbę prawidłowych adresów IPv6 przypisanych z *nx_dhcpv6_get_valid_ip_address_count* usługi:

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

Starsze usługi klienta DHCPv6, które zostały utworzone przed rozpoczęciem obsługi wielu adresów w netx duo, nie mają indeksu adresów. W związku z tym w przypadku tych usług żądane dane są zbierane z podstawowego globalnego adresu IA, niezależnie od tego, ile adresów IA jest przypisanych do klienta. Przykład przedstawiono poniżej:

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>Funkcje wywołania zwrotnego klienta NETX Duo DHCPv6

*nx_dhcpv6_state_change_callback*

Gdy klient DHCPv6 zmieni się na nowy stan DHCPv6 w wyniku przetwarzania żądania DHCPv6, powiadamia aplikację za pomocą tej funkcji wywołania zwrotnego.

*nx_dhcpv6_server_error_handler*

Gdy klient DHCPv6 otrzymuje odpowiedź serwera zawierającą opcję *Stan* ze stanem innym niż zero (niepowodzny), powiadamia aplikację za pomocą tego wywołania zwrotnego, które zawiera kod stanu błędu serwera.

Uwaga: Ponieważ te funkcje wywołania zwrotnego są wywoływane z zadania wątku klienta DHCPv6, aplikacja klienjąca NIE może wywołać żadnych usług klienta DHCPv6 NetX Duo, które wymagają kontroli mutex klienta DHCPv6, takich jak *nx_dhcpv6_start, nx_dhcpv6_stop,* ani żadnego interfejsu API, który wysyła komunikaty bezpośrednio z wywołania zwrotnego, np. *nx_dhcpv6_request_release*.

## <a name="dhcpv6-rfcs"></a>DhCPv6 RFC

Protokół DHCP NetX Duo jest zgodny ze standardami RFC3315, RFC3646 i powiązanymi RFC.