---
title: Dodatek A — kody błędów krytycznych SNTP usługi Azure RTO NetX Duo
description: Następujące kody błędów spowodują przerwanie aktualizacji czasu klienta SNTP usługi Azure RTO NetX Duo przy użyciu bieżącego serwera.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 065e7a3e65b3cf8d7fcfb34bb9568a673791609a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821666"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>Dodatek A — kody błędów krytycznych SNTP usługi Azure RTO NetX Duo

Następujące kody błędów spowodują przerwanie aktualizacji czasu klienta SNTP usługi Azure RTO NetX Duo przy użyciu bieżącego serwera. Do aplikacji można zdecydować, czy serwer powinien zostać usunięty z listy klientów SNTP dostępnych serwerów, czy po prostu przełączyć się na następny dostępny serwer na liście. Definicja każdego stanu błędu jest zdefiniowana w * nxd_sntp_client. h. *

Gdy klient SNTP zwróci błąd z poniższej listy do aplikacji, serwer powinien prawdopodobnie zostać zastąpiony innym serwerem. Należy zauważyć, że NX_SNTP_KOD_REMOVE_SERVER stan błędu jest pozostawiony do wypróbowania klienta SNTP (funkcja wywołania zwrotnego) do ustawienia:

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

Gdy klient SNTP zwraca błąd z poniższej listy do aplikacji, serwer może tymczasowo być niew stanie zapewnić prawidłowe aktualizacje czasu i nie należy go usuwać:

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24