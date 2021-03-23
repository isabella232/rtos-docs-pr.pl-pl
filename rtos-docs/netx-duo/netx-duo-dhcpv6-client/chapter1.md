---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo klient DHCPv6
description: W przypadku sieci IPv6 protokół DHCPv6 zastępuje protokół DHCP na potrzeby dynamicznego przypisywania globalnego adresu IP z serwera DHCPv6 i oferuje większość tych samych funkcji, a także wiele ulepszeń.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3bf3b52c53bb26e2c9c2c736ae35817eb967f609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822002"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo klient DHCPv6

W przypadku sieci IPv6 protokół DHCPv6 zastępuje protokół DHCP na potrzeby dynamicznego przypisywania globalnego adresu IP z serwera DHCPv6 i oferuje większość tych samych funkcji, a także wiele ulepszeń. W tym dokumencie opisano szczegółowo, w jaki sposób interfejs API klienta DHCPv6 usługi Azure RTO NetX Duo jest używany do uzyskiwania adresów IPv6.

## <a name="dhcpv6-communication"></a>Komunikacja DHCPv6

Protokół DHCPv6 używa protokołu UDP. Klient używa portu 546, a serwer używa portu 547 do wymiany komunikatów protokołu DHCPv6. Klient używa swojego adresu lokalnego linku dla adresu źródłowego, aby zainicjować żądania protokołu DHCPv6 dla dostępnych serwerów DHCPv6. Gdy klient wysyła komunikaty przeznaczone dla wszystkich serwerów DHCPv6 w sieci, używa adresu multiemisji *All_DHCP_Relay_Agents_and_Servers* *FF02:: 01:02*. Jest to zarezerwowany adres multiemisji z zakresem linków.

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>Proces DHCPv6 żądania adresu IPv6

Aby rozpocząć proces żądania globalnego przypisania adresu IPv6, klient najpierw wysyła komunikat żądania przy użyciu usługi *nx_dhcpv6_send_solicit* :

**UINT nx_dhcpv6_request_solicit (NX_DHCPV6 \* dhcpv6_ptr)**

Ta wiadomość jest wysyłana do wszystkich serwerów przy użyciu adresu *All_DHCP_Relay_Agents_and_Servers* . W żądaniu żądania klient może zażądać przypisania określonych adresów IPv6 jako wskazówkę do serwera. Może również zażądać innych informacji o konfiguracji sieci z serwera, takiego jak serwer DNS, serwer NTP i inne opcje w żądaniu w wiadomości żądania.

Serwer DHCPv6, który może obsłużyć żądanie klienta, odpowiada za pomocą wiadomości ANONSOWANej zawierającej adresy IPv6, które można przypisać do klienta, czas dzierżawy adresu IPv6 i wszelkie dodatkowe informacje wymagane przez klienta. Protokół klienta DHCPv6 wymaga, aby klient czekał przez pewien czas na otrzymywanie ANONSów komunikatów ze wszystkich serwerów DHCPv6 w sieci. Przetwarza wstępnie każdy komunikat ANONSOWANy jako prawidłowy komunikat i skanuje dane opcji dla różnych parametrów protokołu DHCPv6. Sprawdza również wartość preferencji w preferencjach, jeśli jest ona dostarczana przez serwer. W przypadku odebrania więcej niż jednego komunikatu ANONSu NetX klient DHCPv6 wybiera serwer o najwyższej wartości preferencji otrzymanej na koniec okresu oczekiwania.

Wyjątek polega na tym, że klient otrzymuje komunikat ANONSu z wartością preferencji 255. Akceptuje on komunikat natychmiast i odrzuca wszystkie kolejne komunikaty ANONSOWANe.

Okres oczekiwania jest definiowany jako okres retransmisji, który czeka klient DHCPv6 przed wysłaniem kolejnego komunikatu żądania, jeśli nie otrzymał odpowiedzi z żadnego serwera. Początkowy limit czasu ponownej transmisji w stanie żądania jest definiowany przez protokół DHCPv6 opisany w dokumencie RFC 3315 to 1 sekunda. Kolejne interwały ponownej transmisji, jeśli klient DHCPv6 nie otrzymuje prawidłowej odpowiedzi na serwerze, zostanie podwojony do maksymalnie 120 sekund.

Po wybraniu serwera klient wyodrębnia dane z wiadomości ANONSOWANej i wysyła komunikat żądania z powrotem do serwera w celu zaakceptowania przypisanych informacji o adresie i czasów dzierżawy. Serwer reaguje na komunikat odpowiedzi, aby potwierdzić, że adresy IPv6 klienta są zarejestrowane na serwerze przypisanym do klienta.

Klient DHCPv6 rejestruje przypisane adresy IPv6 z wystąpieniem IP (np. NetX Duo). Jeśli skonfigurowano dla protokołu wykrywania duplikatów adresów (DAD) (domyślnie włączony), NetX Duo automatycznie wyśle komunikaty żądania sąsiada, aby sprawdzić, czy przypisane adresy są unikatowe w sieci. Jeśli tak, powiadamia klienta protokołu DHCPv6, gdy każdy przypisany adres zostanie podwyższony do nieprawidłowej ważności. Klient DHCPv6 zostanie podwyższony do stanu POWIĄZANEgo, a urządzenie może używać tego adresu IPv6 do wysyłania i przesyłania komunikatów. W przypadku niepowodzenia protokołu DAD NetX Duo powiadamia klienta protokołu DHCPv6, a klient DHCPv6 wysyła komunikat odrzucania dla adresów IPv6 przypisanych do serwera i resetuje stan klienta DHCPv6 do stanu INIT.

### <a name="notification-of-successful-address-assignment-and-validation"></a>Powiadomienie o pomyślnym przypisaniu i sprawdzeniu adresu

Aplikacja może określić wynik żądania adresu klienta DHCPv6 od zmiany stanu, jeśli klient DHCPv6 zostanie skonfigurowany przy użyciu wywołania zwrotnego zmiany stanu w usłudze *nx_dhcpv6_client_create* . Jeśli odbierze odpowiedź od serwera, zaobserwowane zmiany stanu są z żądania do INIT. Jeśli odebrano odpowiedź z serwera, ale serwer nie może przypisać adresu, aplikacja zostanie powiadomiona przez wywołanie zwrotne błędu serwera klienta DHCPv6, jeśli zostało skonfigurowane z jednym (również w *nx_dhcpv6_client_create).* Jeśli klient osiągnął stan związany, ale nie zakończył się sprawdzaniem DAD, zobaczy zmianę stanu z powiązania z elementem INIT. Należy pamiętać, że aplikacja, która jest włączona dla DAD, musi przekroczyć czas dla nieprawidłowego sprawdzenia po rozpoczęciu procesu żądania. Zwykle jest to około 400-500 taktów (4-5 s w większości przypadków).

### <a name="relinquishing-an-ipv6-address"></a>Zwalnianie adresu IPv6

Jeśli i kiedy klient musi zwolnić przypisany adres IPv6, informuje serwer DHCPv6 przez wywołanie usługi *nx_dhcpv6_request_release* :

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release (NX_DHCPV6 \* dhcpv6_ptr)

Klient DHCPv6 wysyła komunikat o wydanie emisji pojedynczej zawierający przypisane adresy do serwera, który przypisał adres, i czeka na odpowiedź potwierdzające, że serwer odebrał komunikat.

Uwaga: istnieje inny proces dla klienta, który jest włączony, ale planuje dalsze używanie przypisanych adresów IPv6 przy ponownym uruchomieniu. Komunikat o ZWOLNIeniu nie jest wysyłany na wyłączność, chyba że planuje zażądanie nowego adresu. Aby uzyskać wyjaśnienie tej sytuacji, zobacz "wymagania dotyczące pamięci nietrwałej".

### <a name="dhcpv6-lease-timeouts"></a>Limity czasu dzierżawy DHCPv6

Dzierżawa IPv6 przypisana przez serwer zawiera dwa parametry limitu czasu (T1 i T2) w każdym skojarzeniu tożsamości — bez adresów tymczasowych (IANA). Organizacja IANA jest opisana w innym miejscu tego podręcznika użytkownika. Jeśli czas, który upłynął od momentu powiązania klienta DHCPv6 z przypisanym adresem IPv6 równa T1, klient DHCPv6 automatycznie rozpocznie odnowienie adresu IPv6 przez wysłanie komunikatu o ODNOWIENIu. Jeśli czas, który upłynął, jest równy T2, klient DHCPv6 automatycznie wyśle komunikat o konieczności ponownego powiązania, jeśli nie otrzymał odpowiedzi na żądania ODNOWIENIa.

Dwa inne parametry dzierżawy IPv6, preferowany i prawidłowy okres istnienia są przypisywane do każdego bloku skojarzenia tożsamości zawartego w bloku IANA. Preferowany i prawidłowy okres istnienia to w przypadku, gdy przypisany adres IPv6 jest przestarzały lub nieprawidłowy. T1 musi być krótszy niż preferowany okres istnienia. Wartość T2 musi być mniejsza niż prawidłowy okres istnienia.

### <a name="ip-thread-task-requirements"></a>Wymagania zadania wątku IP

Klient DHCPv6 NetX Duo wymaga utworzenia wystąpienia adresu IP w programie NetX Duo przed utworzeniem klienta DHCPv6 do korzystania z usług klienta DHCPv6.

Protokoły UDP, IPv6 i ICMPv6 muszą być włączone w wystąpieniu IP przed użyciem klienta DHCPv6.

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>Wymagania dotyczące puli pakietów

Tworzenie klienta DHCPv6 w NetX Duo wymaga wcześniej utworzonej puli pakietów do wysyłania komunikatów protokołu DHCPv6. Rozmiar puli pakietów pod względem ładunku pakietu i liczby dostępnych pakietów jest konfigurowany przez użytkownika i zależy od przewidywanej ilości komunikatów protokołu DHCPv6 oraz innych przesyłanych aplikacji.

Typowy komunikat protokołu DHCPv6 ma około 200 bajtów w zależności od liczby adresów IA i opcji protokołu DHCPv6 żądanych przez klienta.

### <a name="network-requirements"></a>Wymagania dotyczące sieci

Klient DHCPv6 NetX Duo wymaga utworzenia gniazda UDP powiązanego z portem 546. Gniazdo jest tworzone podczas tworzenia zadania klienta DHCPv6.

### <a name="non-volatile-memory-requirements"></a>Wymagania dotyczące pamięci nietrwałej

Jeśli klient DHCPv6 zwolni dzierżawę protokołu IPv6 przy użyciu serwera DHCPv6 podczas włączania i żąda nowych adresów IPv6 po ponownym uruchomieniu, nietrwały Magazyn pamięci nie jest wymagany. Jeśli klient chce nadal korzystać z przypisanej dzierżawy, musi przechowywać pewne informacje o kliencie DHCPv6 do nietrwałej pamięci w ramach ponownych uruchomień.

Wymagania dotyczące pamięci nieulotnej i interfejsu API klienta protokołu DHCPv6 zostały omówione w dalszej części w temacie **Korzystanie z klienta Dhcpv6 NetX Duo** w rozdziale dwa.

### <a name="netx-duo-dhcpv6-client-limitations"></a>Ograniczenia klienta DHCPv6 NetX Duo

Bieżąca wersja klienta DHCPv6 NetX Duo ma następujące ograniczenia:

  - Klient DHCPv6 NetX Duo nie obsługuje opcji serwer emisji pojedynczej do wysyłania komunikatów protokołu DHCPv6 emisji pojedynczej do serwera DHCPv6, nawet jeśli serwer wskazuje, że jest to dozwolone.

  - Klient DHCPv6 NetX Duo nie obsługuje żądania ponownego skonfigurowania, w którym serwer inicjuje zmiany adresów IPv6 klientom w sieci.

  - Klient DHCPv6 NetX Duo nie obsługuje formatu przedsiębiorstwa dla bloku kontroli unikatowy identyfikator protokołu DHCPv6. Obsługuje tylko warstwy łączy i warstwy łączy oraz format czasu.

  - Klient DHCPv6 NetX Duo nie obsługuje żądań adresów tymczasowych skojarzenia (), ale obsługuje żądania opcji innych niż tymczasowe (IANA).

## <a name="multihome-and-multiple-address-support"></a>Obsługa wielu użytkowników i adresów

Klient DHCPv6 obsługuje wiele interfejsów i wiele adresów na interfejs. Usługa klienta DHCPv6 *nx_dhcpv6_client_set_interface* umożliwia aplikacji klienckiej Ustawianie interfejsu sieciowego, na którym aplikacja będzie komunikować się z serwerem DHCPv6. Klient DHCPv6 domyślnie jest interfejsem podstawowym (indeks zero).

W przypadku wielu adresów na interfejs klient DHCPv6 utrzymuje wewnętrzną listę adresów, zaczynając od indeksu 0. Należy pamiętać, że ten sam adres zarejestrowany z klientem DHCPv6 nie musi znajdować się w tym samym indeksie w tabeli IP adresów interfejsów.

W przypadku usług klienta DHCPv6, które pobierają informacje o dzierżawie adresów IPv6 klienta, niektóre wymagają określenia indeksu adresu. Poniżej przedstawiono przykład uzyskiwania preferowanych i prawidłowych okresów istnienia:

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

Aplikacja kliencka może również pobrać liczbę prawidłowych adresów IPv6 przypisanych z usługi *nx_dhcpv6_get_valid_ip_address_count* :

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

Starsze usługi klienta DHCPv6 utworzone przed obsługą wielu adresów w NetX Duo nie pobierają indeksu adresu. W związku z tym te usługi są z tego powodu wykonywane z podstawowego globalnego adresu IA, niezależnie od tego, jak wiele adresów IA jest przypisanych do klienta. Przykład przedstawiono poniżej:

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>Funkcje wywołania zwrotnego klienta DHCPv6 NetX Duo

*nx_dhcpv6_state_change_callback*

Gdy klient DHCPv6 zmieni stan protokołu DHCPv6 w wyniku przetwarzania żądania DHCPv6, powiadamia aplikację za pomocą tej funkcji wywołania zwrotnego.

*nx_dhcpv6_server_error_handler*

Gdy klient DHCPv6 odbiera odpowiedź serwera zawierającą opcję *stanu* o stanie innym niż zero (niepowodzenie), powiadamia aplikację za pomocą tego wywołania zwrotnego, które zawiera kod stanu błędu serwera.

Uwaga: ponieważ te funkcje wywołania zwrotnego są wywoływane z zadania wątku klienta protokołu DHCPv6, aplikacja kliencka nie może wywołać żadnych usług klienta DHCPv6 NetX Duo, które wymagają kontroli muteksów klienta DHCPv6, takich jak *nx_dhcpv6_start, nx_dhcpv6_stop* i dowolny interfejs API, który wysyła wiadomości bezpośrednio z wywołania zwrotnego, np. *nx_dhcpv6_request_release*.

## <a name="dhcpv6-rfcs"></a>Specyfikacje RFC protokołu DHCPv6

Usługa DHCP NetX Duo jest zgodna z RFC3315, RFC3646 i powiązanymi specyfikacjami RFC.