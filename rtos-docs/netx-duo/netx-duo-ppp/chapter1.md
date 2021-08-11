---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo Point-to-Point Protocol (PPP)
description: W tym rozdziale oprowadzono Azure RTOS NetX Duo Point-to-Point Protocol (PPP).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56343d563833f30ca0d48f594b547f37fa264b8961a7cd75b0786aac4791d065
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797215"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo Point-to-Point Protocol (PPP)

Zazwyczaj aplikacje NetX łączą się z rzeczywistą siecią fizyczną za pośrednictwem sieci Ethernet. Zapewnia to szybki i wydajny dostęp do sieci. Istnieją jednak sytuacje, w których aplikacja nie ma dostępu do sieci Ethernet. W takich przypadkach aplikacja może nadal łączyć się z siecią za pośrednictwem interfejsu szeregowego podłączonego bezpośrednio do innego członka sieci. Najpopularniejszym protokołem oprogramowania używanym do zarządzania takim połączeniem jest protokół Point-to-Point Protocol (PPP).

Mimo że komunikacja szeregowa jest stosunkowo prosta, protokół PPP jest nieco złożony. Protokół PPP w rzeczywistości składa się z wielu protokołów, takich jak protokół kontroli linków (LCP), IpCP (Internet Protocol Control Protocol), Password Authentication Protocol (PAP) i Challenge-Handshake Authentication Protocol (CHAP). LCP jest głównym protokołem dla protokołu PPP. W tym miejscu podstawowe składniki łącza są negocjowane dynamicznie w sposób równorzędny. Po pomyślnym wynegocjowania podstawowych cech połączenia są używane parametry PAP i/lub CHAP, aby upewnić się, że połączony równorzędny komputer równorzędny jest prawidłowy. Jeśli oba połączenia równorzędne są prawidłowe, protokół IPCP jest następnie używany do negocjowania adresów IP używanych przez te sieci równorzędne. Po zakończeniu procesu IPCP protokół PPP może wysyłać i odbierać pakiety IP.

NetX przede wszystkim widoki PROTOKOŁU PPP jako sterownik urządzenia. Funkcja *nx_ppp_driver* jest dostarczana do funkcji tworzenia adresu IP NetX, *nx_ip_create*. W przeciwnym razie NetX nie ma bezpośredniej wiedzy na temat protokołu PPP.

## <a name="ppp-serial-communication"></a>Komunikacja szeregowa PPP

Pakiet NETX PPP wymaga, aby aplikacja dostarczała sterownik komunikacji szeregowej. Sterownik musi obsługiwać znaki 8-bitowe i może również stosować sterowanie przepływem oprogramowania. Aplikacja odpowiada za zainicjowanie sterownika, co należy wykonać przed utworzeniem wystąpienia protokołu PPP.

Aby można było wysyłać pakiety PROTOKOŁU PPP, należy podać procedurę bajtów wyjściowych sterownika szeregowego do protokołu PPP (określoną w *nx_ppp_create* funkcji). Ta procedura danych wyjściowych bajtów sterownika szeregowego będzie wywoływana powtarzalnie w celu przesyłania całego pakietu PPP. Za buforowanie danych wyjściowych odpowiada sterownik szeregowy. Po stronie odbierania sterownik szeregowy aplikacji musi wywołać funkcję *nx_ppp_byte_receive* PPP za każdym razem, gdy pojawi się nowy bajt. Zwykle odbywa się to w kontekście procedury usługi przerwań (ISR). Funkcja *nx_ppp_byte_receive* umieszcza przychodzący bajt w buforze cyklicznym i ostrzega protokół PPP o jego obecności.

## <a name="ppp-over-ethernet-communication"></a>Komunikacja za pośrednictwem protokołu PPP przez Ethernet

NetX PPP może również przesyłać komunikat PROTOKOŁU PPP za pośrednictwem sieci Ethernet. W takiej sytuacji pakiet NETX PPP wymaga, aby aplikacja dostarczała sterownik komunikacji Ethernet.

Aby wysyłać pakiety PROTOKOŁU PPP za pośrednictwem sieci Ethernet, należy podać procedurę wyjściową do protokołu PPP (określoną w *nx_ppp_packet_send_set* protokołu ). Ta procedura wyjściowa będzie wywoływana powtarzalnie w celu przesyłania całego pakietu PPP. Po stronie odbierania odbiornik aplikacji musi wywołać funkcję *nx_ppp_packet_receive* PPP za każdym razem, gdy nadejdzie nowy pakiet.

## <a name="ppp-packet"></a>Pakiet PPP

Protokół PPP używa ramek AHDLC (podzestawu HDLC) do hermetyzacji wszystkich kontrolek protokołu PPP i danych użytkownika. Ramka AHDLC wygląda następująco:

|**Flaga**|**Addr**|**Ctrl**|**Informacje**|**Crc**|**Flaga**|
|--------|--------|--------|---------------|-------|--------|
|7E |Ff|03|[0–1502 bajty]|2-bajtowe| 7E|

Każda ramka PROTOKOŁU PPP ma taki ogólny wygląd. Pierwsze dwa bajty pola informacji zawierają typ protokołu PPP. Prawidłowe wartości są zdefiniowane w następujący sposób:

- C021: LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: Pakiet danych IP

Jeśli typ 0x0021 jest obecny, pakiet IP następuje natychmiast. W przeciwnym razie, jeśli istnieje jeden z innych protokołów, następujące bajty odpowiadają konkretnemu protokołowi.

W celu zapewnienia unikatowego 0x7E znaczników na początku/na końcu ramki i obsługi sterowania przepływem oprogramowania programowy program AHDLC używa sekwencji ucieczki do reprezentowania różnych wartości bajtów. Wartość 0x7D określa, że poniższy znak jest zakodowany, czyli zasadniczo oryginalny znak wyłączny ORed z 0x20. Na przykład wartość 0x03 pola Ctrl w nagłówku jest reprezentowana przez sekwencję dwóch bajtów: 7D 23. Domyślnie wartości mniejsze niż 0x20 są konwertowane na sekwencję ucieczki, a także wartości 0x7E i 0x7D w polu Informacje. Należy pamiętać, że sekwencje ucieczki mają również zastosowanie do pola CRC.

## <a name="link-control-protocol-lcp"></a>protokół kontroli linków (LCP)

LCP jest podstawowym protokołem PPP i jest pierwszym protokołem do uruchomienia. Protokół LCP jest odpowiedzialny za negocjowanie różnych parametrów protokołu PPP, w tym maksymalnej jednostki odbioru (MRU) i protokołu uwierzytelniania (PAP, CHAP lub none) do użycia. Gdy obie strony LCP uzgodnią parametry PROTOKOŁU PPP, protokoły uwierzytelniania — jeśli są — zaczynają działać.

## <a name="password-authentication-protocol-pap"></a>Protokół uwierzytelniania haseł (PAP)

PAP to stosunkowo prosty protokół, który opiera się na nazwie i hasłach dostarczanych przez jedną stronę połączenia (wynegocjowanych podczas LCP). Druga strona następnie weryfikuje te informacje. Jeśli jest to poprawne, komunikat akceptacji jest zwracany do nadawcy, a protokół PPP może przejść do maszyny stanu IPCP. W przeciwnym razie, jeśli nazwa lub hasło jest niepoprawne, połączenie zostanie odrzucone.

>[!NOTE]
> Obie strony interfejsu mogą żądać certyfikatu PAP, ale PAP jest zwykle używany tylko w jednym kierunku.

## <a name="challenge-handshake-authentication-protocol-chap"></a>Challenge-Handshake uwierzytelniania protokołu (CHAP)

Protokół CHAP jest bardziej złożonym protokołem uwierzytelniania niż PAP. Wystawca uwierzytelniania PROTOKOŁU CHAP dostarcza swój współpracownikowi nazwę i wartość. Następnie element równorzędny używa podanej nazwy, aby znaleźć wspólny "klucz tajny" między dwiema jednostkami. Obliczenia są następnie wykonywane na identyfikatorze, wartości i "kluczu tajnym". Wynik tego obliczenia jest zwracany w odpowiedzi. Jeśli jest to poprawne, protokół PPP może przejść do maszyny stanu IPCP. W przeciwnym razie, jeśli wynik będzie niepoprawny, połączenie zostanie odrzucone.

Innym interesującym aspektem protokołu CHAP jest to, że może on wystąpić w losowych odstępach czasu po nawiązaniu połączenia. Służy to do zapobiegania przejmowaniu połączenia — po jego uwierzytelnieniu. Jeśli wyzwanie nie powiedzie się w jednym z tych losowych momentów, połączenie zostanie natychmiast przerwane.

>[!NOTE]
> Obie strony interfejsu mogą żądać protokołu CHAP, ale protokół CHAP jest zwykle używany tylko w jednym kierunku.

## <a name="internet-protocol-control-protocol-ipcp"></a>Protokół IPCP (Internet Protocol Control Protocol)

IPCP jest ostatnim protokołem do wykonania, zanim komunikacja PPP będzie dostępna do transferu danych NETX IP. Głównym celem tego protokołu jest poinformowanie drugiego elementu równorzędnego o jego adresie IP. Po konfiguracji adresu IP transfer danych NETX IP jest włączony.

## <a name="data-transfer"></a>Transfer danych

Jak wspomniano wcześniej, pakiety danych NETX IP znajdują się w ramkach PROTOKOŁU PPP z identyfikatorem protokołu 0x0021. Wszystkie odebrane pakiety danych są umieszczane w co najmniej jednej strukturze NX_PACKET i przesyłane do przetwarzania odbierania NetX. Podczas transmisji zawartość pakietu NetX jest umieszczana w ramce AHDLC i przesyłana.

## <a name="ppp-rfcs"></a>RFC PPP

NetX PPP jest zgodny ze standardami RFC1332, RFC1334, RFC1661, RFC1994 i powiązanymi RFC.