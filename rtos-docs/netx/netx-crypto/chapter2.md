---
title: Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX Crypto
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika kryptograficznego NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e04ea357c4e24f28d15f4f141bc001d4bbe8ac06bb641e10a7bd81653e60fda
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796771"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>Rozdział 2 — Instalowanie i używanie oprogramowania Azure RTOS NetX Crypto

W tym rozdziale opisano instalację, konfigurację i użycie składnika Azure RTOS NetX Crypto.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS kryptograficzne NetX są dostępne na stronie [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera pliki źródłowe, pliki dołączane i plik PDF zawierający ten dokument w następujący sposób:

- **nx_crypto.h:** moduł NetX Crypto pliku nagłówkowego publicznego interfejsu API
- **nx_crypto_*.c/h:** pliki źródłowe C/H dla programu NetX Crypto
- **nx_crypto_port.h:** plik nagłówkowy C zawierający wszystkie narzędzia deweloperskich i docelowych określonych definicji danych i struktur.
- **NetX_Crypto_User_Guide.pdf:** opis PDF modułu kryptograficznego NetX.

## <a name="netx-crypto-installation"></a>Instalacja kryptograficzna NetX

Cała wymieniona wcześniej dystrybucja jest dostępna w katalogu **crypto_libraries,** który znajduje się na poziomie głównym repozytorium NetX Duo.

Aby można było korzystać z usługi NetX Crypto, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana na ten sam poziom katalogu, na którym zainstalowano program NetX. Jeśli na przykład netx jest zainstalowany w katalogu "\threadx\arm7\NetX", wówczas nx_crypto *.* katalogi powinny zostać skopiowane do katalogu "\threadx\arm7\NetXCrypto".

Aby kryptografia NetX była używana w trybie autonomicznym, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do projektu aplikacji. Na przykład **crypto_libraries** katalog powinien zostać skopiowany do projektu aplikacji lub projektu biblioteki z katalogiem **crypto_libraries** powinien zostać utworzony i połączony z projektem aplikacji. 

## <a name="using-netx-crypto"></a>Korzystanie z usługi NetX Crypto

Kod aplikacji musi zawierać *nx_crypto.h.*  Po *nx_crypto.h* kod aplikacji może następnie wykonać wywołania funkcji Kryptograficzne NetX określone w dalszej części tego przewodnika.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji tworzenia usług Kryptograficznych NetX. Poniżej znajduje się lista wszystkich opcji, gdzie każda z nich jest szczegółowo opisana:

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE:** zdefiniowana, ta opcja zapewnia oczekiwaną maksymalną wartość modulo RSA w bitach. Wartość domyślna to 4096 dla modulo 4096-bitowego. Inne wartości to 3072, 2048 lub 1024 (nie jest to zalecane).
- **NX_CRYPTO_SELF_TEST:** zdefiniowane, umożliwia samodzielne testy modułu NetX Crypto. **NX_CRYPTO_FIPS** symbol jest teraz przestarzały i zmieniono jego nazwę na **NX_CRYPTO_SELF_TEST**
- **NX_CRYPTO_STANDALONE_ENABLE:** Zdefiniowane umożliwia korzystanie z kryptografii NetX w trybie autonomicznym (bez Azure RTOS). Domyślnie ten symbol nie jest zdefiniowany.
