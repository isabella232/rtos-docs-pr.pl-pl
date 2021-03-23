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
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a><span data-ttu-id="ce104-103">Dodatek A — kody błędów krytycznych SNTP usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ce104-103">Appendix A - Azure RTOS NetX Duo SNTP Fatal Error Codes</span></span>

<span data-ttu-id="ce104-104">Następujące kody błędów spowodują przerwanie aktualizacji czasu klienta SNTP usługi Azure RTO NetX Duo przy użyciu bieżącego serwera.</span><span class="sxs-lookup"><span data-stu-id="ce104-104">The following error codes will result in the Azure RTOS NetX Duo SNTP Client aborting time updates with the current server.</span></span> <span data-ttu-id="ce104-105">Do aplikacji można zdecydować, czy serwer powinien zostać usunięty z listy klientów SNTP dostępnych serwerów, czy po prostu przełączyć się na następny dostępny serwer na liście.</span><span class="sxs-lookup"><span data-stu-id="ce104-105">It is up to the application to decide if the server should be removed from the SNTP Client list of available servers, or simply switch to the next available server on the list.</span></span> <span data-ttu-id="ce104-106">Definicja każdego stanu błędu jest zdefiniowana w \* nxd_sntp_client. h.</span><span class="sxs-lookup"><span data-stu-id="ce104-106">The definition of each error status is defined in \*nxd_sntp_client.h.</span></span> *

<span data-ttu-id="ce104-107">Gdy klient SNTP zwróci błąd z poniższej listy do aplikacji, serwer powinien prawdopodobnie zostać zastąpiony innym serwerem.</span><span class="sxs-lookup"><span data-stu-id="ce104-107">When the SNTP Client returns an error from the list below to the application, the Server should probably be replaced with another Server.</span></span> <span data-ttu-id="ce104-108">Należy zauważyć, że NX_SNTP_KOD_REMOVE_SERVER stan błędu jest pozostawiony do wypróbowania klienta SNTP (funkcja wywołania zwrotnego) do ustawienia:</span><span class="sxs-lookup"><span data-stu-id="ce104-108">Note that the NX_SNTP_KOD_REMOVE_SERVER error status is left to the SNTP Client kiss of death handler (callback function) to set:</span></span>

- <span data-ttu-id="ce104-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span><span class="sxs-lookup"><span data-stu-id="ce104-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span></span>  
- <span data-ttu-id="ce104-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span><span class="sxs-lookup"><span data-stu-id="ce104-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span></span>  
- <span data-ttu-id="ce104-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span><span class="sxs-lookup"><span data-stu-id="ce104-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span></span>  
- <span data-ttu-id="ce104-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span><span class="sxs-lookup"><span data-stu-id="ce104-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span></span>  
- <span data-ttu-id="ce104-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span><span class="sxs-lookup"><span data-stu-id="ce104-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span></span>  

<span data-ttu-id="ce104-114">Gdy klient SNTP zwraca błąd z poniższej listy do aplikacji, serwer może tymczasowo być niew stanie zapewnić prawidłowe aktualizacje czasu i nie należy go usuwać:</span><span class="sxs-lookup"><span data-stu-id="ce104-114">When the SNTP Client returns an error from the list below to the application, the Server may only temporarily be unable to provide valid time updates and need not be removed:</span></span>

- <span data-ttu-id="ce104-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span><span class="sxs-lookup"><span data-stu-id="ce104-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span></span>  
- <span data-ttu-id="ce104-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span><span class="sxs-lookup"><span data-stu-id="ce104-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span></span>  
- <span data-ttu-id="ce104-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span><span class="sxs-lookup"><span data-stu-id="ce104-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span></span>  
- <span data-ttu-id="ce104-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span><span class="sxs-lookup"><span data-stu-id="ce104-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span></span>  
- <span data-ttu-id="ce104-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span><span class="sxs-lookup"><span data-stu-id="ce104-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span></span>  
- <span data-ttu-id="ce104-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span><span class="sxs-lookup"><span data-stu-id="ce104-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span></span>  
- <span data-ttu-id="ce104-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span><span class="sxs-lookup"><span data-stu-id="ce104-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span></span>