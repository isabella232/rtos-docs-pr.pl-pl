---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO LevelX
description: Instalacja i użycie programu LevelX są proste i opisane w poniższych sekcjach tego rozdziału.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 575776875452cfc718401556a6440d787cb18893
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822969"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO LevelX

Instalacja i użycie usługi Azure RTO LevelX jest proste i opisane w poniższych sekcjach tego rozdziału.

## <a name="distribution"></a>Dystrybucja

LevelX jest dystrybuowana w standardzie ANSI C, gdzie każda funkcja jest zawarta w osobnym pliku C. Pliki w dystrybucji LevelX są następujące.
- lx_api. h
- lx_nand_flash_256byte_ecc_check. c
- lx_nand_flash_256byte_ecc_compute. c
- lx_nand_flash_block_full_update. c
- lx_nand_flash_block_reclaim. c
- lx_nand_flash_close. c
- lx_nand_flash_defragment. c  
- lx_nand_flash_extended_cache_enable. c
- lx_nand_flash_initialize. c
- lx_nand_flash_logical_sector_find. c
- lx_nand_flash_next_block_to_erase_find. c
- lx_nand_flash_open. c
- lx_nand_flash_page_ecc_check. c
- lx_nand_flash_page_ecc_compute. c  
- lx_nand_flash_partial_defragment. c
- lx_nand_flash_physical_page_allocate. c
- lx_nand_flash_sector_mapping_cache_invalidate. c
- lx_nand_flash_sector_read. c
- lx_nand_flash_sector_release. c
- lx_nand_flash_sector_write. c
- lx_nand_flash_system_error. c
- lx_nor_flash_block_reclaim. c
- lx_nor_flash_close. c
- lx_nor_flash_defragment. c  
- lx_nor_flash_extended_cache_enable. c
- lx_nor_flash_initialize. c
- lx_nor_flash_logical_sector_find. c
- lx_nor_flash_next_block_to_erase_find. c
- lx_nor_flash_open. c
- lx_nor_flash_partial_defragment. c
- lx_nor_flash_physical_sector_allocate. c
- lx_nor_flash_sector_mapping_cache_invalidate. c
- lx_nor_flash_sector_read. c
- lx_nor_flash_sector_release. c
- lx_nor_flash_sector_write. c
- lx_nor_flash_system_error. c

Dostępne są również przykłady sterowników i FileX dla LevelX ni i i wystąpień.

- demo_filex_nand_flash. c  
- fx_nand_flash_simulated_driver. c
- lx_nand_flash_simulator. c
- demo_filex_nor_flash. c  
- fx_nor_flash_simulated_driver. c
- lx_nor_flash_simulator. c

Oczywiście, jeśli tylko ni flash jest wymagany, wymagane są tylko pliki Flash ni LevelX (***lx_nand_ \* . c***). Podobnie, jeśli wymagany jest tylko plik lub Flash (* *_lx_nor_ \_ . c * * *).

## <a name="configuration-options"></a>Opcje konfiguracji

LevelX można skonfigurować w czasie kompilacji za pośrednictwem warunku zdefiniowanego poniżej. Wystarczy dodać odpowiednie polecenie Definiuj do kompilacji każdego źródła LevelX, aby można było użyć opcji.

- **LX_DIRECT_READ**: zdefiniowane, ta opcja pomija procedurę odczytu lub sterownika programu Flash w celu zapełnienia lub odczytywania bezwolnej pamięci, co znacznie zwiększa wydajność.
- **LX_FREE_SECTOR_DATA_VERIFY**: zdefiniowane, spowoduje to, że LevelX i niezależne od wystąpień logikę można zweryfikować bezpłatnie, ani sektorów.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: Domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektora logicznego. Duże wartości zwiększają wydajność, ale kosztem pamięci. Minimalny rozmiar to 8, a wszystkie wartości muszą być potęgą liczby 2.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: zdefiniowane, spowoduje to utworzenie bezpośredniej pamięci podręcznej mapowania, tak że nie ma żadnych chybień w pamięci podręcznej. Wymaga również, aby LX_NAND_SECTOR_MAPPING_CACHE_SIZE reprezentuje dokładną liczbę stron na urządzeniu Flash.
- **LX_NOR_DISABLE_EXTENDED_CACHE**: zdefiniowane, wyłączono rozszerzoną pamięć podręczną.
- **LX_NOR_EXTENDED_CACHE_SIZE**: Domyślnie ta wartość to 8, która reprezentuje maksymalnie 8 sektorów, które mogą być buforowane w wystąpieniu i.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: Domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektora logicznego. Duże wartości zwiększają wydajność, ale kosztem pamięci. Minimalny rozmiar to 8, a wszystkie wartości muszą być potęgą liczby 2.
- **LX_THREAD_SAFE_ENABLE**: zdefiniowane, sprawia, że LevelX bezpieczne wątki przy użyciu obiektu mutex ThreadX w całym interfejsie API.

## <a name="using-levelx"></a>Korzystanie z LevelX

Aby użyć LevelX, albo samodzielnie lub z FileX, Uwzględnij plik ***lx_api. h** _ w kodzie, który odwołuje się do interfejsu API LevelX. Upewnij się również, że kod obiektu LevelX jest dostępny w czasie łącza. Zapoznaj się z plikami _*_demo_filex_nand_flash. c_*_ i _ *_demo_filex_nor_flash. c_**, aby poznać przykłady użycia LevelX.
