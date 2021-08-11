---
title: Dodatek A — Azure RTOS błędów krytycznych NetX Duo SNTP
description: Następujące kody błędów spowoduje, że klient Azure RTOS NetX Duo SNTP przerywa aktualizacje czasu przy użyciu bieżącego serwera.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e0152c1342b3edffd42f7442c51e7c5d62b199a5b38085dac06b4c0dbee9e9a8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790109"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>Dodatek A — Azure RTOS błędów krytycznych NetX Duo SNTP

Następujące kody błędów spowoduje, że klient Azure RTOS NetX Duo SNTP przerywa aktualizacje czasu przy użyciu bieżącego serwera. To aplikacja decyduje, czy serwer powinien zostać usunięty z listy dostępnych serwerów klienta SNTP, czy po prostu przełącz się na następny dostępny serwer na liście. Definicja każdego stanu błędu jest zdefiniowana w *nxd_sntp_client.h. *

Gdy klient SNTP zwraca błąd z poniższej listy do aplikacji, serwer powinien zostać prawdopodobnie zastąpiony innym serwerem. Zwróć uwagę, NX_SNTP_KOD_REMOVE_SERVER stan błędu jest pozostawiony w aplikacji SNTP Client of death handler (funkcja wywołania zwrotnego), aby ustawić:

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

Gdy klient SNTP zwraca błąd z poniższej listy do aplikacji, serwer może tylko tymczasowo nie być w stanie dostarczyć aktualizacji prawidłowego czasu i nie trzeba go usuwać:

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24