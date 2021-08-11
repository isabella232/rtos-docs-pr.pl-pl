---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX PPPoE Client
description: Ten rozdział zawiera szczegółowe informacje o Azure RTOS NetX PPPoE.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 08edb5b332426d4ab5d2f92462438e1cb84245db6c2f6ab2ef72f28eab8a313f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798920"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX PPPoE Client

Protokół PPP over Ethernet (PPPoE) umożliwia hostom łączenie się z serwerem PPP za pośrednictwem sieci Ethernet zamiast tradycyjnej komunikacji szeregowej opartej na znakach.  Szczegóły techniczne ppPoE są opisane w dokumencie RFC 2516: A Method for Transmiting PPP over Ethernet (PPPoE) (RFC 2516: Metoda przesyłania protokołu PPP przez Ethernet( PPPoE). Ten dokument koncentruje się na szczegółach Azure RTOS NetX PPPoE.

Aby zapewnić połączenie typu punkt-punkt za pośrednictwem sieci Ethernet, każda sesja PPP musi poznać adres Ethernet zdalnego elementu równorzędnego, a także ustanowić unikatowy identyfikator sesji.

Zgodnie ze specyfikacji RFC 2516 projekt PPPoE składa się z dwóch etapów: etapu odnajdywania i etapu sesji PPPoE. Gdy host (klient) chce uruchomić sesję PROTOKOŁU PPP, musi najpierw wykonać odnajdywanie w celu znalezienia serwera PPPoE. Ten krok umożliwia również serwerowi i klientowi identyfikowanie adresów MAC sieci Ethernet i adresów SESSION_ID, które będą używane w pozostałej części sesji PPP.

Ramka Ethernet jest następująca:

![Ramka Ethernet](media/ethernet-frame.png)

Ładunek Ethernet dla ppPoE jest następujący:

![Ładunek sieci Ethernet](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a>Etap odnajdywania pppoe

Etap odnajdywania PPPoE umożliwia klientom wybranie serwera ze wszystkich dostępnych serwerów w sieci, efektywnie tworząc sesję przed wymianą ramek PPP.  Na koniec etapu odnajdywania klient i serwer muszą uzgodnić unikatowy identyfikator sesji, a obie strony muszą znać adres MAC elementu równorzędnego.

| Komunikat odnajdywania | Kod | Kierunek |
| ----------------- | ---- | --------- |
| Inicjowanie aktywnego odnajdywania (PPPoE) | 0x09 | Z klienta do emisji |
| Oferta aktywnego odnajdywania PPPoE (PADO) | 0x07 | Z serwera do klienta |
| Aktywne żądanie odnajdywania PPPoE (PADR) | 0x19 | Z klienta do serwera |
| Potwierdzenie sesji aktywnego odnajdywania PPPOE (PADS) | 0x65 | Z serwera do klienta |
| Zakończenie aktywnego odnajdywania pppoe (PADT) | 0xa7 | Można zainicjować z serwera lub klienta |

Wszystkie ramki Ethernet odnajdywania mają pole ETHER_TYPE ustawione na wartość 0x8863.

## <a name="pppoe-session-message"></a>Komunikat sesji PPPoE

Po utworzeniu sesji przez klienta i serwer ramki PROTOKOŁU PPP mogą być przesyłane jako komunikaty sesji PPPoE.  Podczas sesji nie można SESSION_ID zmienić wartości serwera przypisanego podczas etapu odnajdywania.

Wszystkie ramki ethernet sesji PPPoE mają pole ETHER_TYPE ustawione na wartość 0x8864.
