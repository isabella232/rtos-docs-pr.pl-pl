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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX Crypto

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika Azure RTOS NetX Crypto.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS netx crypto jest dostępna na stronie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera pliki źródłowe, pliki dołączane i plik PDF zawierający ten dokument w następujący sposób:

- **nx_crypto.h:** moduł NetX Crypto pliku nagłówkowego publicznego interfejsu API
- **nx_crypto_*.c/h:** pliki źródłowe C/H dla programu NetX Crypto
- **nx_crypto_port.h:** plik nagłówkowy C zawierający wszystkie narzędzia programowe i docelowe definicje i struktury danych.
- **NetX_Crypto_User_Guide.pdf:** opis PDF modułu kryptograficznego NetX.

## <a name="netx-crypto-installation"></a>Instalacja kryptograficzna netx

Cała wymieniona wcześniej dystrybucja jest dostępna w katalogu **crypto_libraries,** który znajduje się na poziomie głównym repozytorium NetX Duo.

Aby można było korzystać z usługi NetX Crypto, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana na ten sam poziom katalogu, na którym zainstalowano program NetX. Jeśli na przykład netx jest zainstalowany w katalogu "\threadx\arm7\NetX", to nx_crypto *.* Katalogi powinny zostać skopiowane do folderu "\threadx\arm7\NetXCrypto".

Aby kryptografia NetX była używana w trybie autonomicznym, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do projektu aplikacji. Na **przykład crypto_libraries** powinien zostać skopiowany do projektu aplikacji lub do projektu biblioteki z crypto_libraries **powinien** zostać utworzony i połączony z projektem aplikacji. 

## <a name="using-netx-crypto"></a>Korzystanie z usługi NetX Crypto

W tym rozdziale opisano instalację, konfigurację i użycie Azure RTOS NetX Crypto. Zasadniczo kod aplikacji musi zawierać kod *nx_crypto.h.*  Po *nx_crypto.h* kod aplikacji może następnie wykonać wywołania funkcji Kryptograficzne NetX określone w dalszej części tego przewodnika.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji tworzenia usług Kryptograficznych NetX. Poniżej znajduje się lista wszystkich opcji, gdzie każda z nich jest szczegółowo opisana:

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE:** zdefiniowana, ta opcja zapewnia oczekiwaną maksymalną wartość modulo RSA w bitach. Wartość domyślna to 4096 dla modulo 4096-bitowego. Inne wartości to 3072, 2048 lub 1024 (nie jest to zalecane).
- **NX_CRYPTO_SELF_TEST:** zdefiniowane, umożliwia samodzielne testy modułu NetX Crypto. **NX_CRYPTO_FIPS** symbol jest teraz przestarzały i zmieniono jego nazwę na **NX_CRYPTO_SELF_TEST**
- **NX_CRYPTO_STANDALONE_ENABLE:** Zdefiniowane umożliwia korzystanie z kryptografii NetX w trybie autonomicznym (bez Azure RTOS). Domyślnie ten symbol nie jest zdefiniowany.
