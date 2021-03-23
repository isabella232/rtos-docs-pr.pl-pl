---
title: Rozdział 1 — wprowadzenie do klienta SMTP usługi Azure RTO NetX Duo
description: Simple Mail Transfer Protocol (SMTP) to protokół służący do przesyłania poczty między sieciami i Internetem.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f58a0c235f5c2cd108ba97afe676ffa9b66e715c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821697"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-smtp-client"></a>Rozdział 1 — wprowadzenie do klienta SMTP usługi Azure RTO NetX Duo

Simple Mail Transfer Protocol (SMTP) to protokół służący do przesyłania poczty między sieciami i Internetem. Wykorzystuje ona niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości.

## <a name="netx-duo-smtp-client-requirements"></a>Wymagania dotyczące klienta SMTP NetX Duo

Klient SMTP NetX Duo wymaga utworzenia wystąpienia IP NetX Duo i puli pakietów NetX Duo. Klient SMTP używa gniazda TCP do łączenia się z serwerem SMTP na *dobrze znanym porcie 25. W związku z tym* należy najpierw włączyć protokół TCP, wywołując usługę *nx_tcp_enable* na wcześniej UTWORZONYM wystąpieniu adresu IP.

Wywołanie Create klient SMTP (nxd_smtp_client_create) wymaga wcześniej utworzonej puli pakietów do przesyłania poleceń SMTP do serwera, a także do wysyłania rzeczywistej wiadomości e-mail. Ładunek pakietu zależy od przewidywanego rozmiaru zawartości poczty i musi zezwalać na użycie protokołu TCP, nagłówka IP i nagłówka MAC. (Należy pamiętać, że nagłówek IPv6 jest 40 bajtów, podczas gdy nagłówek IPv4 ma 20 bajtów).

Jeśli cała wiadomość e-mail nie mieści się w jednym pakiecie, klient SMTP przydziela dodatkowe pakiety, aby zawierały resztę komunikatu.

## <a name="netx-duo-smtp-client-constraints"></a>Ograniczenia klienta SMTP NetX Duo

Chociaż protokół SMTP NetX Duo implementuje standardy RFC 2821 i 2554, istnieją pewne ograniczenia:

1. Klient SMTP NetX Duo obsługuje tylko logowanie i uwierzytelnianie zwykłe, ale nie uwierzytelnianie szyfrowane CRAM-MD5.
2. Komunikaty klienta SMTP w systemie NetX Duo są ograniczone do jednego adresata dla każdego elementu poczty, a tylko jedna wiadomość e-mail na połączenie TCP z serwerem SMTP.
3. Opcje SMTP VRFY, SEND, SOML, EXPN, SAML, ETRN, nie zmieniają ani SIZE są nieobsługiwane.
4. Klient SMTP nie jest przeglądarką poczty e-mail ("agent użytkownika poczty"), która jest zwykle używana do tworzenia wiadomości e-mail. Jest to tylko "Agent transferu poczty". Zapewni to wymagane przetwarzanie treści wiadomości e-mail na potrzeby transportu SMTP, zgodnie z opisem w dokumencie RFC 2821. Nie sprawdza zawartości pod kątem poprawnej składni, np. odbiorcy i ścieżki odwrotnej. Nie ma żadnych ograniczeń dotyczących buforu poczty, np. danych MIME lub wiadomości tekstowych. Format wiadomości e-mail określony w dokumencie RFC 2822 dla dołączania nagłówków i treści wiadomości wykracza poza zakres interfejsu API klienta SMTP.

## <a name="commands-supported-by-netx-duo-smtp-client"></a>Polecenia obsługiwane przez klienta SMTP NetX Duo

Klient SMTP NetX Duo używa następujących poleceń w trakcie sesji poczty z serwerem SMTP.

- **EHLO** Klient chce zainicjować sesję obejmującą niektóre lub wszystkie usługi protokołu SMTP dostępne z serwera SMTP. Jest to opcja domyślna.
- **HELO** Klient chce zainicjować sesję ograniczoną do podstawowych usług SMTP.
- **Poczta** Klient chce, aby serwer odbierał pocztę e-mail.
- **Uwierzytelnianie** Klient chce zainicjować uwierzytelnianie przez serwer.
- **Przyjęcie** Klient chciałby przesłać skrzynkę pocztową innego hosta, do którego ma zostać dostarczona poczta.
- **Dane** Klient chce zainicjować wysyłanie danych wiadomości e-mail na serwer.
- **Zakończ** Klient chce zakończyć sesję.

## <a name="getting-started"></a>Wprowadzenie

Aplikacja kliencka SMTP tworzy wystąpienie IP i włącza protokół TCP dla tego wystąpienia IP. Następnie tworzy klienta SMTP przy użyciu następującej usługi:

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

*Client_packet_pool_ptr* jest wskaźnikiem do wcześniej utworzonej puli pakietów, która będzie używana przez klienta SMTP do wysyłania komunikatów do serwera SMTP.

Należy pamiętać, że aplikacja musi udostępnić *from_address* dla urządzenia lokalnego i adresu IP serwera. Wszystkie adresy muszą być w pełni kwalifikowanymi nazwami domen. W pełni kwalifikowana nazwa domeny zawiera część lokalną i nazwę domeny oddzieloną znakiem "@". Zwróć uwagę, że klient SMTP nie sprawdza składni *from_address* lub *recipient_address* w usłudze nx_smtp_mail_send poniżej.

Po utworzeniu klienta SMTP aplikacja kliencka SMTP tworzy element poczty z prawidłowo sformatowaną wiadomością e-mail, a następnie wysyła żądanie wysłania żądania do klienta SMTP przy użyciu następującego interfejsu API:

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address, UINT priority,
    CHAR *subject, CHAR *mail_body,
    UINT mail_body_length);
```

W przypadku korzystania z klienta SMTP w przypadku protokołu IPv4 lub IPv6 w perspektywie użytkownika nie ma żadnej różnicy. Różnice między dwoma protokołami IP są obsługiwane w podstawowej warstwie NetX Duo.

Należy pamiętać, że aplikacja, która chce wysyłać wiadomości e-mail, musi podać adres odbiorcy w wywołaniu *nx_smtp_client_mail* .

W przypadku uwierzytelniania nazwy użytkowników mogą być w pełni kwalifikowanymi nazwami domen lub wyświetlać nazwy użytkownika. Jest to zależne od tego, jak serwer wykonuje uwierzytelnianie.

W dalszej części tego podręcznika użytkownika pokazano, jak należy sformatować komunikat. Stan, w którym pomyślnie wysłano element poczty, zostanie NX_SUCCESS. Jeśli wystąpi błąd, niezależnie od tego, czy jest to błąd wewnętrzny, zerwano połączenie TCP lub Odebrano kod błędu odpowiedzi serwera, *nx_smtp_mail_send* zwróci stan błędu różny od zera.

Podczas wysyłania elementu poczty klient SMTP NetX Duo tworzy nowe połączenie TCP z serwerem SMTP i rozpoczyna sesję SMTP. W tej sesji klient wysyła serię poleceń do serwera SMTP jako część protokołu SMTP, culminating w wysyłaniu rzeczywistej wiadomości e-mail. Połączenie TCP jest następnie przerywane, niezależnie od wyniku sesji SMTP.

Po przekazaniu poczty, niezależnie od sukcesu lub niepowodzenia, klient SMTP jest zwracany do stanu początkowego i może być używany przez inną sesję transferu poczty.

## <a name="netx-duo-smtp-authentication"></a>NetX Duo — uwierzytelnianie SMTP

Uwierzytelnianie to sposób, w jaki klienci SMTP mogą udowodnić swoją tożsamość na serwerze SMTP i mieć pocztę dostarczaną jako zaufani użytkownicy. Większość komercyjnych serwerów SMTP wymaga uwierzytelnienia klientów.

Zwykle dane uwierzytelniania składają się z nazwy użytkownika i hasła nadawcy. Podczas wyzwania uwierzytelniania serwer monituje o te informacje, a klient odpowiada przez wysyłanie żądanych danych w zakodowanym formacie. Serwer dekoduje dane i próbuje znaleźć dopasowanie w swojej bazie danych użytkownika. Jeśli zostanie znaleziony, serwer wskazuje, że uwierzytelnianie zakończyło się pomyślnie. Uwierzytelnianie SMTP jest zdefiniowane w [dokumencie RFC 2554](http://www.ietf.org/rfc/rfc2554.txt).

Istnieją dwa typy uwierzytelniania, czyli *podstawowe* i *szyfrowane*. Skrót nie jest obsługiwany w bieżącym kliencie SMTP NetX Duo i nie zostanie omówiona w tym miejscu. Uwierzytelnianie podstawowe jest równoważne z powyższym uwierzytelnianiem *nazwy* i *hasła* . W podstawowym uwierzytelnianiu SMTP nazwy i hasła są zakodowane w formacie base64. Zaletą uwierzytelniania podstawowego jest łatwość wdrażania i powszechnego użycia. Główną wadą uwierzytelniania podstawowego jest nazwa i hasło, które są przesyłane w sposób otwarty w żądaniu.

### <a name="plain-authentication"></a>Zwykłe uwierzytelnianie

Klient SMTP NetX Duo wysyła polecenie AUTH z parametrem ZWYKŁYm. Jeśli serwer SMTP NetX Duo obsługuje ten typ uwierzytelniania, otrzyma odpowiedź z kodem odpowiedzi 334. Klient odpowie na serwer przy użyciu pojedynczej nazwy użytkownika i hasła szyfrowanego algorytmem Base64. Jeśli serwer ustali, że uwierzytelnianie klienta powiedzie się, reaguje na kod sukcesu 235.

### <a name="login-authentication"></a>Uwierzytelnianie logowania

Klient SMTP NetX Duo wysyła polecenie uwierzytelniania z parametrem logowania. Jeśli serwer SMTP NetX Duo obsługuje ten typ uwierzytelniania, odpowie przy użyciu kodu odpowiedzi 334 jako początku uwierzytelniania "wyzwanie". Wysyła monit kodowany algorytmem Base64 z powrotem do klienta, który jest zwykle "username". Klient dekoduje monit i odpowiada za pomocą nazwy użytkownika kodowanej algorytmem Base64. Jeśli serwer akceptuje nazwę użytkownika klienta, wysyła do hasła klienta komunikat kodowany algorytmem Base64. Klient reaguje na hasło zakodowane w formacie base64. Jeśli serwer ustali, że uwierzytelnianie klienta powiedzie się, reaguje na kod sukcesu 235.

### <a name="no-authentication"></a>Bez uwierzytelniania

Niektóre serwery SMTP są skonfigurowane bez uwierzytelniania. W takim przypadku ich odpowiedź 250 na komunikat EHLO klienta nie będzie wyświetlać żadnych typów uwierzytelniania. Jednak żadne z wymienionych typów uwierzytelniania nie musi oznaczać, że serwer nie wymaga ani nie obsługuje uwierzytelniania. Jeśli klient jest skonfigurowany do uwierzytelniania ZWYKŁEgo lub logowania w tej sytuacji, zadanie wątku klienta NetX Duo będzie miało wartość domyślną. Jeśli klient jest skonfigurowany pod kątem braku, krok uwierzytelniania zostanie pominięty, a stan SMTP zostanie zaawansowany do stanu poczty.

Należy pamiętać, że jeśli klient jest skonfigurowany do uwierzytelniania, a serwer SMTP obsługuje uwierzytelnianie, typ uwierzytelniania klienta jest przełączany do ZWYKŁEgo.

## <a name="rfcs-supported-by-netx-duo-smtp-client"></a>Specyfikacje RFC obsługiwane przez klienta SMTP NetX Duo

Interfejs API klienta SMTP NetX Duo jest zgodny z RFC2821 "Simple Mail Transfer Protocol" oraz rozszerzenia usługi SMTP RFC 2554 dla uwierzytelniania. “
