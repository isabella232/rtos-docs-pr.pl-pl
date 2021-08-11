---
title: Rozdział 1 — Wprowadzenie do klienta SMTP Azure RTOS NetX Duo
description: Protokół Simple Mail Transfer Protocol (SMTP) to protokół do przesyłania poczty między sieciami i Internetem.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: df8c6b6920577ebfc18ed9252761401c30822c034e30d7ae95b25778707f53d5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797826"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-smtp-client"></a>Rozdział 1 — Wprowadzenie do klienta SMTP Azure RTOS NetX Duo

Protokół Simple Mail Transfer Protocol (SMTP) to protokół do przesyłania poczty między sieciami i Internetem. Korzysta ona z niezawodnych usług Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości.

## <a name="netx-duo-smtp-client-requirements"></a>Wymagania klienta SMTP aplikacji NetX Duo

Klient SMTP NetX Duo wymaga utworzenia wystąpienia adresu IP NetX Duo i puli pakietów NetX Duo. Klient SMTP używa gniazda TCP do nawiązywania połączenia z serwerem SMTP na dobrze *znanym porcie 25. W* związku z tym protokół TCP należy najpierw włączyć, wywołując *usługę nx_tcp_enable* na wcześniej utworzonym wystąpieniu adresu IP.

Wywołanie tworzenia klienta SMTP (nxd_smtp_client_create) wymaga wcześniej utworzonej puli pakietów do przesyłania poleceń SMTP na serwer oraz wysyłania rzeczywistej wiadomości e-mail. Ładunek pakietu zależy od przewidywanego rozmiaru zawartości poczty e-mail i musi zezwalać na nagłówki TCP, IP i MAC. (Należy pamiętać, że nagłówek IPv6 ma 40 bajtów, a nagłówek IPv4 to 20 bajtów).

Jeśli cała wiadomość e-mail nie mieści się w jednym pakiecie, klient SMTP przydziela dodatkowe pakiety zawierające pozostałą część wiadomości.

## <a name="netx-duo-smtp-client-constraints"></a>Ograniczenia klienta SMTP aplikacji NetX Duo

Protokół SMTP NetX Duo implementuje standardy RFC 2821 i 2554, jednak istnieją pewne ograniczenia:

1. Klient SMTP NetX Duo obsługuje tylko uwierzytelnianie LOGIN i PLAIN, ale nie uwierzytelnianie szyfrowane CRAM-MD5.
2. Komunikaty klienta SMTP NetX Duo są ograniczone do jednego adresata na element poczty e-mail i tylko jednej wiadomości e-mail na połączenie TCP z serwerem SMTP.
3. Opcje SMTP VRFY, SEND, SOML, EXPN, SAML, ETRN, TURN i SIZE nie są obsługiwane.
4. Klient SMTP nie jest przeglądarką poczty ("agentem użytkownika poczty"), która jest zwykle używana do tworzenia wiadomości e-mail. Jest to tylko "agent transferu poczty". Zapewni to niezbędne przetwarzanie treści wiadomości e-mail na potrzeby transportu SMTP zgodnie z informacjami podanymi w dokumencie RFC 2821. Nie sprawdza on zawartości pod celu sprawdzenia poprawnej składni, np. odbiorcy i ścieżki odwrotnej. Nie ma żadnych ograniczeń co do tego, co znajduje się w buforze poczty, np. dane MIME lub wiadomości SMS wyczysz Format wiadomości e-mail określony w dokumencie RFC 2822 w celu uwzględnienia nagłówków i treści wiadomości wykracza poza zakres interfejsu API klienta SMTP.

## <a name="commands-supported-by-netx-duo-smtp-client"></a>Polecenia obsługiwane przez klienta SMTP NetX Duo

Klient SMTP NetX Duo używa następujących poleceń podczas sesji poczty e-mail z serwerem SMTP.

- **EHLO** Klient chce zainicjować sesję, która obejmuje niektóre lub wszystkie usługi SMTP protokołu rozszerzeń dostępne na serwerze SMTP. Jest to opcja domyślna.
- **HELO** Klient chce zainicjować sesję ograniczoną do podstawowych usług SMTP.
- **POCZTA** Klient chce, aby serwer odbierał pocztę klienta.
- **UWIERZYTELNIANIE** Klient chce zainicjować uwierzytelnianie przez serwer.
- **RCPT** Klient chce przesłać skrzynkę pocztową innego hosta, do których ma zostać dostarczona wiadomość e-mail.
- **DANE** Klient chce zainicjować wysyłanie danych wiadomości e-mail na serwer.
- **ZAMKNIJ** Klient chce zakończyć sesję.

## <a name="getting-started"></a>Wprowadzenie

Aplikacja klienta SMTP tworzy wystąpienie adresu IP, a element włącza protokół TCP w tym wystąpieniu adresu IP. Następnie tworzy klienta SMTP przy użyciu następującej usługi:

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type,
    NXD_ADDRESS *server_address, UINT port);
```

Adres *client_packet_pool_ptr* jest wskaźnikiem do wcześniej utworzonej puli pakietów, która będzie przez klienta SMTP wysyłać komunikaty do serwera SMTP.

Należy pamiętać, że aplikacja musi from_address *dla* urządzenia lokalnego i adresu IP serwera. Wszystkie adresy muszą być w pełni kwalifikowane nazwami domen. W pełni kwalifikowana nazwa domeny zawiera część lokalną i nazwę domeny rozdzielone znakiem "@". Należy pamiętać, że klient SMTP nie  sprawdza składni from_address ani recipient_address *w* nx_smtp_mail_send usługi.

Po utworzeniu klienta SMTP aplikacja klienta SMTP tworzy element poczty e-mail z poprawnie sformatowaną wiadomością e-mail SMTP i wysyła żądanie wysłania elementu poczty do klienta SMTP przy użyciu następującego interfejsu API:

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address, UINT priority,
    CHAR *subject, CHAR *mail_body,
    UINT mail_body_length);
```

Zasadniczo nie ma różnicy w uruchamianiu klienta SMTP za pośrednictwem protokołu IPv4 lub IPv6 z perspektywy użytkownika. Różnice między tymi dwoma protokołami IP są obsługiwane w podstawowej warstwie NetX Duo.

Pamiętaj, że aplikacja, która chce wysłać wiadomość e-mail, musi podać adres odbiorcy w *nx_smtp_client_mail* połączenia.

W przypadku uwierzytelniania nazwy użytkowników mogą być w pełni kwalifikowane lub wyświetlane. Zależy to od tego, jak serwer przeprowadza uwierzytelnianie.

Pokaz w sekcji Mały przykład w dalszej części tego podręcznika użytkownika pokazuje sposób formatowania komunikatu. Stan pomyślnego wysłania elementu poczty e-mail będzie NX_SUCCESS. Jeśli wystąpi błąd, niezależnie od tego, czy *jest to* błąd wewnętrzny, przerwane połączenie TCP, czy otrzymujesz kod błędu odpowiedzi serwera, nx_smtp_mail_send zwróci stan błędu innego niż zero.

Podczas wysyłania elementu poczty klient SMTP NetX Duo tworzy nowe połączenie TCP z serwerem SMTP i rozpoczyna sesję SMTP. W tej sesji klient wysyła serię poleceń do serwera SMTP w ramach protokołu SMTP, co oznacza wysłanie rzeczywistej wiadomości e-mail. Połączenie TCP jest następnie przerywane, niezależnie od wyniku sesji SMTP.

Po przesłaniu wiadomości e-mail, niezależnie od powodzenia lub niepowodzenia, klient SMTP jest zwracany do stanu "początkowego" i może być używany w innej sesji transferu poczty e-mail.

## <a name="netx-duo-smtp-authentication"></a>NetX Duo SMTP Authentication

Uwierzytelnianie to sposób, w jaki klienci SMTP mogą potwierdzić swoją tożsamość na serwerze SMTP i dostarczyć pocztę jako zaufani użytkownicy. Większość komercyjnych serwerów SMTP wymaga uwierzytelnienia klientów.

Zazwyczaj dane uwierzytelniania składają się z nazwy użytkownika i hasła nadawcy. Podczas uwierzytelniania serwer wyświetla monit o te informacje, a klient odpowiada, wysyłając żądane dane w zakodowanym formacie. Serwer dekoduje dane i próbuje znaleźć dopasowanie w bazie danych użytkownika. Jeśli zostanie znaleziony, serwer wskazuje, że uwierzytelnianie powiodło się. Uwierzytelnianie SMTP jest zdefiniowane w [dokumencie RFC 2554.](http://www.ietf.org/rfc/rfc2554.txt)

Istnieją dwa rodzaje uwierzytelniania: *podstawowy i* *skrótowy*. Skrót nie jest obsługiwany w bieżącym kliencie SMTP NetX Duo i nie zostanie omówiony w tym miejscu. Uwierzytelnianie podstawowe jest równoważne nazwie *i* *uwierzytelnianiu za pomocą* hasła opisanego powyżej. W przypadku podstawowego uwierzytelniania SMTP nazwy i hasła są zakodowane w formacie base64. Zaletą uwierzytelniania podstawowego jest łatwość implementacji i szerokie zastosowanie. Główną wadą uwierzytelniania podstawowego jest to, że dane nazwy i hasła są przesyłane otwarcie w żądaniu.

### <a name="plain-authentication"></a>Uwierzytelnianie zwykłego

Klient SMTP NetX Duo wysyła polecenie AUTH z parametrem PLAIN. Jeśli serwer SMTP NetX Duo obsługuje ten typ uwierzytelniania, odpowie kodem odpowiedzi 334. Klient odpowiada na serwer pojedynczym komunikatem o nazwie użytkownika i hasłem zakodowanym w formacie base64. Jeśli serwer ustali, że uwierzytelnianie klienta powiodło się, odpowiada kodem powodzenia 235.

### <a name="login-authentication"></a>Uwierzytelnianie logowania

Klient SMTP NetX Duo wysyła polecenie AUTH z parametrem LOGIN. Jeśli serwer SMTP NetX Duo obsługuje ten typ uwierzytelniania, na początku "wyzwania" uwierzytelniania odpowie kodem odpowiedzi 334. Wysyła on zakodowany w formacie base64 monit z powrotem do klienta, który jest zwykle "Username" (Nazwa użytkownika). Klient dekoduje monit i odpowiada przy użyciu nazwy użytkownika zakodowanej w formacie base64. Jeśli serwer akceptuje nazwę użytkownika klienta, wysyła zakodowany w formacie base64 monit o hasło klienta. Klient odpowiada hasłem zakodowanym w formacie base64. Jeśli serwer ustali, że uwierzytelnianie klienta powiodło się, odpowiada kodem powodzenia 235.

### <a name="no-authentication"></a>Bez uwierzytelniania

Niektóre serwery SMTP są konfigurowane bez uwierzytelniania. Jeśli tak, odpowiedź 250 na komunikat EHLO klienta nie będzie zawierała żadnych typów uwierzytelniania. Jednak brak wymienionych typów uwierzytelniania nie musi oznaczać, że serwer nie wymaga ani nie obsługuje uwierzytelniania. Jeśli klient jest skonfigurowany do uwierzytelniania PLAIN lub LOGIN w tej sytuacji, zadanie wątku klienta NetX Duo domyślnie ma wartość PLAIN. Jeśli dla klienta skonfigurowano wartość BRAK, krok uwierzytelniania jest pomijany, a stan SMTP jest przenoszony do stanu MAIL.

Należy pamiętać, że jeśli klient jest skonfigurowany do bez uwierzytelniania, a serwer SMTP obsługuje uwierzytelnianie, typ uwierzytelniania klienta zostanie przełączony na PLAIN.

## <a name="rfcs-supported-by-netx-duo-smtp-client"></a>RFC obsługiwane przez klienta SMTP NetX Duo

Interfejs API klienta SMTP NetX Duo jest zgodny ze specyfikacją RFC2821 "Simple Mail Transfer Protocol" i "Rozszerzeniem usługi SMTP dla uwierzytelniania" RFC 2554. “
