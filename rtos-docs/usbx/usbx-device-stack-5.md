---
title: Capítulo 5 - Considerações da classe do dispositivo USBX
description: Saiba mais sobre as considerações da Classe dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826540"
---
# <a name="chapter-5---usbx-device-class-considerations"></a><span data-ttu-id="733bd-103">Capítulo 5 - Considerações da classe do dispositivo USBX</span><span class="sxs-lookup"><span data-stu-id="733bd-103">Chapter 5 - USBX Device Class Considerations</span></span>

## <a name="device-class-registration"></a><span data-ttu-id="733bd-104">Registo da classe do dispositivo</span><span class="sxs-lookup"><span data-stu-id="733bd-104">Device Class registration</span></span>

<span data-ttu-id="733bd-105">Cada classe de dispositivo segue o mesmo princípio para o registo.</span><span class="sxs-lookup"><span data-stu-id="733bd-105">Each device class follows the same principle for registration.</span></span> <span data-ttu-id="733bd-106">Uma estrutura que contenha parâmetros de classe específicos é passada para a função de inicialização da classe.</span><span class="sxs-lookup"><span data-stu-id="733bd-106">A structure containing specific class parameters is passed to the class initialize function.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

<span data-ttu-id="733bd-107">Cada classe pode registar-se, opcionalmente, numa função de retorno quando uma instância da classe é ativada.</span><span class="sxs-lookup"><span data-stu-id="733bd-107">Each class can register, optionally, a callback function when a instance of the class gets activated.</span></span> <span data-ttu-id="733bd-108">O retorno é então chamado pela pilha do dispositivo para informar a aplicação de que um caso foi criado.</span><span class="sxs-lookup"><span data-stu-id="733bd-108">The callback is then called by the device stack to inform the application that an instance was created.</span></span>

<span data-ttu-id="733bd-109">A aplicação teria no seu corpo as 2 funções de ativação e desativação, como mostra o exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="733bd-109">The application would have in its body the 2 functions for activation and deactivation, as shown in the following example.</span></span>

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

<span data-ttu-id="733bd-110">Não é aconselhável fazer nada dentro destas funções, mas memorizar a instância da classe e sincronizar com o resto da aplicação.</span><span class="sxs-lookup"><span data-stu-id="733bd-110">It is not recommended to do anything within these functions but to memorize the instance of the class and synchronize with the rest of the application.</span></span>

## <a name="usb-device-storage-class"></a><span data-ttu-id="733bd-111">Classe de armazenamento de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="733bd-111">USB Device Storage Class</span></span>

<span data-ttu-id="733bd-112">A classe de armazenamento de dispositivos USB permite que um dispositivo de armazenamento incorporado no sistema seja tornado visível para um hospedeiro USB.</span><span class="sxs-lookup"><span data-stu-id="733bd-112">The USB device storage class allows for a storage device embedded in the system to be made visible to a USB host.</span></span>

<span data-ttu-id="733bd-113">A classe de armazenamento de dispositivos USB não fornece, por si só, uma solução de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="733bd-113">The USB device storage class does not by itself provide a storage solution.</span></span> <span data-ttu-id="733bd-114">Apenas aceita e interpreta pedidos scsi vindos do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="733bd-114">It merely accepts and interprets SCSI requests coming from the host.</span></span> <span data-ttu-id="733bd-115">Quando um destes pedidos é um comando de leitura ou de escrita, invoca uma chamada pré-definida para um manipulador de dispositivos de armazenamento real, como um controlador de dispositivo ATA ou um controlador de dispositivo Flash.</span><span class="sxs-lookup"><span data-stu-id="733bd-115">When one of these requests is a read or a write command, it will invoke a pre-defined call back to a real storage device handler, such as an ATA device driver or a Flash device driver.</span></span>

<span data-ttu-id="733bd-116">Ao inicializar a classe de armazenamento do dispositivo, é dada uma estrutura de ponteiro à classe que contém todas as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="733bd-116">When initializing the device storage class, a pointer structure is given to the class that contains all the information necessary.</span></span> <span data-ttu-id="733bd-117">Um exemplo é dado abaixo.</span><span class="sxs-lookup"><span data-stu-id="733bd-117">An example is given below.</span></span>

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

<span data-ttu-id="733bd-118">Neste exemplo, as cordas de armazenamento do controlador são personalizadas atribuindo ponteiros de corda ao parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="733bd-118">In this example, the driver storage strings are customized by assigning string pointers to corresponding parameter.</span></span> <span data-ttu-id="733bd-119">Se um dos ponteiros de corda for deixado para UX_NULL, é utilizada a cadeia Azure RTOS padrão.</span><span class="sxs-lookup"><span data-stu-id="733bd-119">If any one of the string pointer is left to UX_NULL, the default Azure RTOS string is used.</span></span>

<span data-ttu-id="733bd-120">Neste exemplo, o último endereço de bloco da unidade ou LBA é dado, bem como o tamanho do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="733bd-120">In this example, the drive's last block address or LBA is given as well as the logical sector size.</span></span> <span data-ttu-id="733bd-121">A LBA é o número de sectores disponíveis nos meios de comunicação social –1.</span><span class="sxs-lookup"><span data-stu-id="733bd-121">The LBA is the number of sectors available in the media –1.</span></span> <span data-ttu-id="733bd-122">O comprimento do bloco é definido para 512 em meios de armazenamento regulares.</span><span class="sxs-lookup"><span data-stu-id="733bd-122">The block length is set to 512 in regular storage media.</span></span> <span data-ttu-id="733bd-123">Pode ser definido para 2048 para unidades óticas.</span><span class="sxs-lookup"><span data-stu-id="733bd-123">It can be set to 2048 for optical drives.</span></span>

<span data-ttu-id="733bd-124">A aplicação precisa de passar três ponteiros de função de retorno para permitir que a classe de armazenamento leia, escreva e obtenha o estado para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="733bd-124">The application needs to pass three callback function pointers to allow the storage class to read, write and obtain status for the media.</span></span>

<span data-ttu-id="733bd-125">Os protótipos para as funções de leitura e escrita são mostrados no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="733bd-125">The prototypes for the read and write functions are shown in the example below.</span></span>

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

<span data-ttu-id="733bd-126">Em que:</span><span class="sxs-lookup"><span data-stu-id="733bd-126">Where:</span></span>

- <span data-ttu-id="733bd-127">*armazenamento* é o exemplo da classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="733bd-127">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="733bd-128">*lun* é o LUN o comando é direcionado para.</span><span class="sxs-lookup"><span data-stu-id="733bd-128">*lun* is the LUN the command is directed to.</span></span>
- <span data-ttu-id="733bd-129">*data_pointer* é o endereço do tampão a ser usado para ler ou escrever.</span><span class="sxs-lookup"><span data-stu-id="733bd-129">*data_pointer* is the address of the buffer to be used for reading or writing.</span></span>
- <span data-ttu-id="733bd-130">*number_blocks* é o número de sectores para ler/escrever.</span><span class="sxs-lookup"><span data-stu-id="733bd-130">*number_blocks* is the number of sectors to read/write.</span></span>
- <span data-ttu-id="733bd-131">*LBA* é o endereço do sector para ler.</span><span class="sxs-lookup"><span data-stu-id="733bd-131">*lba* is the sector address to read.</span></span>
- <span data-ttu-id="733bd-132">*media_status* deve ser preenchido exatamente como o valor de retorno do estado de retorno dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="733bd-132">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="733bd-133">O valor de retorno pode ter o valor UX_SUCCESS ou UX_ERROR indicando uma operação bem sucedida ou mal sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-133">The return value can have either the value UX_SUCCESS or UX_ERROR indicating a successful or unsuccessful operation.</span></span> <span data-ttu-id="733bd-134">Estas operações não necessitam de devolver quaisquer outros códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="733bd-134">These operations do not need to return any other error codes.</span></span> <span data-ttu-id="733bd-135">Se houver um erro em qualquer operação, a classe de armazenamento invocará a função de chamada de estado de volta.</span><span class="sxs-lookup"><span data-stu-id="733bd-135">If there is an error in any operation, the storage class will invoke the status call back function.</span></span>

<span data-ttu-id="733bd-136">Esta função tem o seguinte protótipo.</span><span class="sxs-lookup"><span data-stu-id="733bd-136">This function has the following prototype.</span></span>

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

<span data-ttu-id="733bd-137">O parâmetro de chamada media_id não é atualmente utilizado e deve ser sempre 0.</span><span class="sxs-lookup"><span data-stu-id="733bd-137">The calling parameter media_id is not currently used and should always be 0.</span></span> <span data-ttu-id="733bd-138">No futuro, poderá ser utilizado para distinguir vários dispositivos de armazenamento ou dispositivos de armazenamento com vários SCSI LUNs.</span><span class="sxs-lookup"><span data-stu-id="733bd-138">In the future it may be used to distinguish multiple storage devices or storage devices with multiple SCSI LUNs.</span></span> <span data-ttu-id="733bd-139">Esta versão da classe de armazenamento não suporta múltiplas instâncias da classe de armazenamento ou dispositivos de armazenamento com vários SCSI LUNs.</span><span class="sxs-lookup"><span data-stu-id="733bd-139">This version of the storage class does not support multiple instances of the storage class or storage devices with multiple SCSI LUNs.</span></span>

<span data-ttu-id="733bd-140">O valor de retorno é um código de erro SCSI que pode ter o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="733bd-140">The return value is a SCSI error code that can have the following format.</span></span>

- <span data-ttu-id="733bd-141">**Bits 0-7** Sense_key</span><span class="sxs-lookup"><span data-stu-id="733bd-141">**Bits 0-7** Sense_key</span></span>
- <span data-ttu-id="733bd-142">**Bits 8-15** Código de Sentido Adicional</span><span class="sxs-lookup"><span data-stu-id="733bd-142">**Bits 8-15** Additional Sense Code</span></span>
- <span data-ttu-id="733bd-143">**Bits 16-23** Qualificação adicional do Código de Sentido</span><span class="sxs-lookup"><span data-stu-id="733bd-143">**Bits 16-23** Additional Sense Code Qualifier</span></span>

<span data-ttu-id="733bd-144">A tabela a seguir fornece as possíveis combinações Sense/ASC/ASCQ.</span><span class="sxs-lookup"><span data-stu-id="733bd-144">The following table provides the possible Sense/ASC/ASCQ combinations.</span></span>

| <span data-ttu-id="733bd-145">Chave do sentido</span><span class="sxs-lookup"><span data-stu-id="733bd-145">Sense Key</span></span> | <span data-ttu-id="733bd-146">ASC</span><span class="sxs-lookup"><span data-stu-id="733bd-146">ASC</span></span> | <span data-ttu-id="733bd-147">ASCQ</span><span class="sxs-lookup"><span data-stu-id="733bd-147">ASCQ</span></span> | <span data-ttu-id="733bd-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-148">Description</span></span>                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| <span data-ttu-id="733bd-149">00</span><span class="sxs-lookup"><span data-stu-id="733bd-149">00</span></span>        | <span data-ttu-id="733bd-150">00</span><span class="sxs-lookup"><span data-stu-id="733bd-150">00</span></span>  | <span data-ttu-id="733bd-151">00</span><span class="sxs-lookup"><span data-stu-id="733bd-151">00</span></span>   | <span data-ttu-id="733bd-152">SEM SENTIDO</span><span class="sxs-lookup"><span data-stu-id="733bd-152">NO SENSE</span></span>                                          |
| <span data-ttu-id="733bd-153">01</span><span class="sxs-lookup"><span data-stu-id="733bd-153">01</span></span>        | <span data-ttu-id="733bd-154">17</span><span class="sxs-lookup"><span data-stu-id="733bd-154">17</span></span>  | <span data-ttu-id="733bd-155">01</span><span class="sxs-lookup"><span data-stu-id="733bd-155">01</span></span>   | <span data-ttu-id="733bd-156">DADOS RECUPERADOS COM RETRÓSCA</span><span class="sxs-lookup"><span data-stu-id="733bd-156">RECOVERED DATA WITH RETRIES</span></span>                       |
| <span data-ttu-id="733bd-157">01</span><span class="sxs-lookup"><span data-stu-id="733bd-157">01</span></span>        | <span data-ttu-id="733bd-158">18</span><span class="sxs-lookup"><span data-stu-id="733bd-158">18</span></span>  | <span data-ttu-id="733bd-159">00</span><span class="sxs-lookup"><span data-stu-id="733bd-159">00</span></span>   | <span data-ttu-id="733bd-160">DADOS RECUPERADOS COM ECC</span><span class="sxs-lookup"><span data-stu-id="733bd-160">RECOVERED DATA WITH ECC</span></span>                           |
| <span data-ttu-id="733bd-161">02</span><span class="sxs-lookup"><span data-stu-id="733bd-161">02</span></span>        | <span data-ttu-id="733bd-162">04</span><span class="sxs-lookup"><span data-stu-id="733bd-162">04</span></span>  | <span data-ttu-id="733bd-163">01</span><span class="sxs-lookup"><span data-stu-id="733bd-163">01</span></span>   | <span data-ttu-id="733bd-164">UNIDADE LÓGICA NÃO PRONTA - FICANDO PRONTA</span><span class="sxs-lookup"><span data-stu-id="733bd-164">LOGICAL DRIVE NOT READY - BECOMING READY</span></span>          |
| <span data-ttu-id="733bd-165">02</span><span class="sxs-lookup"><span data-stu-id="733bd-165">02</span></span>        | <span data-ttu-id="733bd-166">04</span><span class="sxs-lookup"><span data-stu-id="733bd-166">04</span></span>  | <span data-ttu-id="733bd-167">02</span><span class="sxs-lookup"><span data-stu-id="733bd-167">02</span></span>   | <span data-ttu-id="733bd-168">UNIDADE LÓGICA NÃO PRONTA - INICIALIZAÇÃO NECESSÁRIA</span><span class="sxs-lookup"><span data-stu-id="733bd-168">LOGICAL DRIVE NOT READY - INITIALIZATION REQUIRED</span></span> |
| <span data-ttu-id="733bd-169">02</span><span class="sxs-lookup"><span data-stu-id="733bd-169">02</span></span>        | <span data-ttu-id="733bd-170">04</span><span class="sxs-lookup"><span data-stu-id="733bd-170">04</span></span>  | <span data-ttu-id="733bd-171">04</span><span class="sxs-lookup"><span data-stu-id="733bd-171">04</span></span>   | <span data-ttu-id="733bd-172">UNIDADE LÓGICA NÃO PRONTA - FORMATO EM CURSO</span><span class="sxs-lookup"><span data-stu-id="733bd-172">LOGICAL UNIT NOT READY - FORMAT IN PROGRESS</span></span>       |
| <span data-ttu-id="733bd-173">02</span><span class="sxs-lookup"><span data-stu-id="733bd-173">02</span></span>        | <span data-ttu-id="733bd-174">04</span><span class="sxs-lookup"><span data-stu-id="733bd-174">04</span></span>  | <span data-ttu-id="733bd-175">FF</span><span class="sxs-lookup"><span data-stu-id="733bd-175">FF</span></span>   | <span data-ttu-id="733bd-176">UNIDADE LÓGICA NÃO ESTÁ PRONTA - DISPOSITIVO ESTÁ OCUPADO</span><span class="sxs-lookup"><span data-stu-id="733bd-176">LOGICAL DRIVE NOT READY - DEVICE IS BUSY</span></span>          |
| <span data-ttu-id="733bd-177">02</span><span class="sxs-lookup"><span data-stu-id="733bd-177">02</span></span>        | <span data-ttu-id="733bd-178">06</span><span class="sxs-lookup"><span data-stu-id="733bd-178">06</span></span>  | <span data-ttu-id="733bd-179">00</span><span class="sxs-lookup"><span data-stu-id="733bd-179">00</span></span>   | <span data-ttu-id="733bd-180">NENHUMA POSIÇÃO DE REFERÊNCIA ENCONTRADA</span><span class="sxs-lookup"><span data-stu-id="733bd-180">NO REFERENCE POSITION FOUND</span></span>                       |
| <span data-ttu-id="733bd-181">02</span><span class="sxs-lookup"><span data-stu-id="733bd-181">02</span></span>        | <span data-ttu-id="733bd-182">08</span><span class="sxs-lookup"><span data-stu-id="733bd-182">08</span></span>  | <span data-ttu-id="733bd-183">00</span><span class="sxs-lookup"><span data-stu-id="733bd-183">00</span></span>   | <span data-ttu-id="733bd-184">FALHA DE COMUNICAÇÃO DA UNIDADE LÓGICA</span><span class="sxs-lookup"><span data-stu-id="733bd-184">LOGICAL UNIT COMMUNICATION FAILURE</span></span>                |
| <span data-ttu-id="733bd-185">02</span><span class="sxs-lookup"><span data-stu-id="733bd-185">02</span></span>        | <span data-ttu-id="733bd-186">08</span><span class="sxs-lookup"><span data-stu-id="733bd-186">08</span></span>  | <span data-ttu-id="733bd-187">01</span><span class="sxs-lookup"><span data-stu-id="733bd-187">01</span></span>   | <span data-ttu-id="733bd-188">TEMPO DE TEMPO DE COMUNICAÇÃO DA UNIDADE LÓGICA</span><span class="sxs-lookup"><span data-stu-id="733bd-188">LOGICAL UNIT COMMUNICATION TIME-OUT</span></span>               |
| <span data-ttu-id="733bd-189">02</span><span class="sxs-lookup"><span data-stu-id="733bd-189">02</span></span>        | <span data-ttu-id="733bd-190">08</span><span class="sxs-lookup"><span data-stu-id="733bd-190">08</span></span>  | <span data-ttu-id="733bd-191">80</span><span class="sxs-lookup"><span data-stu-id="733bd-191">80</span></span>   | <span data-ttu-id="733bd-192">FALHA DE COMUNICAÇÃO DA UNIDADE LÓGICA</span><span class="sxs-lookup"><span data-stu-id="733bd-192">LOGICAL UNIT COMMUNICATION OVERRUN</span></span>                |
| <span data-ttu-id="733bd-193">02</span><span class="sxs-lookup"><span data-stu-id="733bd-193">02</span></span>        | <span data-ttu-id="733bd-194">3A</span><span class="sxs-lookup"><span data-stu-id="733bd-194">3A</span></span>  | <span data-ttu-id="733bd-195">00</span><span class="sxs-lookup"><span data-stu-id="733bd-195">00</span></span>   | <span data-ttu-id="733bd-196">MEIO NÃO PRESENTE</span><span class="sxs-lookup"><span data-stu-id="733bd-196">MEDIUM NOT PRESENT</span></span>                                |
| <span data-ttu-id="733bd-197">02</span><span class="sxs-lookup"><span data-stu-id="733bd-197">02</span></span>        | <span data-ttu-id="733bd-198">54</span><span class="sxs-lookup"><span data-stu-id="733bd-198">54</span></span>  | <span data-ttu-id="733bd-199">00</span><span class="sxs-lookup"><span data-stu-id="733bd-199">00</span></span>   | <span data-ttu-id="733bd-200">USB PARA HOSPEDAR FALHA NA INTERFACE DO SISTEMA</span><span class="sxs-lookup"><span data-stu-id="733bd-200">USB TO HOST SYSTEM INTERFACE FAILURE</span></span>              |
| <span data-ttu-id="733bd-201">02</span><span class="sxs-lookup"><span data-stu-id="733bd-201">02</span></span>        | <span data-ttu-id="733bd-202">80</span><span class="sxs-lookup"><span data-stu-id="733bd-202">80</span></span>  | <span data-ttu-id="733bd-203">00</span><span class="sxs-lookup"><span data-stu-id="733bd-203">00</span></span>   | <span data-ttu-id="733bd-204">RECURSOS INSUFICIENTES</span><span class="sxs-lookup"><span data-stu-id="733bd-204">INSUFFICIENT RESOURCES</span></span>                            |
| <span data-ttu-id="733bd-205">02</span><span class="sxs-lookup"><span data-stu-id="733bd-205">02</span></span>        | <span data-ttu-id="733bd-206">FF</span><span class="sxs-lookup"><span data-stu-id="733bd-206">FF</span></span>  | <span data-ttu-id="733bd-207">FF</span><span class="sxs-lookup"><span data-stu-id="733bd-207">FF</span></span>   | <span data-ttu-id="733bd-208">ERRO DESCONHECIDO</span><span class="sxs-lookup"><span data-stu-id="733bd-208">UNKNOWN ERROR</span></span>                                     |
| <span data-ttu-id="733bd-209">03</span><span class="sxs-lookup"><span data-stu-id="733bd-209">03</span></span>        | <span data-ttu-id="733bd-210">02</span><span class="sxs-lookup"><span data-stu-id="733bd-210">02</span></span>  | <span data-ttu-id="733bd-211">00</span><span class="sxs-lookup"><span data-stu-id="733bd-211">00</span></span>   | <span data-ttu-id="733bd-212">SEM PROCURAR COMPLETO</span><span class="sxs-lookup"><span data-stu-id="733bd-212">NO SEEK COMPLETE</span></span>                                  |
| <span data-ttu-id="733bd-213">03</span><span class="sxs-lookup"><span data-stu-id="733bd-213">03</span></span>        | <span data-ttu-id="733bd-214">03</span><span class="sxs-lookup"><span data-stu-id="733bd-214">03</span></span>  | <span data-ttu-id="733bd-215">00</span><span class="sxs-lookup"><span data-stu-id="733bd-215">00</span></span>   | <span data-ttu-id="733bd-216">CULPA DE ESCREVER</span><span class="sxs-lookup"><span data-stu-id="733bd-216">WRITE FAULT</span></span>                                       |
| <span data-ttu-id="733bd-217">03</span><span class="sxs-lookup"><span data-stu-id="733bd-217">03</span></span>        | <span data-ttu-id="733bd-218">10</span><span class="sxs-lookup"><span data-stu-id="733bd-218">10</span></span>  | <span data-ttu-id="733bd-219">00</span><span class="sxs-lookup"><span data-stu-id="733bd-219">00</span></span>   | <span data-ttu-id="733bd-220">Erro de ID CRC</span><span class="sxs-lookup"><span data-stu-id="733bd-220">ID CRC ERROR</span></span>                                      |
| <span data-ttu-id="733bd-221">03</span><span class="sxs-lookup"><span data-stu-id="733bd-221">03</span></span>        | <span data-ttu-id="733bd-222">11</span><span class="sxs-lookup"><span data-stu-id="733bd-222">11</span></span>  | <span data-ttu-id="733bd-223">00</span><span class="sxs-lookup"><span data-stu-id="733bd-223">00</span></span>   | <span data-ttu-id="733bd-224">ERRO DE LEITURA NÃO DESCOBERTO</span><span class="sxs-lookup"><span data-stu-id="733bd-224">UNRECOVERED READ ERROR</span></span>                            |
| <span data-ttu-id="733bd-225">03</span><span class="sxs-lookup"><span data-stu-id="733bd-225">03</span></span>        | <span data-ttu-id="733bd-226">12</span><span class="sxs-lookup"><span data-stu-id="733bd-226">12</span></span>  | <span data-ttu-id="733bd-227">00</span><span class="sxs-lookup"><span data-stu-id="733bd-227">00</span></span>   | <span data-ttu-id="733bd-228">MARCA DE ENDEREÇO NÃO ENCONTRADA PARA CAMPO DE ID</span><span class="sxs-lookup"><span data-stu-id="733bd-228">ADDRESS MARK NOT FOUND FOR ID FIELD</span></span>               |
| <span data-ttu-id="733bd-229">03</span><span class="sxs-lookup"><span data-stu-id="733bd-229">03</span></span>        | <span data-ttu-id="733bd-230">13</span><span class="sxs-lookup"><span data-stu-id="733bd-230">13</span></span>  | <span data-ttu-id="733bd-231">00</span><span class="sxs-lookup"><span data-stu-id="733bd-231">00</span></span>   | <span data-ttu-id="733bd-232">MARCA DE ENDEREÇO NÃO ENCONTRADA PARA CAMPO DE DADOS</span><span class="sxs-lookup"><span data-stu-id="733bd-232">ADDRESS MARK NOT FOUND FOR DATA FIELD</span></span>             |
| <span data-ttu-id="733bd-233">03</span><span class="sxs-lookup"><span data-stu-id="733bd-233">03</span></span>        | <span data-ttu-id="733bd-234">14</span><span class="sxs-lookup"><span data-stu-id="733bd-234">14</span></span>  | <span data-ttu-id="733bd-235">00</span><span class="sxs-lookup"><span data-stu-id="733bd-235">00</span></span>   | <span data-ttu-id="733bd-236">ENTIDADE GRAVADA NÃO ENCONTRADA</span><span class="sxs-lookup"><span data-stu-id="733bd-236">RECORDED ENTITY NOT FOUND</span></span>                         |
| <span data-ttu-id="733bd-237">03</span><span class="sxs-lookup"><span data-stu-id="733bd-237">03</span></span>        | <span data-ttu-id="733bd-238">30</span><span class="sxs-lookup"><span data-stu-id="733bd-238">30</span></span>  | <span data-ttu-id="733bd-239">01</span><span class="sxs-lookup"><span data-stu-id="733bd-239">01</span></span>   | <span data-ttu-id="733bd-240">NÃO PODE LER MEIO - FORMATO DESCONHECIDO</span><span class="sxs-lookup"><span data-stu-id="733bd-240">CANNOT READ MEDIUM - UNKNOWN FORMAT</span></span>               |
| <span data-ttu-id="733bd-241">03</span><span class="sxs-lookup"><span data-stu-id="733bd-241">03</span></span>        | <span data-ttu-id="733bd-242">31</span><span class="sxs-lookup"><span data-stu-id="733bd-242">31</span></span>  | <span data-ttu-id="733bd-243">01</span><span class="sxs-lookup"><span data-stu-id="733bd-243">01</span></span>   | <span data-ttu-id="733bd-244">O COMANDO DO FORMATO FALHOU</span><span class="sxs-lookup"><span data-stu-id="733bd-244">FORMAT COMMAND FAILED</span></span>                             |
| <span data-ttu-id="733bd-245">04</span><span class="sxs-lookup"><span data-stu-id="733bd-245">04</span></span>        | <span data-ttu-id="733bd-246">40</span><span class="sxs-lookup"><span data-stu-id="733bd-246">40</span></span>  | <span data-ttu-id="733bd-247">NN</span><span class="sxs-lookup"><span data-stu-id="733bd-247">NN</span></span>   | <span data-ttu-id="733bd-248">FALHA DE DIAGNÓSTICO NO COMPONENTE NN (80H-FFH)</span><span class="sxs-lookup"><span data-stu-id="733bd-248">DIAGNOSTIC FAILURE ON COMPONENT NN (80H-FFH)</span></span>      |
| <span data-ttu-id="733bd-249">05</span><span class="sxs-lookup"><span data-stu-id="733bd-249">05</span></span>        | <span data-ttu-id="733bd-250">1A</span><span class="sxs-lookup"><span data-stu-id="733bd-250">1A</span></span>  | <span data-ttu-id="733bd-251">00</span><span class="sxs-lookup"><span data-stu-id="733bd-251">00</span></span>   | <span data-ttu-id="733bd-252">ERRO DE COMPRIMENTO DA LISTA DE PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="733bd-252">PARAMETER LIST LENGTH ERROR</span></span>                       |
| <span data-ttu-id="733bd-253">05</span><span class="sxs-lookup"><span data-stu-id="733bd-253">05</span></span>        | <span data-ttu-id="733bd-254">20</span><span class="sxs-lookup"><span data-stu-id="733bd-254">20</span></span>  | <span data-ttu-id="733bd-255">00</span><span class="sxs-lookup"><span data-stu-id="733bd-255">00</span></span>   | <span data-ttu-id="733bd-256">CÓDIGO DE FUNCIONAMENTO DO COMANDO INVÁLIDO</span><span class="sxs-lookup"><span data-stu-id="733bd-256">INVALID COMMAND OPERATION CODE</span></span>                    |
| <span data-ttu-id="733bd-257">05</span><span class="sxs-lookup"><span data-stu-id="733bd-257">05</span></span>        | <span data-ttu-id="733bd-258">21</span><span class="sxs-lookup"><span data-stu-id="733bd-258">21</span></span>  | <span data-ttu-id="733bd-259">00</span><span class="sxs-lookup"><span data-stu-id="733bd-259">00</span></span>   | <span data-ttu-id="733bd-260">ENDEREÇO DE BLOCO LÓGICO FORA DO ALCANCE</span><span class="sxs-lookup"><span data-stu-id="733bd-260">LOGICAL BLOCK ADDRESS OUT OF RANGE</span></span>                |
| <span data-ttu-id="733bd-261">05</span><span class="sxs-lookup"><span data-stu-id="733bd-261">05</span></span>        | <span data-ttu-id="733bd-262">24</span><span class="sxs-lookup"><span data-stu-id="733bd-262">24</span></span>  | <span data-ttu-id="733bd-263">00</span><span class="sxs-lookup"><span data-stu-id="733bd-263">00</span></span>   | <span data-ttu-id="733bd-264">CAMPO INVÁLIDO NO PACOTE DE COMANDO</span><span class="sxs-lookup"><span data-stu-id="733bd-264">INVALID FIELD IN COMMAND PACKET</span></span>                   |
| <span data-ttu-id="733bd-265">05</span><span class="sxs-lookup"><span data-stu-id="733bd-265">05</span></span>        | <span data-ttu-id="733bd-266">25</span><span class="sxs-lookup"><span data-stu-id="733bd-266">25</span></span>  | <span data-ttu-id="733bd-267">00</span><span class="sxs-lookup"><span data-stu-id="733bd-267">00</span></span>   | <span data-ttu-id="733bd-268">UNIDADE LÓGICA NÃO SUPORTADA</span><span class="sxs-lookup"><span data-stu-id="733bd-268">LOGICAL UNIT NOT SUPPORTED</span></span>                        |
| <span data-ttu-id="733bd-269">05</span><span class="sxs-lookup"><span data-stu-id="733bd-269">05</span></span>        | <span data-ttu-id="733bd-270">26</span><span class="sxs-lookup"><span data-stu-id="733bd-270">26</span></span>  | <span data-ttu-id="733bd-271">00</span><span class="sxs-lookup"><span data-stu-id="733bd-271">00</span></span>   | <span data-ttu-id="733bd-272">CAMPO INVÁLIDO NA LISTA DE PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="733bd-272">INVALID FIELD IN PARAMETER LIST</span></span>                   |
| <span data-ttu-id="733bd-273">05</span><span class="sxs-lookup"><span data-stu-id="733bd-273">05</span></span>        | <span data-ttu-id="733bd-274">26</span><span class="sxs-lookup"><span data-stu-id="733bd-274">26</span></span>  | <span data-ttu-id="733bd-275">01</span><span class="sxs-lookup"><span data-stu-id="733bd-275">01</span></span>   | <span data-ttu-id="733bd-276">PARÂMETRO NÃO SUPORTADO</span><span class="sxs-lookup"><span data-stu-id="733bd-276">PARAMETER NOT SUPPORTED</span></span>                           |
| <span data-ttu-id="733bd-277">05</span><span class="sxs-lookup"><span data-stu-id="733bd-277">05</span></span>        | <span data-ttu-id="733bd-278">26</span><span class="sxs-lookup"><span data-stu-id="733bd-278">26</span></span>  | <span data-ttu-id="733bd-279">02</span><span class="sxs-lookup"><span data-stu-id="733bd-279">02</span></span>   | <span data-ttu-id="733bd-280">VALOR DO PARÂMETRO INVÁLIDO</span><span class="sxs-lookup"><span data-stu-id="733bd-280">PARAMETER VALUE INVALID</span></span>                           |
| <span data-ttu-id="733bd-281">05</span><span class="sxs-lookup"><span data-stu-id="733bd-281">05</span></span>        | <span data-ttu-id="733bd-282">39</span><span class="sxs-lookup"><span data-stu-id="733bd-282">39</span></span>  | <span data-ttu-id="733bd-283">00</span><span class="sxs-lookup"><span data-stu-id="733bd-283">00</span></span>   | <span data-ttu-id="733bd-284">PARÂMETROS DE POUPANÇA NÃO SUPORTE</span><span class="sxs-lookup"><span data-stu-id="733bd-284">SAVING PARAMETERS NOT SUPPORT</span></span>                     |
| <span data-ttu-id="733bd-285">06</span><span class="sxs-lookup"><span data-stu-id="733bd-285">06</span></span>        | <span data-ttu-id="733bd-286">28</span><span class="sxs-lookup"><span data-stu-id="733bd-286">28</span></span>  | <span data-ttu-id="733bd-287">00</span><span class="sxs-lookup"><span data-stu-id="733bd-287">00</span></span>   | <span data-ttu-id="733bd-288">NÃO PRONTO PARA A TRANSIÇÃO PRONTA - MEDIA ALTERADO</span><span class="sxs-lookup"><span data-stu-id="733bd-288">NOT READY TO READY TRANSITION – MEDIA CHANGED</span></span>     |
| <span data-ttu-id="733bd-289">06</span><span class="sxs-lookup"><span data-stu-id="733bd-289">06</span></span>        | <span data-ttu-id="733bd-290">29</span><span class="sxs-lookup"><span data-stu-id="733bd-290">29</span></span>  | <span data-ttu-id="733bd-291">00</span><span class="sxs-lookup"><span data-stu-id="733bd-291">00</span></span>   | <span data-ttu-id="733bd-292">POTÊNCIA NO RESET OU RESET DO DISPOSITIVO DE AUTOCARRO OCORREU</span><span class="sxs-lookup"><span data-stu-id="733bd-292">POWER ON RESET OR BUS DEVICE RESET OCCURRED</span></span>       |
| <span data-ttu-id="733bd-293">06</span><span class="sxs-lookup"><span data-stu-id="733bd-293">06</span></span>        | <span data-ttu-id="733bd-294">2F</span><span class="sxs-lookup"><span data-stu-id="733bd-294">2F</span></span>  | <span data-ttu-id="733bd-295">00</span><span class="sxs-lookup"><span data-stu-id="733bd-295">00</span></span>   | <span data-ttu-id="733bd-296">COMANDOS APURADOS POR OUTRO INICIADOR</span><span class="sxs-lookup"><span data-stu-id="733bd-296">COMMANDS CLEARED BY ANOTHER INITIATOR</span></span>             |
| <span data-ttu-id="733bd-297">07</span><span class="sxs-lookup"><span data-stu-id="733bd-297">07</span></span>        | <span data-ttu-id="733bd-298">27</span><span class="sxs-lookup"><span data-stu-id="733bd-298">27</span></span>  | <span data-ttu-id="733bd-299">00</span><span class="sxs-lookup"><span data-stu-id="733bd-299">00</span></span>   | <span data-ttu-id="733bd-300">ESCREVER MEIOS PROTEGIDOS</span><span class="sxs-lookup"><span data-stu-id="733bd-300">WRITE PROTECTED MEDIA</span></span>                             |
| <span data-ttu-id="733bd-301">0B</span><span class="sxs-lookup"><span data-stu-id="733bd-301">0B</span></span>        | <span data-ttu-id="733bd-302">4E</span><span class="sxs-lookup"><span data-stu-id="733bd-302">4E</span></span>  | <span data-ttu-id="733bd-303">00</span><span class="sxs-lookup"><span data-stu-id="733bd-303">00</span></span>   | <span data-ttu-id="733bd-304">COMANDO SOBREPOSTO TENTADO</span><span class="sxs-lookup"><span data-stu-id="733bd-304">OVERLAPPED COMMAND ATTEMPTED</span></span>                      |

<span data-ttu-id="733bd-305">Existem duas chamadas adicionais e opcionais que a aplicação pode implementar; um é para responder a um comando **GET_STATUS_NOTIFICATION** e o outro é para responder ao **comando SYNCHRONIZE_CACHE.**</span><span class="sxs-lookup"><span data-stu-id="733bd-305">There are two additional, optional callbacks the application may implement; one is for responding to a **GET_STATUS_NOTIFICATION** command and the other is for responding to the **SYNCHRONIZE_CACHE** command.</span></span>

<span data-ttu-id="733bd-306">Se a aplicação quiser lidar com o comando GET_STATUS_NOTIFICATION do anfitrião, deverá implementar uma chamada com o seguinte protótipo.</span><span class="sxs-lookup"><span data-stu-id="733bd-306">If the application would like to handle the GET_STATUS_NOTIFICATION command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

<span data-ttu-id="733bd-307">Em que:</span><span class="sxs-lookup"><span data-stu-id="733bd-307">Where:</span></span>

- <span data-ttu-id="733bd-308">*armazenamento* é o exemplo da classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="733bd-308">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="733bd-309">*media_id* não é atualmente utilizada.</span><span class="sxs-lookup"><span data-stu-id="733bd-309">*media_id* is not currently used.</span></span> <span data-ttu-id="733bd-310">notification_class especifica a classe de notificação.</span><span class="sxs-lookup"><span data-stu-id="733bd-310">notification_class specifies the class of notification.</span></span>
- <span data-ttu-id="733bd-311">*media_notification* deve ser definido pelo pedido ao tampão que contém a resposta para a notificação.</span><span class="sxs-lookup"><span data-stu-id="733bd-311">*media_notification* should be set by the application to the buffer containing the response for the notification.</span></span>
- <span data-ttu-id="733bd-312">*media_notification_length* deve ser definido pela aplicação para conter o comprimento do tampão de resposta.</span><span class="sxs-lookup"><span data-stu-id="733bd-312">*media_notification_length* should be set by the application to contain the length of the response buffer.</span></span>

<span data-ttu-id="733bd-313">O valor de retorno indica se o comando foi ou não bem sucedido – deve ser **UX_SUCCESS** ou **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="733bd-313">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

<span data-ttu-id="733bd-314">Se a aplicação não implementar esta chamada, então ao receber o comando **GET_STATUS_NOTIFICATION,** a USBX notificará o anfitrião de que o comando não é implementado.</span><span class="sxs-lookup"><span data-stu-id="733bd-314">If the application does not implement this callback, then upon receiving the **GET_STATUS_NOTIFICATION** command, USBX will notify the host that the command is not implemented.</span></span>

<span data-ttu-id="733bd-315">O **comando SYNCHRONIZE_CACHE** deve ser manuseado se a aplicação estiver a utilizar uma cache para escritas do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="733bd-315">The **SYNCHRONIZE_CACHE** command should be handled if the application is utilizing a cache for writes from the host.</span></span> <span data-ttu-id="733bd-316">Um anfitrião pode enviar este comando se souber que o dispositivo de armazenamento está prestes a ser desligado, por exemplo, no Windows, se clicar corretamente num ícone de pen na barra de ferramentas e selecionar "Ejetar o \[ nome do dispositivo de \] armazenamento", o Windows emitirá o comando **SYNCHRONIZE_CACHE** para esse dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-316">A host may send this command if it knows the storage device is about to be disconnected, for example, in Windows, if you right click a flash drive icon in the toolbar and select "Eject \[storage device name\]", Windows will issue the **SYNCHRONIZE_CACHE** command to that device.</span></span>

<span data-ttu-id="733bd-317">Se a aplicação quiser lidar com o comando **GET_STATUS_NOTIFICATION** do anfitrião, deverá implementar uma chamada com o seguinte protótipo.</span><span class="sxs-lookup"><span data-stu-id="733bd-317">If the application would like to handle the **GET_STATUS_NOTIFICATION** command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

<span data-ttu-id="733bd-318">Em que:</span><span class="sxs-lookup"><span data-stu-id="733bd-318">Where:</span></span>

- <span data-ttu-id="733bd-319">*armazenamento* é o exemplo da classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="733bd-319">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="733bd-320">o parâmetro *lun* especifica a que LUN o comando é dirigido.</span><span class="sxs-lookup"><span data-stu-id="733bd-320">*lun* parameter specifies which LUN the command is directed to.</span></span>
- <span data-ttu-id="733bd-321">*number_blocks* especifica o número de blocos para sincronizar.</span><span class="sxs-lookup"><span data-stu-id="733bd-321">*number_blocks* specifies the number of blocks to synchronize.</span></span>
- <span data-ttu-id="733bd-322">*LBA* é o endereço do sector do primeiro bloco para sincronizar.</span><span class="sxs-lookup"><span data-stu-id="733bd-322">*lba* is the sector address of the first block to synchronize.</span></span>
- <span data-ttu-id="733bd-323">*media_status* deve ser preenchido exatamente como o valor de retorno do estado de retorno dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="733bd-323">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="733bd-324">O valor de retorno indica se o comando foi ou não bem sucedido – deve ser **UX_SUCCESS** ou **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="733bd-324">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

### <a name="multiple-scsi-lun"></a><span data-ttu-id="733bd-325">Vários SCSI LUN</span><span class="sxs-lookup"><span data-stu-id="733bd-325">Multiple SCSI LUN</span></span>

<span data-ttu-id="733bd-326">A classe de armazenamento de dispositivos USBX suporta vários LUNs.</span><span class="sxs-lookup"><span data-stu-id="733bd-326">The USBX device storage class supports multiple LUNs.</span></span> <span data-ttu-id="733bd-327">É, portanto, possível criar um dispositivo de armazenamento que atue como UM CD-ROM e um disco Flash ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="733bd-327">It is therefore possible to create a storage device that acts as a CD-ROM and a Flash disk at the same time.</span></span> <span data-ttu-id="733bd-328">Neste caso, a inicialização seria ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="733bd-328">In such a case, the initialization would be slightly different.</span></span> <span data-ttu-id="733bd-329">Aqui está um exemplo para um Flash Disk e CD-ROM:</span><span class="sxs-lookup"><span data-stu-id="733bd-329">Here is an example for a Flash Disk and CD-ROM:</span></span>

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a><span data-ttu-id="733bd-330">Classe CDC-ACM do dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="733bd-330">USB Device CDC-ACM Class</span></span>

<span data-ttu-id="733bd-331">A classe CDC-ACM do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como dispositivo de série.</span><span class="sxs-lookup"><span data-stu-id="733bd-331">The USB device CDC-ACM class allows for a USB host system to communicate with the device as a serial device.</span></span> <span data-ttu-id="733bd-332">Esta classe baseia-se na norma USB e é um subconjunto da norma CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-332">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="733bd-333">Uma estrutura do dispositivo em conformidade CDC-ACM tem de ser declarada pela pilha do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-333">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="733bd-334">Um exemplo é encontrado aqui em baixo.</span><span class="sxs-lookup"><span data-stu-id="733bd-334">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

<span data-ttu-id="733bd-335">A classe CDC-ACM utiliza uma estrutura de dispositivo composto para interfaces de grupo (controlo e dados).</span><span class="sxs-lookup"><span data-stu-id="733bd-335">The CDC-ACM class uses a composite device framework to group interfaces (control and data).</span></span> <span data-ttu-id="733bd-336">Como resultado, deve ter-se cuidado ao definir o descritor do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-336">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="733bd-337">O USBX conta com o descritor da IAD para saber internamente como ligar interfaces.</span><span class="sxs-lookup"><span data-stu-id="733bd-337">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="733bd-338">O descritor da IAD deve ser declarado antes das interfaces e conter a primeira interface da classe CDC-ACM e quantas interfaces estão anexadas.</span><span class="sxs-lookup"><span data-stu-id="733bd-338">The IAD descriptor should be declared before the interfaces and contain the first interface of the CDC-ACM class and how many interfaces are attached.</span></span>

<span data-ttu-id="733bd-339">A classe CDC-ACM também usa um descritor funcional da união que desempenha a mesma função que o descritor mais recente da IAD.</span><span class="sxs-lookup"><span data-stu-id="733bd-339">The CDC-ACM class also uses a union functional descriptor which performs the same function as the newer IAD descriptor.</span></span> <span data-ttu-id="733bd-340">Embora um descritor funcional da União deva ser declarado por razões históricas e compatibilidade com o lado anfitrião, este não é utilizado pela USBX.</span><span class="sxs-lookup"><span data-stu-id="733bd-340">Although a Union Functional descriptor must be declared for historical reasons and compatibility with the host side, it is not used by USBX.</span></span>

<span data-ttu-id="733bd-341">A inicialização da classe CDC-ACM espera os seguintes parâmetros.</span><span class="sxs-lookup"><span data-stu-id="733bd-341">The initialization of the CDC-ACM class expects the following parameters.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

<span data-ttu-id="733bd-342">Os 2 parâmetros definidos são os ponteiros de retorno nas aplicações do utilizador que serão chamados quando a stack ativar ou desativar esta classe.</span><span class="sxs-lookup"><span data-stu-id="733bd-342">The 2 parameters defined are callback pointers into the user applications that will be called when the stack activates or deactivate this class.</span></span>

<span data-ttu-id="733bd-343">O terceiro parâmetro definido é um ponteiro de retorno para a aplicação do utilizador que será chamado quando houver codificação de linha ou mudança de parâmetro de linha.</span><span class="sxs-lookup"><span data-stu-id="733bd-343">The third parameter defined is a callback pointer to the user application that will be called when there is line coding or line states parameter change.</span></span> <span data-ttu-id="733bd-344">Por exemplo, quando há pedido do anfitrião para alterar o estado DTR para **TRUE,** a chamada é invocada, na sua aplicação o utilizador pode verificar os estados da linha através da função IOCTL para o anfitrião kow está pronto para comunicação.</span><span class="sxs-lookup"><span data-stu-id="733bd-344">E.g., when there is request from host to change DTR state to **TRUE**, the callback is invoked, in it user application can check line states through IOCTL function to kow host is ready for communication.</span></span>

<span data-ttu-id="733bd-345">O CDC-ACM baseia-se numa norma USB-IF e é automaticamente reconhecido pelos sistemas operativos MACOs e Linux.</span><span class="sxs-lookup"><span data-stu-id="733bd-345">The CDC-ACM is based on a USB-IF standard and is automatically recognized by MACOs and Linux operating systems.</span></span> <span data-ttu-id="733bd-346">Nas plataformas do Windows, esta classe requer um ficheiro .inf para a versão do Windows antes de 10.</span><span class="sxs-lookup"><span data-stu-id="733bd-346">On Windows platforms, this class requires a .inf file for Windows version prior to 10.</span></span> <span data-ttu-id="733bd-347">O Windows 10 não requer ficheiros .inf.</span><span class="sxs-lookup"><span data-stu-id="733bd-347">Windows 10 does not require any .inf files.</span></span> <span data-ttu-id="733bd-348">Fornecemos um modelo para a classe CDC-ACM e pode ser encontrado no ***diretório usbx_windows_host_files.***</span><span class="sxs-lookup"><span data-stu-id="733bd-348">We supply a template for the CDC-ACM class and it can be found in the ***usbx_windows_host_files*** directory.</span></span> <span data-ttu-id="733bd-349">Para a versão mais recente do Windows, o ficheiro CDC_ACM_Template_Win7_64bit.inf deve ser utilizado (exceto Win10).</span><span class="sxs-lookup"><span data-stu-id="733bd-349">For more recent version of Windows the file CDC_ACM_Template_Win7_64bit.inf should be used (except Win10).</span></span> <span data-ttu-id="733bd-350">Este ficheiro precisa de ser modificado para refletir o PID/VID utilizado pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-350">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="733bd-351">O PID/VID será específico para o cliente final quando a empresa e o produto estiverem registados no USB-IF.</span><span class="sxs-lookup"><span data-stu-id="733bd-351">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="733bd-352">No ficheiro inf, os campos a modificar estão localizados aqui.</span><span class="sxs-lookup"><span data-stu-id="733bd-352">In the inf file, the fields to modify are located here.</span></span>

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

<span data-ttu-id="733bd-353">Na estrutura do dispositivo do dispositivo CDC-ACM, o PID/VID é armazenado no descritor do dispositivo (ver descritor do dispositivo acima declarado).</span><span class="sxs-lookup"><span data-stu-id="733bd-353">In the device framework of the CDC-ACM device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="733bd-354">Quando um sistema de anfitrião USB descobrir o dispositivo USB CDC-ACM, montará uma classe de série e o dispositivo pode ser utilizado com qualquer programa de terminal de série.</span><span class="sxs-lookup"><span data-stu-id="733bd-354">When a USB host systems discovers the USB CDC-ACM device, it will mount a serial class and the device can be used with any serial terminal program.</span></span> <span data-ttu-id="733bd-355">Consulte o Sistema Operativo do anfitrião para obter referência.</span><span class="sxs-lookup"><span data-stu-id="733bd-355">See the host Operating System for reference.</span></span>

<span data-ttu-id="733bd-356">As funções API da classe CDC-ACM são definidas abaixo.</span><span class="sxs-lookup"><span data-stu-id="733bd-356">The CDC-ACM class API functions are defined below.</span></span>

### <a name="ux_device_class_cdc_acm_ioctl"></a><span data-ttu-id="733bd-357">ux_device_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="733bd-357">ux_device_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="733bd-358">Execute o IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-358">Perform IOCTL on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-359">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-359">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-360">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-360">Description</span></span>

<span data-ttu-id="733bd-361">Esta função é chamada quando uma aplicação precisa executar várias chamadas ioctl para a interface cdc acm</span><span class="sxs-lookup"><span data-stu-id="733bd-361">This function is called when an application needs to perform various ioctl calls to the cdc acm interface</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-362">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-362">Parameters</span></span>

- <span data-ttu-id="733bd-363">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-363">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-364">**ioctl_function**: Função ioctl a desempenhar.</span><span class="sxs-lookup"><span data-stu-id="733bd-364">**ioctl_function**: Ioctl function to be performed.</span></span>
- <span data-ttu-id="733bd-365">**parâmetro**: Ponteiro para um parâmetro específico da chamada do ioctl.</span><span class="sxs-lookup"><span data-stu-id="733bd-365">**parameter**: Pointer to a parameter specific to the ioctl call.</span></span>

### <a name="return-value"></a><span data-ttu-id="733bd-366">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-366">Return Value</span></span>

- <span data-ttu-id="733bd-367">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-367">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-368">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="733bd-368">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="733bd-369">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-369">Example</span></span>

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a><span data-ttu-id="733bd-370">Funções ioctl:</span><span class="sxs-lookup"><span data-stu-id="733bd-370">Ioctl functions:</span></span>

| <span data-ttu-id="733bd-371">Função</span><span class="sxs-lookup"><span data-stu-id="733bd-371">Function</span></span>                                        | <span data-ttu-id="733bd-372">Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-372">Value</span></span> |
| ----------------------------------------------- | - |
| <span data-ttu-id="733bd-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="733bd-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>    | <span data-ttu-id="733bd-374">1</span><span class="sxs-lookup"><span data-stu-id="733bd-374">1</span></span> |
| <span data-ttu-id="733bd-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="733bd-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>    | <span data-ttu-id="733bd-376">2</span><span class="sxs-lookup"><span data-stu-id="733bd-376">2</span></span> |
| <span data-ttu-id="733bd-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="733bd-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>     | <span data-ttu-id="733bd-378">3</span><span class="sxs-lookup"><span data-stu-id="733bd-378">3</span></span> |
| <span data-ttu-id="733bd-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="733bd-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>         | <span data-ttu-id="733bd-380">4</span><span class="sxs-lookup"><span data-stu-id="733bd-380">4</span></span> |
| <span data-ttu-id="733bd-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="733bd-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>     | <span data-ttu-id="733bd-382">5</span><span class="sxs-lookup"><span data-stu-id="733bd-382">5</span></span> |
| <span data-ttu-id="733bd-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="733bd-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span> | <span data-ttu-id="733bd-384">6</span><span class="sxs-lookup"><span data-stu-id="733bd-384">6</span></span> |
| <span data-ttu-id="733bd-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="733bd-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>  | <span data-ttu-id="733bd-386">7</span><span class="sxs-lookup"><span data-stu-id="733bd-386">7</span></span> |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="733bd-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="733bd-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>

<span data-ttu-id="733bd-388">Executar codificação de linha de conjunto IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-388">Perform IOCTL Set Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-389">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-389">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-390">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-390">Description</span></span>

<span data-ttu-id="733bd-391">Esta função é chamada quando uma aplicação precisa de definir os parâmetros de codificação da linha.</span><span class="sxs-lookup"><span data-stu-id="733bd-391">This function is called when an application needs to Set the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-392">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-392">Parameters</span></span>

- <span data-ttu-id="733bd-393">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-393">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="733bd-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="733bd-395">**parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:</span><span class="sxs-lookup"><span data-stu-id="733bd-395">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="733bd-396">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-396">Return Value</span></span>

<span data-ttu-id="733bd-397">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-397">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-398">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-398">Example</span></span>

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="733bd-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="733bd-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>

<span data-ttu-id="733bd-400">Executar codificação de linha DO IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-400">Perform IOCTL Get Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-401">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-401">Prototype</span></span>

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-402">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-402">Description</span></span>

<span data-ttu-id="733bd-403">Esta função é chamada quando uma aplicação precisa de obter os parâmetros de codificação da linha.</span><span class="sxs-lookup"><span data-stu-id="733bd-403">This function is called when an application needs to Get the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-404">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-404">Parameters</span></span>

- <span data-ttu-id="733bd-405">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-405">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="733bd-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span></span>
- <span data-ttu-id="733bd-407">**parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:</span><span class="sxs-lookup"><span data-stu-id="733bd-407">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="733bd-408">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-408">Return Value</span></span>

- <span data-ttu-id="733bd-409">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-409">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-410">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-410">Example</span></span>

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a><span data-ttu-id="733bd-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="733bd-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>

<span data-ttu-id="733bd-412">Executar o Estado de Linha DO IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-412">Perform IOCTL Get Line State on the CDC-ACM interface</span></span>

## <a name="prototype"></a><span data-ttu-id="733bd-413">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-413">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-414">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-414">Description</span></span>

<span data-ttu-id="733bd-415">Esta função é chamada quando uma aplicação precisa de obter os parâmetros do Estado da Linha.</span><span class="sxs-lookup"><span data-stu-id="733bd-415">This function is called when an application needs to Get the Line State parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-416">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-416">Parameters</span></span>

- <span data-ttu-id="733bd-417">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-417">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="733bd-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>
- <span data-ttu-id="733bd-419">**parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:</span><span class="sxs-lookup"><span data-stu-id="733bd-419">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="733bd-420">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-420">Return Value</span></span>

- <span data-ttu-id="733bd-421">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-421">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-422">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-422">Example</span></span>

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="733bd-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="733bd-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>

<span data-ttu-id="733bd-424">Execute o Estado da linha de fixação do IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-424">Perform IOCTL Set Line State on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-425">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-425">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-426">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-426">Description</span></span>

<span data-ttu-id="733bd-427">Esta função é chamada quando uma aplicação precisa de obter os parâmetros do Estado da Linha</span><span class="sxs-lookup"><span data-stu-id="733bd-427">This function is called when an application needs to Get the Line State parameters</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-428">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-428">Parameters</span></span>

- <span data-ttu-id="733bd-429">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-429">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="733bd-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="733bd-431">**parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:</span><span class="sxs-lookup"><span data-stu-id="733bd-431">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="733bd-432">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-432">Return Value</span></span>

- <span data-ttu-id="733bd-433">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-433">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-434">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-434">Example</span></span>

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a><span data-ttu-id="733bd-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="733bd-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>

<span data-ttu-id="733bd-436">Executar TUBO ABORTO IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-436">Perform IOCTL ABORT PIPE on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-437">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-437">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-438">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-438">Description</span></span>

<span data-ttu-id="733bd-439">Esta função é chamada quando uma aplicação precisa de abortar um tubo.</span><span class="sxs-lookup"><span data-stu-id="733bd-439">This function is called when an application needs to abort a pipe.</span></span> <span data-ttu-id="733bd-440">Por exemplo, para abortar uma escrita em curso, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT deve ser passado como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="733bd-440">For example, to abort an ongoing write, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT should be passed as the parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-441">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-441">Parameters</span></span>

- <span data-ttu-id="733bd-442">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-442">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="733bd-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>
- <span data-ttu-id="733bd-444">**parâmetro**: A direção do tubo:</span><span class="sxs-lookup"><span data-stu-id="733bd-444">**parameter**: The pipe direction:</span></span>

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a><span data-ttu-id="733bd-445">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-445">Return Value</span></span>

- <span data-ttu-id="733bd-446">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-446">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Direção do tubo inválido.</span><span class="sxs-lookup"><span data-stu-id="733bd-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Invalid pipe direction.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-448">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-448">Example</span></span>

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a><span data-ttu-id="733bd-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="733bd-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>

<span data-ttu-id="733bd-450">Executar início de transmissão IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-450">Perform IOCTL Transmission Start on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-451">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-451">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-452">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-452">Description</span></span>

<span data-ttu-id="733bd-453">Esta função é chamada quando uma aplicação quer utilizar a transmissão com retorno.</span><span class="sxs-lookup"><span data-stu-id="733bd-453">This function is called when an application wants to use transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-454">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-454">Parameters</span></span>

- <span data-ttu-id="733bd-455">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-455">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="733bd-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>
- <span data-ttu-id="733bd-457">**parâmetro**: Ponteiro para a estrutura do parâmetro de transmissão inicial:</span><span class="sxs-lookup"><span data-stu-id="733bd-457">**parameter**: Pointer to the Start Transmission parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="733bd-458">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-458">Return Value</span></span>

- <span data-ttu-id="733bd-459">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-459">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-460">**UX_ERROR** (0xFF) A transmissão já começou.</span><span class="sxs-lookup"><span data-stu-id="733bd-460">**UX_ERROR** (0xFF) Transmission already started.</span></span>
- <span data-ttu-id="733bd-461">**UX_MEMORY_INSUFFICIENT** (0x12) Uma atribuição de memória falhou.</span><span class="sxs-lookup"><span data-stu-id="733bd-461">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-462">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-462">Example</span></span>

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a><span data-ttu-id="733bd-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="733bd-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>

<span data-ttu-id="733bd-464">Execute a paragem de transmissão do IOCTL na interface CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-464">Perform IOCTL Transmission Stop on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-465">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-465">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="733bd-466">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-466">Description</span></span>

<span data-ttu-id="733bd-467">Esta função é chamada quando uma aplicação quer parar de usar a transmissão com retorno.</span><span class="sxs-lookup"><span data-stu-id="733bd-467">This function is called when an application wants to stop using transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-468">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-468">Parameters</span></span>

- <span data-ttu-id="733bd-469">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-469">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span><span class="sxs-lookup"><span data-stu-id="733bd-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span></span>
- <span data-ttu-id="733bd-471">**parâmetro**: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="733bd-471">**parameter**: Not used</span></span>

### <a name="return-value"></a><span data-ttu-id="733bd-472">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-472">Return Value</span></span>

- <span data-ttu-id="733bd-473">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-473">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-474">**UX_ERROR** (0xFF) Nenhuma transmissão em curso.</span><span class="sxs-lookup"><span data-stu-id="733bd-474">**UX_ERROR** (0xFF) No ongoing transmission.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-475">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-475">Example</span></span>

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a><span data-ttu-id="733bd-476">ux_device_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="733bd-476">ux_device_class_cdc_acm_read</span></span>

<span data-ttu-id="733bd-477">Leia do tubo CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-477">Read from CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-478">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-478">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="733bd-479">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-479">Description</span></span>

<span data-ttu-id="733bd-480">Esta função é chamada quando uma aplicação precisa de ser lida a partir do tubo de dados OUT (OUT do anfitrião, IN do dispositivo).</span><span class="sxs-lookup"><span data-stu-id="733bd-480">This function is called when an application needs to read from the OUT data pipe (OUT from the host, IN from the device).</span></span> <span data-ttu-id="733bd-481">Está a bloquear.</span><span class="sxs-lookup"><span data-stu-id="733bd-481">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-482">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-482">Parameters</span></span>

- <span data-ttu-id="733bd-483">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-483">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-484">**tampão**: Endereço tampão onde os dados serão armazenados.</span><span class="sxs-lookup"><span data-stu-id="733bd-484">**buffer**: Buffer address where data will be stored.</span></span>
- <span data-ttu-id="733bd-485">**requested_length:** O comprimento máximo que esperamos.</span><span class="sxs-lookup"><span data-stu-id="733bd-485">**requested_length**: The maximum length we expect.</span></span>
- <span data-ttu-id="733bd-486">**atual_length:** O comprimento devolvido ao tampão.</span><span class="sxs-lookup"><span data-stu-id="733bd-486">**actual_length**: The length returned into the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="733bd-487">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-487">Return Value</span></span>

- <span data-ttu-id="733bd-488">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-488">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** dispositivo (0x51) já não se encontra no estado configurado.</span><span class="sxs-lookup"><span data-stu-id="733bd-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="733bd-490">**UX_TRANSFER_NO_ANSWER** (0x22) Nenhuma resposta do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-490">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="733bd-491">O dispositivo deve ter sido desligado enquanto a transferência estava pendente.</span><span class="sxs-lookup"><span data-stu-id="733bd-491">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-492">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-492">Example</span></span>

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a><span data-ttu-id="733bd-493">ux_device_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="733bd-493">ux_device_class_cdc_acm_write</span></span>

<span data-ttu-id="733bd-494">Escreva para um tubo CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="733bd-494">Write to a CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-495">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-495">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="733bd-496">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-496">Description</span></span>

<span data-ttu-id="733bd-497">Esta função é chamada quando uma aplicação precisa de escrever para o tubo de dados IN (IN do anfitrião, OUT do dispositivo).</span><span class="sxs-lookup"><span data-stu-id="733bd-497">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="733bd-498">Está a bloquear.</span><span class="sxs-lookup"><span data-stu-id="733bd-498">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-499">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-499">Parameters</span></span>

- <span data-ttu-id="733bd-500">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-500">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-501">**tampão**: Endereço tampão onde os dados são armazenados.</span><span class="sxs-lookup"><span data-stu-id="733bd-501">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="733bd-502">**requested_length:** O comprimento do tampão para escrever.</span><span class="sxs-lookup"><span data-stu-id="733bd-502">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="733bd-503">**atual_length**: O comprimento devolvido ao tampão após a escrita é executado.</span><span class="sxs-lookup"><span data-stu-id="733bd-503">**actual_length**: The length returned into the buffer after write is performed.</span></span>

### <a name="return-value"></a><span data-ttu-id="733bd-504">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-504">Return Value</span></span>
- <span data-ttu-id="733bd-505">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-505">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** dispositivo (0x51) já não se encontra no estado configurado.</span><span class="sxs-lookup"><span data-stu-id="733bd-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="733bd-507">**UX_TRANSFER_NO_ANSWER** (0x22) Nenhuma resposta do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-507">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="733bd-508">O dispositivo deve ter sido desligado enquanto a transferência estava pendente.</span><span class="sxs-lookup"><span data-stu-id="733bd-508">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-509">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-509">Example</span></span>

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a><span data-ttu-id="733bd-510">ux_device_class_cdc_acm_write_with_callback</span><span class="sxs-lookup"><span data-stu-id="733bd-510">ux_device_class_cdc_acm_write_with_callback</span></span>

<span data-ttu-id="733bd-511">Escrever para um tubo CDC-ACM com retorno</span><span class="sxs-lookup"><span data-stu-id="733bd-511">Writing to a CDC-ACM pipe with callback</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-512">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-512">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a><span data-ttu-id="733bd-513">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-513">Description</span></span>

<span data-ttu-id="733bd-514">Esta função é chamada quando uma aplicação precisa de escrever para o tubo de dados IN (IN do anfitrião, OUT do dispositivo).</span><span class="sxs-lookup"><span data-stu-id="733bd-514">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="733bd-515">Esta função não bloqueia e a conclusão será feita através de um revés definido em UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span><span class="sxs-lookup"><span data-stu-id="733bd-515">This function is non-blocking and the completion will be done through a callback set in UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-516">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-516">Parameters</span></span>

- <span data-ttu-id="733bd-517">**cdc_acm**: Ponte para a instância da classe CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-517">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="733bd-518">**tampão**: Endereço tampão onde os dados são armazenados.</span><span class="sxs-lookup"><span data-stu-id="733bd-518">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="733bd-519">**requested_length:** O comprimento do tampão para escrever.</span><span class="sxs-lookup"><span data-stu-id="733bd-519">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="733bd-520">**atual_length**: O comprimento devolvido ao tampão após a escrita é realizado</span><span class="sxs-lookup"><span data-stu-id="733bd-520">**actual_length**: The length returned into the buffer after write is performed</span></span>

### <a name="return-value"></a><span data-ttu-id="733bd-521">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-521">Return Value</span></span>

- <span data-ttu-id="733bd-522">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-522">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** dispositivo (0x51) já não se encontra no estado configurado.</span><span class="sxs-lookup"><span data-stu-id="733bd-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="733bd-524">**UX_TRANSFER_NO_ANSWER** (0x22) Nenhuma resposta do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-524">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="733bd-525">O dispositivo deve ter sido desligado enquanto a transferência estava pendente.</span><span class="sxs-lookup"><span data-stu-id="733bd-525">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-526">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-526">Example</span></span>

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a><span data-ttu-id="733bd-527">Classe CDC-ECM do dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="733bd-527">USB Device CDC-ECM Class</span></span>

<span data-ttu-id="733bd-528">A classe CDC-ECM do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como um dispositivo ethernet.</span><span class="sxs-lookup"><span data-stu-id="733bd-528">The USB device CDC-ECM class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="733bd-529">Esta classe baseia-se na norma USB e é um subconjunto da norma CDC.</span><span class="sxs-lookup"><span data-stu-id="733bd-529">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="733bd-530">Uma estrutura do dispositivo em conformidade CDC-ACM tem de ser declarada pela pilha do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-530">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="733bd-531">Um exemplo é encontrado aqui em baixo.</span><span class="sxs-lookup"><span data-stu-id="733bd-531">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

<span data-ttu-id="733bd-532">A classe CDC-ECM utiliza uma abordagem de descritor de dispositivos muito semelhante ao CDC-ACM e também requer um descritor de IAD.</span><span class="sxs-lookup"><span data-stu-id="733bd-532">The CDC-ECM class uses a very similar device descriptor approach to the CDC-ACM and also requires an IAD descriptor.</span></span> <span data-ttu-id="733bd-533">Consulte a classe CDC-ACM para definição.</span><span class="sxs-lookup"><span data-stu-id="733bd-533">See the CDC-ACM class for definition.</span></span>

<span data-ttu-id="733bd-534">Além da estrutura regular do dispositivo, o CDC-ECM requer descritores especiais de cordas.</span><span class="sxs-lookup"><span data-stu-id="733bd-534">In addition to the regular device framework, the CDC-ECM requires special string descriptors.</span></span> <span data-ttu-id="733bd-535">Um exemplo é dado abaixo.</span><span class="sxs-lookup"><span data-stu-id="733bd-535">An example is given below.</span></span>

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

<span data-ttu-id="733bd-536">O descritor de cordas de endereço MAC é utilizado pela classe CDC-ECM para responder às perguntas do anfitrião sobre o endereço MAC a que o dispositivo está a responder no protocolo TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="733bd-536">The MAC address string descriptor is used by the CDC-ECM class to reply to the host queries as to what MAC address the device is answering to at the TCP/IP protocol.</span></span> <span data-ttu-id="733bd-537">Pode ser definido para a escolha do dispositivo, mas deve ser definido aqui.</span><span class="sxs-lookup"><span data-stu-id="733bd-537">It can be set to the device choice but must be defined here.</span></span>

<span data-ttu-id="733bd-538">A inicialização da classe CDC-ECM é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="733bd-538">The initialization of the CDC-ECM class is as follows.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

<span data-ttu-id="733bd-539">A inicialização desta classe espera a mesma função de retorno para ativação e desativação, embora aqui como um exercício eles estão definidos para NU PARA que não seja realizada nenhuma chamada.</span><span class="sxs-lookup"><span data-stu-id="733bd-539">The initialization of this class expects the same function callback for activation and deactivation, although here as an exercise they are set to NULL so that no callback is performed.</span></span>

<span data-ttu-id="733bd-540">Os próximos parâmetros são para a definição dos IDs do nó.</span><span class="sxs-lookup"><span data-stu-id="733bd-540">The next parameters are for the definition of the node IDs.</span></span> <span data-ttu-id="733bd-541">2 Os nós são necessários para o CDC-ECM, um nó local e um nó remoto.</span><span class="sxs-lookup"><span data-stu-id="733bd-541">2 Nodes are necessary for the CDC-ECM, a local node and a remote node.</span></span> <span data-ttu-id="733bd-542">O nó local especifica o endereço MAC do dispositivo, enquanto o nó remoto especifica o endereço MAC do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="733bd-542">The local node specifies the MAC address of the device, while the remote node specifies the MAC address of the host.</span></span> <span data-ttu-id="733bd-543">O nó remoto deve ser o mesmo que o declarado no descritor de cordas de estrutura do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-543">The remote node must be the same one as the one declared in the device framework string descriptor.</span></span>

<span data-ttu-id="733bd-544">A classe CDC-ECM tem APIs incorporados para transferir dados em ambos os sentidos, mas estão escondidos à aplicação, uma vez que a aplicação do utilizador comunicará com o dispositivo USB Ethernet através do NetX.</span><span class="sxs-lookup"><span data-stu-id="733bd-544">The CDC-ECM class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="733bd-545">A classe USBX CDC-ECM está intimamente ligada à pilha de rede Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="733bd-545">The USBX CDC-ECM class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="733bd-546">Uma aplicação utilizando a classe NetX e USBX CDC-ECM irá ativar a pilha de rede NetX da forma habitual, mas além disso precisa de ativar a pilha de rede USB da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="733bd-546">An application using both NetX and USBX CDC-ECM class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="733bd-547">A pilha de rede USB precisa de ser ativada apenas uma vez e não é específica da CDCECM, mas é exigida por qualquer classe USB que exija serviços NetX.</span><span class="sxs-lookup"><span data-stu-id="733bd-547">The USB network stack needs to be activated only once and is not specific to CDCECM but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="733bd-548">A classe CDC-ECM será reconhecida pelos anfitriões MAC OS e Linux.</span><span class="sxs-lookup"><span data-stu-id="733bd-548">The CDC-ECM class will be recognized by MAC OS and Linux hosts.</span></span> <span data-ttu-id="733bd-549">Mas não existe nenhum controlador fornecido pelo Microsoft Windows para reconhecer o CDC-ECM de forma nativa.</span><span class="sxs-lookup"><span data-stu-id="733bd-549">But there is no driver supplied by Microsoft Windows to recognize CDC-ECM natively.</span></span> <span data-ttu-id="733bd-550">Alguns produtos comerciais existem para as plataformas do Windows e fornecem o seu próprio ficheiro .inf.</span><span class="sxs-lookup"><span data-stu-id="733bd-550">Some commercial products do exist for Windows platforms and they supply their own .inf file.</span></span> <span data-ttu-id="733bd-551">Este ficheiro terá de ser modificado da mesma forma que o modelo inf CDC-ACM para corresponder ao PID/VID do dispositivo de rede USB.</span><span class="sxs-lookup"><span data-stu-id="733bd-551">This file will need to be modified the same way as the CDC-ACM inf template to match the PID/VID of the USB network device.</span></span>

## <a name="usb-device-hid-class"></a><span data-ttu-id="733bd-552">Classe HID dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="733bd-552">USB Device HID Class</span></span>

<span data-ttu-id="733bd-553">A classe HID do dispositivo USB permite que um sistema de anfitrião USB se conecte a um dispositivo HID com capacidades específicas do cliente HID.</span><span class="sxs-lookup"><span data-stu-id="733bd-553">The USB device HID class allows for a USB host system to connect to a HID device with specific HID client capabilities.</span></span>

<span data-ttu-id="733bd-554">A classe do dispositivo USBX HID é relativamente simples em comparação com o lado do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="733bd-554">USBX HID device class is relatively simple compared to the host side.</span></span> <span data-ttu-id="733bd-555">Está intimamente ligado ao comportamento do dispositivo e do seu descritor HID.</span><span class="sxs-lookup"><span data-stu-id="733bd-555">It is closely tied to the behavior of the device and its HID descriptor.</span></span>

<span data-ttu-id="733bd-556">Qualquer cliente HID requer primeiro definir uma estrutura do dispositivo HID como o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="733bd-556">Any HID client requires first to define a HID device framework as the example below.</span></span>

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

<span data-ttu-id="733bd-557">A estrutura HID contém um descritor de interface que descreve a classe HID e a subclasse do dispositivo HID.</span><span class="sxs-lookup"><span data-stu-id="733bd-557">The HID framework contains an interface descriptor that describes the HID class and the HID device subclass.</span></span> <span data-ttu-id="733bd-558">A interface HID pode ser uma classe autónoma ou parte de um dispositivo composto.</span><span class="sxs-lookup"><span data-stu-id="733bd-558">The HID interface can be a standalone class or part of a composite device.</span></span>

<span data-ttu-id="733bd-559">Atualmente, a classe USBX HID não suporta múltiplos IDs de relatório, uma vez que a maioria das aplicações requer apenas um ID (ID zero).</span><span class="sxs-lookup"><span data-stu-id="733bd-559">Currently, the USBX HID class does not support multiple report IDs, as most applications only require one ID (ID zero).</span></span> <span data-ttu-id="733bd-560">Se várias IDs de relatório forem uma funcionalidade que lhe interessa, contacte-nos.</span><span class="sxs-lookup"><span data-stu-id="733bd-560">If multiple report IDs is a feature you are interested in, please contact us.</span></span>

<span data-ttu-id="733bd-561">A inicialização da classe HID é a seguinte, usando um teclado USB como exemplo.</span><span class="sxs-lookup"><span data-stu-id="733bd-561">The initialization of the HID class is as follow, using a USB keyboard as an example.</span></span>

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

<span data-ttu-id="733bd-562">A aplicação tem de passar para a classe HID um descritor de relatório HID e seu comprimento.</span><span class="sxs-lookup"><span data-stu-id="733bd-562">The application needs to pass to the HID class a HID report descriptor and its length.</span></span> <span data-ttu-id="733bd-563">O descritor de relatórios é uma coleção de itens que descrevem o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-563">The report descriptor is a collection of items that describe the device.</span></span> <span data-ttu-id="733bd-564">Para obter mais informações sobre a gramática HID consulte a especificação da classe USB HID.</span><span class="sxs-lookup"><span data-stu-id="733bd-564">For more information on the HID grammar refer to the HID USB class specification.</span></span>

<span data-ttu-id="733bd-565">Além do descritor de relatórios, a aplicação passa uma chamada de volta quando um evento HID acontece.</span><span class="sxs-lookup"><span data-stu-id="733bd-565">In addition to the report descriptor, the application passes a call back when a HID event happens.</span></span>

<span data-ttu-id="733bd-566">A classe USBX HID suporta os seguintes comandos HID padrão do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="733bd-566">The USBX HID class supports the following standard HID commands from the host.</span></span>

| <span data-ttu-id="733bd-567">Nome de comando</span><span class="sxs-lookup"><span data-stu-id="733bd-567">Command name</span></span>                             | <span data-ttu-id="733bd-568">Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-568">Value</span></span> | <span data-ttu-id="733bd-569">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-569">Description</span></span>                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| <span data-ttu-id="733bd-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span><span class="sxs-lookup"><span data-stu-id="733bd-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span></span>   | <span data-ttu-id="733bd-571">0x01</span><span class="sxs-lookup"><span data-stu-id="733bd-571">0x01</span></span>  | <span data-ttu-id="733bd-572">Obtenha um relatório do dispositivo</span><span class="sxs-lookup"><span data-stu-id="733bd-572">Get a report from the device</span></span>                     |
| <span data-ttu-id="733bd-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span><span class="sxs-lookup"><span data-stu-id="733bd-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span></span>     | <span data-ttu-id="733bd-574">0x02</span><span class="sxs-lookup"><span data-stu-id="733bd-574">0x02</span></span>  | <span data-ttu-id="733bd-575">Obtenha a frequência ociosa do ponto final de interrupção</span><span class="sxs-lookup"><span data-stu-id="733bd-575">Get the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="733bd-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="733bd-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span></span> | <span data-ttu-id="733bd-577">0x03</span><span class="sxs-lookup"><span data-stu-id="733bd-577">0x03</span></span>  | <span data-ttu-id="733bd-578">Obter o protocolo em funcionamento no dispositivo</span><span class="sxs-lookup"><span data-stu-id="733bd-578">Get the protocol running on the device</span></span>           |
| <span data-ttu-id="733bd-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span><span class="sxs-lookup"><span data-stu-id="733bd-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span></span>   | <span data-ttu-id="733bd-580">0x09</span><span class="sxs-lookup"><span data-stu-id="733bd-580">0x09</span></span>  | <span data-ttu-id="733bd-581">Desa estação de relatório para o dispositivo</span><span class="sxs-lookup"><span data-stu-id="733bd-581">Set a report to the device</span></span>                       |
| <span data-ttu-id="733bd-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span><span class="sxs-lookup"><span data-stu-id="733bd-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span></span>     | <span data-ttu-id="733bd-583">0x0a</span><span class="sxs-lookup"><span data-stu-id="733bd-583">0x0a</span></span>  | <span data-ttu-id="733bd-584">Desaponte a frequência ociosa do ponto final de interrupção</span><span class="sxs-lookup"><span data-stu-id="733bd-584">Set the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="733bd-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="733bd-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span></span> | <span data-ttu-id="733bd-586">0x0b</span><span class="sxs-lookup"><span data-stu-id="733bd-586">0x0b</span></span>  | <span data-ttu-id="733bd-587">Obter o protocolo em funcionamento no dispositivo</span><span class="sxs-lookup"><span data-stu-id="733bd-587">Get the protocol running on the device</span></span>           |

<span data-ttu-id="733bd-588">O relatório Get and set são os comandos mais utilizados pela HID para transferir dados de um lado para o outro entre o anfitrião e o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="733bd-588">The Get and Set report are the most commonly used commands by HID to transfer data back and forth between the host and the device.</span></span> <span data-ttu-id="733bd-589">Mais frequentemente, o hospedeiro envia dados sobre o ponto final de controlo, mas pode receber dados quer no ponto final de interrupção, quer emitindo um comando GET_REPORT para obter os dados no ponto final de controlo.</span><span class="sxs-lookup"><span data-stu-id="733bd-589">Most commonly the host sends data on the control endpoint but can receive data either on the interrupt endpoint or by issuing a GET_REPORT command to fetch the data on the control endpoint.</span></span>

<span data-ttu-id="733bd-590">A classe HID pode enviar dados de volta ao anfitrião no ponto de terminação de interrupção utilizando a função ux_device_class_hid_event_set.</span><span class="sxs-lookup"><span data-stu-id="733bd-590">The HID class can send data back to the host on the interrupt endpoint by using the ux_device_class_hid_event_set function.</span></span>

### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="733bd-591">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="733bd-591">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="733bd-592">Definição de um evento para a classe HID</span><span class="sxs-lookup"><span data-stu-id="733bd-592">Setting an event to the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-593">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-593">Prototype</span></span>

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="733bd-594">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-594">Description</span></span>

<span data-ttu-id="733bd-595">Esta função é chamada quando uma aplicação precisa enviar um evento HID de volta para o anfitrião.</span><span class="sxs-lookup"><span data-stu-id="733bd-595">This function is called when an application needs to send a HID event back to the host.</span></span> <span data-ttu-id="733bd-596">A função não é bloquear, apenas coloca o relatório numa fila circular e regressa à aplicação.</span><span class="sxs-lookup"><span data-stu-id="733bd-596">The function is not blocking, it merely puts the report into a circular queue and returns to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-597">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-597">Parameters</span></span>

- <span data-ttu-id="733bd-598">**escondido:** Ponteiro para a instância de classe escondida.</span><span class="sxs-lookup"><span data-stu-id="733bd-598">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="733bd-599">**hid_event**: Ponteiro para a estrutura do evento escondido.</span><span class="sxs-lookup"><span data-stu-id="733bd-599">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="return-value"></a><span data-ttu-id="733bd-600">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="733bd-600">Return Value</span></span>

- <span data-ttu-id="733bd-601">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="733bd-601">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="733bd-602">**UX_ERROR** (0xFF) Erro nenhum espaço disponível na fila circular.</span><span class="sxs-lookup"><span data-stu-id="733bd-602">**UX_ERROR** (0xFF) Error no space available in circular queue.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-603">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-603">Example</span></span>

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

<span data-ttu-id="733bd-604">A chamada definida na inicialização da classe HID realiza o oposto de enviar um evento.</span><span class="sxs-lookup"><span data-stu-id="733bd-604">The callback defined at the initialization of the HID class performs the opposite of sending an event.</span></span> <span data-ttu-id="733bd-605">Obtém-se como entrada o evento enviado pelo anfitrião.</span><span class="sxs-lookup"><span data-stu-id="733bd-605">It gets as input the event sent by the host.</span></span> <span data-ttu-id="733bd-606">O protótipo da chamada é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="733bd-606">The prototype of the callback is as follows.</span></span>

### <a name="hid_callback"></a><span data-ttu-id="733bd-607">hid_callback</span><span class="sxs-lookup"><span data-stu-id="733bd-607">hid_callback</span></span>

<span data-ttu-id="733bd-608">Obtenção de um evento da classe HID</span><span class="sxs-lookup"><span data-stu-id="733bd-608">Getting an event from the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="733bd-609">Prototype</span><span class="sxs-lookup"><span data-stu-id="733bd-609">Prototype</span></span>

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="733bd-610">Descrição</span><span class="sxs-lookup"><span data-stu-id="733bd-610">Description</span></span>

<span data-ttu-id="733bd-611">Esta função é chamada quando o anfitrião envia um relatório HID para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="733bd-611">This function is called when the host sends a HID report to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="733bd-612">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733bd-612">Parameters</span></span>

- <span data-ttu-id="733bd-613">**escondido:** Ponteiro para a instância de classe escondida.</span><span class="sxs-lookup"><span data-stu-id="733bd-613">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="733bd-614">**hid_event**: Ponteiro para a estrutura do evento escondido.</span><span class="sxs-lookup"><span data-stu-id="733bd-614">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="example"></a><span data-ttu-id="733bd-615">Exemplo</span><span class="sxs-lookup"><span data-stu-id="733bd-615">Example</span></span>

<span data-ttu-id="733bd-616">O exemplo a seguir mostra como interpretar um evento para um teclado HID:</span><span class="sxs-lookup"><span data-stu-id="733bd-616">The following example shows how to interpret an event for a HID keyboard:</span></span>

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
