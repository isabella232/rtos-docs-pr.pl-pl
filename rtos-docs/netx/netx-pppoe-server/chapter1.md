---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX PPPoE Server
description: Ten dokument koncentruje się na szczegółach Azure RTOS NetX PPPoE.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2f79cba35991555f7f8d10e589aa251387ce25c48c3b729da371b548f13321bd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798325"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX PPPoE Server

Protokół PPPoE (PPP over Ethernet) umożliwia hostom łączenie się z serwerem PPP za pośrednictwem sieci Ethernet zamiast tradycyjnej komunikacji szeregowej opartej na znakach. Szczegóły techniczne ppPoE są opisane w dokumencie RFC 2516: A Method for Transmiting PPP over Ethernet (PPPoE). Ten dokument koncentruje się na szczegółach Azure RTOS NetX PPPoE.

Aby zapewnić połączenie typu punkt-punkt za pośrednictwem sieci Ethernet, każda sesja PROTOKOŁU PPP musi poznać adres Ethernet zdalnego elementu równorzędnego, a także ustanowić unikatowy identyfikator sesji.

Zgodnie ze dokumencie RFC 2516 ppPoE składa się z dwóch etapów: etapu odnajdywania i sesji PPPoE. Gdy host (klient) chce uruchomić sesję PROTOKOŁU PPP, musi najpierw wykonać odnajdywanie w celu znalezienia serwera PPPoE. Ten krok umożliwia również serwerowi i klientowi identyfikowanie adresów MAC sieci Ethernet i adresów SESSION_ID, które będą używane w pozostałej części sesji PROTOKOŁU PPP.

Ramka Ethernet jest następująca:

![Diagram przedstawiający ramkę ethernetową.](media/netx-pppoe-server-01.png)

Ładunek Ethernet dla ppPoE jest następujący:

![Diagram przedstawiający ładunek Ethernet dla ppPoE.](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a>Etap odnajdywania PPPoE

Etap odnajdywania PPPoE umożliwia klientom wybranie serwera ze wszystkich dostępnych serwerów w sieci, efektywnie tworząc sesję przed wymianą ramek PROTOKOŁU DHCP. Na koniec etapu odnajdywania klient i serwer muszą uzgodnić unikatowy identyfikator sesji, a obie strony muszą znać adres MAC elementu równorzędnego.

| Komunikat odnajdywania                                  | Kod | Kierunek                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| Inicjacja aktywnego odnajdywania PPPoE (PADI)           | 0x09 | Z klienta do emisji                      |
| Oferta aktywnego odnajdywania PPPoE (PADO)                | 0x07 | Z serwera do klienta                         |
| Aktywne żądanie odnajdywania PPPoE (PADR)              | 0x19 | Z klienta na serwer                         |
| Potwierdzanie sesji aktywnego odnajdywania (PADS) protokołu PPPOE | 0x65 | Z serwera do klienta                         |
| Aktywne zakończenie odnajdywania PPPoE (PADT)            | 0xa7 | Mogą być inicjowane z serwera lub klienta |

Wszystkie ramki Ethernet odnajdywania mają pole ETHER_TYPE ustawione na wartość 0x8863.

## <a name="pppoe-session-message"></a>Komunikat sesji PPPoE

Po utworzeniu sesji przez klienta i serwer ramki PROTOKOŁU DHCP mogą być przesyłane jako komunikaty sesji PPPoE. Podczas sesji nie może SESSION_ID i musi być wartością serwera przypisaną na etapie odnajdywania.

Wszystkie ramki ethernet sesji PPPoE mają pole ETHER_TYPE ustawione na wartość 0x8864.