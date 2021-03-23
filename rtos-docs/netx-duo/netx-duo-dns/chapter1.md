---
title: Rozdział 1 — wprowadzenie do klienta DNS usługi Azure RTO NetX Duo
description: System DNS udostępnia rozproszoną bazę danych, która zawiera mapowanie między nazwami domen i fizycznymi adresami IP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4c07d6e3183d421c637874dcdeff3767554fca78
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821930"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dns-client"></a>Rozdział 1 — wprowadzenie do klienta DNS usługi Azure RTO NetX Duo

System DNS udostępnia rozproszoną bazę danych, która zawiera mapowanie między nazwami domen i fizycznymi adresami IP. Baza danych jest określana jako *dystrybuowana* , ponieważ nie ma żadnej pojedynczej jednostki w Internecie zawierającej kompletne mapowanie. Jednostka, która utrzymuje część mapowania, nazywa się serwerem DNS. Internet składa się z wielu serwerów DNS, z których każdy zawiera podzestaw bazy danych. Serwery DNS odpowiadają również na żądania klientów DNS dotyczące informacji o mapowaniu nazw domen, tylko jeśli serwer ma żądane mapowanie.

Protokół klienta DNS dla NetX Duo udostępnia aplikację z usługami do żądania informacji o mapowaniu z jednego lub większej liczby serwerów DNS.

## <a name="dns-client-setup"></a>Konfiguracja klienta DNS

Aby zapewnić prawidłowe działanie, pakiet klienta DNS wymaga, aby wystąpienie adresu IP NetX Duo zostało już utworzone.

Po utworzeniu klienta DNS aplikacja musi dodać jeden lub więcej serwerów DNS do listy serwerów obsługiwanej przez klienta DNS. Aby dodać serwery DNS, aplikacja używa usługi *nxd_dns_server_add* . *Nx_dns_server_add* usługi klienta DNS NetX Duo można także użyć do dodawania serwerów. Jednak akceptuje tylko adresy IPv4 i zaleca się, aby deweloperzy używali usługi *nxd_dns_server_add* .

Jeśli opcja NX_DNS_IP_GATEWAY_SERVER jest włączona, a adres bramy wystąpienia IP jest różny od zera, Brama wystąpienia IP jest automatycznie dodawana jako podstawowy serwer DNS. Jeśli informacje o serwerze DNS nie są identyfikowane statycznie, mogą również pochodzić z Dynamic Host Configuration Protocol (DHCP) dla NetX Duo. Aby uzyskać więcej informacji, zapoznaj się z podręcznikiem użytkownika DHCP NetX Duo.

Klient DNS wymaga puli pakietów do przesyłania komunikatów DNS. Domyślnie klient DNS tworzy tę pulę pakietów, gdy zostanie wywołana usługa *nx_dns_create* . Opcje konfiguracji NX_DNS_PACKET_PAYLOAD_UNALIGNED i NX_DNS_PACKET_POOL_SIZE umożliwiają aplikacji określenie rozmiaru ładunku pakietu i puli pakietów (np. liczby pakietów) odpowiednio do tej puli pakietów. Te opcje są opisane w sekcji "Opcje konfiguracji" w rozdziale dwa.

Alternatywą dla klienta DNS tworzenia własnej puli pakietów jest utworzenie puli pakietów przez aplikację i ustawienie jej jako puli pakietów klienta DNS przy użyciu usługi *nx_dns_packet_pool_set* . Aby to zrobić, należy zdefiniować opcję NX_DNS_CLIENT_USER_CREATE_PACKET_POOL. Ta opcja wymaga również, aby wcześniej utworzona Pula pakietów była używana *nx_packet_pool_create* jako dane wejściowe wskaźnika puli pakietów do *nx_dns_packet_pool_set* . Po usunięciu wystąpienia klienta DNS aplikacja jest odpowiedzialna za usunięcie puli pakietów klienta DNS, jeśli NX_DNS_CLIENT_USER_CREATE_PACKET_POOL jest włączona, jeśli nie jest już potrzebne.

> [!NOTE] 
> W przypadku aplikacji, które umożliwiają udostępnienie własnej puli pakietów przy użyciu opcji NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, rozmiar pakietu musi mieć możliwość przechowywania maksymalnego rozmiaru Massage systemu DNS (512 bajtów) oraz pokojów dla nagłówka UDP, adresu IPv4 lub IPv6 oraz nagłówka MAC.

## <a name="dns-messages"></a>Komunikaty DNS

System DNS ma bardzo prosty mechanizm uzyskiwania mapowania między nazwami hostów i adresami IP. Aby uzyskać mapowanie, klient DNS przygotuje komunikat zapytania DNS zawierający nazwę lub adres IP, który musi zostać rozpoznany. Wiadomość jest następnie wysyłana do pierwszego serwera DNS na liście serwerów. Jeśli serwer ma takie mapowanie, wysyła odpowiedź do klienta DNS przy użyciu komunikatu odpowiedzi DNS zawierającego żądane informacje mapowania. Jeśli serwer nie odpowiada, klient DNS wysyła zapytanie do następnego serwera na jego liście do momentu, gdy wszystkie jego serwery DNS nie zostały zbadane. Jeśli nie otrzymasz odpowiedzi ze wszystkich serwerów DNS, klient DNS ma logikę ponowień, aby ponownie przesłać komunikat DNS. Po ponownym wysłaniu zapytania DNS zostaje podwojony limit czasu retransmisji. Ten proces jest kontynuowany do momentu osiągnięcia maksymalnego limitu czasu transmisji (zdefiniowanego jako NX_DNS_MAX_RETRANS_TIMEOUT w *nxd_dns. h*) lub do momentu otrzymania pomyślnej odpowiedzi z tego serwera.

Klient DNS NetX Duo może wykonywać operacje wyszukiwania adresów IPv6 (typu AAAA) i wyszukiwania adresów IPv4 (typ A), określając wersję adresu IP w wywołaniu *nxd_dns_host_by_name_get* . Klient DNS może wykonywać odwrotne wyszukiwania adresów IP (typ zapytania PTR), aby uzyskać nazwy hostów sieci Web przy użyciu *nxd_dns_host_by_address_get*. Klient DNS NetX Duo nadal obsługuje *nx_dns_host_by_name_get* i *nx_dns_host_by_address_get* , które są równoważnymi usługami, ale które są ograniczone do komunikacji sieciowej IPv4. Jednak deweloperzy są zachęcani do portów istniejących aplikacji klienckich DNS do *nxd_dns_host_by_name_get* i *nxd_dns_host_by_address_get* usług.

Obsługa komunikatów DNS wykorzystuje protokół UDP do wysyłania żądań i odpowiedzi pól. Serwer DNS nasłuchuje na porcie numer 53 dla zapytań od klientów. W związku z tym usługi UDP muszą być włączone w NetX Duo przy użyciu usługi ***nx_udp_enable** _ dla utworzonego wcześniej wystąpienia adresu IP (_ *_nx_ip_create_* *).

W tym momencie klient DNS jest gotowy do akceptowania żądań z aplikacji i wysyłania zapytań DNS.

## <a name="extended-dns-resource-record-types"></a>Rozszerzone typy rekordów zasobów DNS

Jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest włączona, klient DNS NetX Duo obsługuje również następujące zapytania dotyczące typu rekordu:

- CNAME: zawiera nazwę kanoniczną aliasu
- TXT: zawiera ciąg tekstowy
- NS: zawiera autorytatywny serwer nazw
- SOA: zawiera początek strefy urzędu
- MX: używany do wymiany poczty
- SRV: zawiera informacje o usłudze oferowanej przez domenę

Z wyjątkiem typów rekordów CNAME i TXT aplikacja musi dostarczyć bufor wyrównany z 4 bajtami, aby otrzymać rekord danych DNS.

W przypadku klienta DNS w systemie NetX Duo dane rekordów są przechowywane w taki sposób, aby najbardziej efektywnie wykorzystać miejsce w buforze.

Poniżej przedstawiono przykład buforu rekordu o stałej długości (typ rekordu AAAA):

![Bufor rekordu o stałej długości](media/image2.png)

Dla tych zapytań, których typy rekordów mają zmienną długość danych, taką jak rekordy NS, których nazwy hostów mają zmienną długość, klient DNS NetX Duo zapisuje dane w następujący sposób. Bufor podany w zapytaniu klienta DNS jest zorganizowany w obszarze danych o stałej długości i w obszarze pamięci bez struktury. Górna część buforu pamięci jest zorganizowana w 4-bajtowe wpisy rekordów. Każdy wpis rekordu zawiera adres IP i wskaźnik do danych o zmiennej długości dla tego adresu IP. Dane o zmiennej długości dla każdego adresu IP są przechowywane w pamięci obszaru niestrukturalnego, rozpoczynając od końca bufora pamięci. Dane o zmiennej długości dla każdego kolejnego wpisu rekordu są zapisywane w następnej pamięci obszaru sąsiadującej z poprzednimi pozycjami rekordów. W związku z tym dane zmiennych "zwiększają się" do obszaru strukturalnego pamięci zawierającej wpisy rekordu do momentu braku wystarczającej ilości pamięci do przechowywania innego wpisu rekordu i danych zmiennych.

Jest to pokazane na poniższym rysunku:

![Rysunek 2](media/image3.png)

Przykład przechowywania danych nazwy domeny DNS (NS) znajduje się powyżej.

Zapytania klienta DNS NetX Duo przy użyciu formatu magazynu rekordów zwracają liczbę rekordów zapisanych w buforze rekordów. Te informacje umożliwiają aplikacji wyodrębnianie rekordów NS z bufora rekordów.

Przykładem kwerendy klienta DNS, która przechowuje dane DNS o zmiennej długości przy użyciu tego formatu przechowywania rekordów, przedstawiono poniżej:

```C
UINT  _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, 
                    UCHAR *host_name, VOID *record_buffer, 
                    UINT buffer_size, UINT *record_count, 
                    ULONG wait_option);
```


Więcej szczegółów można znaleźć w rozdziale 3, "Opis usług klienta DNS".

## <a name="dns-cache"></a>Pamięć podręczna DNS

Jeśli NX_DNS_CACHE_ENABLE jest włączona, klient DNS NetX Duo obsługuje funkcję pamięci podręcznej systemu DNS. Po utworzeniu klienta DNS aplikacja może wywołać interfejs API *nx_dns_cache_initialize ()* , aby ustawić specjalną pamięć podręczną DNS. W przypadku włączenia funkcji pamięci podręcznej DNS klient DNS znajdzie dostępną odpowiedź z pamięci podręcznej DNS przed rozpoczęciem wysyłania zapytania DNS, jeśli znajdziesz dostępną odpowiedź, bezpośrednio Zwróć odpowiedź do aplikacji, w przeciwnym razie klient DNS wysyła komunikat zapytania do serwera DNS i czeka na odpowiedź. Gdy klient DNS otrzymuje komunikat odpowiedzi i dostępna jest bezpłatna pamięć podręczna, klient DNS zwróci odpowiedź do aplikacji, a także dodaje odpowiedź jako rekord zasobu do pamięci podręcznej DNS.

Każda odpowiedź na strukturę danych *NX_DNS_RR* (rekord zasobu) w pamięci podręcznej. Ciągi (nazwa rekordu zasobu i dane) w rekordach są długością zmiennej, dlatego nie są przechowywane w strukturze NX_DNS_RR. Rekord zawiera wskaźniki do rzeczywistej lokalizacji pamięci, w której są przechowywane ciągi. Tabela ciągów i rekordy współużytkują pamięć podręczną. Rekordy są przechowywane na początku pamięci podręcznej i rosną do końca pamięci podręcznej. Tabela ciągów rozpoczyna się od końca pamięci podręcznej i powiększa się do początku pamięci podręcznej. Każdy ciąg w tabeli ciągów ma pole długości i pole licznika. Gdy ciąg zostanie dodany do tabeli ciągów, jeśli ten sam ciąg już występuje w tabeli, wartość licznika jest zwiększana i nie jest przydzielono żadnej pamięci dla ciągu. Pamięć podręczna jest traktowana jako pełna, jeśli do pamięci podręcznej nie można dodać więcej rekordów zasobów lub nowych ciągów.

## <a name="dns-client-limitations"></a>Ograniczenia klienta DNS

Klient DNS obsługuje jedno żądanie DNS jednocześnie. Wątki próbujące wprowadzić inne żądanie DNS są tymczasowo blokowane do momentu ukończenia poprzedniego żądania DNS.

Klient DNS NetX Duo nie używa danych z odpowiedzi autorytatywnych do przesyłania dalej dodatkowych zapytań DNS do innych serwerów DNS.

## <a name="dns-rfcs"></a>Specyfikacje RFC systemu DNS

System DNS NetX Duo jest zgodny z następującymi specyfikacjami RFC:

- RFC1034 NAZWY DOMEN — KONCEPCJE I UDOGODNIENIA
- RFC1035 NAZWY DOMEN — IMPLEMENTACJA I SPECYFIKACJA
- RFC1480 domenę US
- RFC 2782 A RR DNS do określania lokalizacji usług (DNS SRV)
- Rozszerzenia DNS RFC 3596 do obsługi protokołu IP w wersji 6