---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS LevelX
description: Instalacja i używanie oprogramowania LevelX jest proste i opisane w poniższych sekcjach tego rozdziału.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cfd2d616896e1797114e55abcaf1a7559685282f29c2d0dee8274d2a26ea8f0e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790313"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS LevelX

Instalacja i korzystanie z Azure RTOS LevelX jest proste i opisane w poniższych sekcjach tego rozdziału.

## <a name="distribution"></a>Dystrybucja

LevelX jest dystrybuowany w języku ANSI C, gdzie każda funkcja znajduje się we własnym oddzielnym pliku C. Pliki w dystrybucji LevelX są następujące.
- lx_api.h
- lx_nand_flash_256byte_ecc_check.c
- lx_nand_flash_256byte_ecc_compute.c
- lx_nand_flash_block_full_update.c
- lx_nand_flash_block_reclaim.c
- lx_nand_flash_close.c
- lx_nand_flash_defragment.c  
- lx_nand_flash_extended_cache_enable.c
- lx_nand_flash_initialize.c
- lx_nand_flash_logical_sector_find.c
- lx_nand_flash_next_block_to_erase_find.c
- lx_nand_flash_open.c
- lx_nand_flash_page_ecc_check.c
- lx_nand_flash_page_ecc_compute.c  
- lx_nand_flash_partial_defragment.c
- lx_nand_flash_physical_page_allocate.c
- lx_nand_flash_sector_mapping_cache_invalidate.c
- lx_nand_flash_sector_read.c
- lx_nand_flash_sector_release.c
- lx_nand_flash_sector_write.c
- lx_nand_flash_system_error.c
- lx_nor_flash_block_reclaim.c
- lx_nor_flash_close.c
- lx_nor_flash_defragment.c  
- lx_nor_flash_extended_cache_enable.c
- lx_nor_flash_initialize.c
- lx_nor_flash_logical_sector_find.c
- lx_nor_flash_next_block_to_erase_find.c
- lx_nor_flash_open.c
- lx_nor_flash_partial_defragment.c
- lx_nor_flash_physical_sector_allocate.c
- lx_nor_flash_sector_mapping_cache_invalidate.c
- lx_nor_flash_sector_read.c
- lx_nor_flash_sector_release.c
- lx_nor_flash_sector_write.c
- lx_nor_flash_system_error.c

Dostępne są również przykłady sterowników Symulator i FileX dla wystąpień levelX NAND i NOR w następujący sposób.

- demo_filex_nand_flash.c  
- fx_nand_flash_simulated_driver.c
- lx_nand_flash_simulator.c
- demo_filex_nor_flash.c  
- fx_nor_flash_simulated_driver.c
- lx_nor_flash_simulator.c

Oczywiście jeśli wymagana jest tylko flash NAND, potrzebne są tylko pliki flash NaND LevelX (***lx_nand_ \* .c).*** Podobnie, jeśli wymagany jest tylko flash NOR, wymagane są tylko pliki flash NOR (**_lx_nor_ \_ .c!).

## <a name="configuration-options"></a>Opcje konfiguracji

LevelX można skonfigurować w czasie kompilacji za pomocą opisanych poniżej zdefiniowania warunkowego. Po prostu dodaj żądaną definicję do kompilacji każdego źródła LevelX, aby użyć opcji .

- **LX_DIRECT_READ:** zdefiniowana, ta opcja pomija procedurę odczytu sterownika flash NOR na korzyść lub bezpośrednie odczytywanie pamięci NOR, co powoduje znaczący wzrost wydajności.
- **LX_FREE_SECTOR_DATA_VERIFY:** Zdefiniowane, powoduje to, że otwarta logika LevelX NOR wystąpienia sprawdza, czy wszystkie sektory NIE są wolnymi sektorami.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE:** domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektorów logicznych. Duże wartości poprawiają wydajność, ale kosztują pamięć. Minimalny rozmiar to 8, a wszystkie wartości muszą mieć potęgę 2.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE:** zdefiniowane, powoduje utworzenie pamięci podręcznej mapowania bezpośredniego, tak aby nie było żadnych chybień pamięci podręcznej. Wymagane jest również, LX_NAND_SECTOR_MAPPING_CACHE_SIZE reprezentuje dokładną liczbę wszystkich stron na urządzeniu flash.
- **LX_NOR_DISABLE_EXTENDED_CACHE:** zdefiniowane, to wyłączyło rozszerzoną pamięć podręczną NOR.
- **LX_NOR_EXTENDED_CACHE_SIZE:** domyślnie ta wartość to 8, która reprezentuje maksymalnie 8 sektorów, które mogą być buforowane w wystąpieniu NOR.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE:** domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektorów logicznych. Duże wartości poprawiają wydajność, ale kosztują pamięć. Minimalny rozmiar to 8, a wszystkie wartości muszą mieć potęgę 2.
- **LX_THREAD_SAFE_ENABLE:** zdefiniowane, dzięki temu poziomX jest bezpieczny wątkowo przy użyciu obiektu mutex ThreadX w całym interfejsie API.
- **LX_STANDALONE_ENABLE:** zdefiniowane, umożliwia korzystanie z levelX w trybie autonomicznym (bez Azure RTOS). Domyślnie ten symbol nie jest zdefiniowany.

> [!IMPORTANT]
> W przypadku korzystania z bibliotek LevelX w trybie **autonomicznym (LX_STANDALONE_ENABLE** musi być zdefiniowany), pliki/biblioteki ThreadX nie są wymagane. Funkcja bezpiecznej wątkowo funkcji LevelX jest wyłączona w tym trybie.

## <a name="using-levelx"></a>Korzystanie z levelX

Aby użyć levelX, samodzielnie lub z FileX, należy dołączyć plik ***lx_api.h** _ w kodzie, który odwołuje się do interfejsu API LevelX. Upewnij się również, że kod obiektu LevelX jest dostępny w czasie łączenia. Zapoznaj się z _*_plikami demo_filex_nand_flash.c_*_ i _ *_demo_filex_nor_flash.c_**, aby uzyskać przykłady użycia levelX.
