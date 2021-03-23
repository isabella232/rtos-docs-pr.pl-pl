---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX LWM2M
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika LWM2M usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822603"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="405a3-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="405a3-103">Chapter 2 - Installation and use of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="405a3-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika LWM2M usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="405a3-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX LWM2M component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="405a3-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="405a3-105">Product Distribution</span></span>

<span data-ttu-id="405a3-106">NetX LWM2M jest dostępny pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="405a3-106">NetX LWM2M is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="405a3-107">Pakiet zawiera trzy pliki źródłowe, jedno dołączane pliki i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="405a3-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="405a3-108">**nx_lwm2m_client. h**: plik nagłówkowy dla klienta NetX lwm2m</span><span class="sxs-lookup"><span data-stu-id="405a3-108">**nx_lwm2m_client.h**: Header file for the NetX LWM2M Client</span></span>

- <span data-ttu-id="405a3-109">\*\*nx_lwm2m_ \*. c/h\*\*: pliki źródłowe c/h dla NetX lwm2m</span><span class="sxs-lookup"><span data-stu-id="405a3-109">**nx_lwm2m_\*.c/h**: C/H Source files for NetX LWM2M</span></span>

- <span data-ttu-id="405a3-110">plik źródłowy **demo_netx_lwm2m_client. c**: c dla pokazu klienta NetX lwm2m</span><span class="sxs-lookup"><span data-stu-id="405a3-110">**demo_netx_lwm2m_client.c**: C Source file for NetX LWM2M Client Demo</span></span>

- <span data-ttu-id="405a3-111">**NetX_LWM2M_User_Guide.pdf**: Opis PDF NetX produktu LWM2M</span><span class="sxs-lookup"><span data-stu-id="405a3-111">**NetX_LWM2M_User_Guide.pdf**: PDF description of NetX LWM2M product</span></span>

## <a name="netx-lwm2m-installation"></a><span data-ttu-id="405a3-112">Instalacja LWM2M NetX</span><span class="sxs-lookup"><span data-stu-id="405a3-112">NetX LWM2M Installation</span></span>

<span data-ttu-id="405a3-113">Aby można było korzystać z programu NetX LWM2M, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="405a3-113">In order to use NetX LWM2M, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="405a3-114">Na przykład jeśli NetX jest zainstalowana w katalogu "*\\ ThreadX \\ ARM7 \\ zielony*", wówczas *&#42; nx_lwm2m. pliki &#42;* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="405a3-114">For example, if NetX is installed in the directory "*\\threadx\\arm7\\green*" then the *nx_lwm2m&#42;.&#42;* files should be copied into this directory.</span></span>

## <a name="using-netx-lwm2m"></a><span data-ttu-id="405a3-115">Korzystanie z NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="405a3-115">Using NetX LWM2M</span></span>

<span data-ttu-id="405a3-116">Korzystanie z programu NetX LWM2M jest proste.</span><span class="sxs-lookup"><span data-stu-id="405a3-116">Using NetX LWM2M is easy.</span></span> <span data-ttu-id="405a3-117">W zasadzie kod aplikacji musi zawierać *nx_lwm2m_client. h* po zawiera *tx_api. h* i *nx_api. h*, aby można było użyć ThreadX i NetX.</span><span class="sxs-lookup"><span data-stu-id="405a3-117">Basically, the application code must include *nx_lwm2m_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="405a3-118">Po dołączeniu *nx_lwm2m_client. h* kod aplikacji może następnie wprowadzić wywołania funkcji NetX lwm2m w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="405a3-118">Once *nx_lwm2m_client.h* is included, the application code is then able to make the NetX LWM2M function calls specified later in this guide.</span></span> <span data-ttu-id="405a3-119">Aplikacja musi również zaimportować pliki *nx_lwm2m&#42;. &#42;* do biblioteki NetX.</span><span class="sxs-lookup"><span data-stu-id="405a3-119">The application must also import the *nx_lwm2m&#42;.&#42;* files into the NetX library.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="405a3-120">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="405a3-120">Configuration Options</span></span>

<span data-ttu-id="405a3-121">Podczas kompilowania biblioteki klienta LWM2M i aplikacji przy użyciu klienta LWM2M istnieje kilka opcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="405a3-121">There are several configuration options when building the LWM2M Client library and the application using the LWM2M Client.</span></span> <span data-ttu-id="405a3-122">Opcje konfiguracji można definiować w źródle aplikacji w wierszu polecenia, o ile nie określono inaczej.</span><span class="sxs-lookup"><span data-stu-id="405a3-122">The configuration options can be defined in the application source, on the command line, unless otherwise specified.</span></span>

### <a name="nx_lwm2m_client_disable_error_checking"></a><span data-ttu-id="405a3-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span><span class="sxs-lookup"><span data-stu-id="405a3-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span></span>

<span data-ttu-id="405a3-124">Zdefiniowane, usuwa interfejs API podstawowego sprawdzania błędów klienta LWM2M i zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="405a3-124">Defined, removes the basic LWM2M Client error checking API and improves performance.</span></span> <span data-ttu-id="405a3-125">Kody powrotne interfejsu API, których nie dotyczy wyłączenie sprawdzania błędów, są wymienione w pogrubionym kroju pisma w definicji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="405a3-125">API return codes not affected by disabling error checking are listed in bold typeface in the API definition.</span></span>

### <a name="nx_lwm2m_client_disable_float"></a><span data-ttu-id="405a3-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span><span class="sxs-lookup"><span data-stu-id="405a3-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span></span>

<span data-ttu-id="405a3-127">Zdefiniowane, usuwa obsługę liczb zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="405a3-127">Defined, removes the support of floating point numbers values.</span></span> <span data-ttu-id="405a3-128">Po wyłączeniu klient LWM2M nie może obsługiwać zasobów z typem danych zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="405a3-128">When disabled the LWM2M Client cannot support Resources with Float data type.</span></span>

### <a name="nx_lwm2m_client_disable_float64"></a><span data-ttu-id="405a3-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span><span class="sxs-lookup"><span data-stu-id="405a3-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span></span>

<span data-ttu-id="405a3-130">Zdefiniowane, usuwa obsługę 64-bitowych liczb zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="405a3-130">Defined, removes the support of 64-bit floating point numbers values.</span></span> <span data-ttu-id="405a3-131">Klient LWM2M nadal może odbierać komunikaty TLV zawierające 64-bitowe liczby zmiennoprzecinkowe, ale wartości są konwertowane na 32-bitowe zmiennoprzecinkowe do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="405a3-131">The LWM2M Client can still receive TLV messages containing 64-bit floating numbers, but the values are converted to 32-bit floating point for processing.</span></span>

### <a name="nx_lwm2m_client_priority"></a><span data-ttu-id="405a3-132">NX_LWM2M_CLIENT_PRIORITY</span><span class="sxs-lookup"><span data-stu-id="405a3-132">NX_LWM2M_CLIENT_PRIORITY</span></span>

<span data-ttu-id="405a3-133">Określa priorytet wątku klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="405a3-133">Specifies the priority of the LWM2M Client thread.</span></span> <span data-ttu-id="405a3-134">Domyślnie ta wartość jest definiowana jako 16, aby określić priorytet 16.</span><span class="sxs-lookup"><span data-stu-id="405a3-134">By default, this value is defined as 16 to specify priority 16.</span></span>

### <a name="nx_lwm2m_client_max_device_errors"></a><span data-ttu-id="405a3-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span><span class="sxs-lookup"><span data-stu-id="405a3-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span></span>

<span data-ttu-id="405a3-136">Określa maksymalną liczbę kodów błędów przechowywanych przez obiekt urządzenia.</span><span class="sxs-lookup"><span data-stu-id="405a3-136">Specifies the maximum number of error codes stored by the Device Object.</span></span> <span data-ttu-id="405a3-137">Wartość domyślna to 8.</span><span class="sxs-lookup"><span data-stu-id="405a3-137">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_security_instances"></a><span data-ttu-id="405a3-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="405a3-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span></span>

<span data-ttu-id="405a3-139">Określa maksymalną liczbę wystąpień obiektu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="405a3-139">Specifies the maximum number of Security Object Instances.</span></span> <span data-ttu-id="405a3-140">Wartość domyślna to 2 dla obsługi serwera Bootstrap i serwera standardowego.</span><span class="sxs-lookup"><span data-stu-id="405a3-140">The default value is 2 for supporting a Bootstrap Server and a standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_instances"></a><span data-ttu-id="405a3-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="405a3-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span></span>

<span data-ttu-id="405a3-142">Określa maksymalną liczbę wystąpień obiektów serwera.</span><span class="sxs-lookup"><span data-stu-id="405a3-142">Specifies the maximum number of Server Object Instances.</span></span> <span data-ttu-id="405a3-143">Wartość domyślna to 1 w przypadku obsługi pojedynczego serwera w warstwie Standardowa.</span><span class="sxs-lookup"><span data-stu-id="405a3-143">The default value is 1 for supporting a single standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_uri"></a><span data-ttu-id="405a3-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span><span class="sxs-lookup"><span data-stu-id="405a3-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span></span>

<span data-ttu-id="405a3-145">Określa maksymalną długość identyfikatora URI serwera, włącznie z przerwaniem znaku Nil.</span><span class="sxs-lookup"><span data-stu-id="405a3-145">Specifies the maximum length of a server URI, including terminating nil character.</span></span> <span data-ttu-id="405a3-146">Wartość domyślna to 128.</span><span class="sxs-lookup"><span data-stu-id="405a3-146">The default value is 128.</span></span>

### <a name="nx_lwm2m_client_max_access_control_instances"></a><span data-ttu-id="405a3-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="405a3-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span></span>

<span data-ttu-id="405a3-148">Określa maksymalną liczbę wystąpień Access Control.</span><span class="sxs-lookup"><span data-stu-id="405a3-148">Specifies the maximum number of Access Control Instances.</span></span> <span data-ttu-id="405a3-149">Wartość domyślna to 0, co powoduje wyłączenie kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="405a3-149">The default value is 0, which disables access control.</span></span> <span data-ttu-id="405a3-150">Jeśli aplikacja obsługuje więcej niż jeden serwer LWM2M, Maksymalna liczba wystąpień Access Control musi być ustawiona na maksymalną liczbę wystąpień obiektów obsługiwanych przez klienta LWM2M, ponieważ należy utworzyć jedno wystąpienie Access Control dla każdego wystąpienia obiektu (z wyjątkiem wystąpień obiektu zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="405a3-150">If the application supports more than one LWM2M Server, the maximum number of Access Control Instances must be set to the maximum number of Object Instances that the LWM2M Client will support, as one Access Control Instance must be created for each Object Instance (except for the Security Object Instances).</span></span>

### <a name="nx_lwm2m_client_max_access_control_acls"></a><span data-ttu-id="405a3-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span><span class="sxs-lookup"><span data-stu-id="405a3-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span></span>

<span data-ttu-id="405a3-152">Określa maksymalną liczbę zasobów listy ACL na wystąpienie Access Control.</span><span class="sxs-lookup"><span data-stu-id="405a3-152">Specifies the maximum number of ACL resources per Access Control Instance.</span></span> <span data-ttu-id="405a3-153">Wartość domyślna to 4.</span><span class="sxs-lookup"><span data-stu-id="405a3-153">The default value is 4.</span></span>

### <a name="nx_lwm2m_client_max_notifications"></a><span data-ttu-id="405a3-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="405a3-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span></span>

<span data-ttu-id="405a3-155">Określa maksymalną liczbę powiadomień, które będą obsługiwane przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="405a3-155">Specifies the maximum number of notifications that the LWM2M Client will support.</span></span> <span data-ttu-id="405a3-156">Serwer LWM2M może ustawiać powiadomienia dotyczące obiektów, wystąpień obiektów i zasobów.</span><span class="sxs-lookup"><span data-stu-id="405a3-156">A LWM2M Server can set notifications on Objects, Object Instances, and Resources.</span></span> <span data-ttu-id="405a3-157">Wartość domyślna to 8.</span><span class="sxs-lookup"><span data-stu-id="405a3-157">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_resources"></a><span data-ttu-id="405a3-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="405a3-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span></span>

<span data-ttu-id="405a3-159">Określa maksymalną liczbę zasobów na obiekt.</span><span class="sxs-lookup"><span data-stu-id="405a3-159">Specifies the maximum number of Resources per Object.</span></span> <span data-ttu-id="405a3-160">Wartość domyślna to 32.</span><span class="sxs-lookup"><span data-stu-id="405a3-160">The default value is 32.</span></span>

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a><span data-ttu-id="405a3-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span><span class="sxs-lookup"><span data-stu-id="405a3-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span></span>

<span data-ttu-id="405a3-162">Określa maksymalny czas oczekiwania na żądania serwera ładowania początkowego, gdy sesja ładowania początkowego zostanie zainicjowana przed przerwaniem sesji.</span><span class="sxs-lookup"><span data-stu-id="405a3-162">Specifies the maximum time to wait for bootstrap server requests when the bootstrap session is initiated before aborting the session.</span></span> <span data-ttu-id="405a3-163">Wartość domyślna to 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="405a3-163">The default value is 60 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_start_timeout"></a><span data-ttu-id="405a3-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="405a3-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span></span>

<span data-ttu-id="405a3-165">Określa maksymalny czas oczekiwania na zakończenie uzgadniania DTLS.</span><span class="sxs-lookup"><span data-stu-id="405a3-165">Specifies the maximum time to wait for DTLS handshake completion.</span></span> <span data-ttu-id="405a3-166">Wartość domyślna to 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="405a3-166">The default value is 30 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_end_timeout"></a><span data-ttu-id="405a3-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="405a3-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span></span>

<span data-ttu-id="405a3-168">Określa maksymalny czas oczekiwania na zakończenie zamykania DTLS.</span><span class="sxs-lookup"><span data-stu-id="405a3-168">Specifies the maximum time to wait for DTLS shutdown completion.</span></span> <span data-ttu-id="405a3-169">Wartość domyślna to 5 sekund.</span><span class="sxs-lookup"><span data-stu-id="405a3-169">The default value is 5 seconds.</span></span>
