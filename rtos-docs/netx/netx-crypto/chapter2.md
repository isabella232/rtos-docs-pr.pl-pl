---
title: Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX Crypto
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd736cf6bbe15e1f407d1812072a4308435c8007
ms.sourcegitcommit: c2f5da5d6c7b230799f8fbd77885e9940acfbab4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2021
ms.locfileid: "110236156"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="24fee-103">Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="24fee-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="24fee-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika Azure RTOS NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="24fee-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="24fee-105">Dystrybucja produktów</span><span class="sxs-lookup"><span data-stu-id="24fee-105">Product Distribution</span></span>

<span data-ttu-id="24fee-106">Azure RTOS netx crypto jest dostępna na stronie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="24fee-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="24fee-107">Pakiet zawiera pliki źródłowe, pliki dołączane i plik PDF zawierający ten dokument w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="24fee-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="24fee-108">**nx_crypto.h:** moduł NetX Crypto pliku nagłówkowego publicznego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="24fee-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="24fee-109">**nx_crypto_\*.c/h:** pliki źródłowe C/H dla programu NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="24fee-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="24fee-110">**nx_crypto_port.h:** plik nagłówkowy C zawierający wszystkie narzędzia programowe i docelowe definicje i struktury danych.</span><span class="sxs-lookup"><span data-stu-id="24fee-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="24fee-111">**NetX_Crypto_User_Guide.pdf:** opis PDF modułu kryptograficznego NetX.</span><span class="sxs-lookup"><span data-stu-id="24fee-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="24fee-112">Instalacja kryptograficzna netx</span><span class="sxs-lookup"><span data-stu-id="24fee-112">NetX Crypto Installation</span></span>

<span data-ttu-id="24fee-113">Cała wymieniona wcześniej dystrybucja jest dostępna w katalogu **crypto_libraries,** który znajduje się na poziomie głównym repozytorium NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="24fee-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="24fee-114">Aby można było korzystać z usługi NetX Crypto, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana na ten sam poziom katalogu, na którym zainstalowano program NetX.</span><span class="sxs-lookup"><span data-stu-id="24fee-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="24fee-115">Jeśli na przykład netx jest zainstalowany w katalogu "\threadx\arm7\NetX", to nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="24fee-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="24fee-116">Katalogi powinny zostać skopiowane do folderu "\threadx\arm7\NetXCrypto".</span><span class="sxs-lookup"><span data-stu-id="24fee-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="24fee-117">Aby kryptografia NetX była używana w trybie autonomicznym, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24fee-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="24fee-118">Na **przykład crypto_libraries** powinien zostać skopiowany do projektu aplikacji lub do projektu biblioteki z crypto_libraries **powinien** zostać utworzony i połączony z projektem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24fee-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="24fee-119">Korzystanie z usługi NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="24fee-119">Using NetX Crypto</span></span>

<span data-ttu-id="24fee-120">W tym rozdziale opisano instalację, konfigurację i użycie Azure RTOS NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="24fee-120">This chapter describes installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span> <span data-ttu-id="24fee-121">Zasadniczo kod aplikacji musi zawierać kod *nx_crypto.h.*</span><span class="sxs-lookup"><span data-stu-id="24fee-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="24fee-122">Po *nx_crypto.h* kod aplikacji może następnie wykonać wywołania funkcji Kryptograficzne NetX określone w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="24fee-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="24fee-123">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="24fee-123">Configuration Options</span></span>

<span data-ttu-id="24fee-124">Istnieje kilka opcji konfiguracji tworzenia usług Kryptograficznych NetX.</span><span class="sxs-lookup"><span data-stu-id="24fee-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="24fee-125">Poniżej znajduje się lista wszystkich opcji, gdzie każda z nich jest szczegółowo opisana:</span><span class="sxs-lookup"><span data-stu-id="24fee-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="24fee-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE:** zdefiniowana, ta opcja zapewnia oczekiwaną maksymalną wartość modulo RSA w bitach.</span><span class="sxs-lookup"><span data-stu-id="24fee-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="24fee-127">Wartość domyślna to 4096 dla modulo 4096-bitowego.</span><span class="sxs-lookup"><span data-stu-id="24fee-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="24fee-128">Inne wartości to 3072, 2048 lub 1024 (nie jest to zalecane).</span><span class="sxs-lookup"><span data-stu-id="24fee-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="24fee-129">**NX_CRYPTO_SELF_TEST:** zdefiniowane, umożliwia samodzielne testy modułu NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="24fee-129">**NX_CRYPTO_SELF_TEST**: Defined, enables self tests for NetX Crypto module.</span></span> <span data-ttu-id="24fee-130">**NX_CRYPTO_FIPS** symbol jest teraz przestarzały i zmieniono jego nazwę na **NX_CRYPTO_SELF_TEST**</span><span class="sxs-lookup"><span data-stu-id="24fee-130">**NX_CRYPTO_FIPS** symbol is now deprecated and renamed to **NX_CRYPTO_SELF_TEST**</span></span>
- <span data-ttu-id="24fee-131">**NX_CRYPTO_STANDALONE_ENABLE:** Zdefiniowane umożliwia korzystanie z kryptografii NetX w trybie autonomicznym (bez Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="24fee-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="24fee-132">Domyślnie ten symbol nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="24fee-132">By default this symbol is not defined.</span></span>
