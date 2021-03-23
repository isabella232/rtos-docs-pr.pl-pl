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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Crypto

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika kryptografii Azure RTO NetX.

## <a name="product-distribution"></a>Dystrybucja produktu

Kryptografia NetX usługi Azure RTO jest dostępna pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera pliki źródłowe, pliki dołączane oraz plik PDF, który zawiera ten dokument, w następujący sposób:

- **nx_crypto. h**: publiczny plik NAGŁÓWKOWY interfejsu API NetX moduł kryptograficzny
- **nx_crypto_ *. c/h**: pliki źródłowe c/h dla kryptografii NetX
- **nx_crypto_port. h**: plik nagłówkowy C zawierający wszystkie narzędzia deweloperskie i specyficzne dla określonych struktur danych.
- **NetX_Crypto_User_Guide.pdf**: Opis PDF modułu kryptograficznego NetX.

## <a name="netx-crypto-installation"></a>NetX kryptografii

Cała wymieniona wcześniej dystrybucja jest dostępna w katalogu **crypto_libraries** , obecnym na poziomie głównym repozytorium NetX Duo.

Aby można było użyć kryptografii NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego poziomu katalogu, na którym zainstalowano NetX. Na przykład, jeśli NetX jest zainstalowany w katalogu "\threadx\arm7\NetX", wówczas nx_crypto *.* katalogi powinny być kopiowane do "\threadx\arm7\NetXCrypto".

Aby można było użyć kryptografii NetX w trybie autonomicznym, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do projektu aplikacji. Na przykład katalog **crypto_libraries** powinien być skopiowany do projektu aplikacji lub projektu biblioteki z **crypto_libraries** Directory powinien być utworzony i połączony z projektem aplikacji. 

## <a name="using-netx-crypto"></a>Korzystanie z kryptografii NetX

Używanie kryptografii NetX jest proste. W zasadzie kod aplikacji musi zawierać *nx_crypto. h*.  Po dołączeniu *nx_crypto. h* kod aplikacji jest następnie umożliwiający wywołanie funkcji kryptograficznych NetX określonych w dalszej części tego przewodnika.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania kryptografii NetX. Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: zdefiniowane, ta opcja zapewnia maksymalny rozmiar modułu RSA oczekiwany w bitach. Wartość domyślna to 4096 dla modułu 4096-bitowego. Inne wartości mogą być 3072, 2048 lub 1024 (niezalecane).
- **NX_CRYPTO_FIPS**: zdefiniowane, ta opcja włącza dodatkowe funkcje zabezpieczeń wymagane do FIPS-Compliant użycia. Ta opcja nie jest włączona dla kompilacji niezgodnej ze standardem FIPS.
- **NX_CRYPTO_STANDALONE_ENABLE**: defined włącza kryptografię NetX do użycia w trybie autonomicznym (bez usługi Azure RTO). Domyślnie ten symbol nie jest zdefiniowany.
