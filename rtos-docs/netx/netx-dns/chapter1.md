---
title: Rozdział 1 — Wprowadzenie do Azure RTOS DNS NetX
description: Usługa Azure RTOS NetX DNS udostępnia rozproszoną bazę danych, która zawiera mapowanie między nazwami domen i fizycznymi adresami IP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fda8c5b1bdb35e8312204374592e411a6a1e44f79a4a75a035a7886223c22b53
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796393"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-dns-client"></a>Rozdział 1 — Wprowadzenie do Azure RTOS DNS NetX

Usługa Azure RTOS NetX DNS udostępnia rozproszoną bazę danych, która zawiera mapowanie między nazwami domen i fizycznymi adresami IP. Baza danych jest określana jako  rozproszona, ponieważ w Internecie nie ma pojedynczej jednostki zawierającej pełne mapowanie. Jednostka, która przechowuje część mapowania, jest nazywana serwerem DNS. Internet składa się z wielu serwerów DNS, z których każdy zawiera podzbiór bazy danych. Serwery DNS również odpowiadać na żądania klienta DNS informacje mapowania nazw domen, tylko wtedy, gdy serwer ma żądane mapowanie.

Protokół klienta DNS dla NetX zapewnia aplikacji z usługami żądania informacji mapowania z jednego lub większej liczby serwerów DNS.

## <a name="dns-client-setup"></a>Konfiguracja klienta DNS

Aby pakiet klienta DNS działał prawidłowo, wymaga, aby wystąpienie adresu IP NetX zostało już utworzone.

Po utworzeniu klienta DNS aplikacja musi dodać co najmniej jeden serwer DNS do listy serwerów utrzymywanej przez klienta DNS. Aby dodać serwery DNS, aplikacja używa *nx_dns_server_add* usługi.

Jeśli opcja NX_DNS_IP_GATEWAY_SERVER jest włączona, a adres bramy wystąpienia IP jest niezerowy, brama wystąpienia adresu IP jest automatycznie dodawana jako podstawowy serwer DNS. Jeśli informacje o serwerze DNS nie są znane statycznie, mogą być również uzyskiwane za pośrednictwem Dynamic Host Configuration Protocol (DHCP) dla NetX. Aby uzyskać więcej informacji, zapoznaj się z podręcznikiem użytkownika protokołu DHCP netx.

Klient DNS wymaga puli pakietów do przesyłania komunikatów DNS. Domyślnie klient DNS tworzy tę pulę pakietów, gdy *nx_dns_create* wywoływana jest usługa DNS. Opcje konfiguracji NX_DNS_PACKET_PAYLOAD i NX_DNS_PACKET_POOL_SIZE umożliwiają aplikacji określenie ładunku pakietu i rozmiaru puli pakietów (np. liczby pakietów) dla tej puli pakietów. Te opcje są opisane w sekcji "Opcje konfiguracji" w rozdziale 2.

Alternatywą dla klienta DNS tworzącego własną pulę pakietów jest utworzenie puli pakietów przez aplikację i ustawienie jej jako puli pakietów klienta DNS przy użyciu usługi *nx_dns_packet_pool_set* dns. Aby to zrobić, NX_DNS_CLIENT_USER_CREATE_PACKET_POOL musi być zdefiniowana opcja. Ta opcja wymaga również wcześniej utworzonej puli pakietów przy *użyciu nx_packet_pool_create* jako danych wejściowych wskaźnika puli pakietów do *nx_dns_packet_pool_set*. Po usunięciu wystąpienia klienta DNS aplikacja jest odpowiedzialna za usunięcie puli pakietów klienta DNS, jeśli NX_DNS_CLIENT_USER_CREATE_PACKET_POOL jest włączona, jeśli nie jest już potrzebna.

>[!NOTE] 
> W przypadku aplikacji wybierających własną pulę pakietów przy użyciu opcji **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** rozmiar pakietu musi być w stanie przechowywać maksymalny rozmiar systemu DNS (512 bajtów) plus pomieszczenia dla nagłówka UDP, nagłówka IPv4 i nagłówka MAC.

## <a name="dns-messages"></a>Komunikaty DNS

System DNS ma bardzo prosty mechanizm uzyskiwania mapowania między nazwami hostów i adresami IP. Aby uzyskać mapowanie, klient DNS przygotowuje komunikat zapytania DNS zawierający nazwę lub adres IP, który musi zostać rozpoznany. Komunikat jest następnie wysyłany do pierwszego serwera DNS na liście serwerów. Jeśli serwer ma takie mapowanie, odpowiada klientowi DNS przy użyciu komunikatu odpowiedzi DNS, który zawiera żądane informacje mapowania. Jeśli serwer nie odpowiada, klient DNS wysyła zapytanie do następnego serwera na swojej liście, dopóki wszystkie jego serwery DNS nie zostały zbadane. Jeśli nie zostanie odebrana żadna odpowiedź ze wszystkich serwerów DNS, klient DNS ma logikę ponawiania próby ponownego przesłania komunikatu DNS. Podczas ponownego wysyłanie zapytania DNS limit czasu ponownej transmisji jest dwukrotnie. Ten proces jest kontynuowany do momentu osiągnięciu maksymalnego limitu czasu transmisji (zdefiniowanego jako NX_DNS_MAX_RETRANS_TIMEOUT w *nxd_dns.h*) lub do momentu, gdy zostanie odebrana pomyślna odpowiedź z tego serwera.

Klient DNS NetX może wykonywać wyszukiwania adresów IPv4 (typ A), wywołując nx_dns_host_by_name_get *lub* *nx_dns_ipv4_address_by_name_get*. Klient DNS może wykonywać wyszukiwania wsteczne adresów IP (typ zapytań PTR), aby uzyskać nazwy hostów internetowych przy *użyciu nx_dns_host_by_address_get*.

Obsługa komunikatów DNS wykorzystuje protokół UDP do wysyłania żądań i odpowiedzi w polach. Serwer DNS nasłuchuje zapytań od klientów na porcie o numerze 53. W związku z tym usługi UDP muszą być włączone w programie NetX przy użyciu usługi ***nx_udp_enable** _ na wcześniej utworzonym wystąpieniu adresu IP (_*nx_ip_create **).

W tym momencie klient DNS jest gotowy do akceptowania żądań z aplikacji i wysyłania zapytań DNS.

## <a name="extended-dns-resource-record-types"></a>Rozszerzone typy rekordów zasobów DNS

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest włączona, klient DNS NetX obsługuje również następujące zapytania dotyczące typu rekordu:

- **CNAME**: zawiera nazwę kanoniczną aliasu

- **TXT**: zawiera ciąg tekstowy

- **NS**: zawiera autorytatywny serwer nazw

- **SOA:** zawiera początek strefy urzędu

- **MX**: używany do wymiany poczty e-mail

- **SRV**: zawiera informacje o usłudze oferowanej przez domenę

Z wyjątkiem typów rekordów CNAME i TXT aplikacja musi podać 4-bajtowy bufor wyrównany w celu odbierania rekordu danych DNS.

W kliencie DNS NetX dane rekordu są przechowywane w taki sposób, aby jak najbardziej efektywne wykorzystanie miejsca w buforze.

W przypadku zapytań, których typy rekordów mają zmienną długość danych, takich jak rekordy NS, których nazwy hostów mają zmienną długość, klient DNS NetX zapisuje dane w następujący sposób. Bufor podany w zapytaniu klienta DNS jest zorganizowany w obszarze danych o stałej długości i obszarze pamięci bez struktury. Górna część buforu pamięci jest zorganizowana w 4-bajtowe wpisy rekordu wyrównane. Każdy wpis rekordu zawiera adres IP i wskaźnik do danych o zmiennej długości dla tego adresu IP. Dane o zmiennej długości dla każdego adresu IP są przechowywane w pamięci obszaru bez struktury, począwszy od końca bufora pamięci. Dane o zmiennej długości dla każdego kolejnego wpisu rekordu są zapisywane w następnej pamięci obszaru sąsiadujące z poprzednimi wpisami rekordu dane zmiennych. W związku z tym dane zmiennych "rozrastają się" w kierunku ustrukturyzowanego obszaru pamięci zawierającego wpisy rekordu, dopóki nie za mało pamięci do przechowywania innego wpisu rekordu i danych zmiennych.

Pokazano to na poniższej ilustracji:

![Diagram przykładu magazynu danych nazwy domeny S (N S)](media/image1.png)

Przykład magazynu danych nazwy domeny DNS (NS) przedstawiono powyżej.

Zapytania klienta DNS NetX przy użyciu formatu magazynu rekordów zwracają liczbę rekordów zapisanych w buforze rekordów. Te informacje umożliwiają aplikacji wyodrębnienie rekordów NS z buforu rekordów.

Poniżej przedstawiono przykład zapytania klienta DNS, które przechowuje dane DNS o zmiennej długości przy użyciu tego formatu magazynu rekordów:

```c
UINT     _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR  *host_name, 
                                        VOID *record_buffer, UINT buffer_size, 
                                        UINT *record_count, ULONG wait_option);
```

Więcej szczegółów można znaleźć w rozdziale 3 "Opis usług klienta DNS".

## <a name="dns-cache"></a>Pamięć podręczna DNS

Jeśli NX_DNS_CACHE_ENABLE jest włączona, klient DNS NetX obsługuje funkcję pamięci podręcznej DNS. Po utworzeniu klienta DNS aplikacja może wywołać interfejs API *nx_dns_cache_initialize(),* aby ustawić specjalną pamięć podręczną DNS. Jeśli włączy funkcję pamięci podręcznej DNS, klient DNS znajdzie dostępną odpowiedź z pamięci podręcznej DNS przed rozpoczęciem wysyłania zapytania DNS, jeśli znajdzie dostępną odpowiedź, bezpośrednio zwróci odpowiedź do aplikacji. W przeciwnym razie klient DNS wysyła komunikat zapytania do serwera DNS i czeka na odpowiedź. Gdy klient DNS pobiera komunikat odpowiedzi i jest dostępna bezpłatna pamięć podręczna, klient DNS zwraca odpowiedź do aplikacji, a także dodaje odpowiedź jako rekord zasobu do pamięci podręcznej DNS.

Każda odpowiedź na pytanie *o* NX_DNS_RR (rekord zasobu) w pamięci podręcznej. Ciągi (nazwa rekordu zasobu i dane) w rekordach mają zmienną długość, dlatego nie są przechowywane w NX_DNS_RR danych. Rekord zawiera wskaźniki do rzeczywistej lokalizacji pamięci, w której są przechowywane ciągi. Tabela ciągów i rekordy współdzielą pamięć podręczną. Rekordy są przechowywane od początku pamięci podręcznej i rosną pod koniec pamięci podręcznej. Tabela ciągów zaczyna się od końca pamięci podręcznej i powiększa się do początku pamięci podręcznej. Każdy ciąg w tabeli ciągów ma pole długości i pole licznika. Gdy ciąg jest dodawany do tabeli ciągów, jeśli ten sam ciąg jest już obecny w tabeli, wartość licznika jest zwiększana i nie jest przydzielana pamięć dla ciągu. Pamięć podręczna jest uważana za zapełnianą, jeśli do pamięci podręcznej nie można dodać żadnych dodatkowych rekordów zasobów lub nowych ciągów.

## <a name="dns-client-limitations"></a>Ograniczenia klienta DNS

Klient DNS obsługuje jedno żądanie DNS na raz. Wątki próbujące wykonać kolejne żądanie DNS są tymczasowo blokowane do czasu ukończenia poprzedniego żądania DNS.

Klient DNS NetX nie używa danych z autorytatywnych odpowiedzi do przekazywania dodatkowych zapytań DNS do innych serwerów DNS.

## <a name="dns-rfcs"></a>RFC DNS

System DNS NetX jest zgodny z następującymi RFC:

- NAZWY DOMEN RFC1034 — POJĘCIA I OBIEKTY
- NAZWY DOMEN RFC1035 — IMPLEMENTACJA I SPECYFIKACJA
- RFC1480 domena USA
- RFC 2782 A DNS RR do określania lokalizacji usług (DNS SRV)