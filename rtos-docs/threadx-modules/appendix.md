---
title: Apêndice - Exemplos específicos do porto
description: Este artigo mostra exemplos específicos da porta para módulos ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c2324a2057bf2ddb2d255b2ff611d34fc664560a
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549815"
---
# <a name="appendix---port-specific-examples"></a><span data-ttu-id="dd40e-103">Apêndice - Exemplos específicos do porto</span><span class="sxs-lookup"><span data-stu-id="dd40e-103">Appendix - Port-specific examples</span></span>

## <a name="arm11-processor"></a><span data-ttu-id="dd40e-104">Processador ARM11</span><span class="sxs-lookup"><span data-stu-id="dd40e-104">ARM11 processor</span></span>

### <a name="arm11-using-gcc"></a><span data-ttu-id="dd40e-105">ARM11 usando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-105">ARM11 using GCC</span></span>

#### <a name="module-preamble-for-arm11-using-gcc"></a><span data-ttu-id="dd40e-106">Preâmbulo do módulo para ARM11 utilizando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-106">Module preamble for ARM11 using GCC</span></span>

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

#### <a name="module-properties-for-arm11-using-gcc"></a><span data-ttu-id="dd40e-107">Propriedades do módulo para ARM11 usando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-107">Module properties for ARM11 using GCC</span></span>

| <span data-ttu-id="dd40e-108">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-108">Bit</span></span> | <span data-ttu-id="dd40e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-109">Value</span></span> | <span data-ttu-id="dd40e-110">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-110">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-111">[23-0]</span><span class="sxs-lookup"><span data-stu-id="dd40e-111">[23-0]</span></span> | <span data-ttu-id="dd40e-112">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-112">0</span></span> | <span data-ttu-id="dd40e-113">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-113">Reserved</span></span>
| <span data-ttu-id="dd40e-114">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-114">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-115">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-115">0x00</span></span><br /><span data-ttu-id="dd40e-116">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-116">0x01</span></span><br /><span data-ttu-id="dd40e-117">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-117">0x02</span></span> | <span data-ttu-id="dd40e-118">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-118">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-119">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-119">IAR</span></span><br /><span data-ttu-id="dd40e-120">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-120">ARM</span></span><br /><span data-ttu-id="dd40e-121">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-121">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-gcc"></a><span data-ttu-id="dd40e-122">Linker do módulo para ARM11 usando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-122">Module linker for ARM11 using GCC</span></span>

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

#### <a name="building-modules-for-arm11-using-gcc"></a><span data-ttu-id="dd40e-123">Módulos de construção para ARM11 usando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-123">Building Modules for ARM11 using GCC</span></span>

<span data-ttu-id="dd40e-124">Um exemplo simples de linha de comando para a construção de um módulo ARM11 utilizando gCC:</span><span class="sxs-lookup"><span data-stu-id="dd40e-124">A simple command-line example for building an ARM11 module using GCC:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 txm_module_preamble.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 demo_threadx_module.c
arm-none-eabi-ld -A arm1136j-s -T demo_threadx_module.ld txm_module_preamble.o gcc_setup.o demo_threadx_module.o txm.a txm.a -o demo_threadx_module.out -M > demo_threadx_module.map
```

#### <a name="thread-extension-definition-for-arm11-using-gcc"></a><span data-ttu-id="dd40e-125">Definição de extensão de fio para ARM11 usando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-125">Thread extension definition for ARM11 using GCC</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-gcc"></a><span data-ttu-id="dd40e-126">Gestor de módulos de construção para ARM11 usando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-126">Building Module Manager for ARM11 using GCC</span></span>

<span data-ttu-id="dd40e-127">Não é dado nenhum exemplo.</span><span class="sxs-lookup"><span data-stu-id="dd40e-127">No example is provided.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-gcc"></a><span data-ttu-id="dd40e-128">Atributos para memória externa permitem a API para ARM11 usando GCC</span><span class="sxs-lookup"><span data-stu-id="dd40e-128">Attributes for external memory enable API for ARM11 using GCC</span></span>

<span data-ttu-id="dd40e-129">Esta funcionalidade não está ativada nesta porta.</span><span class="sxs-lookup"><span data-stu-id="dd40e-129">This feature not enabled on this port.</span></span>

### <a name="arm11-using-ac5"></a><span data-ttu-id="dd40e-130">ARM11 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-130">ARM11 using AC5</span></span>

#### <a name="module-preamble-for-arm11-using-ac5"></a><span data-ttu-id="dd40e-131">Preâmbulo do módulo para ARM11 utilizando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-131">Module preamble for ARM11 using AC5</span></span>

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

#### <a name="module-properties-for-arm11-using-ac5"></a><span data-ttu-id="dd40e-132">Propriedades do módulo para ARM11 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-132">Module properties for ARM11 using AC5</span></span>

| <span data-ttu-id="dd40e-133">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-133">Bit</span></span> | <span data-ttu-id="dd40e-134">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-134">Value</span></span> | <span data-ttu-id="dd40e-135">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-135">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-136">[23-0]</span><span class="sxs-lookup"><span data-stu-id="dd40e-136">[23-0]</span></span> | <span data-ttu-id="dd40e-137">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-137">0</span></span> | <span data-ttu-id="dd40e-138">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-138">Reserved</span></span>
| <span data-ttu-id="dd40e-139">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-139">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-140">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-140">0x00</span></span><br /><span data-ttu-id="dd40e-141">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-141">0x01</span></span><br /><span data-ttu-id="dd40e-142">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-142">0x02</span></span> | <span data-ttu-id="dd40e-143">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-143">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-144">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-144">IAR</span></span><br /><span data-ttu-id="dd40e-145">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-145">ARM</span></span><br /><span data-ttu-id="dd40e-146">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-146">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-ac5"></a><span data-ttu-id="dd40e-147">Linker do módulo para ARM11 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-147">Module linker for ARM11 using AC5</span></span>

<span data-ttu-id="dd40e-148">Construído na linha de comando, nenhum exemplo de ficheiro linker.</span><span class="sxs-lookup"><span data-stu-id="dd40e-148">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-arm11-using-ac5"></a><span data-ttu-id="dd40e-149">Módulos de construção para ARM11 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-149">Building Modules for ARM11 using AC5</span></span>

<span data-ttu-id="dd40e-150">Um exemplo simples de linha de comando para a construção de um módulo ARM11 utilizando AC5:</span><span class="sxs-lookup"><span data-stu-id="dd40e-150">A simple command-line example for building an ARM11 module using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi txm_module_preamble.s
armcc -g -c -O0 --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-arm11-using-ac5"></a><span data-ttu-id="dd40e-151">Definição de extensão de fio para ARM11 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-151">Thread extension definition for ARM11 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-ac5"></a><span data-ttu-id="dd40e-152">Gestor de módulos de construção para ARM11 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-152">Building Module Manager for ARM11 using AC5</span></span>

<span data-ttu-id="dd40e-153">Um exemplo simples de linha de comando para a construção de um gestor de módulos ARM11 utilizando AC5:</span><span class="sxs-lookup"><span data-stu-id="dd40e-153">A simple command-line example for building an ARM11 module manager using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork tx_initialize_low_level.s
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork demo_threadx_module_manager.c
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0 --first tx_initialize_low_level.o(Init) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-ac5"></a><span data-ttu-id="dd40e-154">Atributos para memória externa permitem a API para ARM11 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-154">Attributes for external memory enable API for ARM11 using AC5</span></span>

<span data-ttu-id="dd40e-155">Esta funcionalidade não está ativada nesta porta.</span><span class="sxs-lookup"><span data-stu-id="dd40e-155">This feature not enabled on this port.</span></span>

## <a name="cortex-a7-processor"></a><span data-ttu-id="dd40e-156">Processador Córtex-A7</span><span class="sxs-lookup"><span data-stu-id="dd40e-156">Cortex-A7 processor</span></span>

### <a name="cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-157">Córtex-A7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-157">Cortex-A7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-158">Preâmbulo do módulo para o Córtex-A7 utilizando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-158">Module preamble for Cortex-A7 using AC5</span></span>

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

#### <a name="module-properties-for-cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-159">Propriedades do módulo para Cortex-A7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-159">Module properties for Cortex-A7 using AC5</span></span>

| <span data-ttu-id="dd40e-160">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-160">Bit</span></span> | <span data-ttu-id="dd40e-161">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-161">Value</span></span> | <span data-ttu-id="dd40e-162">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-162">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-163">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-163">0</span></span> | <span data-ttu-id="dd40e-164">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-164">0</span></span><br /><span data-ttu-id="dd40e-165">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-165">1</span></span> | <span data-ttu-id="dd40e-166">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-166">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-167">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-167">User mode execution</span></span> |
| <span data-ttu-id="dd40e-168">[23-1]</span><span class="sxs-lookup"><span data-stu-id="dd40e-168">[23-1]</span></span> | <span data-ttu-id="dd40e-169">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-169">0</span></span> | <span data-ttu-id="dd40e-170">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-170">Reserved</span></span>
| <span data-ttu-id="dd40e-171">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-171">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-172">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-172">0x00</span></span><br /><span data-ttu-id="dd40e-173">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-173">0x01</span></span><br /><span data-ttu-id="dd40e-174">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-174">0x02</span></span> | <span data-ttu-id="dd40e-175">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-175">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-176">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-176">IAR</span></span><br /><span data-ttu-id="dd40e-177">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-177">ARM</span></span><br /><span data-ttu-id="dd40e-178">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-178">GNU</span></span> |

#### <a name="module-linker-for-cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-179">Linker do módulo para Cortex-A7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-179">Module linker for Cortex-A7 using AC5</span></span>

<span data-ttu-id="dd40e-180">Construído na linha de comando, nenhum exemplo de ficheiro linker.</span><span class="sxs-lookup"><span data-stu-id="dd40e-180">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-181">Módulos de construção para córtex-A7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-181">Building Modules for Cortex-A7 using AC5</span></span>

<span data-ttu-id="dd40e-182">Um exemplo simples de linha de comando para a construção de um módulo Córtex-A7 utilizando AC5:</span><span class="sxs-lookup"><span data-stu-id="dd40e-182">A simple command-line example for building a Cortex-A7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-a7.no_neon --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-183">Definição de extensão de fio para córtex-A7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-183">Thread extension definition for Cortex-A7 using AC5</span></span>

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

#### <a name="building-module-manager-for-cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-184">Gestor de módulos de construção para Cortex-A7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-184">Building Module Manager for Cortex-A7 using AC5</span></span>

<span data-ttu-id="dd40e-185">Um exemplo simples de linha de comando para a construção de um gestor de módulos Cortex-A7 utilizando AC5:</span><span class="sxs-lookup"><span data-stu-id="dd40e-185">A simple command-line example for building a Cortex-A7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x80000000 --first tx_initialize_low_level.o(VECTORS) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-a7-using-ac5"></a><span data-ttu-id="dd40e-186">Atributos para memória externa permitem API para córtex-A7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-186">Attributes for external memory enable API for Cortex-A7 using AC5</span></span>

<span data-ttu-id="dd40e-187">Os seguintes atributos podem ser utilizados para configurar definições de memória partilhada:</span><span class="sxs-lookup"><span data-stu-id="dd40e-187">The following attributes can be used to set up shared memory settings:</span></span>

| <span data-ttu-id="dd40e-188">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-188">Attribute parameter</span></span> | <span data-ttu-id="dd40e-189">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-189">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-190">TXM_MMU_ATTRIBUTE_XN</span><span class="sxs-lookup"><span data-stu-id="dd40e-190">TXM_MMU_ATTRIBUTE_XN</span></span> | <span data-ttu-id="dd40e-191">Executar Nunca</span><span class="sxs-lookup"><span data-stu-id="dd40e-191">Execute Never</span></span> |
| <span data-ttu-id="dd40e-192">TXM_MMU_ATTRIBUTE_B</span><span class="sxs-lookup"><span data-stu-id="dd40e-192">TXM_MMU_ATTRIBUTE_B</span></span> | <span data-ttu-id="dd40e-193">Definição B</span><span class="sxs-lookup"><span data-stu-id="dd40e-193">B setting</span></span> |
| <span data-ttu-id="dd40e-194">TXM_MMU_ATTRIBUTE_C</span><span class="sxs-lookup"><span data-stu-id="dd40e-194">TXM_MMU_ATTRIBUTE_C</span></span> | <span data-ttu-id="dd40e-195">Definição C</span><span class="sxs-lookup"><span data-stu-id="dd40e-195">C setting</span></span> |
| <span data-ttu-id="dd40e-196">TXM_MMU_ATTRIBUTE_AP</span><span class="sxs-lookup"><span data-stu-id="dd40e-196">TXM_MMU_ATTRIBUTE_AP</span></span> | <span data-ttu-id="dd40e-197">Definição AP</span><span class="sxs-lookup"><span data-stu-id="dd40e-197">AP setting</span></span> |
| <span data-ttu-id="dd40e-198">TXM_MMU_ATTRIBUTE_TEX</span><span class="sxs-lookup"><span data-stu-id="dd40e-198">TXM_MMU_ATTRIBUTE_TEX</span></span> | <span data-ttu-id="dd40e-199">Definição de TEX</span><span class="sxs-lookup"><span data-stu-id="dd40e-199">TEX setting</span></span> |

<span data-ttu-id="dd40e-200">Consulte a documentação da ARM sobre a configuração destas definições.</span><span class="sxs-lookup"><span data-stu-id="dd40e-200">See ARM documentation for how these settings are configured.</span></span>

## <a name="cortex-m3-processor"></a><span data-ttu-id="dd40e-201">Processador Córtex-M3</span><span class="sxs-lookup"><span data-stu-id="dd40e-201">Cortex-M3 processor</span></span>

### <a name="cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-202">Córtex-M3 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-202">Cortex-M3 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-203">Preâmbulo do módulo para o Córtex-M3 utilizando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-203">Module preamble for Cortex-M3 using AC5</span></span>

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

#### <a name="module-properties-for-cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-204">Propriedades do módulo para Cortex-M3 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-204">Module properties for Cortex-M3 using AC5</span></span>

| <span data-ttu-id="dd40e-205">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-205">Bit</span></span> | <span data-ttu-id="dd40e-206">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-206">Value</span></span> | <span data-ttu-id="dd40e-207">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-207">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-208">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-208">0</span></span> | <span data-ttu-id="dd40e-209">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-209">0</span></span><br /><span data-ttu-id="dd40e-210">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-210">1</span></span> | <span data-ttu-id="dd40e-211">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-211">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-212">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-212">User mode execution</span></span> |
| <span data-ttu-id="dd40e-213">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-213">1</span></span> | <span data-ttu-id="dd40e-214">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-214">0</span></span><br /><span data-ttu-id="dd40e-215">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-215">1</span></span> | <span data-ttu-id="dd40e-216">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-216">No MPU protection</span></span><br /><span data-ttu-id="dd40e-217">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-217">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-218">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-218">2</span></span> | <span data-ttu-id="dd40e-219">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-219">0</span></span><br /><span data-ttu-id="dd40e-220">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-220">1</span></span> | <span data-ttu-id="dd40e-221">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-221">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-222">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-222">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-223">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-223">[23-3]</span></span> | <span data-ttu-id="dd40e-224">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-224">0</span></span> | <span data-ttu-id="dd40e-225">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-225">Reserved</span></span>
| <span data-ttu-id="dd40e-226">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-226">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-227">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-227">0x00</span></span><br /><span data-ttu-id="dd40e-228">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-228">0x01</span></span><br /><span data-ttu-id="dd40e-229">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-229">0x02</span></span> | <span data-ttu-id="dd40e-230">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-230">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-231">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-231">IAR</span></span><br /><span data-ttu-id="dd40e-232">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-232">ARM</span></span><br /><span data-ttu-id="dd40e-233">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-233">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-234">Linker do módulo para Cortex-M3 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-234">Module linker for Cortex-M3 using AC5</span></span>

<span data-ttu-id="dd40e-235">Não é fornecido nenhum ficheiro de linker de exemplo; a ligação é feita na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dd40e-235">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="dd40e-236">Veja a próxima secção.</span><span class="sxs-lookup"><span data-stu-id="dd40e-236">See next section.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-237">Módulos de construção para córtex-M3 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-237">Building Modules for Cortex-M3 using AC5</span></span>

<span data-ttu-id="dd40e-238">Um script de construção de exemplo é fornecido:</span><span class="sxs-lookup"><span data-stu-id="dd40e-238">An example build script is provided:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m3 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-239">Definição de extensão de fio para córtex-M3 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-239">Thread extension definition for Cortex-M3 using AC5</span></span>

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

#### <a name="building-module-manager-for-cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-240">Gestor de módulos de construção para Cortex-M3 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-240">Building Module Manager for Cortex-M3 using AC5</span></span>

<span data-ttu-id="dd40e-241">Veja o exemplo build_threadx_module_manager_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-241">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m3 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac5"></a><span data-ttu-id="dd40e-242">Atributos para memória externa permitem API para córtex-M3 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-242">Attributes for external memory enable API for Cortex-M3 using AC5</span></span>

<span data-ttu-id="dd40e-243">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-243">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-244">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-244">Attribute parameter</span></span> | <span data-ttu-id="dd40e-245">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-245">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-247">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-247">Write access</span></span> |

### <a name="cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-248">Córtex-M3 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-248">Cortex-M3 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-249">Preâmbulo do módulo para o Córtex-M3 utilizando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-249">Module preamble for Cortex-M3 using AC6</span></span>

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

#### <a name="module-properties-for-cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-250">Propriedades do módulo para Cortex-M3 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-250">Module properties for Cortex-M3 using AC6</span></span>

| <span data-ttu-id="dd40e-251">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-251">Bit</span></span> | <span data-ttu-id="dd40e-252">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-252">Value</span></span> | <span data-ttu-id="dd40e-253">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-253">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-254">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-254">0</span></span> | <span data-ttu-id="dd40e-255">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-255">0</span></span><br /><span data-ttu-id="dd40e-256">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-256">1</span></span> | <span data-ttu-id="dd40e-257">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-257">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-258">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-258">User mode execution</span></span> |
| <span data-ttu-id="dd40e-259">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-259">1</span></span> | <span data-ttu-id="dd40e-260">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-260">0</span></span><br /><span data-ttu-id="dd40e-261">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-261">1</span></span> | <span data-ttu-id="dd40e-262">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-262">No MPU protection</span></span><br /><span data-ttu-id="dd40e-263">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-263">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-264">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-264">2</span></span> | <span data-ttu-id="dd40e-265">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-265">0</span></span><br /><span data-ttu-id="dd40e-266">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-266">1</span></span> | <span data-ttu-id="dd40e-267">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-267">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-268">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-268">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-269">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-269">[23-3]</span></span> | <span data-ttu-id="dd40e-270">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-270">0</span></span> | <span data-ttu-id="dd40e-271">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-271">Reserved</span></span>
| <span data-ttu-id="dd40e-272">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-272">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-273">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-273">0x00</span></span><br /><span data-ttu-id="dd40e-274">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-274">0x01</span></span><br /><span data-ttu-id="dd40e-275">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-275">0x02</span></span> | <span data-ttu-id="dd40e-276">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-276">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-277">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-277">IAR</span></span><br /><span data-ttu-id="dd40e-278">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-278">ARM</span></span><br /><span data-ttu-id="dd40e-279">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-279">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-280">Linker do módulo para Cortex-M3 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-280">Module linker for Cortex-M3 using AC6</span></span>

<span data-ttu-id="dd40e-281">Não é utilizado nenhum ficheiro linker.</span><span class="sxs-lookup"><span data-stu-id="dd40e-281">No linker file is used.</span></span> <span data-ttu-id="dd40e-282">Consulte as definições do projeto.</span><span class="sxs-lookup"><span data-stu-id="dd40e-282">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-283">Módulos de construção para córtex-M3 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-283">Building Modules for Cortex-M3 using AC6</span></span>

<span data-ttu-id="dd40e-284">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-284">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-285">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de amostra e o projeto de gestor de módulos de amostra.</span><span class="sxs-lookup"><span data-stu-id="dd40e-285">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-286">Definição de extensão de fio para córtex-M3 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-286">Thread extension definition for Cortex-M3 using AC6</span></span>

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

#### <a name="building-module-manager-for-cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-287">Gestor de módulos de construção para Cortex-M3 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-287">Building Module Manager for Cortex-M3 using AC6</span></span>

<span data-ttu-id="dd40e-288">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-288">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-289">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de amostra e o projeto de gestor de módulos de amostra.</span><span class="sxs-lookup"><span data-stu-id="dd40e-289">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac6"></a><span data-ttu-id="dd40e-290">Atributos para memória externa permitem API para córtex-M3 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-290">Attributes for external memory enable API for Cortex-M3 using AC6</span></span>

<span data-ttu-id="dd40e-291">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-291">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-292">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-292">Attribute parameter</span></span> | <span data-ttu-id="dd40e-293">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-293">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-295">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-295">Write access</span></span> |

### <a name="cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-296">Córtex-M3 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-296">Cortex-M3 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-297">Preâmbulo do módulo para o Córtex-M3 utilizando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-297">Module preamble for Cortex-M3 using GNU</span></span>

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

#### <a name="module-properties-for-cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-298">Propriedades do módulo para Cortex-M3 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-298">Module properties for Cortex-M3 using GNU</span></span>

| <span data-ttu-id="dd40e-299">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-299">Bit</span></span> | <span data-ttu-id="dd40e-300">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-300">Value</span></span> | <span data-ttu-id="dd40e-301">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-301">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-302">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-302">0</span></span> | <span data-ttu-id="dd40e-303">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-303">0</span></span><br /><span data-ttu-id="dd40e-304">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-304">1</span></span> | <span data-ttu-id="dd40e-305">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-305">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-306">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-306">User mode execution</span></span> |
| <span data-ttu-id="dd40e-307">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-307">1</span></span> | <span data-ttu-id="dd40e-308">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-308">0</span></span><br /><span data-ttu-id="dd40e-309">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-309">1</span></span> | <span data-ttu-id="dd40e-310">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-310">No MPU protection</span></span><br /><span data-ttu-id="dd40e-311">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-311">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-312">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-312">2</span></span> | <span data-ttu-id="dd40e-313">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-313">0</span></span><br /><span data-ttu-id="dd40e-314">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-314">1</span></span> | <span data-ttu-id="dd40e-315">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-315">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-316">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-316">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-317">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-317">[23-3]</span></span> | <span data-ttu-id="dd40e-318">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-318">0</span></span> | <span data-ttu-id="dd40e-319">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-319">Reserved</span></span>
| <span data-ttu-id="dd40e-320">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-320">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-321">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-321">0x00</span></span><br /><span data-ttu-id="dd40e-322">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-322">0x01</span></span><br /><span data-ttu-id="dd40e-323">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-323">0x02</span></span> | <span data-ttu-id="dd40e-324">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-324">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-325">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-325">IAR</span></span><br /><span data-ttu-id="dd40e-326">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-326">ARM</span></span><br /><span data-ttu-id="dd40e-327">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-327">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-328">Linker do módulo para Cortex-M3 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-328">Module linker for Cortex-M3 using GNU</span></span>

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

#### <a name="building-modules-for-cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-329">Módulos de construção para córtex-M3 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-329">Building Modules for Cortex-M3 using GNU</span></span>

<span data-ttu-id="dd40e-330">Ver build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-330">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m3 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-331">Definição de extensão de fio para córtex-M3 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-331">Thread extension definition for Cortex-M3 using GNU</span></span>

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

#### <a name="building-module-manager-for-cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-332">Gestor de módulos de construção para o Cortex-M3 usando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-332">Building Module Manager for Cortex-M3 using GNU</span></span>

<span data-ttu-id="dd40e-333">Ver build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-333">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb cortexm_crt0.S
arm-none-eabi-ld -A cortex-m3 -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a  libc.a -o sample_threadx_module_manager.axf -M > sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-gnu"></a><span data-ttu-id="dd40e-334">Atributos para memória externa permitem API para córtex-M3 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-334">Attributes for external memory enable API for Cortex-M3 using GNU</span></span>

<span data-ttu-id="dd40e-335">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-335">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-336">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-336">Attribute parameter</span></span> | <span data-ttu-id="dd40e-337">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-337">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-339">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-339">Write access</span></span> |

### <a name="cortex-m3-using-iar"></a><span data-ttu-id="dd40e-340">Córtex-M3 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-340">Cortex-M3 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m3-using-iar"></a><span data-ttu-id="dd40e-341">Preâmbulo do módulo para o Córtex-M3 utilizando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-341">Module preamble for Cortex-M3 using IAR</span></span>

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

#### <a name="module-properties-for-cortex-m3-using-iar"></a><span data-ttu-id="dd40e-342">Propriedades do módulo para Cortex-M3 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-342">Module properties for Cortex-M3 using IAR</span></span>

| <span data-ttu-id="dd40e-343">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-343">Bit</span></span> | <span data-ttu-id="dd40e-344">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-344">Value</span></span> | <span data-ttu-id="dd40e-345">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-345">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-346">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-346">0</span></span> | <span data-ttu-id="dd40e-347">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-347">0</span></span><br /><span data-ttu-id="dd40e-348">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-348">1</span></span> | <span data-ttu-id="dd40e-349">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-349">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-350">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-350">User mode execution</span></span> |
| <span data-ttu-id="dd40e-351">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-351">1</span></span> | <span data-ttu-id="dd40e-352">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-352">0</span></span><br /><span data-ttu-id="dd40e-353">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-353">1</span></span> | <span data-ttu-id="dd40e-354">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-354">No MPU protection</span></span><br /><span data-ttu-id="dd40e-355">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-355">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-356">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-356">2</span></span> | <span data-ttu-id="dd40e-357">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-357">0</span></span><br /><span data-ttu-id="dd40e-358">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-358">1</span></span> | <span data-ttu-id="dd40e-359">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-359">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-360">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-360">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-361">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-361">[23-3]</span></span> | <span data-ttu-id="dd40e-362">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-362">0</span></span> | <span data-ttu-id="dd40e-363">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-363">Reserved</span></span>
| <span data-ttu-id="dd40e-364">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-364">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-365">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-365">0x00</span></span><br /><span data-ttu-id="dd40e-366">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-366">0x01</span></span><br /><span data-ttu-id="dd40e-367">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-367">0x02</span></span> | <span data-ttu-id="dd40e-368">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-368">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-369">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-369">IAR</span></span><br /><span data-ttu-id="dd40e-370">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-370">ARM</span></span><br /><span data-ttu-id="dd40e-371">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-371">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-iar"></a><span data-ttu-id="dd40e-372">Linker do módulo para córtex-M3 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-372">Module linker for Cortex-M3 using IAR</span></span>

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

#### <a name="building-modules-for-cortex-m3-using-iar"></a><span data-ttu-id="dd40e-373">Módulos de construção para córtex-M3 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-373">Building Modules for Cortex-M3 using IAR</span></span>

<span data-ttu-id="dd40e-374">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-374">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-375">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-375">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-iar"></a><span data-ttu-id="dd40e-376">Definição de extensão de fio para córtex-M3 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-376">Thread extension definition for Cortex-M3 using IAR</span></span>

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

#### <a name="building-module-manager-for-cortex-m3-using-iar"></a><span data-ttu-id="dd40e-377">Gestor de módulos de construção para Cortex-M3 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-377">Building Module Manager for Cortex-M3 using IAR</span></span>

<span data-ttu-id="dd40e-378">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-378">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-379">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-379">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-iar"></a><span data-ttu-id="dd40e-380">Atributos para memória externa permitem a API para o Córtex-M3 usando O IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-380">Attributes for external memory enable API for Cortex-M3 using IAR</span></span>

<span data-ttu-id="dd40e-381">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-381">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-382">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-382">Attribute parameter</span></span> | <span data-ttu-id="dd40e-383">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-383">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-385">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-385">Write access</span></span> |

## <a name="cortex-m33-processor"></a><span data-ttu-id="dd40e-386">Processador Córtex-M33</span><span class="sxs-lookup"><span data-stu-id="dd40e-386">Cortex-M33 processor</span></span>

### <a name="cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-387">Córtex-M33 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-387">Cortex-M33 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-388">Preâmbulo do módulo para o Córtex-M33 utilizando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-388">Module preamble for Cortex-M33 using AC6</span></span>

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

#### <a name="module-properties-for-cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-389">Propriedades do módulo para Cortex-M33 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-389">Module properties for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="dd40e-390">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-390">Bit</span></span> | <span data-ttu-id="dd40e-391">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-391">Value</span></span> | <span data-ttu-id="dd40e-392">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-392">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-393">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-393">0</span></span> | <span data-ttu-id="dd40e-394">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-394">0</span></span><br /><span data-ttu-id="dd40e-395">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-395">1</span></span> | <span data-ttu-id="dd40e-396">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-396">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-397">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-397">User mode execution</span></span> |
| <span data-ttu-id="dd40e-398">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-398">1</span></span> | <span data-ttu-id="dd40e-399">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-399">0</span></span><br /><span data-ttu-id="dd40e-400">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-400">1</span></span> | <span data-ttu-id="dd40e-401">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-401">No MPU protection</span></span><br /><span data-ttu-id="dd40e-402">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-402">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-403">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-403">2</span></span> | <span data-ttu-id="dd40e-404">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-404">0</span></span><br /><span data-ttu-id="dd40e-405">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-405">1</span></span> | <span data-ttu-id="dd40e-406">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-406">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-407">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-407">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-408">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-408">[23-3]</span></span> | <span data-ttu-id="dd40e-409">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-409">0</span></span> | <span data-ttu-id="dd40e-410">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-410">Reserved</span></span>
| <span data-ttu-id="dd40e-411">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-411">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-412">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-412">0x00</span></span><br /><span data-ttu-id="dd40e-413">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-413">0x01</span></span><br /><span data-ttu-id="dd40e-414">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-414">0x02</span></span> | <span data-ttu-id="dd40e-415">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-415">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-416">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-416">IAR</span></span><br /><span data-ttu-id="dd40e-417">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-417">ARM</span></span><br /><span data-ttu-id="dd40e-418">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-418">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-419">Linker do módulo para Cortex-M33 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-419">Module linker for Cortex-M33 using AC6</span></span>

<span data-ttu-id="dd40e-420">Não é necessário nenhum ficheiro linker para o keil toolchain.</span><span class="sxs-lookup"><span data-stu-id="dd40e-420">No linker file needed for Keil toolchain.</span></span> <span data-ttu-id="dd40e-421">Consulte as definições de construção no projeto exemplo.</span><span class="sxs-lookup"><span data-stu-id="dd40e-421">See build settings in example project.</span></span>
<span data-ttu-id="dd40e-422">As opções importantes do linker são listadas abaixo:</span><span class="sxs-lookup"><span data-stu-id="dd40e-422">Important linker options are listed below:</span></span>

```c
--entry demo_module_start --first __txm_module_preamble
```

#### <a name="building-modules-for-cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-423">Módulos de construção para córtex-M33 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-423">Building Modules for Cortex-M33 using AC6</span></span>

<span data-ttu-id="dd40e-424">Definições do compilador:</span><span class="sxs-lookup"><span data-stu-id="dd40e-424">Compiler settings:</span></span>

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

#### <a name="thread-extension-definition-for-cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-425">Definição de extensão de fio para córtex-M33 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-425">Thread extension definition for Cortex-M33 using AC6</span></span>

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

#### <a name="building-module-manager-for-cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-426">Gestor de módulos de construção para Cortex-M33 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-426">Building Module Manager for Cortex-M33 using AC6</span></span>

<span data-ttu-id="dd40e-427">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-427">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-428">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, sample_threadx_module projeto e demo_threadx_non projeto de secure_zone.</span><span class="sxs-lookup"><span data-stu-id="dd40e-428">Build the ThreadX library, ThreadX Modules library, sample_threadx_module project, and demo_threadx_non-secure_zone project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-ac6"></a><span data-ttu-id="dd40e-429">Atributos para memória externa permitem API para córtex-M33 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-429">Attributes for external memory enable API for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="dd40e-430">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-430">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="dd40e-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="dd40e-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="dd40e-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-436">Córtex-M33 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-436">Cortex-M33 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-437">Preâmbulo do módulo para o Córtex-M33 utilizando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-437">Module preamble for Cortex-M33 using GNU</span></span>

#### <a name="module-properties-for-cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-438">Propriedades do módulo para Cortex-M33 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-438">Module properties for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="dd40e-439">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-439">Bit</span></span> | <span data-ttu-id="dd40e-440">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-440">Value</span></span> | <span data-ttu-id="dd40e-441">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-441">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-442">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-442">0</span></span> | <span data-ttu-id="dd40e-443">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-443">0</span></span><br /><span data-ttu-id="dd40e-444">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-444">1</span></span> | <span data-ttu-id="dd40e-445">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-445">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-446">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-446">User mode execution</span></span> |
| <span data-ttu-id="dd40e-447">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-447">1</span></span> | <span data-ttu-id="dd40e-448">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-448">0</span></span><br /><span data-ttu-id="dd40e-449">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-449">1</span></span> | <span data-ttu-id="dd40e-450">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-450">No MPU protection</span></span><br /><span data-ttu-id="dd40e-451">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-451">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-452">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-452">2</span></span> | <span data-ttu-id="dd40e-453">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-453">0</span></span><br /><span data-ttu-id="dd40e-454">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-454">1</span></span> | <span data-ttu-id="dd40e-455">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-455">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-456">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-456">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-457">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-457">[23-3]</span></span> | <span data-ttu-id="dd40e-458">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-458">0</span></span> | <span data-ttu-id="dd40e-459">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-459">Reserved</span></span>
| <span data-ttu-id="dd40e-460">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-460">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-461">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-461">0x00</span></span><br /><span data-ttu-id="dd40e-462">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-462">0x01</span></span><br /><span data-ttu-id="dd40e-463">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-463">0x02</span></span> | <span data-ttu-id="dd40e-464">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-464">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-465">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-465">IAR</span></span><br /><span data-ttu-id="dd40e-466">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-466">ARM</span></span><br /><span data-ttu-id="dd40e-467">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-467">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-468">Linker do módulo para córtex-M33 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-468">Module linker for Cortex-M33 using GNU</span></span>

#### <a name="building-modules-for-cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-469">Módulos de construção para córtex-M33 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-469">Building Modules for Cortex-M33 using GNU</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-470">Definição de extensão de fio para córtex-M33 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-470">Thread extension definition for Cortex-M33 using GNU</span></span>

#### <a name="building-module-manager-for-cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-471">Gestor de módulos de construção para o Cortex-M33 usando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-471">Building Module Manager for Cortex-M33 using GNU</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-gnu"></a><span data-ttu-id="dd40e-472">Atributos para memória externa permitem API para córtex M33 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-472">Attributes for external memory enable API for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="dd40e-473">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-473">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="dd40e-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="dd40e-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="dd40e-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-iar"></a><span data-ttu-id="dd40e-479">Córtex-M33 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-479">Cortex-M33 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m33-using-iar"></a><span data-ttu-id="dd40e-480">Preâmbulo do módulo para o Córtex-M33 utilizando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-480">Module preamble for Cortex-M33 using IAR</span></span>

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

#### <a name="module-properties-for-cortex-m33-using-iar"></a><span data-ttu-id="dd40e-481">Propriedades do módulo para Cortex-M33 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-481">Module properties for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="dd40e-482">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-482">Bit</span></span> | <span data-ttu-id="dd40e-483">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-483">Value</span></span> | <span data-ttu-id="dd40e-484">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-484">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-485">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-485">0</span></span> | <span data-ttu-id="dd40e-486">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-486">0</span></span><br /><span data-ttu-id="dd40e-487">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-487">1</span></span> | <span data-ttu-id="dd40e-488">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-488">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-489">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-489">User mode execution</span></span> |
| <span data-ttu-id="dd40e-490">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-490">1</span></span> | <span data-ttu-id="dd40e-491">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-491">0</span></span><br /><span data-ttu-id="dd40e-492">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-492">1</span></span> | <span data-ttu-id="dd40e-493">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-493">No MPU protection</span></span><br /><span data-ttu-id="dd40e-494">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-494">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-495">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-495">2</span></span> | <span data-ttu-id="dd40e-496">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-496">0</span></span><br /><span data-ttu-id="dd40e-497">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-497">1</span></span> | <span data-ttu-id="dd40e-498">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-498">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-499">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-499">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-500">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-500">[23-3]</span></span> | <span data-ttu-id="dd40e-501">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-501">0</span></span> | <span data-ttu-id="dd40e-502">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-502">Reserved</span></span>
| <span data-ttu-id="dd40e-503">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-503">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-504">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-504">0x00</span></span><br /><span data-ttu-id="dd40e-505">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-505">0x01</span></span><br /><span data-ttu-id="dd40e-506">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-506">0x02</span></span> | <span data-ttu-id="dd40e-507">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-507">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-508">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-508">IAR</span></span><br /><span data-ttu-id="dd40e-509">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-509">ARM</span></span><br /><span data-ttu-id="dd40e-510">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-510">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-iar"></a><span data-ttu-id="dd40e-511">Linker do módulo para córtex-M33 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-511">Module linker for Cortex-M33 using IAR</span></span>

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

#### <a name="building-modules-for-cortex-m33-using-iar"></a><span data-ttu-id="dd40e-512">Módulos de construção para córtex-M33 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-512">Building Modules for Cortex-M33 using IAR</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-iar"></a><span data-ttu-id="dd40e-513">Definição de extensão de fio para córtex-M33 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-513">Thread extension definition for Cortex-M33 using IAR</span></span>

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

#### <a name="building-module-manager-for-cortex-m33-using-iar"></a><span data-ttu-id="dd40e-514">Gestor de módulos de construção para Cortex-M33 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-514">Building Module Manager for Cortex-M33 using IAR</span></span>

<span data-ttu-id="dd40e-515">Um espaço de trabalho exemplo ainda não é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-515">An example workspace is not yet provided.</span></span> <span data-ttu-id="dd40e-516">Brevemente.</span><span class="sxs-lookup"><span data-stu-id="dd40e-516">Coming soon.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-iar"></a><span data-ttu-id="dd40e-517">Atributos para memória externa permitem a API para o Córtex-M33 usando OAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-517">Attributes for external memory enable API for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="dd40e-518">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-518">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="dd40e-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="dd40e-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="dd40e-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="dd40e-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="dd40e-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

## <a name="cortex-m4-processor"></a><span data-ttu-id="dd40e-524">Processador Córtex-M4</span><span class="sxs-lookup"><span data-stu-id="dd40e-524">Cortex-M4 processor</span></span>

### <a name="cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-525">Córtex-M4 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-525">Cortex-M4 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-526">Preâmbulo do módulo para o Córtex-M4 utilizando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-526">Module preamble for Cortex-M4 using AC5</span></span>

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

#### <a name="module-properties-for-cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-527">Propriedades do módulo para Cortex-M4 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-527">Module properties for Cortex-M4 using AC5</span></span>

| <span data-ttu-id="dd40e-528">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-528">Bit</span></span> | <span data-ttu-id="dd40e-529">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-529">Value</span></span> | <span data-ttu-id="dd40e-530">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-530">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-531">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-531">0</span></span> | <span data-ttu-id="dd40e-532">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-532">0</span></span><br /><span data-ttu-id="dd40e-533">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-533">1</span></span> | <span data-ttu-id="dd40e-534">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-534">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-535">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-535">User mode execution</span></span> |
| <span data-ttu-id="dd40e-536">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-536">1</span></span> | <span data-ttu-id="dd40e-537">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-537">0</span></span><br /><span data-ttu-id="dd40e-538">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-538">1</span></span> | <span data-ttu-id="dd40e-539">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-539">No MPU protection</span></span><br /><span data-ttu-id="dd40e-540">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-540">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-541">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-541">2</span></span> | <span data-ttu-id="dd40e-542">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-542">0</span></span><br /><span data-ttu-id="dd40e-543">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-543">1</span></span> | <span data-ttu-id="dd40e-544">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-544">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-545">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-545">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-546">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-546">[23-3]</span></span> | <span data-ttu-id="dd40e-547">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-547">0</span></span> | <span data-ttu-id="dd40e-548">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-548">Reserved</span></span>
| <span data-ttu-id="dd40e-549">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-549">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-550">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-550">0x00</span></span><br /><span data-ttu-id="dd40e-551">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-551">0x01</span></span><br /><span data-ttu-id="dd40e-552">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-552">0x02</span></span> | <span data-ttu-id="dd40e-553">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-553">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-554">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-554">IAR</span></span><br /><span data-ttu-id="dd40e-555">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-555">ARM</span></span><br /><span data-ttu-id="dd40e-556">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-556">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-557">Linker do módulo para Cortex-M4 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-557">Module linker for Cortex-M4 using AC5</span></span>

<span data-ttu-id="dd40e-558">Não é fornecido nenhum ficheiro de linker de exemplo; a ligação é feita na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dd40e-558">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="dd40e-559">Veja a próxima secção.</span><span class="sxs-lookup"><span data-stu-id="dd40e-559">See next section.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-560">Módulos de construção para córtex-M4 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-560">Building Modules for Cortex-M4 using AC5</span></span>

<span data-ttu-id="dd40e-561">Veja o exemplo build_threadx_module_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-561">See example build_threadx_module_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m4 --fpu=vfpv4 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-562">Definição de extensão de fio para córtex-M4 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-562">Thread extension definition for Cortex-M4 using AC5</span></span>

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

#### <a name="building-module-manager-for-cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-563">Gestor de módulos de construção para o Cortex-M4 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-563">Building Module Manager for Cortex-M4 using AC5</span></span>

<span data-ttu-id="dd40e-564">Veja o exemplo build_threadx_module_manager_demo.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-564">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m4 --fpu=vfpv4 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac5"></a><span data-ttu-id="dd40e-565">Atributos para memória externa permitem API para córtex-M4 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-565">Attributes for external memory enable API for Cortex-M4 using AC5</span></span>

<span data-ttu-id="dd40e-566">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-566">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-567">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-567">Attribute parameter</span></span> | <span data-ttu-id="dd40e-568">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-568">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-570">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-570">Write access</span></span> |

### <a name="cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-571">Córtex-M4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-571">Cortex-M4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-572">Preâmbulo do módulo para o Córtex-M4 utilizando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-572">Module preamble for Cortex-M4 using AC6</span></span>

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

#### <a name="module-properties-for-cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-573">Propriedades do módulo para Cortex-M4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-573">Module properties for Cortex-M4 using AC6</span></span>

| <span data-ttu-id="dd40e-574">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-574">Bit</span></span> | <span data-ttu-id="dd40e-575">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-575">Value</span></span> | <span data-ttu-id="dd40e-576">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-576">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-577">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-577">0</span></span> | <span data-ttu-id="dd40e-578">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-578">0</span></span><br /><span data-ttu-id="dd40e-579">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-579">1</span></span> | <span data-ttu-id="dd40e-580">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-580">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-581">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-581">User mode execution</span></span> |
| <span data-ttu-id="dd40e-582">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-582">1</span></span> | <span data-ttu-id="dd40e-583">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-583">0</span></span><br /><span data-ttu-id="dd40e-584">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-584">1</span></span> | <span data-ttu-id="dd40e-585">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-585">No MPU protection</span></span><br /><span data-ttu-id="dd40e-586">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-586">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-587">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-587">2</span></span> | <span data-ttu-id="dd40e-588">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-588">0</span></span><br /><span data-ttu-id="dd40e-589">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-589">1</span></span> | <span data-ttu-id="dd40e-590">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-590">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-591">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-591">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-592">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-592">[23-3]</span></span> | <span data-ttu-id="dd40e-593">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-593">0</span></span> | <span data-ttu-id="dd40e-594">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-594">Reserved</span></span>
| <span data-ttu-id="dd40e-595">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-595">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-596">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-596">0x00</span></span><br /><span data-ttu-id="dd40e-597">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-597">0x01</span></span><br /><span data-ttu-id="dd40e-598">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-598">0x02</span></span> | <span data-ttu-id="dd40e-599">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-599">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-600">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-600">IAR</span></span><br /><span data-ttu-id="dd40e-601">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-601">ARM</span></span><br /><span data-ttu-id="dd40e-602">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-602">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-603">Linker do módulo para Cortex-M4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-603">Module linker for Cortex-M4 using AC6</span></span>

<span data-ttu-id="dd40e-604">Não é utilizado nenhum ficheiro linker.</span><span class="sxs-lookup"><span data-stu-id="dd40e-604">No linker file is used.</span></span> <span data-ttu-id="dd40e-605">Consulte as definições do projeto.</span><span class="sxs-lookup"><span data-stu-id="dd40e-605">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-606">Módulos de construção para córtex-M4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-606">Building Modules for Cortex-M4 using AC6</span></span>

<span data-ttu-id="dd40e-607">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-607">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-608">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de amostra e o projeto de gestor de módulos de amostra.</span><span class="sxs-lookup"><span data-stu-id="dd40e-608">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-609">Definição de extensão de fio para córtex-M4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-609">Thread extension definition for Cortex-M4 using AC6</span></span>

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

#### <a name="building-module-manager-for-cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-610">Gestor de módulos de construção para o Cortex-M4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-610">Building Module Manager for Cortex-M4 using AC6</span></span>

<span data-ttu-id="dd40e-611">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-611">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-612">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de amostra e o projeto de gestor de módulos de amostra.</span><span class="sxs-lookup"><span data-stu-id="dd40e-612">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac6"></a><span data-ttu-id="dd40e-613">Atributos para memória externa permitem API para córtex-M4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-613">Attributes for external memory enable API for Cortex-M4 using AC6</span></span>

<span data-ttu-id="dd40e-614">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-614">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-615">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-615">Attribute parameter</span></span> | <span data-ttu-id="dd40e-616">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-616">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-618">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-618">Write access</span></span> |

### <a name="cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-619">Córtex-M4 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-619">Cortex-M4 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-620">Preâmbulo do módulo para o Córtex-M4 utilizando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-620">Module preamble for Cortex-M4 using GNU</span></span>

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

#### <a name="module-properties-for-cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-621">Propriedades do módulo para o Cortex-M4 utilizando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-621">Module properties for Cortex-M4 using GNU</span></span>

| <span data-ttu-id="dd40e-622">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-622">Bit</span></span> | <span data-ttu-id="dd40e-623">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-623">Value</span></span> | <span data-ttu-id="dd40e-624">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-624">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-625">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-625">0</span></span> | <span data-ttu-id="dd40e-626">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-626">0</span></span><br /><span data-ttu-id="dd40e-627">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-627">1</span></span> | <span data-ttu-id="dd40e-628">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-628">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-629">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-629">User mode execution</span></span> |
| <span data-ttu-id="dd40e-630">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-630">1</span></span> | <span data-ttu-id="dd40e-631">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-631">0</span></span><br /><span data-ttu-id="dd40e-632">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-632">1</span></span> | <span data-ttu-id="dd40e-633">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-633">No MPU protection</span></span><br /><span data-ttu-id="dd40e-634">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-634">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-635">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-635">2</span></span> | <span data-ttu-id="dd40e-636">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-636">0</span></span><br /><span data-ttu-id="dd40e-637">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-637">1</span></span> | <span data-ttu-id="dd40e-638">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-638">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-639">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-639">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-640">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-640">[23-3]</span></span> | <span data-ttu-id="dd40e-641">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-641">0</span></span> | <span data-ttu-id="dd40e-642">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-642">Reserved</span></span>
| <span data-ttu-id="dd40e-643">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-643">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-644">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-644">0x00</span></span><br /><span data-ttu-id="dd40e-645">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-645">0x01</span></span><br /><span data-ttu-id="dd40e-646">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-646">0x02</span></span> | <span data-ttu-id="dd40e-647">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-647">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-648">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-648">IAR</span></span><br /><span data-ttu-id="dd40e-649">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-649">ARM</span></span><br /><span data-ttu-id="dd40e-650">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-650">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-651">Linker do módulo para córtex-M4 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-651">Module linker for Cortex-M4 using GNU</span></span>

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

#### <a name="building-modules-for-cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-652">Módulos de construção para córtex-M4 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-652">Building Modules for Cortex-M4 using GNU</span></span>

<span data-ttu-id="dd40e-653">Ver build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-653">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m4 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-654">Definição de extensão de fio para córtex-M4 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-654">Thread extension definition for Cortex-M4 using GNU</span></span>

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

#### <a name="building-module-manager-for-cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-655">Gestor de módulos de construção para o Cortex-M4 usando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-655">Building Module Manager for Cortex-M4 using GNU</span></span>

<span data-ttu-id="dd40e-656">Ver build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-656">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_vectors.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb tx_initialize_low_level.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -T sample_threadx.ld -ereset_handler -nostartfiles -o sample_threadx_module_manager.out -Wl,-Map=sample_threadx_module_manager.map cortexm_vectors.o cortexm_crt0.o tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-gnu"></a><span data-ttu-id="dd40e-657">Atributos para memória externa permitem API para córtex-M4 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-657">Attributes for external memory enable API for Cortex-M4 using GNU</span></span>

<span data-ttu-id="dd40e-658">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-658">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-659">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-659">Attribute parameter</span></span> | <span data-ttu-id="dd40e-660">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-660">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-662">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-662">Write access</span></span> |

### <a name="cortex-m4-using-iar"></a><span data-ttu-id="dd40e-663">Córtex-M4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-663">Cortex-M4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m4-using-iar"></a><span data-ttu-id="dd40e-664">Preâmbulo do módulo para o Córtex-M4 utilizando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-664">Module preamble for Cortex-M4 using IAR</span></span>

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

#### <a name="module-properties-for-cortex-m4-using-iar"></a><span data-ttu-id="dd40e-665">Propriedades do módulo para Cortex-M4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-665">Module properties for Cortex-M4 using IAR</span></span>

| <span data-ttu-id="dd40e-666">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-666">Bit</span></span> | <span data-ttu-id="dd40e-667">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-667">Value</span></span> | <span data-ttu-id="dd40e-668">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-668">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-669">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-669">0</span></span> | <span data-ttu-id="dd40e-670">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-670">0</span></span><br /><span data-ttu-id="dd40e-671">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-671">1</span></span> | <span data-ttu-id="dd40e-672">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-672">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-673">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-673">User mode execution</span></span> |
| <span data-ttu-id="dd40e-674">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-674">1</span></span> | <span data-ttu-id="dd40e-675">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-675">0</span></span><br /><span data-ttu-id="dd40e-676">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-676">1</span></span> | <span data-ttu-id="dd40e-677">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-677">No MPU protection</span></span><br /><span data-ttu-id="dd40e-678">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-678">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-679">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-679">2</span></span> | <span data-ttu-id="dd40e-680">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-680">0</span></span><br /><span data-ttu-id="dd40e-681">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-681">1</span></span> | <span data-ttu-id="dd40e-682">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-682">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-683">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-683">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-684">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-684">[23-3]</span></span> | <span data-ttu-id="dd40e-685">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-685">0</span></span> | <span data-ttu-id="dd40e-686">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-686">Reserved</span></span>
| <span data-ttu-id="dd40e-687">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-687">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-688">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-688">0x00</span></span><br /><span data-ttu-id="dd40e-689">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-689">0x01</span></span><br /><span data-ttu-id="dd40e-690">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-690">0x02</span></span> | <span data-ttu-id="dd40e-691">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-691">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-692">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-692">IAR</span></span><br /><span data-ttu-id="dd40e-693">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-693">ARM</span></span><br /><span data-ttu-id="dd40e-694">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-694">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-iar"></a><span data-ttu-id="dd40e-695">Linker do módulo para córtex-M4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-695">Module linker for Cortex-M4 using IAR</span></span>

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

#### <a name="building-modules-for-cortex-m4-using-iar"></a><span data-ttu-id="dd40e-696">Módulos de construção para córtex-M4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-696">Building Modules for Cortex-M4 using IAR</span></span>

<span data-ttu-id="dd40e-697">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-697">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-698">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-698">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-iar"></a><span data-ttu-id="dd40e-699">Definição de extensão de fio para córtex-M4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-699">Thread extension definition for Cortex-M4 using IAR</span></span>

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

#### <a name="building-module-manager-for-cortex-m4-using-iar"></a><span data-ttu-id="dd40e-700">Gestor de módulos de construção para Cortex-M4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-700">Building Module Manager for Cortex-M4 using IAR</span></span>

<span data-ttu-id="dd40e-701">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-701">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-702">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-702">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-iar"></a><span data-ttu-id="dd40e-703">Atributos para memória externa permitem API para córtex-M4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-703">Attributes for external memory enable API for Cortex-M4 using IAR</span></span>

<span data-ttu-id="dd40e-704">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-704">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-705">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-705">Attribute parameter</span></span> | <span data-ttu-id="dd40e-706">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-706">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-708">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-708">Write access</span></span> |

## <a name="cortex-m7-processor"></a><span data-ttu-id="dd40e-709">Processador Córtex-M7</span><span class="sxs-lookup"><span data-stu-id="dd40e-709">Cortex-M7 processor</span></span>

### <a name="cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-710">Córtex-M7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-710">Cortex-M7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-711">Preâmbulo do módulo para o Córtex-M7 utilizando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-711">Module preamble for Cortex-M7 using AC5</span></span>

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

#### <a name="module-properties-for-cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-712">Propriedades do módulo para Cortex-M7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-712">Module properties for Cortex-M7 using AC5</span></span>

| <span data-ttu-id="dd40e-713">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-713">Bit</span></span> | <span data-ttu-id="dd40e-714">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-714">Value</span></span> | <span data-ttu-id="dd40e-715">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-715">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-716">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-716">0</span></span> | <span data-ttu-id="dd40e-717">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-717">0</span></span><br /><span data-ttu-id="dd40e-718">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-718">1</span></span> | <span data-ttu-id="dd40e-719">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-719">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-720">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-720">User mode execution</span></span> |
| <span data-ttu-id="dd40e-721">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-721">1</span></span> | <span data-ttu-id="dd40e-722">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-722">0</span></span><br /><span data-ttu-id="dd40e-723">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-723">1</span></span> | <span data-ttu-id="dd40e-724">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-724">No MPU protection</span></span><br /><span data-ttu-id="dd40e-725">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-725">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-726">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-726">2</span></span> | <span data-ttu-id="dd40e-727">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-727">0</span></span><br /><span data-ttu-id="dd40e-728">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-728">1</span></span> | <span data-ttu-id="dd40e-729">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-729">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-730">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-730">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-731">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-731">[23-3]</span></span> | <span data-ttu-id="dd40e-732">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-732">0</span></span> | <span data-ttu-id="dd40e-733">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-733">Reserved</span></span>
| <span data-ttu-id="dd40e-734">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-734">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-735">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-735">0x00</span></span><br /><span data-ttu-id="dd40e-736">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-736">0x01</span></span><br /><span data-ttu-id="dd40e-737">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-737">0x02</span></span> | <span data-ttu-id="dd40e-738">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-738">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-739">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-739">IAR</span></span><br /><span data-ttu-id="dd40e-740">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-740">ARM</span></span><br /><span data-ttu-id="dd40e-741">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-741">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-742">Linker do módulo para Cortex-M7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-742">Module linker for Cortex-M7 using AC5</span></span>

<span data-ttu-id="dd40e-743">Construído na linha de comando, nenhum exemplo de ficheiro linker.</span><span class="sxs-lookup"><span data-stu-id="dd40e-743">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-744">Módulos de construção para córtex-M7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-744">Building Modules for Cortex-M7 using AC5</span></span>

<span data-ttu-id="dd40e-745">Um exemplo simples de linha de comando para a construção de um módulo Cortex-M7 utilizando AC5:</span><span class="sxs-lookup"><span data-stu-id="dd40e-745">A simple command-line example for building a Cortex-M7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-m7 --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-746">Definição de extensão de fio para córtex-M7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-746">Thread extension definition for Cortex-M7 using AC5</span></span>

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

#### <a name="building-module-manager-for-cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-747">Gestor de módulos de construção para o Cortex-M7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-747">Building Module Manager for Cortex-M7 using AC5</span></span>

<span data-ttu-id="dd40e-748">Um exemplo simples de linha de comando para a construção de um gestor de módulos Cortex-M7 utilizando AC5:</span><span class="sxs-lookup"><span data-stu-id="dd40e-748">A simple command-line example for building a Cortex-M7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-m7 --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-m7 --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac5"></a><span data-ttu-id="dd40e-749">Atributos para memória externa permitem API para córtex-M7 usando AC5</span><span class="sxs-lookup"><span data-stu-id="dd40e-749">Attributes for external memory enable API for Cortex-M7 using AC5</span></span>

### <a name="cortex-m7-using-ac6"></a><span data-ttu-id="dd40e-750">Córtex-M7 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-750">Cortex-M7 using AC6</span></span>

#### <a name="module-properties-for-cortex-m7-using-ac6"></a><span data-ttu-id="dd40e-751">Propriedades do módulo para Cortex-M7 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-751">Module properties for Cortex-M7 using AC6</span></span>

| <span data-ttu-id="dd40e-752">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-752">Bit</span></span> | <span data-ttu-id="dd40e-753">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-753">Value</span></span> | <span data-ttu-id="dd40e-754">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-754">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-755">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-755">0</span></span> | <span data-ttu-id="dd40e-756">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-756">0</span></span><br /><span data-ttu-id="dd40e-757">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-757">1</span></span> | <span data-ttu-id="dd40e-758">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-758">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-759">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-759">User mode execution</span></span> |
| <span data-ttu-id="dd40e-760">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-760">1</span></span> | <span data-ttu-id="dd40e-761">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-761">0</span></span><br /><span data-ttu-id="dd40e-762">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-762">1</span></span> | <span data-ttu-id="dd40e-763">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-763">No MPU protection</span></span><br /><span data-ttu-id="dd40e-764">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-764">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-765">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-765">2</span></span> | <span data-ttu-id="dd40e-766">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-766">0</span></span><br /><span data-ttu-id="dd40e-767">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-767">1</span></span> | <span data-ttu-id="dd40e-768">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-768">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-769">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-769">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-770">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-770">[23-3]</span></span> | <span data-ttu-id="dd40e-771">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-771">0</span></span> | <span data-ttu-id="dd40e-772">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-772">Reserved</span></span>
| <span data-ttu-id="dd40e-773">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-773">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-774">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-774">0x00</span></span><br /><span data-ttu-id="dd40e-775">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-775">0x01</span></span><br /><span data-ttu-id="dd40e-776">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-776">0x02</span></span> | <span data-ttu-id="dd40e-777">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-777">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-778">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-778">IAR</span></span><br /><span data-ttu-id="dd40e-779">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-779">ARM</span></span><br /><span data-ttu-id="dd40e-780">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-780">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac6"></a><span data-ttu-id="dd40e-781">Linker do módulo para Cortex-M7 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-781">Module linker for Cortex-M7 using AC6</span></span>

<span data-ttu-id="dd40e-782">Não é utilizado nenhum ficheiro linker.</span><span class="sxs-lookup"><span data-stu-id="dd40e-782">No linker file is used.</span></span> <span data-ttu-id="dd40e-783">Consulte as definições do projeto.</span><span class="sxs-lookup"><span data-stu-id="dd40e-783">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac6"></a><span data-ttu-id="dd40e-784">Módulos de construção para córtex-M7 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-784">Building Modules for Cortex-M7 using AC6</span></span>

<span data-ttu-id="dd40e-785">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-785">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-786">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de amostra e o projeto de gestor de módulos de amostra.</span><span class="sxs-lookup"><span data-stu-id="dd40e-786">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-ac6"></a><span data-ttu-id="dd40e-787">Definição de extensão de fio para córtex-M7 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-787">Thread extension definition for Cortex-M7 using AC6</span></span>

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

#### <a name="building-module-manager-for-cortex-m7-using-ac6"></a><span data-ttu-id="dd40e-788">Gestor de módulos de construção para o Cortex-M7 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-788">Building Module Manager for Cortex-M7 using AC6</span></span>

<span data-ttu-id="dd40e-789">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-789">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-790">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de amostra e o projeto de gestor de módulos de amostra.</span><span class="sxs-lookup"><span data-stu-id="dd40e-790">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac6"></a><span data-ttu-id="dd40e-791">Atributos para memória externa permitem API para córtex-M7 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-791">Attributes for external memory enable API for Cortex-M7 using AC6</span></span>

<span data-ttu-id="dd40e-792">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-792">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-793">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-793">Attribute parameter</span></span> | <span data-ttu-id="dd40e-794">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-794">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-796">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-796">Write access</span></span> |

### <a name="cortex-m7-using-gnu"></a><span data-ttu-id="dd40e-797">Córtex-M7 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-797">Cortex-M7 using GNU</span></span>

#### <a name="module-properties-for-cortex-m7-using-gnu"></a><span data-ttu-id="dd40e-798">Propriedades do módulo para Cortex-M7 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-798">Module properties for Cortex-M7 using GNU</span></span>

| <span data-ttu-id="dd40e-799">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-799">Bit</span></span> | <span data-ttu-id="dd40e-800">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-800">Value</span></span> | <span data-ttu-id="dd40e-801">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-801">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-802">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-802">0</span></span> | <span data-ttu-id="dd40e-803">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-803">0</span></span><br /><span data-ttu-id="dd40e-804">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-804">1</span></span> | <span data-ttu-id="dd40e-805">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-805">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-806">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-806">User mode execution</span></span> |
| <span data-ttu-id="dd40e-807">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-807">1</span></span> | <span data-ttu-id="dd40e-808">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-808">0</span></span><br /><span data-ttu-id="dd40e-809">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-809">1</span></span> | <span data-ttu-id="dd40e-810">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-810">No MPU protection</span></span><br /><span data-ttu-id="dd40e-811">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-811">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-812">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-812">2</span></span> | <span data-ttu-id="dd40e-813">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-813">0</span></span><br /><span data-ttu-id="dd40e-814">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-814">1</span></span> | <span data-ttu-id="dd40e-815">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-815">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-816">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-816">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-817">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-817">[23-3]</span></span> | <span data-ttu-id="dd40e-818">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-818">0</span></span> | <span data-ttu-id="dd40e-819">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-819">Reserved</span></span>
| <span data-ttu-id="dd40e-820">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-820">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-821">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-821">0x00</span></span><br /><span data-ttu-id="dd40e-822">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-822">0x01</span></span><br /><span data-ttu-id="dd40e-823">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-823">0x02</span></span> | <span data-ttu-id="dd40e-824">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-824">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-825">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-825">IAR</span></span><br /><span data-ttu-id="dd40e-826">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-826">ARM</span></span><br /><span data-ttu-id="dd40e-827">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-827">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-gnu"></a><span data-ttu-id="dd40e-828">Linker do módulo para córtex-M7 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-828">Module linker for Cortex-M7 using GNU</span></span>

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

#### <a name="building-modules-for-cortex-m7-using-gnu"></a><span data-ttu-id="dd40e-829">Módulos de construção para córtex-M7 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-829">Building Modules for Cortex-M7 using GNU</span></span>

<span data-ttu-id="dd40e-830">Ver build_threadx_module_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-830">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m7 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m7-using-gnu"></a><span data-ttu-id="dd40e-831">Definição de extensão de fio para córtex-M7 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-831">Thread extension definition for Cortex-M7 using GNU</span></span>

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

#### <a name="building-module-manager-for-cortex-m7-using-gnu"></a><span data-ttu-id="dd40e-832">Gestor de módulos de construção para o Cortex-M7 usando o GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-832">Building Module Manager for Cortex-M7 using GNU</span></span>

<span data-ttu-id="dd40e-833">Ver build_threadx_module_manager_sample.bat:</span><span class="sxs-lookup"><span data-stu-id="dd40e-833">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -nostartfiles -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a -o sample_threadx_module_manager.axf -Wl,-Map=sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-gnu"></a><span data-ttu-id="dd40e-834">Atributos para memória externa permitem API para córtex-M7 usando GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-834">Attributes for external memory enable API for Cortex-M7 using GNU</span></span>

<span data-ttu-id="dd40e-835">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-835">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-836">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-836">Attribute parameter</span></span> | <span data-ttu-id="dd40e-837">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-837">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-839">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-839">Write access</span></span> |

### <a name="cortex-m7-using-iar"></a><span data-ttu-id="dd40e-840">Córtex-M7 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-840">Cortex-M7 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m7-using-iar"></a><span data-ttu-id="dd40e-841">Preâmbulo do módulo para o Córtex-M7 utilizando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-841">Module preamble for Cortex-M7 using IAR</span></span>

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

#### <a name="module-properties-for-cortex-m7-using-iar"></a><span data-ttu-id="dd40e-842">Propriedades do módulo para Cortex-M7 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-842">Module properties for Cortex-M7 using IAR</span></span>

| <span data-ttu-id="dd40e-843">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-843">Bit</span></span> | <span data-ttu-id="dd40e-844">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-844">Value</span></span> | <span data-ttu-id="dd40e-845">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-845">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-846">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-846">0</span></span> | <span data-ttu-id="dd40e-847">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-847">0</span></span><br /><span data-ttu-id="dd40e-848">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-848">1</span></span> | <span data-ttu-id="dd40e-849">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-849">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-850">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-850">User mode execution</span></span> |
| <span data-ttu-id="dd40e-851">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-851">1</span></span> | <span data-ttu-id="dd40e-852">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-852">0</span></span><br /><span data-ttu-id="dd40e-853">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-853">1</span></span> | <span data-ttu-id="dd40e-854">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-854">No MPU protection</span></span><br /><span data-ttu-id="dd40e-855">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-855">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-856">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-856">2</span></span> | <span data-ttu-id="dd40e-857">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-857">0</span></span><br /><span data-ttu-id="dd40e-858">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-858">1</span></span> | <span data-ttu-id="dd40e-859">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-859">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-860">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-860">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-861">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-861">[23-3]</span></span> | <span data-ttu-id="dd40e-862">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-862">0</span></span> | <span data-ttu-id="dd40e-863">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-863">Reserved</span></span>
| <span data-ttu-id="dd40e-864">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-864">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-865">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-865">0x00</span></span><br /><span data-ttu-id="dd40e-866">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-866">0x01</span></span><br /><span data-ttu-id="dd40e-867">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-867">0x02</span></span> | <span data-ttu-id="dd40e-868">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-868">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-869">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-869">IAR</span></span><br /><span data-ttu-id="dd40e-870">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-870">ARM</span></span><br /><span data-ttu-id="dd40e-871">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-871">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-iar"></a><span data-ttu-id="dd40e-872">Linker do módulo para córtex-M7 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-872">Module linker for Cortex-M7 using IAR</span></span>

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

#### <a name="building-modules-for-cortex-m7-using-iar"></a><span data-ttu-id="dd40e-873">Módulos de construção para córtex-M7 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-873">Building Modules for Cortex-M7 using IAR</span></span>

<span data-ttu-id="dd40e-874">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-874">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-875">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-875">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-iar"></a><span data-ttu-id="dd40e-876">Definição de extensão de fio para córtex-M7 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-876">Thread extension definition for Cortex-M7 using IAR</span></span>

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

#### <a name="building-module-manager-for-cortex-m7-using-iar"></a><span data-ttu-id="dd40e-877">Gestor de módulos de construção para Cortex-M7 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-877">Building Module Manager for Cortex-M7 using IAR</span></span>

<span data-ttu-id="dd40e-878">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-878">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-879">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-879">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-iar"></a><span data-ttu-id="dd40e-880">Atributos para memória externa permitem a API para córtex-M7 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-880">Attributes for external memory enable API for Cortex-M7 using IAR</span></span>

<span data-ttu-id="dd40e-881">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-881">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-882">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-882">Attribute parameter</span></span> | <span data-ttu-id="dd40e-883">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-883">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-885">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-885">Write access</span></span> |

## <a name="cortex-r4-processor"></a><span data-ttu-id="dd40e-886">Processador Córtex-R4</span><span class="sxs-lookup"><span data-stu-id="dd40e-886">Cortex-R4 processor</span></span>

### <a name="cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-887">Córtex-R4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-887">Cortex-R4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-888">Preâmbulo do módulo para o Córtex-R4 utilizando o CA6</span><span class="sxs-lookup"><span data-stu-id="dd40e-888">Module preamble for Cortex-R4 using AC6</span></span>

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

#### <a name="module-properties-for-cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-889">Propriedades do módulo para Cortex-R4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-889">Module properties for Cortex-R4 using AC6</span></span>

| <span data-ttu-id="dd40e-890">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-890">Bit</span></span> | <span data-ttu-id="dd40e-891">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-891">Value</span></span> | <span data-ttu-id="dd40e-892">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-892">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-893">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-893">0</span></span> | <span data-ttu-id="dd40e-894">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-894">0</span></span><br /><span data-ttu-id="dd40e-895">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-895">1</span></span> | <span data-ttu-id="dd40e-896">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-896">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-897">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-897">User mode execution</span></span> |
| <span data-ttu-id="dd40e-898">[23-1]</span><span class="sxs-lookup"><span data-stu-id="dd40e-898">[23-1]</span></span> | <span data-ttu-id="dd40e-899">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-899">0</span></span> | <span data-ttu-id="dd40e-900">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-900">Reserved</span></span>
| <span data-ttu-id="dd40e-901">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-901">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-902">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-902">0x00</span></span><br /><span data-ttu-id="dd40e-903">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-903">0x01</span></span><br /><span data-ttu-id="dd40e-904">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-904">0x02</span></span> | <span data-ttu-id="dd40e-905">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-905">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-906">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-906">IAR</span></span><br /><span data-ttu-id="dd40e-907">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-907">ARM</span></span><br /><span data-ttu-id="dd40e-908">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-908">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-909">Linker do módulo para Cortex-R4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-909">Module linker for Cortex-R4 using AC6</span></span>

<span data-ttu-id="dd40e-910">Construído na linha de comando, nenhum exemplo de ficheiro linker.</span><span class="sxs-lookup"><span data-stu-id="dd40e-910">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-911">Módulos de construção para córtex-R4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-911">Building Modules for Cortex-R4 using AC6</span></span>

<span data-ttu-id="dd40e-912">Um exemplo simples de linha de comando para a construção de um módulo Cortex-R4 utilizando AC6:</span><span class="sxs-lookup"><span data-stu-id="dd40e-912">A simple command-line example for building a Cortex-R4 module using AC6:</span></span>

```dos
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module.c
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 txm_module_preamble.S
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 semihosting.c
armlink -d -o demo_threadx_module.axf --elf --ro 0x00100000 --first txm_module_preamble.o --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --datacompressor=off --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o semihosting.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-913">Definição de extensão de fio para Cortex-R4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-913">Thread extension definition for Cortex-R4 using AC6</span></span>

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

#### <a name="building-module-manager-for-cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-914">Gestor de módulos de construção para Cortex-R4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-914">Building Module Manager for Cortex-R4 using AC6</span></span>

<span data-ttu-id="dd40e-915">Um exemplo simples de linha de comando para a construção de um gestor de módulos Cortex-R4 utilizando AC6:</span><span class="sxs-lookup"><span data-stu-id="dd40e-915">A simple command-line example for building a Cortex-R4 module manager using AC6:</span></span>

```dos
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module_manager.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 timer.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 gic.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 tx_initialize_low_level.S
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 startup.S
armlink -d -o demo_threadx_module_manager.axf --elf --scatter=demo_threadx.scat --remove --map --symbols --list demo_threadx_module_manager.map startup.o timer.o gic.o demo_threadx_module_manager.o tx_initialize_low_level.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-ac6"></a><span data-ttu-id="dd40e-916">Atributos para memória externa permitem API para córtex-R4 usando AC6</span><span class="sxs-lookup"><span data-stu-id="dd40e-916">Attributes for external memory enable API for Cortex-R4 using AC6</span></span>

<span data-ttu-id="dd40e-917">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-917">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-918">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-918">Attribute parameter</span></span> | <span data-ttu-id="dd40e-919">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-919">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-921">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-921">Write access</span></span> |

### <a name="cortex-r4-using-iar"></a><span data-ttu-id="dd40e-922">Córtex-R4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-922">Cortex-R4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-r4-using-iar"></a><span data-ttu-id="dd40e-923">Preâmbulo do módulo para o Córtex-R4 utilizando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-923">Module preamble for Cortex-R4 using IAR</span></span>

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

#### <a name="module-properties-for-cortex-r4-using-iar"></a><span data-ttu-id="dd40e-924">Propriedades do módulo para Cortex-R4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-924">Module properties for Cortex-R4 using IAR</span></span>

| <span data-ttu-id="dd40e-925">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-925">Bit</span></span> | <span data-ttu-id="dd40e-926">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-926">Value</span></span> | <span data-ttu-id="dd40e-927">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-927">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-928">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-928">0</span></span> | <span data-ttu-id="dd40e-929">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-929">0</span></span><br /><span data-ttu-id="dd40e-930">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-930">1</span></span> | <span data-ttu-id="dd40e-931">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-931">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-932">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-932">User mode execution</span></span> |
| <span data-ttu-id="dd40e-933">[23-1]</span><span class="sxs-lookup"><span data-stu-id="dd40e-933">[23-1]</span></span> | <span data-ttu-id="dd40e-934">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-934">0</span></span> | <span data-ttu-id="dd40e-935">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-935">Reserved</span></span>
| <span data-ttu-id="dd40e-936">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-936">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-937">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-937">0x00</span></span><br /><span data-ttu-id="dd40e-938">0x01</span><span class="sxs-lookup"><span data-stu-id="dd40e-938">0x01</span></span><br /><span data-ttu-id="dd40e-939">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-939">0x02</span></span> | <span data-ttu-id="dd40e-940">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-940">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-941">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-941">IAR</span></span><br /><span data-ttu-id="dd40e-942">ARM</span><span class="sxs-lookup"><span data-stu-id="dd40e-942">ARM</span></span><br /><span data-ttu-id="dd40e-943">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-943">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-iar"></a><span data-ttu-id="dd40e-944">Linker do módulo para Cortex-R4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-944">Module linker for Cortex-R4 using IAR</span></span>

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

#### <a name="building-modules-for-cortex-r4-using-iar"></a><span data-ttu-id="dd40e-945">Módulos de construção para córtex-R4 usando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-945">Building Modules for Cortex-R4 using IAR</span></span>

<span data-ttu-id="dd40e-946">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-946">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-947">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-947">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-r4-using-iar"></a><span data-ttu-id="dd40e-948">Definição de extensão de fio para córtex-R4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-948">Thread extension definition for Cortex-R4 using IAR</span></span>

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

#### <a name="building-module-manager-for-cortex-r4-using-iar"></a><span data-ttu-id="dd40e-949">Gestor de módulos de construção para Cortex-R4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-949">Building Module Manager for Cortex-R4 using IAR</span></span>

<span data-ttu-id="dd40e-950">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-950">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-951">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-951">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-iar"></a><span data-ttu-id="dd40e-952">Atributos para memória externa permitem API para córtex-R4 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-952">Attributes for external memory enable API for Cortex-R4 using IAR</span></span>

<span data-ttu-id="dd40e-953">O módulo sempre leu o acesso à memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="dd40e-953">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="dd40e-954">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-954">Attribute parameter</span></span> | <span data-ttu-id="dd40e-955">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-955">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-957">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-957">Write access</span></span> |

## <a name="mcf544xx-processor"></a><span data-ttu-id="dd40e-958">Processador MCF544xx</span><span class="sxs-lookup"><span data-stu-id="dd40e-958">MCF544xx processor</span></span>

### <a name="mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-959">MCF544x usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-959">MCF544xx using GHS</span></span>

#### <a name="module-preamble-for-mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-960">Preâmbulo do módulo para MCF544xx usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-960">Module preamble for MCF544xx using GHS</span></span>

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

#### <a name="module-properties-for-mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-961">Propriedades de módulos para MCF544xx usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-961">Module properties for MCF544xx using GHS</span></span>

| <span data-ttu-id="dd40e-962">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-962">Bit</span></span> | <span data-ttu-id="dd40e-963">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-963">Value</span></span> | <span data-ttu-id="dd40e-964">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-964">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-965">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-965">0</span></span> | <span data-ttu-id="dd40e-966">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-966">0</span></span><br /><span data-ttu-id="dd40e-967">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-967">1</span></span> | <span data-ttu-id="dd40e-968">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-968">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-969">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-969">User mode execution</span></span> |
| <span data-ttu-id="dd40e-970">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-970">1</span></span> | <span data-ttu-id="dd40e-971">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-971">0</span></span><br /><span data-ttu-id="dd40e-972">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-972">1</span></span> | <span data-ttu-id="dd40e-973">Sem proteção MMU</span><span class="sxs-lookup"><span data-stu-id="dd40e-973">No MMU protection</span></span><br /><span data-ttu-id="dd40e-974">Proteção MMU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-974">MMU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-975">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-975">2</span></span> | <span data-ttu-id="dd40e-976">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-976">0</span></span><br /><span data-ttu-id="dd40e-977">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-977">1</span></span> | <span data-ttu-id="dd40e-978">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-978">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-979">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-979">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-980">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-980">[23-3]</span></span> | <span data-ttu-id="dd40e-981">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-981">0</span></span> | <span data-ttu-id="dd40e-982">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-982">Reserved</span></span>
| <span data-ttu-id="dd40e-983">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-983">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-984">0x03</span><span class="sxs-lookup"><span data-stu-id="dd40e-984">0x03</span></span> | <span data-ttu-id="dd40e-985">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-985">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-986">RIO GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-986">GHS</span></span> |

#### <a name="module-linker-for-mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-987">Linker de módulo para MCF544xx usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-987">Module linker for MCF544xx using GHS</span></span>

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

#### <a name="building-modules-for-mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-988">Módulos de construção para MCF544xx usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-988">Building Modules for MCF544xx using GHS</span></span>

<span data-ttu-id="dd40e-989">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-989">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-990">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-990">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-991">Definição de extensão de fio para MCF544xx usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-991">Thread extension definition for MCF544xx using GHS</span></span>

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

#### <a name="building-module-manager-for-mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-992">Gestor de módulos de construção para MCF544xx usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-992">Building Module Manager for MCF544xx using GHS</span></span>

<span data-ttu-id="dd40e-993">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-993">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-994">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-994">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-mcf544xx-using-ghs"></a><span data-ttu-id="dd40e-995">Atributos para memória externa permitem API para MCF544xx usando GHS</span><span class="sxs-lookup"><span data-stu-id="dd40e-995">Attributes for external memory enable API for MCF544xx using GHS</span></span>

<span data-ttu-id="dd40e-996">Esta funcionalidade não está ativada no MCF544xx.</span><span class="sxs-lookup"><span data-stu-id="dd40e-996">This feature not enabled on MCF544xx.</span></span>

## <a name="rx63-processor"></a><span data-ttu-id="dd40e-997">Processador RX63</span><span class="sxs-lookup"><span data-stu-id="dd40e-997">RX63 processor</span></span>

### <a name="rx63-using-iar"></a><span data-ttu-id="dd40e-998">RX63 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-998">RX63 using IAR</span></span>

#### <a name="module-preamble-for-rx63-using-iar"></a><span data-ttu-id="dd40e-999">Preâmbulo do módulo para RX63 usando OAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-999">Module preamble for RX63 using IAR</span></span>

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

#### <a name="module-properties-for-rx63-using-iar"></a><span data-ttu-id="dd40e-1000">Propriedades do módulo para RX63 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1000">Module properties for RX63 using IAR</span></span>

| <span data-ttu-id="dd40e-1001">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-1001">Bit</span></span> | <span data-ttu-id="dd40e-1002">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-1002">Value</span></span> | <span data-ttu-id="dd40e-1003">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1003">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-1004">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1004">0</span></span> | <span data-ttu-id="dd40e-1005">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1005">0</span></span><br /><span data-ttu-id="dd40e-1006">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1006">1</span></span> | <span data-ttu-id="dd40e-1007">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1007">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-1008">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-1008">User mode execution</span></span> |
| <span data-ttu-id="dd40e-1009">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1009">1</span></span> | <span data-ttu-id="dd40e-1010">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1010">0</span></span><br /><span data-ttu-id="dd40e-1011">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1011">1</span></span> | <span data-ttu-id="dd40e-1012">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-1012">No MPU protection</span></span><br /><span data-ttu-id="dd40e-1013">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-1013">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-1014">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-1014">2</span></span> | <span data-ttu-id="dd40e-1015">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1015">0</span></span><br /><span data-ttu-id="dd40e-1016">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1016">1</span></span> | <span data-ttu-id="dd40e-1017">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-1017">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-1018">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-1018">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-1019">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-1019">[23-3]</span></span> | <span data-ttu-id="dd40e-1020">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1020">0</span></span> | <span data-ttu-id="dd40e-1021">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1021">Reserved</span></span>
| <span data-ttu-id="dd40e-1022">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-1022">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-1023">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-1023">0x00</span></span><br /><span data-ttu-id="dd40e-1024">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-1024">0x02</span></span> | <span data-ttu-id="dd40e-1025">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-1025">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-1026">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1026">IAR</span></span><br /><span data-ttu-id="dd40e-1027">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-1027">GNU</span></span> |

#### <a name="module-linker-for-rx63-using-iar"></a><span data-ttu-id="dd40e-1028">Linker do módulo para RX63 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1028">Module linker for RX63 using IAR</span></span>

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

#### <a name="building-modules-for-rx63-using-iar"></a><span data-ttu-id="dd40e-1029">Módulos de construção para RX63 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1029">Building Modules for RX63 using IAR</span></span>

<span data-ttu-id="dd40e-1030">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1030">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-1031">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1031">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rxrx635n-using-iar"></a><span data-ttu-id="dd40e-1032">Definição de extensão de fio para RXRX635N usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1032">Thread extension definition for RXRX635N using IAR</span></span>

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

#### <a name="building-module-manager-for-rx63-using-iar"></a><span data-ttu-id="dd40e-1033">Gestor de módulos de construção para RX63 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1033">Building Module Manager for RX63 using IAR</span></span>

<span data-ttu-id="dd40e-1034">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1034">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-1035">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1035">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx63-using-iar"></a><span data-ttu-id="dd40e-1036">Atributos para memória externa permitem a API para RX63 usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1036">Attributes for external memory enable API for RX63 using IAR</span></span>

| <span data-ttu-id="dd40e-1037">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-1037">Attribute Parameter</span></span> | <span data-ttu-id="dd40e-1038">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1038">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="dd40e-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="dd40e-1040">Executar código</span><span class="sxs-lookup"><span data-stu-id="dd40e-1040">Execute code</span></span> |
| <span data-ttu-id="dd40e-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-1042">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-1042">Write access</span></span> |
| <span data-ttu-id="dd40e-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="dd40e-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="dd40e-1044">Acesso de leitura</span><span class="sxs-lookup"><span data-stu-id="dd40e-1044">Read access</span></span> |

## <a name="rx65n-processor"></a><span data-ttu-id="dd40e-1045">Processador RX65N</span><span class="sxs-lookup"><span data-stu-id="dd40e-1045">RX65N processor</span></span>

### <a name="rx65n-using-iar"></a><span data-ttu-id="dd40e-1046">RX65N usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1046">RX65N using IAR</span></span>

#### <a name="module-preamble-for-rx65n-using-iar"></a><span data-ttu-id="dd40e-1047">Preâmbulo do módulo para RX65N usando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1047">Module preamble for RX65N using IAR</span></span>

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

#### <a name="module-properties-for-rx65n-using-iar"></a><span data-ttu-id="dd40e-1048">Propriedades do módulo para RX65N usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1048">Module properties for RX65N using IAR</span></span>

| <span data-ttu-id="dd40e-1049">Pouco</span><span class="sxs-lookup"><span data-stu-id="dd40e-1049">Bit</span></span> | <span data-ttu-id="dd40e-1050">Valor</span><span class="sxs-lookup"><span data-stu-id="dd40e-1050">Value</span></span> | <span data-ttu-id="dd40e-1051">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1051">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="dd40e-1052">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1052">0</span></span> | <span data-ttu-id="dd40e-1053">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1053">0</span></span><br /><span data-ttu-id="dd40e-1054">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1054">1</span></span> | <span data-ttu-id="dd40e-1055">Execução de modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1055">Privileged mode execution</span></span><br /><span data-ttu-id="dd40e-1056">Execução do modo de utilizador</span><span class="sxs-lookup"><span data-stu-id="dd40e-1056">User mode execution</span></span> |
| <span data-ttu-id="dd40e-1057">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1057">1</span></span> | <span data-ttu-id="dd40e-1058">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1058">0</span></span><br /><span data-ttu-id="dd40e-1059">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1059">1</span></span> | <span data-ttu-id="dd40e-1060">Sem proteção MPU</span><span class="sxs-lookup"><span data-stu-id="dd40e-1060">No MPU protection</span></span><br /><span data-ttu-id="dd40e-1061">Proteção MPU (deve ter o modo de utilizador selecionado)</span><span class="sxs-lookup"><span data-stu-id="dd40e-1061">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="dd40e-1062">2</span><span class="sxs-lookup"><span data-stu-id="dd40e-1062">2</span></span> | <span data-ttu-id="dd40e-1063">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1063">0</span></span><br /><span data-ttu-id="dd40e-1064">1</span><span class="sxs-lookup"><span data-stu-id="dd40e-1064">1</span></span> | <span data-ttu-id="dd40e-1065">Desativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-1065">Disable shared/external memory access</span></span><br /><span data-ttu-id="dd40e-1066">Ativar o acesso à memória partilhada/externa</span><span class="sxs-lookup"><span data-stu-id="dd40e-1066">Enable shared/external memory access</span></span> |
| <span data-ttu-id="dd40e-1067">[23-3]</span><span class="sxs-lookup"><span data-stu-id="dd40e-1067">[23-3]</span></span> | <span data-ttu-id="dd40e-1068">0</span><span class="sxs-lookup"><span data-stu-id="dd40e-1068">0</span></span> | <span data-ttu-id="dd40e-1069">Reservado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1069">Reserved</span></span>
| <span data-ttu-id="dd40e-1070">[31-24]</span><span class="sxs-lookup"><span data-stu-id="dd40e-1070">[31-24]</span></span> | <br /><span data-ttu-id="dd40e-1071">0x00</span><span class="sxs-lookup"><span data-stu-id="dd40e-1071">0x00</span></span><br /><span data-ttu-id="dd40e-1072">0x02</span><span class="sxs-lookup"><span data-stu-id="dd40e-1072">0x02</span></span> | <span data-ttu-id="dd40e-1073">**ID do compilador**</span><span class="sxs-lookup"><span data-stu-id="dd40e-1073">**Compiler ID**</span></span><br /><span data-ttu-id="dd40e-1074">IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1074">IAR</span></span><br /><span data-ttu-id="dd40e-1075">GNU</span><span class="sxs-lookup"><span data-stu-id="dd40e-1075">GNU</span></span> |

#### <a name="module-linker-for-rx65n-using-iar"></a><span data-ttu-id="dd40e-1076">Linker do módulo para RX65N usando OAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1076">Module linker for RX65N using IAR</span></span>

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

#### <a name="building-modules-for-rx65n-using-iar"></a><span data-ttu-id="dd40e-1077">Módulos de construção para RX65N usando o IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1077">Building Modules for RX65N using IAR</span></span>

<span data-ttu-id="dd40e-1078">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1078">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-1079">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1079">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rx65n-using-iar"></a><span data-ttu-id="dd40e-1080">Definição de extensão de fio para RX65N usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1080">Thread extension definition for RX65N using IAR</span></span>

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

#### <a name="building-module-manager-for-rx65n-using-iar"></a><span data-ttu-id="dd40e-1081">Gestor de módulos de construção para RX65N usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1081">Building Module Manager for RX65N using IAR</span></span>

<span data-ttu-id="dd40e-1082">Um espaço de trabalho exemplo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1082">An example workspace is provided.</span></span> <span data-ttu-id="dd40e-1083">Construa a biblioteca ThreadX, a biblioteca de módulos ThreadX, o projeto do módulo de demonstração e o projeto de gestor de módulos de demonstração.</span><span class="sxs-lookup"><span data-stu-id="dd40e-1083">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx65n-using-iar"></a><span data-ttu-id="dd40e-1084">Atributos para memória externa permitem a API para RX65N usando IAR</span><span class="sxs-lookup"><span data-stu-id="dd40e-1084">Attributes for external memory enable API for RX65N using IAR</span></span>

| <span data-ttu-id="dd40e-1085">Parâmetro de atributo</span><span class="sxs-lookup"><span data-stu-id="dd40e-1085">Attribute Parameter</span></span> | <span data-ttu-id="dd40e-1086">Significado</span><span class="sxs-lookup"><span data-stu-id="dd40e-1086">Meaning</span></span> |
|---|---|
| <span data-ttu-id="dd40e-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="dd40e-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="dd40e-1088">Executar código</span><span class="sxs-lookup"><span data-stu-id="dd40e-1088">Execute code</span></span> |
| <span data-ttu-id="dd40e-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="dd40e-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="dd40e-1090">Acesso de escrita</span><span class="sxs-lookup"><span data-stu-id="dd40e-1090">Write access</span></span> |
| <span data-ttu-id="dd40e-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="dd40e-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="dd40e-1092">Acesso de leitura</span><span class="sxs-lookup"><span data-stu-id="dd40e-1092">Read access</span></span> |
