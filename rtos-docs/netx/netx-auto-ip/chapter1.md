---
title: Capítulo 1 - Introdução ao Azure RTOS NetX AutoIP
description: O Azure RTOS NetX AutoIP Protocol é um protocolo projetado para configurar dinamicamente endereços IPv4 numa rede local.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c26b4112814bb586e056246d68c2597d56df6085
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826851"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-autoip"></a>Capítulo 1 - Introdução ao Azure RTOS NetX AutoIP
  
O Azure RTOS NetX AutoIP Protocol é um protocolo projetado para configurar dinamicamente endereços IPv4 numa rede local. O AutoIP é um protocolo simples que utiliza as capacidades ARP para executar a sua função automática de atribuição de endereços IP. O AutoIP atribui endereços no intervalo de 169.254.1.0 a 169.254.254.255.

## <a name="autoip-requirements"></a>Requisitos de autoIP

Para funcionar corretamente, o pacote NetX AutoIP requer que já tenha sido criada uma instância IP NetX. Além disso, o ARP deve ser ativado nessa mesma instância IP. O pacote NetX AutoIP não tem mais requisitos.

## <a name="autoip-constraints"></a>Restrições autoIP 

O protocolo NetX AutoIP implementa os requisitos da norma RFC3927. No entanto, existem os seguintes constrangimentos:

1. Se o NetX DHCP for utilizado, o fio DHCP deve ser criado com uma prioridade maior do que tanto o fio de instância NetX IP como o fio AutoIP.
1. O NetX AutoIP não fornece um mecanismo para que os antigos endereços IP continuem a ser utilizados.
1. Quando o endereço IP muda, a aplicação é responsável por demolir quaisquer ligações TCP existentes e restabelece-las no novo endereço IP.

## <a name="autoip-protocol-implementation"></a>Implementação do Protocolo AutoIP

O protocolo NetX AutoIP seleciona pela primeira vez um endereço aleatório dentro do intervalo de endereços AutoIP IPv4 de 169.254.1.0 a 169.254.254.255. Em alternativa, a aplicação pode forçar um endereço IP inicial fornecendo-o à função ***nx_auto_ip_start.*** Isto é útil em situações em que um endereço AutoIP foi utilizado com sucesso numa execução prévia.

Uma vez selecionado um endereço AutoIP, o NetX AutoIP envia uma série de sondas ARP para o endereço selecionado. Uma sonda ARP consiste numa mensagem de pedido ARP com o endereço de remetente definido para 0.0.0.0 e o endereço-alvo definido para o endereço AutoIP pretendido. Uma série destas sondas ARP são enviadas (o número real é determinado pela definição NX_AUTO_IP_PROBE_NUM). Se outro nó de rede responder a esta sonda ou enviar uma sonda idêntica para o mesmo endereço, um novo endereço AutoIP é selecionado aleatoriamente dentro da gama de endereços AutoIP IPv4 e o processamento da sonda repete-se.

Se NX_AUTO_IP_PROBE_NUM sondas forem enviadas sem respostas, a NetX AutoIP emite uma série de anúncios ARP para o endereço selecionado. Um anúncio ARP consiste numa mensagem de pedido ARP com o remetente e o endereço-alvo na mensagem ARP definida para o endereço AutoIP selecionado. São enviadas uma série de mensagens de anúncio ARP, correspondentes à definição NX_AUTO_IP_ANNOUNCE_NUM. Se outro nó de rede responder a uma mensagem de anúncio ou enviar um anúncio idêntico para o mesmo endereço, um novo endereço AutoIP é selecionado aleatoriamente dentro da gama de endereços AutoIP IPv4 e o processamento da sonda recomeça.

Quando a sonda e o anúncio terminam sem quaisquer conflitos detetados, o endereço AutoIP selecionado é considerado válido e a instância IP associada é configurada com este endereço.

## <a name="autoip-address-change"></a>Alteração de endereço autoIP

Como mencionado anteriormente, o NetX AutoIP altera o endereço de instância IP após o processamento bem sucedido da sonda e do anúncio. A monitorização deste caso não é muito importante. No entanto, é possível que o endereço AutoIP mude no futuro. As causas potenciais incluem futuros conflitos de endereços autoIP, bem como a resolução de endereços DHCP. Para processar corretamente estas situações potenciais, a aplicação deve utilizar a seguinte API NetX para alertá-la de qualquer e qualquer alteração de endereço IP:

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
                            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
                            VOID *additional_info);
```

O processamento na função *ip_address_change_notify* fornecida deve reiniciar o processador NetX AutoIP ou desativá-lo se o DHCP tiver posteriormente resolvido o endereço IP. Consulte a secção *"Sistema de Pequenos Exemplos"* para processamento de amostras.

## <a name="autoip-rfcs"></a>AutoIP RFCs

O NetX AutoIP está em conformidade com o RFC3927 e com os RFCs relacionados.