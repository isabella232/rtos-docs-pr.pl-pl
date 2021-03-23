---
title: Rozdział 1 — wprowadzenie do serwera Azure RTO NetX PPPoE
description: Ten dokument koncentruje się na szczegółach dotyczących modułu PPPoE usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85a762f669e31c7e753f78b270ced15677a87c4c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822513"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a>Rozdział 1 — wprowadzenie do serwera Azure RTO NetX PPPoE

Protokół PPP przez sieć Ethernet (PPPoE) umożliwia hostom łączenie się z serwerem PPP za pośrednictwem sieci Ethernet zamiast tradycyjnego opartego na znakach komunikacji linii szeregowej. Szczegółowe informacje techniczne dotyczące protokołu PPPoE zostały opisane w dokumencie RFC 2516: Metoda przesyłania PPP przez Ethernet (PPPoE). Ten dokument koncentruje się na szczegółach dotyczących modułu PPPoE usługi Azure RTO NetX.

Aby zapewnić połączenie typu punkt-punkt za pośrednictwem sieci Ethernet, każda sesja PPP musi nauczyć się adresu Ethernet zdalnego elementu równorzędnego, a także ustanowić unikatowy identyfikator sesji.

Zgodnie ze standardem RFC 2516, PPPoE obejmuje dwa etapy: etap odnajdywania i etap sesji PPPoE. Gdy host (klient) chce uruchomić sesję PPP, musi najpierw przeprowadzić odnajdywanie, aby znaleźć serwer PPPoE. Ten krok umożliwia również serwerowi i klientowi zidentyfikowanie adresów MAC sieci Ethernet i SESSION_ID, które będą używane w pozostałej części sesji protokołu PPP.

Ramka Ethernet jest następująca:

![Diagram przedstawiający ramkę sieci Ethernet.](media/netx-pppoe-server-01.png)

Ładunek Ethernet dla protokołu PPPoE jest następujący:

![Diagram przedstawiający ładunek sieci Ethernet dla protokołu PPPoE.](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a>Etap odnajdywania PPPoE

Etap odnajdywania PPPoE umożliwia klientom wybranie serwera ze wszystkich dostępnych serwerów w sieci, efektywnie w celu utworzenia sesji przed wymianą ramek PPP. Na końcu etapu odnajdywania zarówno klient, jak i serwer zgadzają się na unikatowy identyfikator sesji, a obie strony muszą znać adres MAC elementu równorzędnego.

| Komunikat odnajdowania                                  | Kod | Kierunek                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| Inicjowanie odnajdywania aktywnego protokołu PPPoE (PADI)           | 0x09 | Z klienta do emisji                      |
| Oferta aktywnego odnajdowania PPPoE (PADO)                | 0x07 | Z serwera do klienta                         |
| Aktywne żądanie odnajdywania PPPoE (PADR)              | 0x19 | Od klienta do serwera                         |
| Sesja odnajdywania aktywnego protokołu PPPOE — potwierdzenie (KONSOLe) | 0x65 | Z serwera do klienta                         |
| Zakończenie aktywnego odnajdowania PPPoE (PADT)            | 0xa7 | Można inicjować z poziomu serwera lub klienta |

Wszystkie ramki sieci Ethernet odnajdowania mają ustawioną wartość 0x8863 dla pola ETHER_TYPE.

## <a name="pppoe-session-message"></a>Komunikat sesji PPPoE

Po utworzeniu sesji przez klienta i serwer ramki PPP mogą być transferowane jako komunikaty sesji PPPoE. W trakcie sesji SESSION_ID nie może ulec zmianie i musi być wartością przypisywaną przez serwer na etapie odnajdywania.

Wszystkie ramki sieci Ethernet sesji PPPoE mają ustawione ETHER_TYPE wartość 0x8864.