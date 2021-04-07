---
title: Dodatek-przykłady dotyczące portów
description: W tym artykule przedstawiono przykłady specyficzne dla portów dla modułów ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c2324a2057bf2ddb2d255b2ff611d34fc664560a
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549814"
---
# <a name="appendix---port-specific-examples"></a><span data-ttu-id="f335e-103">Dodatek-przykłady dotyczące portów</span><span class="sxs-lookup"><span data-stu-id="f335e-103">Appendix - Port-specific examples</span></span>

## <a name="arm11-processor"></a><span data-ttu-id="f335e-104">Procesor ARM11</span><span class="sxs-lookup"><span data-stu-id="f335e-104">ARM11 processor</span></span>

### <a name="arm11-using-gcc"></a><span data-ttu-id="f335e-105">ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-105">ARM11 using GCC</span></span>

#### <a name="module-preamble-for-arm11-using-gcc"></a><span data-ttu-id="f335e-106">Preambuła modułu dla ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-106">Module preamble for ARM11 using GCC</span></span>

```armasm
    .arm
    .section .preamble, "ax"

    /* Define the module preamble.  */

    .global _txm_module_preamble
_txm_module_preamble:
    .word       0x4D4F4455                                      @ Module ID
    .word       0x5                                             @ Module Major Version
    .word       0x6                                             @ Module Minor Version
    .word       32                                              @ Module Preamble Size in 32-bit words
    .word       0x12345678                                      @ Module ID (application defined)
    .word       0x02000000                                      @ Module Properties where:
                                                                @   Bits 31-24: Compiler ID
                                                                @           0 -> IAR
                                                                @           1 -> ARM
                                                                @           2 -> GNU
    .word       _txm_module_thread_shell_entry - . - 0          @ Module Shell Entry Point
    .word       demo_module_start - . - 0                       @ Module Start Thread Entry Point
    .word       0                                               @ Module Stop Thread Entry Point
    .word       1                                               @ Module Start/Stop Thread Priority
    .word       1024                                            @ Module Start/Stop Thread Stack Size
    .word       _txm_module_callback_request_thread_entry - . - 0   @ Module Callback Thread Entry
    .word       1                                               @ Module Callback Thread Priority
    .word       1024                                            @ Module Callback Thread Stack Size
    .word       __code_size__                                   @ Module Code Size
    .word       __data_size__                                   @ Module Data Size
    .word       0                                               @ Reserved 0
    .word       0                                               @ Reserved 1
    .word       0                                               @ Reserved 2
    .word       0                                               @ Reserved 3
    .word       0                                               @ Reserved 4
    .word       0                                               @ Reserved 5
    .word       0                                               @ Reserved 6
    .word       0                                               @ Reserved 7  
    .word       0                                               @ Reserved 8  
    .word       0                                               @ Reserved 9
    .word       0                                               @ Reserved 10
    .word       0                                               @ Reserved 11
    .word       0                                               @ Reserved 12
    .word       0                                               @ Reserved 13
    .word       0                                               @ Reserved 14
    .word       0                                               @ Reserved 15
```

#### <a name="module-properties-for-arm11-using-gcc"></a><span data-ttu-id="f335e-107">Właściwości modułu dla ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-107">Module properties for ARM11 using GCC</span></span>

| <span data-ttu-id="f335e-108">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-108">Bit</span></span> | <span data-ttu-id="f335e-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-109">Value</span></span> | <span data-ttu-id="f335e-110">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-110">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-111">[23-0]</span><span class="sxs-lookup"><span data-stu-id="f335e-111">[23-0]</span></span> | <span data-ttu-id="f335e-112">0</span><span class="sxs-lookup"><span data-stu-id="f335e-112">0</span></span> | <span data-ttu-id="f335e-113">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-113">Reserved</span></span>
| <span data-ttu-id="f335e-114">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-114">[31-24]</span></span> | <br /><span data-ttu-id="f335e-115">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-115">0x00</span></span><br /><span data-ttu-id="f335e-116">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-116">0x01</span></span><br /><span data-ttu-id="f335e-117">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-117">0x02</span></span> | <span data-ttu-id="f335e-118">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-118">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-119">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-119">IAR</span></span><br /><span data-ttu-id="f335e-120">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-120">ARM</span></span><br /><span data-ttu-id="f335e-121">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-121">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-gcc"></a><span data-ttu-id="f335e-122">Konsolidator modułu dla ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-122">Module linker for ARM11 using GCC</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x080F0000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0x64001800, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x080F0000;
  __FLASH_segment_end__   = 0x080FFFFF;
  __RAM_segment_start__   = 0x64001800;
  __RAM_segment_end__     = 0x64011800;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  }
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);

  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-arm11-using-gcc"></a><span data-ttu-id="f335e-123">Kompilowanie modułów dla ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-123">Building Modules for ARM11 using GCC</span></span>

<span data-ttu-id="f335e-124">Prosty przykład wiersza polecenia służący do kompilowania modułu ARM11 przy użyciu programu w zatoce:</span><span class="sxs-lookup"><span data-stu-id="f335e-124">A simple command-line example for building an ARM11 module using GCC:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 txm_module_preamble.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 demo_threadx_module.c
arm-none-eabi-ld -A arm1136j-s -T demo_threadx_module.ld txm_module_preamble.o gcc_setup.o demo_threadx_module.o txm.a txm.a -o demo_threadx_module.out -M > demo_threadx_module.map
```

#### <a name="thread-extension-definition-for-arm11-using-gcc"></a><span data-ttu-id="f335e-125">Definicja rozszerzenia wątku dla ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-125">Thread extension definition for ARM11 using GCC</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-gcc"></a><span data-ttu-id="f335e-126">Kompilowanie Menedżera modułów dla ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-126">Building Module Manager for ARM11 using GCC</span></span>

<span data-ttu-id="f335e-127">Nie podano przykładu.</span><span class="sxs-lookup"><span data-stu-id="f335e-127">No example is provided.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-gcc"></a><span data-ttu-id="f335e-128">Atrybuty pamięci zewnętrznej Włączanie interfejsu API dla ARM11 przy użyciu programu w zatoce</span><span class="sxs-lookup"><span data-stu-id="f335e-128">Attributes for external memory enable API for ARM11 using GCC</span></span>

<span data-ttu-id="f335e-129">Ta funkcja nie jest włączona na tym porcie.</span><span class="sxs-lookup"><span data-stu-id="f335e-129">This feature not enabled on this port.</span></span>

### <a name="arm11-using-ac5"></a><span data-ttu-id="f335e-130">ARM11 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-130">ARM11 using AC5</span></span>

#### <a name="module-preamble-for-arm11-using-ac5"></a><span data-ttu-id="f335e-131">Preambuła modułu dla ARM11 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-131">Module preamble for ARM11 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|

__txm_module_preamble
        DCD       0x4D4F4455                                        ; Module ID
        DCD       0x5                                               ; Module Major Version
        DCD       0x3                                               ; Module Minor Version
        DCD       32                                                ; Module Preamble Size in 32-bit words
        DCD       0x12345678                                        ; Module ID (application defined)
        DCD       0x01000000                                        ; Module Properties where:
                                                                    ;   Bits 31-24: Compiler ID
                                                                    ;           0 -> IAR
                                                                    ;           1 -> ARM
                                                                    ;           2 -> GNU
                                                                    ;   Bits 23-0:  Reserved
        DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
        DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
        DCD       0                                                 ; Module Stop Thread Entry Point
        DCD       1                                                 ; Module Start/Stop Thread Priority
        DCD       1024                                              ; Module Start/Stop Thread Stack Size
        DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
        DCD       1                                                 ; Module Callback Thread Priority
        DCD       1024                                              ; Module Callback Thread Stack Size
        DCD       |Image$$ER_RO$$Length|                            ; Module Code Size
        DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
        DCD       0                                                 ; Reserved 0
        DCD       0                                                 ; Reserved 1
        DCD       0                                                 ; Reserved 2
        DCD       0                                                 ; Reserved 3
        DCD       0                                                 ; Reserved 4
        DCD       0                                                 ; Reserved 5
        DCD       0                                                 ; Reserved 6
        DCD       0                                                 ; Reserved 7
        DCD       0                                                 ; Reserved 8  
        DCD       0                                                 ; Reserved 9
        DCD       0                                                 ; Reserved 10
        DCD       0                                                 ; Reserved 11
        DCD       0                                                 ; Reserved 12
        DCD       0                                                 ; Reserved 13
        DCD       0                                                 ; Reserved 14
        DCD       0                                                 ; Reserved 15

        END
```

#### <a name="module-properties-for-arm11-using-ac5"></a><span data-ttu-id="f335e-132">Właściwości modułu dla ARM11 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-132">Module properties for ARM11 using AC5</span></span>

| <span data-ttu-id="f335e-133">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-133">Bit</span></span> | <span data-ttu-id="f335e-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-134">Value</span></span> | <span data-ttu-id="f335e-135">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-135">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-136">[23-0]</span><span class="sxs-lookup"><span data-stu-id="f335e-136">[23-0]</span></span> | <span data-ttu-id="f335e-137">0</span><span class="sxs-lookup"><span data-stu-id="f335e-137">0</span></span> | <span data-ttu-id="f335e-138">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-138">Reserved</span></span>
| <span data-ttu-id="f335e-139">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-139">[31-24]</span></span> | <br /><span data-ttu-id="f335e-140">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-140">0x00</span></span><br /><span data-ttu-id="f335e-141">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-141">0x01</span></span><br /><span data-ttu-id="f335e-142">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-142">0x02</span></span> | <span data-ttu-id="f335e-143">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-143">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-144">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-144">IAR</span></span><br /><span data-ttu-id="f335e-145">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-145">ARM</span></span><br /><span data-ttu-id="f335e-146">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-146">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-ac5"></a><span data-ttu-id="f335e-147">Konsolidator modułu dla ARM11 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-147">Module linker for ARM11 using AC5</span></span>

<span data-ttu-id="f335e-148">Kompilacja oparta na wierszu polecenia nie ma przykładu pliku konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="f335e-148">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-arm11-using-ac5"></a><span data-ttu-id="f335e-149">Kompilowanie modułów dla ARM11 za pomocą AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-149">Building Modules for ARM11 using AC5</span></span>

<span data-ttu-id="f335e-150">Prosty przykład wiersza polecenia do kompilowania modułu ARM11 za pomocą AC5:</span><span class="sxs-lookup"><span data-stu-id="f335e-150">A simple command-line example for building an ARM11 module using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi txm_module_preamble.s
armcc -g -c -O0 --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-arm11-using-ac5"></a><span data-ttu-id="f335e-151">Definicja rozszerzenia wątku dla ARM11 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-151">Thread extension definition for ARM11 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-ac5"></a><span data-ttu-id="f335e-152">Kompilowanie Menedżera modułów dla ARM11 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-152">Building Module Manager for ARM11 using AC5</span></span>

<span data-ttu-id="f335e-153">Prosty przykład wiersza polecenia służący do tworzenia Menedżera modułów ARM11 za pomocą AC5:</span><span class="sxs-lookup"><span data-stu-id="f335e-153">A simple command-line example for building an ARM11 module manager using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork tx_initialize_low_level.s
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork demo_threadx_module_manager.c
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0 --first tx_initialize_low_level.o(Init) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-ac5"></a><span data-ttu-id="f335e-154">Atrybuty pamięci zewnętrznej Włącz interfejs API dla ARM11 za pomocą AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-154">Attributes for external memory enable API for ARM11 using AC5</span></span>

<span data-ttu-id="f335e-155">Ta funkcja nie jest włączona na tym porcie.</span><span class="sxs-lookup"><span data-stu-id="f335e-155">This feature not enabled on this port.</span></span>

## <a name="cortex-a7-processor"></a><span data-ttu-id="f335e-156">Procesor Cortex-z</span><span class="sxs-lookup"><span data-stu-id="f335e-156">Cortex-A7 processor</span></span>

### <a name="cortex-a7-using-ac5"></a><span data-ttu-id="f335e-157">Cortex-Wykorzystaj AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-157">Cortex-A7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-a7-using-ac5"></a><span data-ttu-id="f335e-158">Preambuła modułu dla Cortex-Object przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-158">Module preamble for Cortex-A7 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD       0x4D4F4455                                        ; Module ID
    DCD       0x5                                               ; Module Major Version
    DCD       0x3                                               ; Module Minor Version
    DCD       32                                                ; Module Preamble Size in 32-bit words
    DCD       0x12345678                                        ; Module ID (application defined)
    DCD       0x01000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1:  Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                ;           1 -> User mode execution (MMU protection)
    DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
    DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
    DCD       0                                                 ; Module Stop Thread Entry Point
    DCD       1                                                 ; Module Start/Stop Thread Priority
    DCD       1024                                              ; Module Start/Stop Thread Stack Size
    DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD       1                                                 ; Module Callback Thread Priority
    DCD       1024                                              ; Module Callback Thread Stack Size
    DCD       |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|   ; Module Code Size
    DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
    DCD       0                                                 ; Reserved 0
    DCD       0                                                 ; Reserved 1
    DCD       0                                                 ; Reserved 2
    DCD       0                                                 ; Reserved 3
    DCD       0                                                 ; Reserved 4
    DCD       0                                                 ; Reserved 5
    DCD       0                                                 ; Reserved 6
    DCD       0                                                 ; Reserved 7
    DCD       0                                                 ; Reserved 8
    DCD       0                                                 ; Reserved 9
    DCD       0                                                 ; Reserved 10
    DCD       0                                                 ; Reserved 11
    DCD       0                                                 ; Reserved 12
    DCD       0                                                 ; Reserved 13
    DCD       0                                                 ; Reserved 14
    DCD       0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-a7-using-ac5"></a><span data-ttu-id="f335e-159">Właściwości modułu dla Cortex-wyniesień przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-159">Module properties for Cortex-A7 using AC5</span></span>

| <span data-ttu-id="f335e-160">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-160">Bit</span></span> | <span data-ttu-id="f335e-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-161">Value</span></span> | <span data-ttu-id="f335e-162">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-162">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-163">0</span><span class="sxs-lookup"><span data-stu-id="f335e-163">0</span></span> | <span data-ttu-id="f335e-164">0</span><span class="sxs-lookup"><span data-stu-id="f335e-164">0</span></span><br /><span data-ttu-id="f335e-165">1</span><span class="sxs-lookup"><span data-stu-id="f335e-165">1</span></span> | <span data-ttu-id="f335e-166">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-166">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-167">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-167">User mode execution</span></span> |
| <span data-ttu-id="f335e-168">[23-1]</span><span class="sxs-lookup"><span data-stu-id="f335e-168">[23-1]</span></span> | <span data-ttu-id="f335e-169">0</span><span class="sxs-lookup"><span data-stu-id="f335e-169">0</span></span> | <span data-ttu-id="f335e-170">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-170">Reserved</span></span>
| <span data-ttu-id="f335e-171">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-171">[31-24]</span></span> | <br /><span data-ttu-id="f335e-172">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-172">0x00</span></span><br /><span data-ttu-id="f335e-173">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-173">0x01</span></span><br /><span data-ttu-id="f335e-174">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-174">0x02</span></span> | <span data-ttu-id="f335e-175">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-175">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-176">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-176">IAR</span></span><br /><span data-ttu-id="f335e-177">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-177">ARM</span></span><br /><span data-ttu-id="f335e-178">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-178">GNU</span></span> |

#### <a name="module-linker-for-cortex-a7-using-ac5"></a><span data-ttu-id="f335e-179">Konsolidator modułu dla Cortex-Object przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-179">Module linker for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f335e-180">Kompilacja oparta na wierszu polecenia nie ma przykładu pliku konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="f335e-180">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-a7-using-ac5"></a><span data-ttu-id="f335e-181">Kompilowanie modułów dla Cortex-Object przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-181">Building Modules for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f335e-182">Prosty przykład wiersza polecenia do kompilowania modułu Cortex-ODP przy użyciu AC5:</span><span class="sxs-lookup"><span data-stu-id="f335e-182">A simple command-line example for building a Cortex-A7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-a7.no_neon --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-a7-using-ac5"></a><span data-ttu-id="f335e-183">Definicja rozszerzenia wątku dla Cortex-o AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-183">Thread extension definition for Cortex-A7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-a7-using-ac5"></a><span data-ttu-id="f335e-184">Kompilowanie Menedżera modułów dla Cortex-Object przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-184">Building Module Manager for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f335e-185">Prosty przykład wiersza polecenia do kompilowania Menedżera modułów Cortex-ODP przy użyciu AC5:</span><span class="sxs-lookup"><span data-stu-id="f335e-185">A simple command-line example for building a Cortex-A7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x80000000 --first tx_initialize_low_level.o(VECTORS) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-a7-using-ac5"></a><span data-ttu-id="f335e-186">Atrybuty dla pamięci zewnętrznej Włącz interfejs API dla Cortex-wyniesień przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-186">Attributes for external memory enable API for Cortex-A7 using AC5</span></span>

<span data-ttu-id="f335e-187">Następujące atrybuty mogą służyć do konfigurowania ustawień pamięci współużytkowanej:</span><span class="sxs-lookup"><span data-stu-id="f335e-187">The following attributes can be used to set up shared memory settings:</span></span>

| <span data-ttu-id="f335e-188">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-188">Attribute parameter</span></span> | <span data-ttu-id="f335e-189">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-189">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-190">TXM_MMU_ATTRIBUTE_XN</span><span class="sxs-lookup"><span data-stu-id="f335e-190">TXM_MMU_ATTRIBUTE_XN</span></span> | <span data-ttu-id="f335e-191">Wykonaj nigdy</span><span class="sxs-lookup"><span data-stu-id="f335e-191">Execute Never</span></span> |
| <span data-ttu-id="f335e-192">TXM_MMU_ATTRIBUTE_B</span><span class="sxs-lookup"><span data-stu-id="f335e-192">TXM_MMU_ATTRIBUTE_B</span></span> | <span data-ttu-id="f335e-193">Ustawienia B</span><span class="sxs-lookup"><span data-stu-id="f335e-193">B setting</span></span> |
| <span data-ttu-id="f335e-194">TXM_MMU_ATTRIBUTE_C</span><span class="sxs-lookup"><span data-stu-id="f335e-194">TXM_MMU_ATTRIBUTE_C</span></span> | <span data-ttu-id="f335e-195">Ustawienie języka C</span><span class="sxs-lookup"><span data-stu-id="f335e-195">C setting</span></span> |
| <span data-ttu-id="f335e-196">TXM_MMU_ATTRIBUTE_AP</span><span class="sxs-lookup"><span data-stu-id="f335e-196">TXM_MMU_ATTRIBUTE_AP</span></span> | <span data-ttu-id="f335e-197">Ustawienie AP</span><span class="sxs-lookup"><span data-stu-id="f335e-197">AP setting</span></span> |
| <span data-ttu-id="f335e-198">TXM_MMU_ATTRIBUTE_TEX</span><span class="sxs-lookup"><span data-stu-id="f335e-198">TXM_MMU_ATTRIBUTE_TEX</span></span> | <span data-ttu-id="f335e-199">Ustawienie TEX</span><span class="sxs-lookup"><span data-stu-id="f335e-199">TEX setting</span></span> |

<span data-ttu-id="f335e-200">Aby uzyskać informacje na temat konfiguracji tych ustawień, zobacz dokumentację usługi ARM.</span><span class="sxs-lookup"><span data-stu-id="f335e-200">See ARM documentation for how these settings are configured.</span></span>

## <a name="cortex-m3-processor"></a><span data-ttu-id="f335e-201">Procesor Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="f335e-201">Cortex-M3 processor</span></span>

### <a name="cortex-m3-using-ac5"></a><span data-ttu-id="f335e-202">Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-202">Cortex-M3 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac5"></a><span data-ttu-id="f335e-203">Preambuła modułu dla Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-203">Module preamble for Cortex-M3 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x6                                                 ; Module Major Version
    DCD     0x1                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m3-using-ac5"></a><span data-ttu-id="f335e-204">Właściwości modułu dla Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-204">Module properties for Cortex-M3 using AC5</span></span>

| <span data-ttu-id="f335e-205">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-205">Bit</span></span> | <span data-ttu-id="f335e-206">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-206">Value</span></span> | <span data-ttu-id="f335e-207">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-207">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-208">0</span><span class="sxs-lookup"><span data-stu-id="f335e-208">0</span></span> | <span data-ttu-id="f335e-209">0</span><span class="sxs-lookup"><span data-stu-id="f335e-209">0</span></span><br /><span data-ttu-id="f335e-210">1</span><span class="sxs-lookup"><span data-stu-id="f335e-210">1</span></span> | <span data-ttu-id="f335e-211">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-211">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-212">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-212">User mode execution</span></span> |
| <span data-ttu-id="f335e-213">1</span><span class="sxs-lookup"><span data-stu-id="f335e-213">1</span></span> | <span data-ttu-id="f335e-214">0</span><span class="sxs-lookup"><span data-stu-id="f335e-214">0</span></span><br /><span data-ttu-id="f335e-215">1</span><span class="sxs-lookup"><span data-stu-id="f335e-215">1</span></span> | <span data-ttu-id="f335e-216">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-216">No MPU protection</span></span><br /><span data-ttu-id="f335e-217">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-217">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-218">2</span><span class="sxs-lookup"><span data-stu-id="f335e-218">2</span></span> | <span data-ttu-id="f335e-219">0</span><span class="sxs-lookup"><span data-stu-id="f335e-219">0</span></span><br /><span data-ttu-id="f335e-220">1</span><span class="sxs-lookup"><span data-stu-id="f335e-220">1</span></span> | <span data-ttu-id="f335e-221">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-221">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-222">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-222">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-223">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-223">[23-3]</span></span> | <span data-ttu-id="f335e-224">0</span><span class="sxs-lookup"><span data-stu-id="f335e-224">0</span></span> | <span data-ttu-id="f335e-225">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-225">Reserved</span></span>
| <span data-ttu-id="f335e-226">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-226">[31-24]</span></span> | <br /><span data-ttu-id="f335e-227">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-227">0x00</span></span><br /><span data-ttu-id="f335e-228">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-228">0x01</span></span><br /><span data-ttu-id="f335e-229">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-229">0x02</span></span> | <span data-ttu-id="f335e-230">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-230">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-231">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-231">IAR</span></span><br /><span data-ttu-id="f335e-232">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-232">ARM</span></span><br /><span data-ttu-id="f335e-233">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-233">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac5"></a><span data-ttu-id="f335e-234">Konsolidator modułu dla Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-234">Module linker for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f335e-235">Nie podano przykładowego pliku konsolidatora; Konsolidacja jest wykonywana w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f335e-235">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="f335e-236">Zobacz następną sekcję.</span><span class="sxs-lookup"><span data-stu-id="f335e-236">See next section.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac5"></a><span data-ttu-id="f335e-237">Kompilowanie modułów dla Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-237">Building Modules for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f335e-238">Przykładowy skrypt kompilacji jest dostępny:</span><span class="sxs-lookup"><span data-stu-id="f335e-238">An example build script is provided:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m3 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m3-using-ac5"></a><span data-ttu-id="f335e-239">Definicja rozszerzenia wątku dla Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-239">Thread extension definition for Cortex-M3 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac5"></a><span data-ttu-id="f335e-240">Kompilowanie Menedżera modułów dla Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-240">Building Module Manager for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f335e-241">Zobacz przykład build_threadx_module_manager_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-241">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m3 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac5"></a><span data-ttu-id="f335e-242">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M3 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-242">Attributes for external memory enable API for Cortex-M3 using AC5</span></span>

<span data-ttu-id="f335e-243">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-243">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-244">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-244">Attribute parameter</span></span> | <span data-ttu-id="f335e-245">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-245">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-247">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-247">Write access</span></span> |

### <a name="cortex-m3-using-ac6"></a><span data-ttu-id="f335e-248">Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-248">Cortex-M3 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac6"></a><span data-ttu-id="f335e-249">Preambuła modułu dla Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-249">Module preamble for Cortex-M3 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m3-using-ac6"></a><span data-ttu-id="f335e-250">Właściwości modułu dla Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-250">Module properties for Cortex-M3 using AC6</span></span>

| <span data-ttu-id="f335e-251">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-251">Bit</span></span> | <span data-ttu-id="f335e-252">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-252">Value</span></span> | <span data-ttu-id="f335e-253">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-253">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-254">0</span><span class="sxs-lookup"><span data-stu-id="f335e-254">0</span></span> | <span data-ttu-id="f335e-255">0</span><span class="sxs-lookup"><span data-stu-id="f335e-255">0</span></span><br /><span data-ttu-id="f335e-256">1</span><span class="sxs-lookup"><span data-stu-id="f335e-256">1</span></span> | <span data-ttu-id="f335e-257">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-257">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-258">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-258">User mode execution</span></span> |
| <span data-ttu-id="f335e-259">1</span><span class="sxs-lookup"><span data-stu-id="f335e-259">1</span></span> | <span data-ttu-id="f335e-260">0</span><span class="sxs-lookup"><span data-stu-id="f335e-260">0</span></span><br /><span data-ttu-id="f335e-261">1</span><span class="sxs-lookup"><span data-stu-id="f335e-261">1</span></span> | <span data-ttu-id="f335e-262">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-262">No MPU protection</span></span><br /><span data-ttu-id="f335e-263">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-263">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-264">2</span><span class="sxs-lookup"><span data-stu-id="f335e-264">2</span></span> | <span data-ttu-id="f335e-265">0</span><span class="sxs-lookup"><span data-stu-id="f335e-265">0</span></span><br /><span data-ttu-id="f335e-266">1</span><span class="sxs-lookup"><span data-stu-id="f335e-266">1</span></span> | <span data-ttu-id="f335e-267">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-267">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-268">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-268">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-269">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-269">[23-3]</span></span> | <span data-ttu-id="f335e-270">0</span><span class="sxs-lookup"><span data-stu-id="f335e-270">0</span></span> | <span data-ttu-id="f335e-271">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-271">Reserved</span></span>
| <span data-ttu-id="f335e-272">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-272">[31-24]</span></span> | <br /><span data-ttu-id="f335e-273">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-273">0x00</span></span><br /><span data-ttu-id="f335e-274">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-274">0x01</span></span><br /><span data-ttu-id="f335e-275">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-275">0x02</span></span> | <span data-ttu-id="f335e-276">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-276">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-277">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-277">IAR</span></span><br /><span data-ttu-id="f335e-278">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-278">ARM</span></span><br /><span data-ttu-id="f335e-279">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-279">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac6"></a><span data-ttu-id="f335e-280">Konsolidator modułu dla Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-280">Module linker for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f335e-281">Nie jest używany żaden plik konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="f335e-281">No linker file is used.</span></span> <span data-ttu-id="f335e-282">Zobacz ustawienia projektu.</span><span class="sxs-lookup"><span data-stu-id="f335e-282">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac6"></a><span data-ttu-id="f335e-283">Kompilowanie modułów dla Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-283">Building Modules for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f335e-284">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-284">An example workspace is provided.</span></span> <span data-ttu-id="f335e-285">Kompilowanie biblioteki ThreadX, biblioteki modułów ThreadX, przykładowego projektu modułu i przykładowego projektu Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="f335e-285">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-ac6"></a><span data-ttu-id="f335e-286">Definicja rozszerzenia wątku dla Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-286">Thread extension definition for Cortex-M3 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac6"></a><span data-ttu-id="f335e-287">Kompilowanie Menedżera modułów dla Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-287">Building Module Manager for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f335e-288">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-288">An example workspace is provided.</span></span> <span data-ttu-id="f335e-289">Kompilowanie biblioteki ThreadX, biblioteki modułów ThreadX, przykładowego projektu modułu i przykładowego projektu Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="f335e-289">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac6"></a><span data-ttu-id="f335e-290">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M3 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-290">Attributes for external memory enable API for Cortex-M3 using AC6</span></span>

<span data-ttu-id="f335e-291">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-291">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-292">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-292">Attribute parameter</span></span> | <span data-ttu-id="f335e-293">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-293">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-295">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-295">Write access</span></span> |

### <a name="cortex-m3-using-gnu"></a><span data-ttu-id="f335e-296">Cortex — M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-296">Cortex-M3 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m3-using-gnu"></a><span data-ttu-id="f335e-297">Preambuła modułu dla Cortex-M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-297">Module preamble for Cortex-M3 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15

```

#### <a name="module-properties-for-cortex-m3-using-gnu"></a><span data-ttu-id="f335e-298">Właściwości modułu dla Cortex-M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-298">Module properties for Cortex-M3 using GNU</span></span>

| <span data-ttu-id="f335e-299">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-299">Bit</span></span> | <span data-ttu-id="f335e-300">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-300">Value</span></span> | <span data-ttu-id="f335e-301">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-301">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-302">0</span><span class="sxs-lookup"><span data-stu-id="f335e-302">0</span></span> | <span data-ttu-id="f335e-303">0</span><span class="sxs-lookup"><span data-stu-id="f335e-303">0</span></span><br /><span data-ttu-id="f335e-304">1</span><span class="sxs-lookup"><span data-stu-id="f335e-304">1</span></span> | <span data-ttu-id="f335e-305">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-305">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-306">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-306">User mode execution</span></span> |
| <span data-ttu-id="f335e-307">1</span><span class="sxs-lookup"><span data-stu-id="f335e-307">1</span></span> | <span data-ttu-id="f335e-308">0</span><span class="sxs-lookup"><span data-stu-id="f335e-308">0</span></span><br /><span data-ttu-id="f335e-309">1</span><span class="sxs-lookup"><span data-stu-id="f335e-309">1</span></span> | <span data-ttu-id="f335e-310">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-310">No MPU protection</span></span><br /><span data-ttu-id="f335e-311">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-311">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-312">2</span><span class="sxs-lookup"><span data-stu-id="f335e-312">2</span></span> | <span data-ttu-id="f335e-313">0</span><span class="sxs-lookup"><span data-stu-id="f335e-313">0</span></span><br /><span data-ttu-id="f335e-314">1</span><span class="sxs-lookup"><span data-stu-id="f335e-314">1</span></span> | <span data-ttu-id="f335e-315">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-315">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-316">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-316">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-317">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-317">[23-3]</span></span> | <span data-ttu-id="f335e-318">0</span><span class="sxs-lookup"><span data-stu-id="f335e-318">0</span></span> | <span data-ttu-id="f335e-319">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-319">Reserved</span></span>
| <span data-ttu-id="f335e-320">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-320">[31-24]</span></span> | <br /><span data-ttu-id="f335e-321">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-321">0x00</span></span><br /><span data-ttu-id="f335e-322">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-322">0x01</span></span><br /><span data-ttu-id="f335e-323">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-323">0x02</span></span> | <span data-ttu-id="f335e-324">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-324">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-325">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-325">IAR</span></span><br /><span data-ttu-id="f335e-326">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-326">ARM</span></span><br /><span data-ttu-id="f335e-327">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-327">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-gnu"></a><span data-ttu-id="f335e-328">Konsolidator modułu dla Cortex-M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-328">Module linker for Cortex-M3 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m3-using-gnu"></a><span data-ttu-id="f335e-329">Kompilowanie modułów dla Cortex-M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-329">Building Modules for Cortex-M3 using GNU</span></span>

<span data-ttu-id="f335e-330">Zobacz build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-330">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m3 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m3-using-gnu"></a><span data-ttu-id="f335e-331">Definicja rozszerzenia wątku dla Cortex-M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-331">Thread extension definition for Cortex-M3 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-gnu"></a><span data-ttu-id="f335e-332">Kompilowanie Menedżera modułów dla Cortex-M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-332">Building Module Manager for Cortex-M3 using GNU</span></span>

<span data-ttu-id="f335e-333">Zobacz build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-333">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb cortexm_crt0.S
arm-none-eabi-ld -A cortex-m3 -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a  libc.a -o sample_threadx_module_manager.axf -M > sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-gnu"></a><span data-ttu-id="f335e-334">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M3 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-334">Attributes for external memory enable API for Cortex-M3 using GNU</span></span>

<span data-ttu-id="f335e-335">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-335">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-336">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-336">Attribute parameter</span></span> | <span data-ttu-id="f335e-337">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-337">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-339">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-339">Write access</span></span> |

### <a name="cortex-m3-using-iar"></a><span data-ttu-id="f335e-340">Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-340">Cortex-M3 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m3-using-iar"></a><span data-ttu-id="f335e-341">Preambuła modułu dla Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-341">Module preamble for Cortex-M3 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m3-using-iar"></a><span data-ttu-id="f335e-342">Właściwości modułu dla Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-342">Module properties for Cortex-M3 using IAR</span></span>

| <span data-ttu-id="f335e-343">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-343">Bit</span></span> | <span data-ttu-id="f335e-344">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-344">Value</span></span> | <span data-ttu-id="f335e-345">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-345">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-346">0</span><span class="sxs-lookup"><span data-stu-id="f335e-346">0</span></span> | <span data-ttu-id="f335e-347">0</span><span class="sxs-lookup"><span data-stu-id="f335e-347">0</span></span><br /><span data-ttu-id="f335e-348">1</span><span class="sxs-lookup"><span data-stu-id="f335e-348">1</span></span> | <span data-ttu-id="f335e-349">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-349">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-350">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-350">User mode execution</span></span> |
| <span data-ttu-id="f335e-351">1</span><span class="sxs-lookup"><span data-stu-id="f335e-351">1</span></span> | <span data-ttu-id="f335e-352">0</span><span class="sxs-lookup"><span data-stu-id="f335e-352">0</span></span><br /><span data-ttu-id="f335e-353">1</span><span class="sxs-lookup"><span data-stu-id="f335e-353">1</span></span> | <span data-ttu-id="f335e-354">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-354">No MPU protection</span></span><br /><span data-ttu-id="f335e-355">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-355">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-356">2</span><span class="sxs-lookup"><span data-stu-id="f335e-356">2</span></span> | <span data-ttu-id="f335e-357">0</span><span class="sxs-lookup"><span data-stu-id="f335e-357">0</span></span><br /><span data-ttu-id="f335e-358">1</span><span class="sxs-lookup"><span data-stu-id="f335e-358">1</span></span> | <span data-ttu-id="f335e-359">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-359">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-360">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-360">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-361">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-361">[23-3]</span></span> | <span data-ttu-id="f335e-362">0</span><span class="sxs-lookup"><span data-stu-id="f335e-362">0</span></span> | <span data-ttu-id="f335e-363">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-363">Reserved</span></span>
| <span data-ttu-id="f335e-364">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-364">[31-24]</span></span> | <br /><span data-ttu-id="f335e-365">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-365">0x00</span></span><br /><span data-ttu-id="f335e-366">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-366">0x01</span></span><br /><span data-ttu-id="f335e-367">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-367">0x02</span></span> | <span data-ttu-id="f335e-368">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-368">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-369">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-369">IAR</span></span><br /><span data-ttu-id="f335e-370">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-370">ARM</span></span><br /><span data-ttu-id="f335e-371">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-371">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-iar"></a><span data-ttu-id="f335e-372">Konsolidator modułu dla Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-372">Module linker for Cortex-M3 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f2xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m3-using-iar"></a><span data-ttu-id="f335e-373">Kompilowanie modułów dla Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-373">Building Modules for Cortex-M3 using IAR</span></span>

<span data-ttu-id="f335e-374">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-374">An example workspace is provided.</span></span> <span data-ttu-id="f335e-375">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-375">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-iar"></a><span data-ttu-id="f335e-376">Definicja rozszerzenia wątku dla Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-376">Thread extension definition for Cortex-M3 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m3-using-iar"></a><span data-ttu-id="f335e-377">Kompilowanie Menedżera modułów dla Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-377">Building Module Manager for Cortex-M3 using IAR</span></span>

<span data-ttu-id="f335e-378">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-378">An example workspace is provided.</span></span> <span data-ttu-id="f335e-379">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-379">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-iar"></a><span data-ttu-id="f335e-380">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M3 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-380">Attributes for external memory enable API for Cortex-M3 using IAR</span></span>

<span data-ttu-id="f335e-381">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-381">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-382">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-382">Attribute parameter</span></span> | <span data-ttu-id="f335e-383">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-383">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-385">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-385">Write access</span></span> |

## <a name="cortex-m33-processor"></a><span data-ttu-id="f335e-386">Procesor Cortex — — M33</span><span class="sxs-lookup"><span data-stu-id="f335e-386">Cortex-M33 processor</span></span>

### <a name="cortex-m33-using-ac6"></a><span data-ttu-id="f335e-387">Cortex — — M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-387">Cortex-M33 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m33-using-ac6"></a><span data-ttu-id="f335e-388">Preambuła modułu dla Cortex-— M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-388">Module preamble for Cortex-M33 using AC6</span></span>

```c
    .text
    .align 4
    .syntax unified
    .section RESET
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    //the tools can't add two symbols together, but it should look like this:
    //.dc.l   Image$$ER_RO$$Length + Image$$ER_RW$$Length         // Module Code Size
    //.dc.l   Image$$ER_RW$$Length + Image$$ER_ZI$$ZI$$Length     // Module Data Size
    //so instead we'll define hard values:
    .dc.l   0x4000                                              // Module Code Size
    .dc.l   0x4000                                              // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m33-using-ac6"></a><span data-ttu-id="f335e-389">Właściwości modułu dla Cortex-— M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-389">Module properties for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="f335e-390">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-390">Bit</span></span> | <span data-ttu-id="f335e-391">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-391">Value</span></span> | <span data-ttu-id="f335e-392">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-392">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-393">0</span><span class="sxs-lookup"><span data-stu-id="f335e-393">0</span></span> | <span data-ttu-id="f335e-394">0</span><span class="sxs-lookup"><span data-stu-id="f335e-394">0</span></span><br /><span data-ttu-id="f335e-395">1</span><span class="sxs-lookup"><span data-stu-id="f335e-395">1</span></span> | <span data-ttu-id="f335e-396">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-396">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-397">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-397">User mode execution</span></span> |
| <span data-ttu-id="f335e-398">1</span><span class="sxs-lookup"><span data-stu-id="f335e-398">1</span></span> | <span data-ttu-id="f335e-399">0</span><span class="sxs-lookup"><span data-stu-id="f335e-399">0</span></span><br /><span data-ttu-id="f335e-400">1</span><span class="sxs-lookup"><span data-stu-id="f335e-400">1</span></span> | <span data-ttu-id="f335e-401">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-401">No MPU protection</span></span><br /><span data-ttu-id="f335e-402">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-402">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-403">2</span><span class="sxs-lookup"><span data-stu-id="f335e-403">2</span></span> | <span data-ttu-id="f335e-404">0</span><span class="sxs-lookup"><span data-stu-id="f335e-404">0</span></span><br /><span data-ttu-id="f335e-405">1</span><span class="sxs-lookup"><span data-stu-id="f335e-405">1</span></span> | <span data-ttu-id="f335e-406">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-406">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-407">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-407">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-408">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-408">[23-3]</span></span> | <span data-ttu-id="f335e-409">0</span><span class="sxs-lookup"><span data-stu-id="f335e-409">0</span></span> | <span data-ttu-id="f335e-410">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-410">Reserved</span></span>
| <span data-ttu-id="f335e-411">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-411">[31-24]</span></span> | <br /><span data-ttu-id="f335e-412">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-412">0x00</span></span><br /><span data-ttu-id="f335e-413">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-413">0x01</span></span><br /><span data-ttu-id="f335e-414">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-414">0x02</span></span> | <span data-ttu-id="f335e-415">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-415">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-416">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-416">IAR</span></span><br /><span data-ttu-id="f335e-417">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-417">ARM</span></span><br /><span data-ttu-id="f335e-418">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-418">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-ac6"></a><span data-ttu-id="f335e-419">Konsolidator modułu dla Cortex-— M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-419">Module linker for Cortex-M33 using AC6</span></span>

<span data-ttu-id="f335e-420">Nie jest wymagany żaden plik konsolidatora dla Keil łańcucha narzędzi.</span><span class="sxs-lookup"><span data-stu-id="f335e-420">No linker file needed for Keil toolchain.</span></span> <span data-ttu-id="f335e-421">Zobacz Ustawienia kompilacji w przykładowym projekcie.</span><span class="sxs-lookup"><span data-stu-id="f335e-421">See build settings in example project.</span></span>
<span data-ttu-id="f335e-422">Poniżej wymieniono ważne Opcje konsolidatora:</span><span class="sxs-lookup"><span data-stu-id="f335e-422">Important linker options are listed below:</span></span>

```c
--entry demo_module_start --first __txm_module_preamble
```

#### <a name="building-modules-for-cortex-m33-using-ac6"></a><span data-ttu-id="f335e-423">Kompilowanie modułów dla Cortex-— M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-423">Building Modules for Cortex-M33 using AC6</span></span>

<span data-ttu-id="f335e-424">Ustawienia kompilatora:</span><span class="sxs-lookup"><span data-stu-id="f335e-424">Compiler settings:</span></span>

```c
-xc -std=c99 --target=arm-arm-none-eabi -mcpu=cortex-m33 -mfpu=fpv5-sp-d16 -mfloat-abi=hard -c
-fno-rtti -funsigned-char -fshort-enums -fshort-wchar
-mlittle-endian -gdwarf-3 -fropi -frwpi -O1 -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality -I ../../../../../common_modules/inc -I ../../../../../common/inc -I ../../../../../ports_module/cortex_m33/ac6/inc -I ../demo_secure_zone
-I./RTE/_FVP_Simulation_Model
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/CMSIS/Core/Include
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/Device/ARM/ARMCM33/Include
-D__UVISION_VERSION="531" -D_RTE_ -DARMCM33_DSP_FP_TZ -D_RTE_
-o ./Objects/*.o -MD
```

#### <a name="thread-extension-definition-for-cortex-m33-using-ac6"></a><span data-ttu-id="f335e-425">Definicja rozszerzenia wątku dla Cortex-— M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-425">Thread extension definition for Cortex-M33 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m33-using-ac6"></a><span data-ttu-id="f335e-426">Kompilowanie Menedżera modułów dla Cortex-— M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-426">Building Module Manager for Cortex-M33 using AC6</span></span>

<span data-ttu-id="f335e-427">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-427">An example workspace is provided.</span></span> <span data-ttu-id="f335e-428">Kompilowanie biblioteki ThreadX, biblioteki modułów ThreadX, projektu sample_threadx_module i projektu demo_threadx_non secure_zone.</span><span class="sxs-lookup"><span data-stu-id="f335e-428">Build the ThreadX library, ThreadX Modules library, sample_threadx_module project, and demo_threadx_non-secure_zone project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-ac6"></a><span data-ttu-id="f335e-429">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-— M33 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-429">Attributes for external memory enable API for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="f335e-430">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-430">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="f335e-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="f335e-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="f335e-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-gnu"></a><span data-ttu-id="f335e-436">Cortex — — M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-436">Cortex-M33 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m33-using-gnu"></a><span data-ttu-id="f335e-437">Preambuła modułu dla Cortex-— M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-437">Module preamble for Cortex-M33 using GNU</span></span>

#### <a name="module-properties-for-cortex-m33-using-gnu"></a><span data-ttu-id="f335e-438">Właściwości modułu dla Cortex-— M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-438">Module properties for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="f335e-439">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-439">Bit</span></span> | <span data-ttu-id="f335e-440">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-440">Value</span></span> | <span data-ttu-id="f335e-441">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-441">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-442">0</span><span class="sxs-lookup"><span data-stu-id="f335e-442">0</span></span> | <span data-ttu-id="f335e-443">0</span><span class="sxs-lookup"><span data-stu-id="f335e-443">0</span></span><br /><span data-ttu-id="f335e-444">1</span><span class="sxs-lookup"><span data-stu-id="f335e-444">1</span></span> | <span data-ttu-id="f335e-445">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-445">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-446">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-446">User mode execution</span></span> |
| <span data-ttu-id="f335e-447">1</span><span class="sxs-lookup"><span data-stu-id="f335e-447">1</span></span> | <span data-ttu-id="f335e-448">0</span><span class="sxs-lookup"><span data-stu-id="f335e-448">0</span></span><br /><span data-ttu-id="f335e-449">1</span><span class="sxs-lookup"><span data-stu-id="f335e-449">1</span></span> | <span data-ttu-id="f335e-450">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-450">No MPU protection</span></span><br /><span data-ttu-id="f335e-451">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-451">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-452">2</span><span class="sxs-lookup"><span data-stu-id="f335e-452">2</span></span> | <span data-ttu-id="f335e-453">0</span><span class="sxs-lookup"><span data-stu-id="f335e-453">0</span></span><br /><span data-ttu-id="f335e-454">1</span><span class="sxs-lookup"><span data-stu-id="f335e-454">1</span></span> | <span data-ttu-id="f335e-455">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-455">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-456">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-456">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-457">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-457">[23-3]</span></span> | <span data-ttu-id="f335e-458">0</span><span class="sxs-lookup"><span data-stu-id="f335e-458">0</span></span> | <span data-ttu-id="f335e-459">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-459">Reserved</span></span>
| <span data-ttu-id="f335e-460">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-460">[31-24]</span></span> | <br /><span data-ttu-id="f335e-461">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-461">0x00</span></span><br /><span data-ttu-id="f335e-462">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-462">0x01</span></span><br /><span data-ttu-id="f335e-463">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-463">0x02</span></span> | <span data-ttu-id="f335e-464">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-464">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-465">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-465">IAR</span></span><br /><span data-ttu-id="f335e-466">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-466">ARM</span></span><br /><span data-ttu-id="f335e-467">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-467">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-gnu"></a><span data-ttu-id="f335e-468">Konsolidator modułu dla Cortex-— M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-468">Module linker for Cortex-M33 using GNU</span></span>

#### <a name="building-modules-for-cortex-m33-using-gnu"></a><span data-ttu-id="f335e-469">Kompilowanie modułów dla Cortex-— M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-469">Building Modules for Cortex-M33 using GNU</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-gnu"></a><span data-ttu-id="f335e-470">Definicja rozszerzenia wątku dla Cortex-— M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-470">Thread extension definition for Cortex-M33 using GNU</span></span>

#### <a name="building-module-manager-for-cortex-m33-using-gnu"></a><span data-ttu-id="f335e-471">Kompilowanie Menedżera modułów dla Cortex-— M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-471">Building Module Manager for Cortex-M33 using GNU</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-gnu"></a><span data-ttu-id="f335e-472">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-— M33 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-472">Attributes for external memory enable API for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="f335e-473">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-473">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="f335e-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="f335e-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="f335e-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-iar"></a><span data-ttu-id="f335e-479">Cortex — — M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-479">Cortex-M33 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m33-using-iar"></a><span data-ttu-id="f335e-480">Preambuła modułu dla Cortex-— M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-480">Module preamble for Cortex-M33 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external refrences.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x6                                               // Module Major Version
    DC32      0x1                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DC32      _txm_module_thread_shell_entry - . - 0            // Module Shell Entry Point
    DC32      demo_module_start - . - 0                         // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m33-using-iar"></a><span data-ttu-id="f335e-481">Właściwości modułu dla Cortex-— M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-481">Module properties for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="f335e-482">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-482">Bit</span></span> | <span data-ttu-id="f335e-483">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-483">Value</span></span> | <span data-ttu-id="f335e-484">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-484">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-485">0</span><span class="sxs-lookup"><span data-stu-id="f335e-485">0</span></span> | <span data-ttu-id="f335e-486">0</span><span class="sxs-lookup"><span data-stu-id="f335e-486">0</span></span><br /><span data-ttu-id="f335e-487">1</span><span class="sxs-lookup"><span data-stu-id="f335e-487">1</span></span> | <span data-ttu-id="f335e-488">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-488">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-489">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-489">User mode execution</span></span> |
| <span data-ttu-id="f335e-490">1</span><span class="sxs-lookup"><span data-stu-id="f335e-490">1</span></span> | <span data-ttu-id="f335e-491">0</span><span class="sxs-lookup"><span data-stu-id="f335e-491">0</span></span><br /><span data-ttu-id="f335e-492">1</span><span class="sxs-lookup"><span data-stu-id="f335e-492">1</span></span> | <span data-ttu-id="f335e-493">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-493">No MPU protection</span></span><br /><span data-ttu-id="f335e-494">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-494">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-495">2</span><span class="sxs-lookup"><span data-stu-id="f335e-495">2</span></span> | <span data-ttu-id="f335e-496">0</span><span class="sxs-lookup"><span data-stu-id="f335e-496">0</span></span><br /><span data-ttu-id="f335e-497">1</span><span class="sxs-lookup"><span data-stu-id="f335e-497">1</span></span> | <span data-ttu-id="f335e-498">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-498">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-499">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-499">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-500">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-500">[23-3]</span></span> | <span data-ttu-id="f335e-501">0</span><span class="sxs-lookup"><span data-stu-id="f335e-501">0</span></span> | <span data-ttu-id="f335e-502">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-502">Reserved</span></span>
| <span data-ttu-id="f335e-503">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-503">[31-24]</span></span> | <br /><span data-ttu-id="f335e-504">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-504">0x00</span></span><br /><span data-ttu-id="f335e-505">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-505">0x01</span></span><br /><span data-ttu-id="f335e-506">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-506">0x02</span></span> | <span data-ttu-id="f335e-507">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-507">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-508">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-508">IAR</span></span><br /><span data-ttu-id="f335e-509">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-509">ARM</span></span><br /><span data-ttu-id="f335e-510">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-510">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-iar"></a><span data-ttu-id="f335e-511">Konsolidator modułu dla Cortex-— M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-511">Module linker for Cortex-M33 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order 
{ 
  ro object txm_module_preamble.o,
  ro, 
  ro data 
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m33-using-iar"></a><span data-ttu-id="f335e-512">Kompilowanie modułów dla Cortex-— M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-512">Building Modules for Cortex-M33 using IAR</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-iar"></a><span data-ttu-id="f335e-513">Definicja rozszerzenia wątku dla Cortex-— M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-513">Thread extension definition for Cortex-M33 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;             \
                                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m33-using-iar"></a><span data-ttu-id="f335e-514">Kompilowanie Menedżera modułów dla Cortex-— M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-514">Building Module Manager for Cortex-M33 using IAR</span></span>

<span data-ttu-id="f335e-515">Nie podano jeszcze przykładowego obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="f335e-515">An example workspace is not yet provided.</span></span> <span data-ttu-id="f335e-516">Już wkrótce.</span><span class="sxs-lookup"><span data-stu-id="f335e-516">Coming soon.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-iar"></a><span data-ttu-id="f335e-517">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-— M33 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-517">Attributes for external memory enable API for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="f335e-518">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-518">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="f335e-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="f335e-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="f335e-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="f335e-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="f335e-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

## <a name="cortex-m4-processor"></a><span data-ttu-id="f335e-524">Procesor Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="f335e-524">Cortex-M4 processor</span></span>

### <a name="cortex-m4-using-ac5"></a><span data-ttu-id="f335e-525">Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-525">Cortex-M4 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac5"></a><span data-ttu-id="f335e-526">Preambuła modułu dla Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-526">Module preamble for Cortex-M4 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    /* Define public symbols.  */

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          // Module ID
    DCD     0x6                                                 // Module Major Version
    DCD     0x1                                                 // Module Minor Version
    DCD     32                                                  // Module Preamble Size in 32-bit words
    DCD     0x12345678                                          // Module ID (application defined)
    DCD     0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              // Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    DCD     0                                                   // Module Stop Thread Entry Point
    DCD     1                                                   // Module Start/Stop Thread Priority
    DCD     1024                                                // Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   // Module Callback Thread Entry
    DCD     1                                                   // Module Callback Thread Priority
    DCD     1024                                                // Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|     // Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| // Module Data Size
    DCD     0                                                   // Reserved 0
    DCD     0                                                   // Reserved 1
    DCD     0                                                   // Reserved 2
    DCD     0                                                   // Reserved 3
    DCD     0                                                   // Reserved 4
    DCD     0                                                   // Reserved 5
    DCD     0                                                   // Reserved 6
    DCD     0                                                   // Reserved 7
    DCD     0                                                   // Reserved 8
    DCD     0                                                   // Reserved 9
    DCD     0                                                   // Reserved 10
    DCD     0                                                   // Reserved 11
    DCD     0                                                   // Reserved 12
    DCD     0                                                   // Reserved 13
    DCD     0                                                   // Reserved 14
    DCD     0                                                   // Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-ac5"></a><span data-ttu-id="f335e-527">Właściwości modułu dla Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-527">Module properties for Cortex-M4 using AC5</span></span>

| <span data-ttu-id="f335e-528">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-528">Bit</span></span> | <span data-ttu-id="f335e-529">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-529">Value</span></span> | <span data-ttu-id="f335e-530">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-530">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-531">0</span><span class="sxs-lookup"><span data-stu-id="f335e-531">0</span></span> | <span data-ttu-id="f335e-532">0</span><span class="sxs-lookup"><span data-stu-id="f335e-532">0</span></span><br /><span data-ttu-id="f335e-533">1</span><span class="sxs-lookup"><span data-stu-id="f335e-533">1</span></span> | <span data-ttu-id="f335e-534">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-534">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-535">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-535">User mode execution</span></span> |
| <span data-ttu-id="f335e-536">1</span><span class="sxs-lookup"><span data-stu-id="f335e-536">1</span></span> | <span data-ttu-id="f335e-537">0</span><span class="sxs-lookup"><span data-stu-id="f335e-537">0</span></span><br /><span data-ttu-id="f335e-538">1</span><span class="sxs-lookup"><span data-stu-id="f335e-538">1</span></span> | <span data-ttu-id="f335e-539">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-539">No MPU protection</span></span><br /><span data-ttu-id="f335e-540">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-540">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-541">2</span><span class="sxs-lookup"><span data-stu-id="f335e-541">2</span></span> | <span data-ttu-id="f335e-542">0</span><span class="sxs-lookup"><span data-stu-id="f335e-542">0</span></span><br /><span data-ttu-id="f335e-543">1</span><span class="sxs-lookup"><span data-stu-id="f335e-543">1</span></span> | <span data-ttu-id="f335e-544">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-544">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-545">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-545">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-546">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-546">[23-3]</span></span> | <span data-ttu-id="f335e-547">0</span><span class="sxs-lookup"><span data-stu-id="f335e-547">0</span></span> | <span data-ttu-id="f335e-548">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-548">Reserved</span></span>
| <span data-ttu-id="f335e-549">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-549">[31-24]</span></span> | <br /><span data-ttu-id="f335e-550">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-550">0x00</span></span><br /><span data-ttu-id="f335e-551">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-551">0x01</span></span><br /><span data-ttu-id="f335e-552">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-552">0x02</span></span> | <span data-ttu-id="f335e-553">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-553">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-554">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-554">IAR</span></span><br /><span data-ttu-id="f335e-555">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-555">ARM</span></span><br /><span data-ttu-id="f335e-556">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-556">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac5"></a><span data-ttu-id="f335e-557">Konsolidator modułu dla Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-557">Module linker for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f335e-558">Nie podano przykładowego pliku konsolidatora; Konsolidacja jest wykonywana w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f335e-558">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="f335e-559">Zobacz następną sekcję.</span><span class="sxs-lookup"><span data-stu-id="f335e-559">See next section.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac5"></a><span data-ttu-id="f335e-560">Kompilowanie modułów dla Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-560">Building Modules for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f335e-561">Zobacz przykład build_threadx_module_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-561">See example build_threadx_module_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m4 --fpu=vfpv4 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m4-using-ac5"></a><span data-ttu-id="f335e-562">Definicja rozszerzenia wątku dla Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-562">Thread extension definition for Cortex-M4 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac5"></a><span data-ttu-id="f335e-563">Kompilowanie Menedżera modułów dla Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-563">Building Module Manager for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f335e-564">Zobacz przykład build_threadx_module_manager_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-564">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m4 --fpu=vfpv4 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac5"></a><span data-ttu-id="f335e-565">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M4 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-565">Attributes for external memory enable API for Cortex-M4 using AC5</span></span>

<span data-ttu-id="f335e-566">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-566">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-567">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-567">Attribute parameter</span></span> | <span data-ttu-id="f335e-568">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-568">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-570">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-570">Write access</span></span> |

### <a name="cortex-m4-using-ac6"></a><span data-ttu-id="f335e-571">Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-571">Cortex-M4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac6"></a><span data-ttu-id="f335e-572">Preambuła modułu dla Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-572">Module preamble for Cortex-M4 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-ac6"></a><span data-ttu-id="f335e-573">Właściwości modułu dla Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-573">Module properties for Cortex-M4 using AC6</span></span>

| <span data-ttu-id="f335e-574">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-574">Bit</span></span> | <span data-ttu-id="f335e-575">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-575">Value</span></span> | <span data-ttu-id="f335e-576">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-576">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-577">0</span><span class="sxs-lookup"><span data-stu-id="f335e-577">0</span></span> | <span data-ttu-id="f335e-578">0</span><span class="sxs-lookup"><span data-stu-id="f335e-578">0</span></span><br /><span data-ttu-id="f335e-579">1</span><span class="sxs-lookup"><span data-stu-id="f335e-579">1</span></span> | <span data-ttu-id="f335e-580">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-580">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-581">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-581">User mode execution</span></span> |
| <span data-ttu-id="f335e-582">1</span><span class="sxs-lookup"><span data-stu-id="f335e-582">1</span></span> | <span data-ttu-id="f335e-583">0</span><span class="sxs-lookup"><span data-stu-id="f335e-583">0</span></span><br /><span data-ttu-id="f335e-584">1</span><span class="sxs-lookup"><span data-stu-id="f335e-584">1</span></span> | <span data-ttu-id="f335e-585">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-585">No MPU protection</span></span><br /><span data-ttu-id="f335e-586">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-586">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-587">2</span><span class="sxs-lookup"><span data-stu-id="f335e-587">2</span></span> | <span data-ttu-id="f335e-588">0</span><span class="sxs-lookup"><span data-stu-id="f335e-588">0</span></span><br /><span data-ttu-id="f335e-589">1</span><span class="sxs-lookup"><span data-stu-id="f335e-589">1</span></span> | <span data-ttu-id="f335e-590">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-590">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-591">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-591">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-592">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-592">[23-3]</span></span> | <span data-ttu-id="f335e-593">0</span><span class="sxs-lookup"><span data-stu-id="f335e-593">0</span></span> | <span data-ttu-id="f335e-594">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-594">Reserved</span></span>
| <span data-ttu-id="f335e-595">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-595">[31-24]</span></span> | <br /><span data-ttu-id="f335e-596">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-596">0x00</span></span><br /><span data-ttu-id="f335e-597">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-597">0x01</span></span><br /><span data-ttu-id="f335e-598">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-598">0x02</span></span> | <span data-ttu-id="f335e-599">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-599">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-600">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-600">IAR</span></span><br /><span data-ttu-id="f335e-601">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-601">ARM</span></span><br /><span data-ttu-id="f335e-602">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-602">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac6"></a><span data-ttu-id="f335e-603">Konsolidator modułu dla Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-603">Module linker for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f335e-604">Nie jest używany żaden plik konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="f335e-604">No linker file is used.</span></span> <span data-ttu-id="f335e-605">Zobacz ustawienia projektu.</span><span class="sxs-lookup"><span data-stu-id="f335e-605">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac6"></a><span data-ttu-id="f335e-606">Kompilowanie modułów dla Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-606">Building Modules for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f335e-607">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-607">An example workspace is provided.</span></span> <span data-ttu-id="f335e-608">Kompilowanie biblioteki ThreadX, biblioteki modułów ThreadX, przykładowego projektu modułu i przykładowego projektu Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="f335e-608">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-ac6"></a><span data-ttu-id="f335e-609">Definicja rozszerzenia wątku dla Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-609">Thread extension definition for Cortex-M4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac6"></a><span data-ttu-id="f335e-610">Kompilowanie Menedżera modułów dla Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-610">Building Module Manager for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f335e-611">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-611">An example workspace is provided.</span></span> <span data-ttu-id="f335e-612">Kompilowanie biblioteki ThreadX, biblioteki modułów ThreadX, przykładowego projektu modułu i przykładowego projektu Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="f335e-612">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac6"></a><span data-ttu-id="f335e-613">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-613">Attributes for external memory enable API for Cortex-M4 using AC6</span></span>

<span data-ttu-id="f335e-614">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-614">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-615">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-615">Attribute parameter</span></span> | <span data-ttu-id="f335e-616">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-616">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-618">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-618">Write access</span></span> |

### <a name="cortex-m4-using-gnu"></a><span data-ttu-id="f335e-619">Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-619">Cortex-M4 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m4-using-gnu"></a><span data-ttu-id="f335e-620">Preambuła modułu dla Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-620">Module preamble for Cortex-M4 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-gnu"></a><span data-ttu-id="f335e-621">Właściwości modułu dla Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-621">Module properties for Cortex-M4 using GNU</span></span>

| <span data-ttu-id="f335e-622">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-622">Bit</span></span> | <span data-ttu-id="f335e-623">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-623">Value</span></span> | <span data-ttu-id="f335e-624">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-624">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-625">0</span><span class="sxs-lookup"><span data-stu-id="f335e-625">0</span></span> | <span data-ttu-id="f335e-626">0</span><span class="sxs-lookup"><span data-stu-id="f335e-626">0</span></span><br /><span data-ttu-id="f335e-627">1</span><span class="sxs-lookup"><span data-stu-id="f335e-627">1</span></span> | <span data-ttu-id="f335e-628">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-628">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-629">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-629">User mode execution</span></span> |
| <span data-ttu-id="f335e-630">1</span><span class="sxs-lookup"><span data-stu-id="f335e-630">1</span></span> | <span data-ttu-id="f335e-631">0</span><span class="sxs-lookup"><span data-stu-id="f335e-631">0</span></span><br /><span data-ttu-id="f335e-632">1</span><span class="sxs-lookup"><span data-stu-id="f335e-632">1</span></span> | <span data-ttu-id="f335e-633">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-633">No MPU protection</span></span><br /><span data-ttu-id="f335e-634">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-634">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-635">2</span><span class="sxs-lookup"><span data-stu-id="f335e-635">2</span></span> | <span data-ttu-id="f335e-636">0</span><span class="sxs-lookup"><span data-stu-id="f335e-636">0</span></span><br /><span data-ttu-id="f335e-637">1</span><span class="sxs-lookup"><span data-stu-id="f335e-637">1</span></span> | <span data-ttu-id="f335e-638">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-638">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-639">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-639">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-640">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-640">[23-3]</span></span> | <span data-ttu-id="f335e-641">0</span><span class="sxs-lookup"><span data-stu-id="f335e-641">0</span></span> | <span data-ttu-id="f335e-642">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-642">Reserved</span></span>
| <span data-ttu-id="f335e-643">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-643">[31-24]</span></span> | <br /><span data-ttu-id="f335e-644">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-644">0x00</span></span><br /><span data-ttu-id="f335e-645">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-645">0x01</span></span><br /><span data-ttu-id="f335e-646">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-646">0x02</span></span> | <span data-ttu-id="f335e-647">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-647">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-648">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-648">IAR</span></span><br /><span data-ttu-id="f335e-649">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-649">ARM</span></span><br /><span data-ttu-id="f335e-650">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-650">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-gnu"></a><span data-ttu-id="f335e-651">Konsolidator modułu dla Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-651">Module linker for Cortex-M4 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m4-using-gnu"></a><span data-ttu-id="f335e-652">Kompilowanie modułów dla Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-652">Building Modules for Cortex-M4 using GNU</span></span>

<span data-ttu-id="f335e-653">Zobacz build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-653">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m4 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m4-using-gnu"></a><span data-ttu-id="f335e-654">Definicja rozszerzenia wątku dla Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-654">Thread extension definition for Cortex-M4 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-gnu"></a><span data-ttu-id="f335e-655">Kompilowanie Menedżera modułów dla Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-655">Building Module Manager for Cortex-M4 using GNU</span></span>

<span data-ttu-id="f335e-656">Zobacz build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-656">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_vectors.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb tx_initialize_low_level.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -T sample_threadx.ld -ereset_handler -nostartfiles -o sample_threadx_module_manager.out -Wl,-Map=sample_threadx_module_manager.map cortexm_vectors.o cortexm_crt0.o tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-gnu"></a><span data-ttu-id="f335e-657">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M4 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-657">Attributes for external memory enable API for Cortex-M4 using GNU</span></span>

<span data-ttu-id="f335e-658">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-658">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-659">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-659">Attribute parameter</span></span> | <span data-ttu-id="f335e-660">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-660">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-662">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-662">Write access</span></span> |

### <a name="cortex-m4-using-iar"></a><span data-ttu-id="f335e-663">Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-663">Cortex-M4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m4-using-iar"></a><span data-ttu-id="f335e-664">Preambuła modułu dla Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-664">Module preamble for Cortex-M4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-iar"></a><span data-ttu-id="f335e-665">Właściwości modułu dla Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-665">Module properties for Cortex-M4 using IAR</span></span>

| <span data-ttu-id="f335e-666">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-666">Bit</span></span> | <span data-ttu-id="f335e-667">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-667">Value</span></span> | <span data-ttu-id="f335e-668">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-668">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-669">0</span><span class="sxs-lookup"><span data-stu-id="f335e-669">0</span></span> | <span data-ttu-id="f335e-670">0</span><span class="sxs-lookup"><span data-stu-id="f335e-670">0</span></span><br /><span data-ttu-id="f335e-671">1</span><span class="sxs-lookup"><span data-stu-id="f335e-671">1</span></span> | <span data-ttu-id="f335e-672">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-672">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-673">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-673">User mode execution</span></span> |
| <span data-ttu-id="f335e-674">1</span><span class="sxs-lookup"><span data-stu-id="f335e-674">1</span></span> | <span data-ttu-id="f335e-675">0</span><span class="sxs-lookup"><span data-stu-id="f335e-675">0</span></span><br /><span data-ttu-id="f335e-676">1</span><span class="sxs-lookup"><span data-stu-id="f335e-676">1</span></span> | <span data-ttu-id="f335e-677">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-677">No MPU protection</span></span><br /><span data-ttu-id="f335e-678">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-678">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-679">2</span><span class="sxs-lookup"><span data-stu-id="f335e-679">2</span></span> | <span data-ttu-id="f335e-680">0</span><span class="sxs-lookup"><span data-stu-id="f335e-680">0</span></span><br /><span data-ttu-id="f335e-681">1</span><span class="sxs-lookup"><span data-stu-id="f335e-681">1</span></span> | <span data-ttu-id="f335e-682">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-682">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-683">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-683">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-684">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-684">[23-3]</span></span> | <span data-ttu-id="f335e-685">0</span><span class="sxs-lookup"><span data-stu-id="f335e-685">0</span></span> | <span data-ttu-id="f335e-686">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-686">Reserved</span></span>
| <span data-ttu-id="f335e-687">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-687">[31-24]</span></span> | <br /><span data-ttu-id="f335e-688">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-688">0x00</span></span><br /><span data-ttu-id="f335e-689">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-689">0x01</span></span><br /><span data-ttu-id="f335e-690">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-690">0x02</span></span> | <span data-ttu-id="f335e-691">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-691">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-692">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-692">IAR</span></span><br /><span data-ttu-id="f335e-693">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-693">ARM</span></span><br /><span data-ttu-id="f335e-694">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-694">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-iar"></a><span data-ttu-id="f335e-695">Konsolidator modułu dla Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-695">Module linker for Cortex-M4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f4xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m4-using-iar"></a><span data-ttu-id="f335e-696">Kompilowanie modułów dla Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-696">Building Modules for Cortex-M4 using IAR</span></span>

<span data-ttu-id="f335e-697">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-697">An example workspace is provided.</span></span> <span data-ttu-id="f335e-698">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-698">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-iar"></a><span data-ttu-id="f335e-699">Definicja rozszerzenia wątku dla Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-699">Thread extension definition for Cortex-M4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m4-using-iar"></a><span data-ttu-id="f335e-700">Kompilowanie Menedżera modułów dla Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-700">Building Module Manager for Cortex-M4 using IAR</span></span>

<span data-ttu-id="f335e-701">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-701">An example workspace is provided.</span></span> <span data-ttu-id="f335e-702">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-702">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-iar"></a><span data-ttu-id="f335e-703">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-703">Attributes for external memory enable API for Cortex-M4 using IAR</span></span>

<span data-ttu-id="f335e-704">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-704">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-705">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-705">Attribute parameter</span></span> | <span data-ttu-id="f335e-706">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-706">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-708">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-708">Write access</span></span> |

## <a name="cortex-m7-processor"></a><span data-ttu-id="f335e-709">Procesor Cortex — M7</span><span class="sxs-lookup"><span data-stu-id="f335e-709">Cortex-M7 processor</span></span>

### <a name="cortex-m7-using-ac5"></a><span data-ttu-id="f335e-710">Cortex — M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-710">Cortex-M7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m7-using-ac5"></a><span data-ttu-id="f335e-711">Preambuła modułu dla Cortex-M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-711">Module preamble for Cortex-M7 using AC5</span></span>

```c
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble


    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start


    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x5                                                 ; Module Major Version
    DCD     0x6                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-ac5"></a><span data-ttu-id="f335e-712">Właściwości modułu dla Cortex-M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-712">Module properties for Cortex-M7 using AC5</span></span>

| <span data-ttu-id="f335e-713">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-713">Bit</span></span> | <span data-ttu-id="f335e-714">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-714">Value</span></span> | <span data-ttu-id="f335e-715">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-715">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-716">0</span><span class="sxs-lookup"><span data-stu-id="f335e-716">0</span></span> | <span data-ttu-id="f335e-717">0</span><span class="sxs-lookup"><span data-stu-id="f335e-717">0</span></span><br /><span data-ttu-id="f335e-718">1</span><span class="sxs-lookup"><span data-stu-id="f335e-718">1</span></span> | <span data-ttu-id="f335e-719">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-719">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-720">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-720">User mode execution</span></span> |
| <span data-ttu-id="f335e-721">1</span><span class="sxs-lookup"><span data-stu-id="f335e-721">1</span></span> | <span data-ttu-id="f335e-722">0</span><span class="sxs-lookup"><span data-stu-id="f335e-722">0</span></span><br /><span data-ttu-id="f335e-723">1</span><span class="sxs-lookup"><span data-stu-id="f335e-723">1</span></span> | <span data-ttu-id="f335e-724">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-724">No MPU protection</span></span><br /><span data-ttu-id="f335e-725">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-725">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-726">2</span><span class="sxs-lookup"><span data-stu-id="f335e-726">2</span></span> | <span data-ttu-id="f335e-727">0</span><span class="sxs-lookup"><span data-stu-id="f335e-727">0</span></span><br /><span data-ttu-id="f335e-728">1</span><span class="sxs-lookup"><span data-stu-id="f335e-728">1</span></span> | <span data-ttu-id="f335e-729">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-729">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-730">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-730">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-731">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-731">[23-3]</span></span> | <span data-ttu-id="f335e-732">0</span><span class="sxs-lookup"><span data-stu-id="f335e-732">0</span></span> | <span data-ttu-id="f335e-733">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-733">Reserved</span></span>
| <span data-ttu-id="f335e-734">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-734">[31-24]</span></span> | <br /><span data-ttu-id="f335e-735">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-735">0x00</span></span><br /><span data-ttu-id="f335e-736">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-736">0x01</span></span><br /><span data-ttu-id="f335e-737">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-737">0x02</span></span> | <span data-ttu-id="f335e-738">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-738">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-739">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-739">IAR</span></span><br /><span data-ttu-id="f335e-740">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-740">ARM</span></span><br /><span data-ttu-id="f335e-741">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-741">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac5"></a><span data-ttu-id="f335e-742">Konsolidator modułu dla Cortex-M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-742">Module linker for Cortex-M7 using AC5</span></span>

<span data-ttu-id="f335e-743">Kompilacja oparta na wierszu polecenia nie ma przykładu pliku konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="f335e-743">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac5"></a><span data-ttu-id="f335e-744">Kompilowanie modułów dla Cortex-M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-744">Building Modules for Cortex-M7 using AC5</span></span>

<span data-ttu-id="f335e-745">Prosty przykład wiersza polecenia do kompilowania modułu Cortex-M7 przy użyciu AC5:</span><span class="sxs-lookup"><span data-stu-id="f335e-745">A simple command-line example for building a Cortex-M7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-m7 --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m7-using-ac5"></a><span data-ttu-id="f335e-746">Definicja rozszerzenia wątku dla Cortex-M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-746">Thread extension definition for Cortex-M7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac5"></a><span data-ttu-id="f335e-747">Kompilowanie Menedżera modułów dla Cortex-M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-747">Building Module Manager for Cortex-M7 using AC5</span></span>

<span data-ttu-id="f335e-748">Prosty przykład wiersza polecenia do tworzenia Menedżera modułów Cortex-M7 przy użyciu AC5:</span><span class="sxs-lookup"><span data-stu-id="f335e-748">A simple command-line example for building a Cortex-M7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-m7 --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-m7 --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac5"></a><span data-ttu-id="f335e-749">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M7 przy użyciu AC5</span><span class="sxs-lookup"><span data-stu-id="f335e-749">Attributes for external memory enable API for Cortex-M7 using AC5</span></span>

### <a name="cortex-m7-using-ac6"></a><span data-ttu-id="f335e-750">Cortex — M7 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-750">Cortex-M7 using AC6</span></span>

#### <a name="module-properties-for-cortex-m7-using-ac6"></a><span data-ttu-id="f335e-751">Właściwości modułu dla Cortex-M7 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-751">Module properties for Cortex-M7 using AC6</span></span>

| <span data-ttu-id="f335e-752">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-752">Bit</span></span> | <span data-ttu-id="f335e-753">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-753">Value</span></span> | <span data-ttu-id="f335e-754">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-754">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-755">0</span><span class="sxs-lookup"><span data-stu-id="f335e-755">0</span></span> | <span data-ttu-id="f335e-756">0</span><span class="sxs-lookup"><span data-stu-id="f335e-756">0</span></span><br /><span data-ttu-id="f335e-757">1</span><span class="sxs-lookup"><span data-stu-id="f335e-757">1</span></span> | <span data-ttu-id="f335e-758">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-758">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-759">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-759">User mode execution</span></span> |
| <span data-ttu-id="f335e-760">1</span><span class="sxs-lookup"><span data-stu-id="f335e-760">1</span></span> | <span data-ttu-id="f335e-761">0</span><span class="sxs-lookup"><span data-stu-id="f335e-761">0</span></span><br /><span data-ttu-id="f335e-762">1</span><span class="sxs-lookup"><span data-stu-id="f335e-762">1</span></span> | <span data-ttu-id="f335e-763">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-763">No MPU protection</span></span><br /><span data-ttu-id="f335e-764">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-764">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-765">2</span><span class="sxs-lookup"><span data-stu-id="f335e-765">2</span></span> | <span data-ttu-id="f335e-766">0</span><span class="sxs-lookup"><span data-stu-id="f335e-766">0</span></span><br /><span data-ttu-id="f335e-767">1</span><span class="sxs-lookup"><span data-stu-id="f335e-767">1</span></span> | <span data-ttu-id="f335e-768">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-768">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-769">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-769">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-770">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-770">[23-3]</span></span> | <span data-ttu-id="f335e-771">0</span><span class="sxs-lookup"><span data-stu-id="f335e-771">0</span></span> | <span data-ttu-id="f335e-772">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-772">Reserved</span></span>
| <span data-ttu-id="f335e-773">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-773">[31-24]</span></span> | <br /><span data-ttu-id="f335e-774">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-774">0x00</span></span><br /><span data-ttu-id="f335e-775">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-775">0x01</span></span><br /><span data-ttu-id="f335e-776">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-776">0x02</span></span> | <span data-ttu-id="f335e-777">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-777">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-778">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-778">IAR</span></span><br /><span data-ttu-id="f335e-779">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-779">ARM</span></span><br /><span data-ttu-id="f335e-780">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-780">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac6"></a><span data-ttu-id="f335e-781">Konsolidator modułu dla Cortex-M7 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-781">Module linker for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f335e-782">Nie jest używany żaden plik konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="f335e-782">No linker file is used.</span></span> <span data-ttu-id="f335e-783">Zobacz ustawienia projektu.</span><span class="sxs-lookup"><span data-stu-id="f335e-783">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac6"></a><span data-ttu-id="f335e-784">Kompilowanie modułów dla Cortex-M7 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-784">Building Modules for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f335e-785">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-785">An example workspace is provided.</span></span> <span data-ttu-id="f335e-786">Kompilowanie biblioteki ThreadX, biblioteki modułów ThreadX, przykładowego projektu modułu i przykładowego projektu Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="f335e-786">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-ac6"></a><span data-ttu-id="f335e-787">Definicja rozszerzenia wątku dla Cortex-M7 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-787">Thread extension definition for Cortex-M7 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac6"></a><span data-ttu-id="f335e-788">Kompilowanie Menedżera modułów dla Cortex-M7 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-788">Building Module Manager for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f335e-789">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-789">An example workspace is provided.</span></span> <span data-ttu-id="f335e-790">Kompilowanie biblioteki ThreadX, biblioteki modułów ThreadX, przykładowego projektu modułu i przykładowego projektu Menedżera modułów.</span><span class="sxs-lookup"><span data-stu-id="f335e-790">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac6"></a><span data-ttu-id="f335e-791">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M7 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-791">Attributes for external memory enable API for Cortex-M7 using AC6</span></span>

<span data-ttu-id="f335e-792">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-792">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-793">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-793">Attribute parameter</span></span> | <span data-ttu-id="f335e-794">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-794">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-796">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-796">Write access</span></span> |

### <a name="cortex-m7-using-gnu"></a><span data-ttu-id="f335e-797">Cortex — M7 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-797">Cortex-M7 using GNU</span></span>

#### <a name="module-properties-for-cortex-m7-using-gnu"></a><span data-ttu-id="f335e-798">Właściwości modułu dla Cortex-M7 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-798">Module properties for Cortex-M7 using GNU</span></span>

| <span data-ttu-id="f335e-799">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-799">Bit</span></span> | <span data-ttu-id="f335e-800">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-800">Value</span></span> | <span data-ttu-id="f335e-801">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-801">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-802">0</span><span class="sxs-lookup"><span data-stu-id="f335e-802">0</span></span> | <span data-ttu-id="f335e-803">0</span><span class="sxs-lookup"><span data-stu-id="f335e-803">0</span></span><br /><span data-ttu-id="f335e-804">1</span><span class="sxs-lookup"><span data-stu-id="f335e-804">1</span></span> | <span data-ttu-id="f335e-805">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-805">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-806">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-806">User mode execution</span></span> |
| <span data-ttu-id="f335e-807">1</span><span class="sxs-lookup"><span data-stu-id="f335e-807">1</span></span> | <span data-ttu-id="f335e-808">0</span><span class="sxs-lookup"><span data-stu-id="f335e-808">0</span></span><br /><span data-ttu-id="f335e-809">1</span><span class="sxs-lookup"><span data-stu-id="f335e-809">1</span></span> | <span data-ttu-id="f335e-810">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-810">No MPU protection</span></span><br /><span data-ttu-id="f335e-811">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-811">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-812">2</span><span class="sxs-lookup"><span data-stu-id="f335e-812">2</span></span> | <span data-ttu-id="f335e-813">0</span><span class="sxs-lookup"><span data-stu-id="f335e-813">0</span></span><br /><span data-ttu-id="f335e-814">1</span><span class="sxs-lookup"><span data-stu-id="f335e-814">1</span></span> | <span data-ttu-id="f335e-815">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-815">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-816">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-816">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-817">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-817">[23-3]</span></span> | <span data-ttu-id="f335e-818">0</span><span class="sxs-lookup"><span data-stu-id="f335e-818">0</span></span> | <span data-ttu-id="f335e-819">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-819">Reserved</span></span>
| <span data-ttu-id="f335e-820">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-820">[31-24]</span></span> | <br /><span data-ttu-id="f335e-821">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-821">0x00</span></span><br /><span data-ttu-id="f335e-822">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-822">0x01</span></span><br /><span data-ttu-id="f335e-823">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-823">0x02</span></span> | <span data-ttu-id="f335e-824">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-824">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-825">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-825">IAR</span></span><br /><span data-ttu-id="f335e-826">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-826">ARM</span></span><br /><span data-ttu-id="f335e-827">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-827">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-gnu"></a><span data-ttu-id="f335e-828">Konsolidator modułu dla Cortex-M7 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-828">Module linker for Cortex-M7 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m7-using-gnu"></a><span data-ttu-id="f335e-829">Kompilowanie modułów dla Cortex-M7 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-829">Building Modules for Cortex-M7 using GNU</span></span>

<span data-ttu-id="f335e-830">Zobacz build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-830">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m7 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m7-using-gnu"></a><span data-ttu-id="f335e-831">Definicja rozszerzenia wątku dla Cortex-M7 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-831">Thread extension definition for Cortex-M7 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-gnu"></a><span data-ttu-id="f335e-832">Kompilowanie Menedżera modułów dla Cortex-M7 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-832">Building Module Manager for Cortex-M7 using GNU</span></span>

<span data-ttu-id="f335e-833">Zobacz build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="f335e-833">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -nostartfiles -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a -o sample_threadx_module_manager.axf -Wl,-Map=sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-gnu"></a><span data-ttu-id="f335e-834">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M7 przy użyciu GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-834">Attributes for external memory enable API for Cortex-M7 using GNU</span></span>

<span data-ttu-id="f335e-835">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-835">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-836">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-836">Attribute parameter</span></span> | <span data-ttu-id="f335e-837">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-837">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-839">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-839">Write access</span></span> |

### <a name="cortex-m7-using-iar"></a><span data-ttu-id="f335e-840">Cortex — M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-840">Cortex-M7 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m7-using-iar"></a><span data-ttu-id="f335e-841">Preambuła modułu dla Cortex-M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-841">Module preamble for Cortex-M7 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-iar"></a><span data-ttu-id="f335e-842">Właściwości modułu dla Cortex-M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-842">Module properties for Cortex-M7 using IAR</span></span>

| <span data-ttu-id="f335e-843">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-843">Bit</span></span> | <span data-ttu-id="f335e-844">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-844">Value</span></span> | <span data-ttu-id="f335e-845">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-845">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-846">0</span><span class="sxs-lookup"><span data-stu-id="f335e-846">0</span></span> | <span data-ttu-id="f335e-847">0</span><span class="sxs-lookup"><span data-stu-id="f335e-847">0</span></span><br /><span data-ttu-id="f335e-848">1</span><span class="sxs-lookup"><span data-stu-id="f335e-848">1</span></span> | <span data-ttu-id="f335e-849">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-849">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-850">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-850">User mode execution</span></span> |
| <span data-ttu-id="f335e-851">1</span><span class="sxs-lookup"><span data-stu-id="f335e-851">1</span></span> | <span data-ttu-id="f335e-852">0</span><span class="sxs-lookup"><span data-stu-id="f335e-852">0</span></span><br /><span data-ttu-id="f335e-853">1</span><span class="sxs-lookup"><span data-stu-id="f335e-853">1</span></span> | <span data-ttu-id="f335e-854">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-854">No MPU protection</span></span><br /><span data-ttu-id="f335e-855">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-855">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-856">2</span><span class="sxs-lookup"><span data-stu-id="f335e-856">2</span></span> | <span data-ttu-id="f335e-857">0</span><span class="sxs-lookup"><span data-stu-id="f335e-857">0</span></span><br /><span data-ttu-id="f335e-858">1</span><span class="sxs-lookup"><span data-stu-id="f335e-858">1</span></span> | <span data-ttu-id="f335e-859">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-859">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-860">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-860">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-861">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-861">[23-3]</span></span> | <span data-ttu-id="f335e-862">0</span><span class="sxs-lookup"><span data-stu-id="f335e-862">0</span></span> | <span data-ttu-id="f335e-863">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-863">Reserved</span></span>
| <span data-ttu-id="f335e-864">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-864">[31-24]</span></span> | <br /><span data-ttu-id="f335e-865">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-865">0x00</span></span><br /><span data-ttu-id="f335e-866">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-866">0x01</span></span><br /><span data-ttu-id="f335e-867">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-867">0x02</span></span> | <span data-ttu-id="f335e-868">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-868">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-869">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-869">IAR</span></span><br /><span data-ttu-id="f335e-870">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-870">ARM</span></span><br /><span data-ttu-id="f335e-871">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-871">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-iar"></a><span data-ttu-id="f335e-872">Konsolidator modułu dla Cortex-M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-872">Module linker for Cortex-M7 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\cortex_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__     = 0x00400000;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_RAM_start__ = 0x20450000;
define symbol __ICFEDIT_region_RAM_end__   = 0x2045f000 -1;
define symbol __ICFEDIT_region_RAM_NOCACHE_start__ = 0x2045f000;
define symbol __ICFEDIT_region_RAM_NOCACHE_end__   = 0x20460000 -1;
define symbol __ICFEDIT_region_ROM_start__ = 0x00500000;
define symbol __ICFEDIT_region_ROM_end__   = 0x00600000 -1;
define symbol __ICFEDIT_region_SDRAM_start__ = 0x70000000;
define symbol __ICFEDIT_region_SDRAM_end__   = 0x70200000 -1;

/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__      = 0x2000;
define symbol __ICFEDIT_size_heap__        = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region RAM_region    = mem:[from __ICFEDIT_region_RAM_start__ to __ICFEDIT_region_RAM_end__];
define region RAM_NOCACHE_region = mem:[from __ICFEDIT_region_RAM_NOCACHE_start__ to __ICFEDIT_region_RAM_NOCACHE_end__];
define region ROM_region    = mem:[from __ICFEDIT_region_ROM_start__ to __ICFEDIT_region_ROM_end__];
define region SDRAM_region  = mem:[from __ICFEDIT_region_SDRAM_start__ to __ICFEDIT_region_SDRAM_end__];

define block HEAP   with alignment = 8, size = __ICFEDIT_size_heap__   { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m7-using-iar"></a><span data-ttu-id="f335e-873">Kompilowanie modułów dla Cortex-M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-873">Building Modules for Cortex-M7 using IAR</span></span>

<span data-ttu-id="f335e-874">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-874">An example workspace is provided.</span></span> <span data-ttu-id="f335e-875">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-875">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-iar"></a><span data-ttu-id="f335e-876">Definicja rozszerzenia wątku dla Cortex-M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-876">Thread extension definition for Cortex-M7 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m7-using-iar"></a><span data-ttu-id="f335e-877">Kompilowanie Menedżera modułów dla Cortex-M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-877">Building Module Manager for Cortex-M7 using IAR</span></span>

<span data-ttu-id="f335e-878">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-878">An example workspace is provided.</span></span> <span data-ttu-id="f335e-879">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-879">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-iar"></a><span data-ttu-id="f335e-880">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-M7 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-880">Attributes for external memory enable API for Cortex-M7 using IAR</span></span>

<span data-ttu-id="f335e-881">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-881">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-882">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-882">Attribute parameter</span></span> | <span data-ttu-id="f335e-883">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-883">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-885">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-885">Write access</span></span> |

## <a name="cortex-r4-processor"></a><span data-ttu-id="f335e-886">Procesor Cortex-R4</span><span class="sxs-lookup"><span data-stu-id="f335e-886">Cortex-R4 processor</span></span>

### <a name="cortex-r4-using-ac6"></a><span data-ttu-id="f335e-887">Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-887">Cortex-R4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-r4-using-ac6"></a><span data-ttu-id="f335e-888">Preambuła modułu dla Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-888">Module preamble for Cortex-R4 using AC6</span></span>

```c
    .text

/* Define common external references.  */

.global     _txm_module_thread_shell_entry
.global     demo_module_start
.global     _txm_module_callback_request_thread_entry
.global     Image$$ER_RO$$Length
.global     Image$$ER_RW$$Length
.global     Image$$ER_ZI$$ZI$$Length

/* Stack aligned, ROPI and RWPI, R9 used as data offset register.  */
.eabi_attribute Tag_ABI_align_preserved, 1
.eabi_attribute Tag_ABI_PCS_RO_data, 1
.eabi_attribute Tag_ABI_PCS_R9_use,  1
.eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
.word   0x4D4F4455                                          /* Module ID  */
.word   0x5                                                 /* Module Major Version  */
.word   0x3                                                 /* Module Minor Version  */
.word   32                                                  /* Module Preamble Size in 32-bit words  */
.word   0x12345678                                          /* Module ID (application defined)  */
.word   0x01000001                                          /* Module Properties where:
                                                               Bits 31-24: Compiler ID
                                                                       0 -> IAR
                                                                       1 -> RVDS/ARM
                                                                       2 -> GNU
                                                               Bits 23-1:  Reserved
                                                               Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                       1 -> User mode execution (MMU protection)  */
.word   _txm_module_thread_shell_entry - __txm_module_preamble  /* Module Shell Entry Point  */
.word   demo_module_start - __txm_module_preamble           /* Module Start Thread Entry Point  */
.word   0                                                   /* Module Stop Thread Entry Point   */
.word   1                                                   /* Module Start/Stop Thread Priority  */
.word   1024                                                /* Module Start/Stop Thread Stack Size  */
.word   _txm_module_callback_request_thread_entry - __txm_module_preamble   /* Module Callback Thread Entry  */
.word   1                                                   /* Module Callback Thread Priority  */
.word   1024                                                /* Module Callback Thread Stack Size  */
.word   9000                                                /* Module Code Size */
.word   11000                                               /* Module Data Size */
.word   0                                                   /* Reserved 0  */
.word   0                                                   /* Reserved 1  */
.word   0                                                   /* Reserved 2  */
.word   0                                                   /* Reserved 3  */
.word   0                                                   /* Reserved 4  */
.word   0                                                   /* Reserved 5  */
.word   0                                                   /* Reserved 6  */
.word   0                                                   /* Reserved 7  */
.word   0                                                   /* Reserved 8  */
.word   0                                                   /* Reserved 9  */
.word   0                                                   /* Reserved 10  */
.word   0                                                   /* Reserved 11  */
.word   0                                                   /* Reserved 12  */
.word   0                                                   /* Reserved 13  */
.word   0                                                   /* Reserved 14  */
.word   0                                                   /* Reserved 15  */
```

#### <a name="module-properties-for-cortex-r4-using-ac6"></a><span data-ttu-id="f335e-889">Właściwości modułu dla Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-889">Module properties for Cortex-R4 using AC6</span></span>

| <span data-ttu-id="f335e-890">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-890">Bit</span></span> | <span data-ttu-id="f335e-891">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-891">Value</span></span> | <span data-ttu-id="f335e-892">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-892">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-893">0</span><span class="sxs-lookup"><span data-stu-id="f335e-893">0</span></span> | <span data-ttu-id="f335e-894">0</span><span class="sxs-lookup"><span data-stu-id="f335e-894">0</span></span><br /><span data-ttu-id="f335e-895">1</span><span class="sxs-lookup"><span data-stu-id="f335e-895">1</span></span> | <span data-ttu-id="f335e-896">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-896">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-897">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-897">User mode execution</span></span> |
| <span data-ttu-id="f335e-898">[23-1]</span><span class="sxs-lookup"><span data-stu-id="f335e-898">[23-1]</span></span> | <span data-ttu-id="f335e-899">0</span><span class="sxs-lookup"><span data-stu-id="f335e-899">0</span></span> | <span data-ttu-id="f335e-900">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-900">Reserved</span></span>
| <span data-ttu-id="f335e-901">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-901">[31-24]</span></span> | <br /><span data-ttu-id="f335e-902">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-902">0x00</span></span><br /><span data-ttu-id="f335e-903">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-903">0x01</span></span><br /><span data-ttu-id="f335e-904">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-904">0x02</span></span> | <span data-ttu-id="f335e-905">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-905">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-906">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-906">IAR</span></span><br /><span data-ttu-id="f335e-907">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-907">ARM</span></span><br /><span data-ttu-id="f335e-908">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-908">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-ac6"></a><span data-ttu-id="f335e-909">Konsolidator modułu dla Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-909">Module linker for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f335e-910">Kompilacja oparta na wierszu polecenia nie ma przykładu pliku konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="f335e-910">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-r4-using-ac6"></a><span data-ttu-id="f335e-911">Kompilowanie modułów dla Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-911">Building Modules for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f335e-912">Prosty przykład wiersza polecenia do kompilowania modułu Cortex-R4 przy użyciu AC6:</span><span class="sxs-lookup"><span data-stu-id="f335e-912">A simple command-line example for building a Cortex-R4 module using AC6:</span></span>

```dos
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module.c
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 txm_module_preamble.S
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 semihosting.c
armlink -d -o demo_threadx_module.axf --elf --ro 0x00100000 --first txm_module_preamble.o --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --datacompressor=off --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o semihosting.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-r4-using-ac6"></a><span data-ttu-id="f335e-913">Definicja rozszerzenia wątku dla Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-913">Thread extension definition for Cortex-R4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-r4-using-ac6"></a><span data-ttu-id="f335e-914">Kompilowanie Menedżera modułów dla Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-914">Building Module Manager for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f335e-915">Prosty przykład wiersza polecenia do tworzenia Menedżera modułów Cortex-R4 przy użyciu AC6:</span><span class="sxs-lookup"><span data-stu-id="f335e-915">A simple command-line example for building a Cortex-R4 module manager using AC6:</span></span>

```dos
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module_manager.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 timer.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 gic.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 tx_initialize_low_level.S
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 startup.S
armlink -d -o demo_threadx_module_manager.axf --elf --scatter=demo_threadx.scat --remove --map --symbols --list demo_threadx_module_manager.map startup.o timer.o gic.o demo_threadx_module_manager.o tx_initialize_low_level.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-ac6"></a><span data-ttu-id="f335e-916">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-R4 przy użyciu AC6</span><span class="sxs-lookup"><span data-stu-id="f335e-916">Attributes for external memory enable API for Cortex-R4 using AC6</span></span>

<span data-ttu-id="f335e-917">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-917">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-918">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-918">Attribute parameter</span></span> | <span data-ttu-id="f335e-919">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-919">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-921">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-921">Write access</span></span> |

### <a name="cortex-r4-using-iar"></a><span data-ttu-id="f335e-922">Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-922">Cortex-R4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-r4-using-iar"></a><span data-ttu-id="f335e-923">Preambuła modułu dla Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-923">Module preamble for Cortex-R4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN demo_module_start

    /* Define common external references.  */
    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1: Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MPU protection)
                                                                ;           1 -> User mode execution (MPU protection)
    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-r4-using-iar"></a><span data-ttu-id="f335e-924">Właściwości modułu dla Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-924">Module properties for Cortex-R4 using IAR</span></span>

| <span data-ttu-id="f335e-925">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-925">Bit</span></span> | <span data-ttu-id="f335e-926">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-926">Value</span></span> | <span data-ttu-id="f335e-927">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-927">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-928">0</span><span class="sxs-lookup"><span data-stu-id="f335e-928">0</span></span> | <span data-ttu-id="f335e-929">0</span><span class="sxs-lookup"><span data-stu-id="f335e-929">0</span></span><br /><span data-ttu-id="f335e-930">1</span><span class="sxs-lookup"><span data-stu-id="f335e-930">1</span></span> | <span data-ttu-id="f335e-931">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-931">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-932">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-932">User mode execution</span></span> |
| <span data-ttu-id="f335e-933">[23-1]</span><span class="sxs-lookup"><span data-stu-id="f335e-933">[23-1]</span></span> | <span data-ttu-id="f335e-934">0</span><span class="sxs-lookup"><span data-stu-id="f335e-934">0</span></span> | <span data-ttu-id="f335e-935">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-935">Reserved</span></span>
| <span data-ttu-id="f335e-936">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-936">[31-24]</span></span> | <br /><span data-ttu-id="f335e-937">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-937">0x00</span></span><br /><span data-ttu-id="f335e-938">0x01</span><span class="sxs-lookup"><span data-stu-id="f335e-938">0x01</span></span><br /><span data-ttu-id="f335e-939">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-939">0x02</span></span> | <span data-ttu-id="f335e-940">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-940">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-941">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-941">IAR</span></span><br /><span data-ttu-id="f335e-942">ARM</span><span class="sxs-lookup"><span data-stu-id="f335e-942">ARM</span></span><br /><span data-ttu-id="f335e-943">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-943">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-iar"></a><span data-ttu-id="f335e-944">Konsolidator modułu dla Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-944">Module linker for Cortex-R4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x00100000;
define symbol __ICFEDIT_region_ROM_end__   = 0x0013FFFF;
define symbol __ICFEDIT_region_RAM_start__ = 0x08000000;
define symbol __ICFEDIT_region_RAM_end__   = 0x0800FFFF;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x100;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-r4-using-iar"></a><span data-ttu-id="f335e-945">Kompilowanie modułów dla Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-945">Building Modules for Cortex-R4 using IAR</span></span>

<span data-ttu-id="f335e-946">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-946">An example workspace is provided.</span></span> <span data-ttu-id="f335e-947">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-947">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-r4-using-iar"></a><span data-ttu-id="f335e-948">Definicja rozszerzenia wątku dla Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-948">Thread extension definition for Cortex-R4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-r4-using-iar"></a><span data-ttu-id="f335e-949">Kompilowanie Menedżera modułów dla Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-949">Building Module Manager for Cortex-R4 using IAR</span></span>

<span data-ttu-id="f335e-950">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-950">An example workspace is provided.</span></span> <span data-ttu-id="f335e-951">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-951">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-iar"></a><span data-ttu-id="f335e-952">Atrybuty pamięci zewnętrznej Włącz interfejs API dla Cortex-R4 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-952">Attributes for external memory enable API for Cortex-R4 using IAR</span></span>

<span data-ttu-id="f335e-953">Moduł zawsze ma dostęp do odczytu do pamięci współdzielonej.</span><span class="sxs-lookup"><span data-stu-id="f335e-953">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="f335e-954">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-954">Attribute parameter</span></span> | <span data-ttu-id="f335e-955">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-955">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-957">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-957">Write access</span></span> |

## <a name="mcf544xx-processor"></a><span data-ttu-id="f335e-958">Procesor MCF544xx</span><span class="sxs-lookup"><span data-stu-id="f335e-958">MCF544xx processor</span></span>

### <a name="mcf544xx-using-ghs"></a><span data-ttu-id="f335e-959">MCF544xx przy użyciu GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-959">MCF544xx using GHS</span></span>

#### <a name="module-preamble-for-mcf544xx-using-ghs"></a><span data-ttu-id="f335e-960">Preambuła modułu dla MCF544xx przy użyciu GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-960">Module preamble for MCF544xx using GHS</span></span>

```c
    SECT    .preamble, x

    /* Define public symbols.  */
    XDEF __txm_module_preamble

__txm_module_preamble:
    DC.L    0x4D4F4455                                  /* Module ID                                */
    DC.L    0x5                                         /* Module Major Version                     */
    DC.L    0x3                                         /* Module Minor Version                     */
    DC.L    32                                          /* Module Preamble Size in 32-bit words     */
    DC.L    0x12345678                                  /* Module ID (application defined)          */
    DC.L    0x03000003                                  /* Module Properties where:                 */
                                                        /* Bits 31-24: Compiler ID                  */
                                                        /*           3 -> GHS                       */
                                                        /* Bits 23-2: Reserved                      */
                                                        /* Bit 1:  0 -> No MMU protection           */
                                                        /*         1 -> MMU protection (must have   */
                                                        /*              user mode selected)         */
                                                        /* Bit 0:  0 -> Supervisor mode execution   */
                                                        /*         1 -> User mode execution         */
    DC.L    _txm_module_thread_shell_entry              /* Module Shell Entry Point                 */
    DC.L    demo_module_start                           /* Module Start Thread Entry Point          */
    DC.L    0                                           /* Module Stop Thread Entry Point           */
    DC.L    1                                           /* Module Start/Stop Thread Priority        */
    DC.L    2048                                        /* Module Start/Stop Thread Stack Size      */
    DC.L    _txm_module_callback_request_thread_entry   /* Module Callback Thread Entry             */
    DC.L    1                                           /* Module Callback Thread Priority          */
    DC.L    2048                                        /* Module Callback Thread Stack Size        */
    DC.L    module_code_size                            /* Module Code Size                         */
    DC.L    module_data_size                            /* Module Data Size                         */
    DC.L    0                                           /* Reserved 0                               */
    DC.L    0                                           /* Reserved 1                               */
    DC.L    0                                           /* Reserved 2                               */
    DC.L    0                                           /* Reserved 3                               */
    DC.L    0                                           /* Reserved 4                               */
    DC.L    0                                           /* Reserved 5                               */
    DC.L    0                                           /* Reserved 6                               */
    DC.L    0                                           /* Reserved 7                               */
    DC.L    0                                           /* Reserved 8                               */
    DC.L    0                                           /* Reserved 9                               */
    DC.L    0                                           /* Reserved 10                              */
    DC.L    0                                           /* Reserved 11                              */
    DC.L    0                                           /* Reserved 12                              */
    DC.L    0                                           /* Reserved 13                              */
    DC.L    0                                           /* Reserved 14                              */
    DC.L    0                                           /* Reserved 15                              */

    END
```

#### <a name="module-properties-for-mcf544xx-using-ghs"></a><span data-ttu-id="f335e-961">Właściwości modułu dla MCF544xx przy użyciu GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-961">Module properties for MCF544xx using GHS</span></span>

| <span data-ttu-id="f335e-962">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-962">Bit</span></span> | <span data-ttu-id="f335e-963">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-963">Value</span></span> | <span data-ttu-id="f335e-964">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-964">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-965">0</span><span class="sxs-lookup"><span data-stu-id="f335e-965">0</span></span> | <span data-ttu-id="f335e-966">0</span><span class="sxs-lookup"><span data-stu-id="f335e-966">0</span></span><br /><span data-ttu-id="f335e-967">1</span><span class="sxs-lookup"><span data-stu-id="f335e-967">1</span></span> | <span data-ttu-id="f335e-968">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-968">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-969">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-969">User mode execution</span></span> |
| <span data-ttu-id="f335e-970">1</span><span class="sxs-lookup"><span data-stu-id="f335e-970">1</span></span> | <span data-ttu-id="f335e-971">0</span><span class="sxs-lookup"><span data-stu-id="f335e-971">0</span></span><br /><span data-ttu-id="f335e-972">1</span><span class="sxs-lookup"><span data-stu-id="f335e-972">1</span></span> | <span data-ttu-id="f335e-973">Brak ochrony pamięcią</span><span class="sxs-lookup"><span data-stu-id="f335e-973">No MMU protection</span></span><br /><span data-ttu-id="f335e-974">Ochrona pamięcią (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-974">MMU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-975">2</span><span class="sxs-lookup"><span data-stu-id="f335e-975">2</span></span> | <span data-ttu-id="f335e-976">0</span><span class="sxs-lookup"><span data-stu-id="f335e-976">0</span></span><br /><span data-ttu-id="f335e-977">1</span><span class="sxs-lookup"><span data-stu-id="f335e-977">1</span></span> | <span data-ttu-id="f335e-978">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-978">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-979">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-979">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-980">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-980">[23-3]</span></span> | <span data-ttu-id="f335e-981">0</span><span class="sxs-lookup"><span data-stu-id="f335e-981">0</span></span> | <span data-ttu-id="f335e-982">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-982">Reserved</span></span>
| <span data-ttu-id="f335e-983">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-983">[31-24]</span></span> | <br /><span data-ttu-id="f335e-984">0x03</span><span class="sxs-lookup"><span data-stu-id="f335e-984">0x03</span></span> | <span data-ttu-id="f335e-985">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-985">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-986">GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-986">GHS</span></span> |

#### <a name="module-linker-for-mcf544xx-using-ghs"></a><span data-ttu-id="f335e-987">Konsolidator modułu dla MCF544xx przy użyciu GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-987">Module linker for MCF544xx using GHS</span></span>

```c
DEFAULTS {

    heap_reserve =  256
    stack_reserve = 256
}

//
// Program layout for PIC and PID built programs.
//

-sec
{
//
// The data segment
//
    .pidbase                0x00000000 :
    .sdabase                           :
    .sbss                   NOCLEAR    :
    .sdata                             :
    .data                   NOLOAD     :
    .bss                    NOCLEAR    :
    .heap                   ALIGN(16) PAD( heap_reserve +
        // Add space for call-graph profiling if used:
        (isdefined(__ghs_indgcount)?(2000+(sizeof(.text)/2)):0) +
        // Add estimated space for call-count profiling if used:
        (isdefined(__ghs_indmcount)?10000:0) )
                                             :
    .stack      ALIGN(16) PAD(stack_reserve) :

    module_data_size = sizeof(.pidbase) + sizeof(.sdabase) + sizeof(.sbss) + sizeof(.sdata) + sizeof(.data) + sizeof(.bss) + sizeof(.heap) + sizeof(.stack);

//
// The code segment
//

    .picbase                0x00000000 :
    .preamble                          :
    .text                              :
    .syscall                           :
    .fixaddr                           :
    .fixtype                           :
    .rodata                            :
    .ROM.data               ROM(.data) :
    .secinfo                           :

    module_code_size =  endaddr(.secinfo);
}
```

#### <a name="building-modules-for-mcf544xx-using-ghs"></a><span data-ttu-id="f335e-988">Kompilowanie modułów dla MCF544xx za pomocą GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-988">Building Modules for MCF544xx using GHS</span></span>

<span data-ttu-id="f335e-989">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-989">An example workspace is provided.</span></span> <span data-ttu-id="f335e-990">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-990">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-mcf544xx-using-ghs"></a><span data-ttu-id="f335e-991">Definicja rozszerzenia wątku dla MCF544xx przy użyciu GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-991">Thread extension definition for MCF544xx using GHS</span></span>

```c
#define TX_THREAD_EXTENSION_2   int     Errno;                                  \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_mmu_protection;        \
                                VOID *  tx_thread_module_dispatch_return;       \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-mcf544xx-using-ghs"></a><span data-ttu-id="f335e-992">Kompilowanie Menedżera modułów dla MCF544xx przy użyciu GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-992">Building Module Manager for MCF544xx using GHS</span></span>

<span data-ttu-id="f335e-993">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-993">An example workspace is provided.</span></span> <span data-ttu-id="f335e-994">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-994">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-mcf544xx-using-ghs"></a><span data-ttu-id="f335e-995">Atrybuty pamięci zewnętrznej Włącz interfejs API dla MCF544xx za pomocą GHS</span><span class="sxs-lookup"><span data-stu-id="f335e-995">Attributes for external memory enable API for MCF544xx using GHS</span></span>

<span data-ttu-id="f335e-996">Ta funkcja nie jest włączona w systemie MCF544xx.</span><span class="sxs-lookup"><span data-stu-id="f335e-996">This feature not enabled on MCF544xx.</span></span>

## <a name="rx63-processor"></a><span data-ttu-id="f335e-997">Procesor RX63</span><span class="sxs-lookup"><span data-stu-id="f335e-997">RX63 processor</span></span>

### <a name="rx63-using-iar"></a><span data-ttu-id="f335e-998">RX63 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-998">RX63 using IAR</span></span>

#### <a name="module-preamble-for-rx63-using-iar"></a><span data-ttu-id="f335e-999">Preambuła modułu dla RX63 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-999">Module preamble for RX63 using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx63-using-iar"></a><span data-ttu-id="f335e-1000">Właściwości modułu dla RX63 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1000">Module properties for RX63 using IAR</span></span>

| <span data-ttu-id="f335e-1001">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-1001">Bit</span></span> | <span data-ttu-id="f335e-1002">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-1002">Value</span></span> | <span data-ttu-id="f335e-1003">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-1003">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-1004">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1004">0</span></span> | <span data-ttu-id="f335e-1005">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1005">0</span></span><br /><span data-ttu-id="f335e-1006">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1006">1</span></span> | <span data-ttu-id="f335e-1007">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-1007">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-1008">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-1008">User mode execution</span></span> |
| <span data-ttu-id="f335e-1009">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1009">1</span></span> | <span data-ttu-id="f335e-1010">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1010">0</span></span><br /><span data-ttu-id="f335e-1011">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1011">1</span></span> | <span data-ttu-id="f335e-1012">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-1012">No MPU protection</span></span><br /><span data-ttu-id="f335e-1013">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-1013">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-1014">2</span><span class="sxs-lookup"><span data-stu-id="f335e-1014">2</span></span> | <span data-ttu-id="f335e-1015">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1015">0</span></span><br /><span data-ttu-id="f335e-1016">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1016">1</span></span> | <span data-ttu-id="f335e-1017">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-1017">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-1018">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-1018">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-1019">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-1019">[23-3]</span></span> | <span data-ttu-id="f335e-1020">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1020">0</span></span> | <span data-ttu-id="f335e-1021">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-1021">Reserved</span></span>
| <span data-ttu-id="f335e-1022">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-1022">[31-24]</span></span> | <br /><span data-ttu-id="f335e-1023">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-1023">0x00</span></span><br /><span data-ttu-id="f335e-1024">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-1024">0x02</span></span> | <span data-ttu-id="f335e-1025">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-1025">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-1026">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1026">IAR</span></span><br /><span data-ttu-id="f335e-1027">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-1027">GNU</span></span> |

#### <a name="module-linker-for-rx63-using-iar"></a><span data-ttu-id="f335e-1028">Konsolidator modułu dla RX63 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1028">Module linker for RX63 using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F563NB
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx63n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx63-using-iar"></a><span data-ttu-id="f335e-1029">Kompilowanie modułów dla RX63 za pomocą IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1029">Building Modules for RX63 using IAR</span></span>

<span data-ttu-id="f335e-1030">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-1030">An example workspace is provided.</span></span> <span data-ttu-id="f335e-1031">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-1031">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rxrx635n-using-iar"></a><span data-ttu-id="f335e-1032">Definicja rozszerzenia wątku dla RXRX635N przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1032">Thread extension definition for RXRX635N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;       \
                                VOID    *tx_thread_module_entry_info_ptr;     \
                                ULONG   tx_thread_module_current_user_mode;   \
                                ULONG   tx_thread_module_user_mode;           \
                                VOID    *tx_thread_module_kernel_stack_start; \
                                VOID    *tx_thread_module_kernel_stack_end;   \
                                ULONG   tx_thread_module_kernel_stack_size;   \
                                VOID    *tx_thread_module_stack_ptr;          \
                                VOID    *tx_thread_module_stack_start;        \
                                VOID    *tx_thread_module_stack_end;          \
                                ULONG   tx_thread_module_stack_size;          \
                                VOID    *tx_thread_module_reserved;           \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx63-using-iar"></a><span data-ttu-id="f335e-1033">Kompilowanie Menedżera modułów dla RX63 przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1033">Building Module Manager for RX63 using IAR</span></span>

<span data-ttu-id="f335e-1034">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-1034">An example workspace is provided.</span></span> <span data-ttu-id="f335e-1035">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-1035">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx63-using-iar"></a><span data-ttu-id="f335e-1036">Atrybuty pamięci zewnętrznej Włącz interfejs API dla RX63 za pomocą IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1036">Attributes for external memory enable API for RX63 using IAR</span></span>

| <span data-ttu-id="f335e-1037">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-1037">Attribute Parameter</span></span> | <span data-ttu-id="f335e-1038">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-1038">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="f335e-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="f335e-1040">Wykonaj kod</span><span class="sxs-lookup"><span data-stu-id="f335e-1040">Execute code</span></span> |
| <span data-ttu-id="f335e-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-1042">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-1042">Write access</span></span> |
| <span data-ttu-id="f335e-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="f335e-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="f335e-1044">Dostęp do odczytu</span><span class="sxs-lookup"><span data-stu-id="f335e-1044">Read access</span></span> |

## <a name="rx65n-processor"></a><span data-ttu-id="f335e-1045">Procesor RX65N</span><span class="sxs-lookup"><span data-stu-id="f335e-1045">RX65N processor</span></span>

### <a name="rx65n-using-iar"></a><span data-ttu-id="f335e-1046">RX65N przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1046">RX65N using IAR</span></span>

#### <a name="module-preamble-for-rx65n-using-iar"></a><span data-ttu-id="f335e-1047">Preambuła modułu dla RX65N przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1047">Module preamble for RX65N using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx65n-using-iar"></a><span data-ttu-id="f335e-1048">Właściwości modułu dla RX65N przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1048">Module properties for RX65N using IAR</span></span>

| <span data-ttu-id="f335e-1049">Bit</span><span class="sxs-lookup"><span data-stu-id="f335e-1049">Bit</span></span> | <span data-ttu-id="f335e-1050">Wartość</span><span class="sxs-lookup"><span data-stu-id="f335e-1050">Value</span></span> | <span data-ttu-id="f335e-1051">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-1051">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="f335e-1052">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1052">0</span></span> | <span data-ttu-id="f335e-1053">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1053">0</span></span><br /><span data-ttu-id="f335e-1054">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1054">1</span></span> | <span data-ttu-id="f335e-1055">Wykonywanie trybu uprzywilejowanego</span><span class="sxs-lookup"><span data-stu-id="f335e-1055">Privileged mode execution</span></span><br /><span data-ttu-id="f335e-1056">Wykonywanie w trybie użytkownika</span><span class="sxs-lookup"><span data-stu-id="f335e-1056">User mode execution</span></span> |
| <span data-ttu-id="f335e-1057">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1057">1</span></span> | <span data-ttu-id="f335e-1058">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1058">0</span></span><br /><span data-ttu-id="f335e-1059">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1059">1</span></span> | <span data-ttu-id="f335e-1060">Brak ochrony MPU</span><span class="sxs-lookup"><span data-stu-id="f335e-1060">No MPU protection</span></span><br /><span data-ttu-id="f335e-1061">Ochrona MPU (musi być wybrana w trybie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="f335e-1061">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="f335e-1062">2</span><span class="sxs-lookup"><span data-stu-id="f335e-1062">2</span></span> | <span data-ttu-id="f335e-1063">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1063">0</span></span><br /><span data-ttu-id="f335e-1064">1</span><span class="sxs-lookup"><span data-stu-id="f335e-1064">1</span></span> | <span data-ttu-id="f335e-1065">Wyłącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-1065">Disable shared/external memory access</span></span><br /><span data-ttu-id="f335e-1066">Włącz dostęp do pamięci współdzielonej/zewnętrznej</span><span class="sxs-lookup"><span data-stu-id="f335e-1066">Enable shared/external memory access</span></span> |
| <span data-ttu-id="f335e-1067">[23-3]</span><span class="sxs-lookup"><span data-stu-id="f335e-1067">[23-3]</span></span> | <span data-ttu-id="f335e-1068">0</span><span class="sxs-lookup"><span data-stu-id="f335e-1068">0</span></span> | <span data-ttu-id="f335e-1069">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="f335e-1069">Reserved</span></span>
| <span data-ttu-id="f335e-1070">[31-24]</span><span class="sxs-lookup"><span data-stu-id="f335e-1070">[31-24]</span></span> | <br /><span data-ttu-id="f335e-1071">0x00</span><span class="sxs-lookup"><span data-stu-id="f335e-1071">0x00</span></span><br /><span data-ttu-id="f335e-1072">0x02</span><span class="sxs-lookup"><span data-stu-id="f335e-1072">0x02</span></span> | <span data-ttu-id="f335e-1073">**Identyfikator kompilatora**</span><span class="sxs-lookup"><span data-stu-id="f335e-1073">**Compiler ID**</span></span><br /><span data-ttu-id="f335e-1074">IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1074">IAR</span></span><br /><span data-ttu-id="f335e-1075">GNU</span><span class="sxs-lookup"><span data-stu-id="f335e-1075">GNU</span></span> |

#### <a name="module-linker-for-rx65n-using-iar"></a><span data-ttu-id="f335e-1076">Konsolidator modułu dla RX65N przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1076">Module linker for RX65N using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F565N
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx65n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx65n-using-iar"></a><span data-ttu-id="f335e-1077">Kompilowanie modułów dla RX65N za pomocą IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1077">Building Modules for RX65N using IAR</span></span>

<span data-ttu-id="f335e-1078">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-1078">An example workspace is provided.</span></span> <span data-ttu-id="f335e-1079">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-1079">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rx65n-using-iar"></a><span data-ttu-id="f335e-1080">Definicja rozszerzenia wątku dla RX65N przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1080">Thread extension definition for RX65N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx65n-using-iar"></a><span data-ttu-id="f335e-1081">Kompilowanie Menedżera modułów dla RX65N przy użyciu IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1081">Building Module Manager for RX65N using IAR</span></span>

<span data-ttu-id="f335e-1082">Podano przykładowy obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="f335e-1082">An example workspace is provided.</span></span> <span data-ttu-id="f335e-1083">Kompiluj bibliotekę ThreadX, bibliotekę modułów ThreadX, projekt modułu pokazowego i projekt Menedżera modułów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f335e-1083">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx65n-using-iar"></a><span data-ttu-id="f335e-1084">Atrybuty pamięci zewnętrznej Włącz interfejs API dla RX65N za pomocą IAR</span><span class="sxs-lookup"><span data-stu-id="f335e-1084">Attributes for external memory enable API for RX65N using IAR</span></span>

| <span data-ttu-id="f335e-1085">Parametr atrybutu</span><span class="sxs-lookup"><span data-stu-id="f335e-1085">Attribute Parameter</span></span> | <span data-ttu-id="f335e-1086">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f335e-1086">Meaning</span></span> |
|---|---|
| <span data-ttu-id="f335e-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="f335e-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="f335e-1088">Wykonaj kod</span><span class="sxs-lookup"><span data-stu-id="f335e-1088">Execute code</span></span> |
| <span data-ttu-id="f335e-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="f335e-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="f335e-1090">Dostęp do zapisu</span><span class="sxs-lookup"><span data-stu-id="f335e-1090">Write access</span></span> |
| <span data-ttu-id="f335e-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="f335e-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="f335e-1092">Dostęp do odczytu</span><span class="sxs-lookup"><span data-stu-id="f335e-1092">Read access</span></span> |
