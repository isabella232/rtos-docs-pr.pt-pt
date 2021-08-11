---
title: Capítulo 3 - Componentes funcionais da pilha de dispositivos USBX
description: Este capítulo contém uma descrição da pilha de dispositivo USB USB incorporada de alto desempenho de uma perspetiva funcional.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 104badcbf1ec682cd8b09008578ba91768834d694473ecccf59e35637dfd9f3c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791362"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a>Capítulo 3 - Componentes funcionais da pilha de dispositivos USBX

Este capítulo contém uma descrição da pilha de dispositivo USB USB incorporada de alto desempenho de uma perspetiva funcional.

## <a name="execution-overview"></a>Visão geral da execução

USBX para o dispositivo é composto por vários componentes.

- Inicialização
- Chamadas de interface de aplicação
- Classes de Dispositivos
- Pilha de dispositivo USB
- Controlador de dispositivos
- Gestor VBUS

O diagrama seguinte ilustra a pilha de dispositivo USBX.

![Pilha de dispositivo USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a>Inicialização

Para ativar o USBX, a função ***ux_system_initialize*** deve ser chamada. Esta função inicializa os recursos de memória do USBX.

Para ativar as instalações do dispositivo USBX, a função ***ux_device_stack_initialize*** deve ser chamada. Esta função irá, por sua vez, inicializar todos os recursos utilizados pela pilha de dispositivos USBX, tais como fios ThreadX, mutexes e semáforos.

Cabe à inicialização da aplicação ativar o controlador do dispositivo USB e uma ou mais classes USB. Ao contrário do lado do anfitrião USB, o lado do dispositivo pode ter apenas um controlador USB a funcionar a qualquer momento. Quando as classes estiverem registadas na stack e a função de inicialização do controlador do dispositivo tiver sido chamada, o autocarro está ativo e a pilha responderá aos comandos de reposição de autocarros e de enumeração do anfitrião.

### <a name="application-interface-calls"></a>Chamadas de Interface de Aplicação

Há dois níveis de APIs em USBX.

- APIs de pilha de dispositivos USB
- APIs classe de dispositivo USB

Normalmente, uma aplicação USBX não deve ter de chamar apis de pilha de dispositivo USB. A maioria das aplicações só acederá às APIs da classe USB.

### <a name="usb-device-stack-apis"></a>APIs de pilha de dispositivos USB

As APIs da pilha de dispositivos são responsáveis pelo registo de componentes do dispositivo USBX, tais como classes e a estrutura do dispositivo.

### <a name="usb-device-class-apis"></a>APIs classe de dispositivo USB

As APIs de classe são muito específicas de cada classe USB. A maioria das APIs comuns para classes USB forneceu serviços como abrir/fechar um dispositivo e ler e escrever para um dispositivo. As APIs são semelhantes na natureza ao lado hospedeiro.

## <a name="device-framework"></a>Estrutura do Dispositivo

O lado do dispositivo USB é responsável pela definição da estrutura do dispositivo. A estrutura do dispositivo é dividida em três categorias, conforme descrito nas seguintes secções.

### <a name="definition-of-the-components-of-the-device-framework"></a>Definição dos componentes da estrutura do dispositivo

A definição de cada componente da estrutura do dispositivo está relacionada com a natureza do dispositivo e com os recursos utilizados pelo dispositivo. Seguem-se as principais categorias.

- Descritor de dispositivos
- Descritor de configuração
- Descritor de interface
- Descritor de ponto final

USBX suporta a definição de componente do dispositivo para alta e a velocidade máxima (sendo tratada a baixa velocidade da mesma forma que a velocidade máxima). Isto permite que o dispositivo funcione de forma diferente quando ligado a um hospedeiro de alta velocidade ou a toda a velocidade. As diferenças típicas são o tamanho de cada ponto final e a energia consumida pelo dispositivo.

A definição do componente do dispositivo assume a forma de uma cadeia byte que segue a especificação USB. A definição é contígua e a ordem em que o quadro está representado na memória será a mesma que a devolvida ao hospedeiro durante a enumeração.

Segue-se um exemplo de uma estrutura do dispositivo para um disco FLASH USB de alta velocidade.

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a>Definição das cordas da estrutura do dispositivo

As cordas são opcionais num dispositivo. O seu objetivo é informar o anfitrião USB sobre o fabricante do dispositivo, o nome do produto e o número de revisão através das cordas Unicode.

As cordas principais são índices incorporados nos descritores do dispositivo. Índices de cordas adicionais podem ser incorporados em interfaces individuais.

Assumindo que a estrutura do dispositivo acima tem três índices de cadeia incorporados no descritor do dispositivo, a definição de estrutura de cadeia pode parecer este código de exemplo.

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38
UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

Se tiverem de ser utilizadas diferentes cordas para cada velocidade, devem ser utilizados diferentes índices, uma vez que os índices são agnósticos de velocidade.

A codificação da cadeia é baseada em UNICODE. Para obter mais informações sobre a norma de codificação UNICODE consulte a seguinte publicação:

*O Unicode Standard, Worldwide Character Encoding, Versão 1., Volumes 1 e 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a>Definição dos idiomas suportados pelo dispositivo para cada cadeia

USBX tem a capacidade de suportar vários idiomas, embora o inglês seja o padrão. A definição de cada idioma para os descritores de cordas é na forma de uma variedade de definições de línguas definidas da seguinte forma.

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

Para suportar idiomas adicionais, basta adicionar a definição de código de idioma de duplo byte após o código inglês predefinido. O código de idioma foi definido pela Microsoft no documento.

*Desenvolvimento de Software Internacional para Windows 95 e Windows NT, Nadine Kano, Microsoft Press, Redmond WA*

## <a name="vbus-manager"></a>Gestor VBUS

Na maioria dos desenhos de dispositivos USB, o VBUS não faz parte do núcleo do dispositivo USB, mas sim está ligado a um GPIO externo, que monitoriza o sinal de linha.

Como resultado, a VBUS tem de ser gerida separadamente do controlador do dispositivo.

Cabe à aplicação fornecer ao controlador do dispositivo o endereço do VBUS IO. O VBUS deve ser inicializado antes da inicialização do controlador do dispositivo.

Dependendo da especificação da plataforma de monitorização do VBUS, é possível permitir que o controlador manuseie os sinais VBUS após a inicializada VBUS IO ou, se tal não for possível, a aplicação tem de fornecer o código de manuseamento do VBUS.

Se a aplicação pretender manusear o VBUS por si só, o seu único requisito é chamar a função ***ux_device_stack_disconnect*** quando detetar que um dispositivo foi extraído. Não é necessário informar o controlador quando um dispositivo é inserido porque o controlador acordará quando for detetado o sinal de assert/deassert do BUS RESET.
