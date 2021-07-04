---
title: Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX Crypto
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3323af5eaf31ac9c167966522df6477c82e99fdc
ms.sourcegitcommit: c98e5360c9cedbe773af5a44f5163f563c85b570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2021
ms.locfileid: "110337010"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="bcd11-103">Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="bcd11-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="bcd11-104">W tym rozdziale opisano instalację, konfigurację i użycie składnika Azure RTOS NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="bcd11-104">This chapter describes installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="bcd11-105">Dystrybucja produktów</span><span class="sxs-lookup"><span data-stu-id="bcd11-105">Product Distribution</span></span>

<span data-ttu-id="bcd11-106">Azure RTOS NetX Crypto jest dostępna na stronie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="bcd11-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="bcd11-107">Pakiet zawiera pliki źródłowe, pliki dołączane i plik PDF zawierający ten dokument w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bcd11-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="bcd11-108">**nx_crypto.h:** moduł NetX Crypto pliku nagłówkowego publicznego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="bcd11-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="bcd11-109">**nx_crypto_\*.c/h:** pliki źródłowe C/H dla programu NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="bcd11-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="bcd11-110">**nx_crypto_port.h:** plik nagłówkowy C zawierający wszystkie narzędzia programowe i docelowe definicje i struktury danych.</span><span class="sxs-lookup"><span data-stu-id="bcd11-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="bcd11-111">**NetX_Crypto_User_Guide.pdf:** opis PDF modułu kryptograficznego NetX.</span><span class="sxs-lookup"><span data-stu-id="bcd11-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="bcd11-112">Instalacja kryptograficzna netx</span><span class="sxs-lookup"><span data-stu-id="bcd11-112">NetX Crypto Installation</span></span>

<span data-ttu-id="bcd11-113">Cała wymieniona wcześniej dystrybucja jest dostępna w katalogu **crypto_libraries,** który znajduje się na poziomie głównym repozytorium NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bcd11-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="bcd11-114">Aby można było korzystać z usługi NetX Crypto, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana na ten sam poziom katalogu, na którym zainstalowano program NetX.</span><span class="sxs-lookup"><span data-stu-id="bcd11-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="bcd11-115">Jeśli na przykład netx jest zainstalowany w katalogu "\threadx\arm7\NetX", to nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="bcd11-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="bcd11-116">katalogi powinny zostać skopiowane do folderu "\threadx\arm7\NetXCrypto".</span><span class="sxs-lookup"><span data-stu-id="bcd11-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="bcd11-117">Aby kryptografia NetX była używana w trybie autonomicznym, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bcd11-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="bcd11-118">Na **przykład crypto_libraries** powinien zostać skopiowany do projektu aplikacji lub projektu biblioteki z crypto_libraries **katalog** powinien zostać utworzony i połączony z projektem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bcd11-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="bcd11-119">Korzystanie z usługi NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="bcd11-119">Using NetX Crypto</span></span>

<span data-ttu-id="bcd11-120">Kod aplikacji musi zawierać *kod nx_crypto.h.*</span><span class="sxs-lookup"><span data-stu-id="bcd11-120">The application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="bcd11-121">Po *nx_crypto.h* kod aplikacji może następnie wykonać wywołania funkcji NetX Crypto określone w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="bcd11-121">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="bcd11-122">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bcd11-122">Configuration Options</span></span>

<span data-ttu-id="bcd11-123">Istnieje kilka opcji konfiguracji do tworzenia usługi NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="bcd11-123">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="bcd11-124">Poniżej znajduje się lista wszystkich opcji, z których każda jest szczegółowo opisana:</span><span class="sxs-lookup"><span data-stu-id="bcd11-124">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="bcd11-125">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE:** zdefiniowana, ta opcja zapewnia oczekiwaną maksymalną liczbę modulo RSA w bitach.</span><span class="sxs-lookup"><span data-stu-id="bcd11-125">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="bcd11-126">Wartość domyślna to 4096 dla modulo 4096-bitowych.</span><span class="sxs-lookup"><span data-stu-id="bcd11-126">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="bcd11-127">Inne wartości to 3072, 2048 lub 1024 (zalecane).</span><span class="sxs-lookup"><span data-stu-id="bcd11-127">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="bcd11-128">**NX_CRYPTO_SELF_TEST:** zdefiniowane, umożliwia samodzielne testy modułu NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="bcd11-128">**NX_CRYPTO_SELF_TEST**: Defined, enables self tests for NetX Crypto module.</span></span> <span data-ttu-id="bcd11-129">**NX_CRYPTO_FIPS** symbol jest teraz przestarzały i zmieniono jego nazwę na **NX_CRYPTO_SELF_TEST**</span><span class="sxs-lookup"><span data-stu-id="bcd11-129">**NX_CRYPTO_FIPS** symbol is now deprecated and renamed to **NX_CRYPTO_SELF_TEST**</span></span>
- <span data-ttu-id="bcd11-130">**NX_CRYPTO_STANDALONE_ENABLE:** zdefiniowane umożliwia korzystanie z narzędzia NetX Crypto w trybie autonomicznym (bez Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="bcd11-130">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="bcd11-131">Domyślnie ten symbol nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="bcd11-131">By default this symbol is not defined.</span></span>
