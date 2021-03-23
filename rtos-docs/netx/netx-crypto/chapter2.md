---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Crypto
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika kryptografii NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1616667c5efd73229ed69bcd4e5de5f80e5826f9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822722"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="b1aa6-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="b1aa6-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="b1aa6-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika kryptografii Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="b1aa6-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="b1aa6-105">Product Distribution</span></span>

<span data-ttu-id="b1aa6-106">Kryptografia NetX usługi Azure RTO jest dostępna pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="b1aa6-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="b1aa6-107">Pakiet zawiera pliki źródłowe, pliki dołączane oraz plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b1aa6-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="b1aa6-108">**nx_crypto. h**: publiczny plik NAGŁÓWKOWY interfejsu API NetX moduł kryptograficzny</span><span class="sxs-lookup"><span data-stu-id="b1aa6-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="b1aa6-109">\*\*nx_crypto_ \*. c/h\*\*: pliki źródłowe c/h dla kryptografii NetX</span><span class="sxs-lookup"><span data-stu-id="b1aa6-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="b1aa6-110">**nx_crypto_port. h**: plik nagłówkowy C zawierający wszystkie narzędzia deweloperskie i specyficzne dla określonych struktur danych.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="b1aa6-111">**NetX_Crypto_User_Guide.pdf**: Opis PDF modułu kryptograficznego NetX.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="b1aa6-112">NetX kryptografii</span><span class="sxs-lookup"><span data-stu-id="b1aa6-112">NetX Crypto Installation</span></span>

<span data-ttu-id="b1aa6-113">Cała wymieniona wcześniej dystrybucja jest dostępna w katalogu **crypto_libraries** , obecnym na poziomie głównym repozytorium NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="b1aa6-114">Aby można było użyć kryptografii NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego poziomu katalogu, na którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="b1aa6-115">Na przykład, jeśli NetX jest zainstalowany w katalogu "\threadx\arm7\NetX", wówczas nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="b1aa6-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="b1aa6-116">katalogi powinny być kopiowane do "\threadx\arm7\NetXCrypto".</span><span class="sxs-lookup"><span data-stu-id="b1aa6-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="b1aa6-117">Aby można było użyć kryptografii NetX w trybie autonomicznym, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="b1aa6-118">Na przykład katalog **crypto_libraries** powinien być skopiowany do projektu aplikacji lub projektu biblioteki z **crypto_libraries** Directory powinien być utworzony i połączony z projektem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="b1aa6-119">Korzystanie z kryptografii NetX</span><span class="sxs-lookup"><span data-stu-id="b1aa6-119">Using NetX Crypto</span></span>

<span data-ttu-id="b1aa6-120">Używanie kryptografii NetX jest proste.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-120">Using NetX Crypto is easy.</span></span> <span data-ttu-id="b1aa6-121">W zasadzie kod aplikacji musi zawierać *nx_crypto. h*.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="b1aa6-122">Po dołączeniu *nx_crypto. h* kod aplikacji jest następnie umożliwiający wywołanie funkcji kryptograficznych NetX określonych w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="b1aa6-123">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b1aa6-123">Configuration Options</span></span>

<span data-ttu-id="b1aa6-124">Istnieje kilka opcji konfiguracji do kompilowania kryptografii NetX.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="b1aa6-125">Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:</span><span class="sxs-lookup"><span data-stu-id="b1aa6-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="b1aa6-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: zdefiniowane, ta opcja zapewnia maksymalny rozmiar modułu RSA oczekiwany w bitach.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="b1aa6-127">Wartość domyślna to 4096 dla modułu 4096-bitowego.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="b1aa6-128">Inne wartości mogą być 3072, 2048 lub 1024 (niezalecane).</span><span class="sxs-lookup"><span data-stu-id="b1aa6-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="b1aa6-129">**NX_CRYPTO_FIPS**: zdefiniowane, ta opcja włącza dodatkowe funkcje zabezpieczeń wymagane do FIPS-Compliant użycia.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-129">**NX_CRYPTO_FIPS**: Defined, this option enables extra security features required for FIPS-Compliant usage.</span></span> <span data-ttu-id="b1aa6-130">Ta opcja nie jest włączona dla kompilacji niezgodnej ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-130">This option is not enabled for non-FIPS build.</span></span>
- <span data-ttu-id="b1aa6-131">**NX_CRYPTO_STANDALONE_ENABLE**: defined włącza kryptografię NetX do użycia w trybie autonomicznym (bez usługi Azure RTO).</span><span class="sxs-lookup"><span data-stu-id="b1aa6-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="b1aa6-132">Domyślnie ten symbol nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="b1aa6-132">By default this symbol is not defined.</span></span>
