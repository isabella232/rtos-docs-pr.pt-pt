---
title: Capítulo 3 - Descrição dos serviços do Protocolo Azure RTOS NetX Ponto-a-Ponto (PPP)
description: Este capítulo contém uma descrição de todos os serviços de PPP Azure RTOS NetX (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 980348b5c50acfb82b2d8fda8786a1d48bf59c69e7949b6f62b64515b59bf42d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798763"
---
# <a name="chapter-3---description-of-azure-rtos-netx-point-to-point-protocol-ppp-services"></a>Capítulo 3 - Descrição dos serviços do Protocolo Azure RTOS NetX Ponto-a-Ponto (PPP)

Este capítulo contém uma descrição de todos os serviços de PPP Azure RTOS NetX (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_ppp_byte_receive**: *Receba um byte da SÉRIE ISR*
- **nx_ppp_chap_challenge**: *Gerar um desafio CHAP*
- **nx_ppp_chap_enable**: *Ativar a autenticação CHAP*
- **nx_ppp_create**: *Criar uma instância PPP*
- **nx_ppp_delete**: *Eliminar uma instância de PPP*
- **nx_ppp_dns_address_get**: *Obtenha endereço IP DNS*
- **nx_ppp_dns_address_set**:*Definir endereço IP do servidor DNS*
- **nx_ppp_secondary_dns_address_get**: *Obtenha o endereço IP do servidor DNS Secundário*
- **nx_ppp_secondary_dns_address_set**: *Definir Secondary_DNS endereço IP do servidor*
- **nx_ppp_interface_index_get**: *Obtenha índice de interface IP*
- **nx_ppp_ip_address_assign**: *Atribuir endereços IP para IPCP*
- **nx_ppp_link_down_notify**: *Notifique o pedido no link para baixo*
- **nx_ppp_link_up_notify**: *Notificar o pedido no link*
- **nx_ppp_nak_authentication_notify**: Notificar o pedido se a *NAK de autenticação for recebida*
- **nx_ppp_pap_enable**: *Ativar a autenticação do PAP*
- **nx_ppp_ping_request**: *Enviar um pedido de eco LCP*
- **nx_ppp_raw_string_send**: *Enviar cadeia não PPP*
- **nx_ppp_restart**: *Reiniciar o processamento de PPP*
- **nx_ppp_start**: *Iniciar o processamento de PPP*
- **nx_ppp_status_get**: *Obtenha o estado atual de PPP*
- **nx_ppp_stop**: *Parar o processamento de PPP*
- **nx_ppp_packet_receive**: *Receber pacote de PPP*
- **nx_ppp_packet_send_set**: *Definir função de envio de pacote de PPP*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

Receba um byte da SÉRIE ISR

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>Description

Este serviço é normalmente chamado do controlador em série Interrupt Service Routine (ISR) para transferir um byte recebido para PPP. Quando chamado, esta rotina coloca o byte recebido num tampão de byte circular e notifica o fio de PPP apropriado para o processamento.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **byte**: Byte recebido de dispositivo de série

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Adição de PPP bem sucedida.
- **NX_PPP_BUFFER_FULL**: (0xB1) O tampão de série PPP já está cheio.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, ISRs

### <a name="example"></a>Exemplo

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

Gerar um desafio CHAP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Description

Este serviço inicia um desafio CHAP depois da ligação PPP já estar em funcionamento. Isto dá à aplicação a capacidade de verificar a autenticidade da ligação numa base periódica. Se o desafio não for bem sucedido, a ligação PPP está fechada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Desafio PPP bem sucedido iniciado.
- **NX_PPP_FAILURE**: (0xB0) Desafio PPP inválido, CHAP foi habilitado apenas para resposta.
- **NX_NOT_IMPLEMENTED**: (0x80) a lógica CHAP foi desativada através de NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a>nx_ppp_chap_enable

Ativar a autenticação CHAP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>Description

Este serviço permite o Protocolo de Autenticação Challenge-Handshake (CHAP) para a instância de PPP especificada.

Se os ponteiros de função "***get_challenge_values**_" e "_ * _get_verification_values_**" forem especificados, chap é exigido por esta instância de PPP. Caso contrário, a CHAP apenas responde aos pedidos de impugnação do colega.

Existem vários itens de dados referenciados abaixo nas funções de retorno necessários. Espera-se que os dados *sejam fios de* terminação NU, com um tamanho máximo de NX_PPP_NAME_SIZE-1.  Espera-se que o *rand_value* de dados seja uma cadeia terminada com um tamanho máximo de NX_PPP_VALUE_SIZE-1. O id de item *de dados* é um tipo simples de caracteres não assinado.

>[!NOTE]
> Esta função deve ser chamada após *nx_ppp_create* mas antes de nx_ip_create ou *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **get_challenge_values**: Função de inscrição para recuperar valores utilizados para o desafio. Note que os *rand_value*, *id*, e valores *secretos* devem ser copiados para os destinos fornecidos.
- **get_responder_values**: Ponteiro para a função de aplicação que recupera valores utilizados para responder a um desafio. Note que o *sistema,* *nome* e valores *secretos* devem ser copiados para os destinos fornecidos.
- **get_verification_values**: Ponteiro para a função de aplicação que recupera os valores utilizados para verificar a resposta do desafio. Note que o *sistema,**nome* e valores *secretos* devem ser copiados para os destinos fornecidos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) PPP CHAP bem sucedido
- **NX_NOT_IMPLEMENTED**: (0x80) a lógica CHAP foi desativada através de NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido ou ponteiro da função de retorno. Note que, se *get_challenge_values* for especificado, a função *get_verification_values* também deve ser fornecida.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a>nx_ppp_create

Criar uma instância PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a>Description

Este serviço cria uma instância PPP para a instância IP netx especificada.

>[!NOTE]
> É geralmente uma boa ideia criar o fio IP NetX com uma prioridade maior do que a prioridade do fio PPP. Consulte o serviço *nx_ip_create* para obter mais informações sobre a especificação da prioridade do fio IP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **nome**: Nome desta instância PPP.
- **ip_ptr**: Ponteiro para bloquear para instância IP ainda não criada.
- **stack_memory_ptr**: Ponteiro para o início da área de pilha do fio PPP.
- **stack_size:** Tamanho dos bytes na pilha do fio.
- **pool_ptr**: Ponteiro para a piscina de pacotes predefinidos.
- **thread_priority**: Prioridade das linhas internas de PPP (1-31).
- **ppp_invalid_packet_handler**: Função pointer para o manipulador da aplicação para todos os pacotes não PPP. O NetX PPP normalmente chama esta rotina durante a inicialização. É aqui que a aplicação pode responder aos comandos de modem ou no caso de Windows XP, a aplicação De PPP NetX pode iniciar PPP respondendo com" CLIENT SERVER" ao "CLIENTE" inicial enviado por Windows XP.
- **ppp_byte_send**: Funríssem o ponteiro para a rotina de saída de byte de série da aplicação.


### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) PPP bem sucedida cria.
- NX_PTR_ERROR: (0x07) PPP inválido, IP ou byte output function pointer.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

Eliminar uma instância de PPP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Description

Este serviço elimina a instância PPP anteriormente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Supressão bem sucedida de PPP.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

Obtenha endereço IP DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Description

Este serviço recupera o endereço DNS IP fornecido pelo par. Se nenhum endereço IP foi fornecido pelo par, um endereço IP de 0 é devolvido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **dns_address_ptr**: Destino para endereço IP DNS

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Endereço de PPP bem sucedido obtém.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="example"></a>Exemplo

```c

ULONG  my_dns_address;

/* Get IP Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

Obtenha o endereço IP do servidor DNS secundário

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Description

Este serviço recupera o endereço IP DNS secundário fornecido pelo par no aperto de mão IPCP. Se nenhum endereço IP foi fornecido pelo par, um endereço IP de 0 é devolvido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **dns_address_ptr**: Destino para endereço de servidor DNS secundário

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) O endereço DNS bem sucedido obtém.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="example"></a>Exemplo

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

Definir o endereço IP do servidor DE DNS primário

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Description

Este serviço define o endereço IP do Servidor DNS. Se o par enviar um pedido de opção DNS Server no estado IPCP, este anfitrião fornecerá a informação.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **dns_address**: Endereço do servidor DNS

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Conjunto de endereços DNS bem sucedidos.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

Definir endereço IP do servidor DNS secundário

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Description

Este serviço define o endereço IP do servidor DNS secundário. Se o par enviar um pedido de opção dNS Server secundário no estado IPCP, este anfitrião fornecerá as informações.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **dns_address**: Endereço secundário do servidor DNS

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Conjunto de endereços DNS bem sucedidos. 
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

Obtenha índice de interface IP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>Description

Este serviço recupera o índice de interface IP associado a esta instância de PPP. Isto só é útil quando a instância PPP não é a interface primária de uma instância IP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **index_ptr**: Destino para índice de interface

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Índice de PPP bem sucedido obtém.
- **NX_IN_PROGRESS**: (0x37) PPP não concluiu a inicialização.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="example"></a>Exemplo

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

Atribuir endereços IP para IPCP

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>Description

Este serviço configura os endereços IP locais e pares para utilização no Protocolo de Controlo do Protocolo de Internet (IPCP). O pedido de PPP deve invocar este serviço numa instância PPP com endereços IP válidos para si e para o outro par.  Se não forem registados endereços válidos com uma instância PPP, deve contar com o par de PPP para definir o seu endereço IP.


### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **local_ip_address**: Endereço IP local.
- **peer_ip_address:** Endereço IP do peer.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Atribuição de endereços de PPP bem-sucedido.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

Notifique o pedido no link para baixo

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>Description

Este serviço regista a chamada de notificação de ligação da aplicação com a instância de PPP especificada. Se não for NULO, a função de retorno de ligação da aplicação é chamada sempre que o link se apaga.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **link_down_callback**: Link da aplicação para baixo ponteiro da função de notificação. Se a NOTificação DE NULA, a notificação de ligação para baixo está desativada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Link de retorno de notificação com sucesso.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="example"></a>Exemplo

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a>nx_ppp_link_up_notify

Notificar o pedido no link

### <a name="prototype"></a>Prototype

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>Description

Este serviço regista a chamada de notificação de ligação da aplicação com a instância de PPP especificada. Se não for NULO, a função de chamada de ligação da aplicação é chamada sempre que o link aparece.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **link_up_callback**: Link-up de serviço de notificação da aplicação. Se o NU, a notificação de ligação é desativada.**

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Link com sucesso link up registration de chamada de notificação.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="example"></a>Exemplo

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a>nx_ppp_nak_authentication_notify

Notificar o pedido se a autenticação NAK recebida

### <a name="prototype"></a>Prototype

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>Description

Este serviço regista a chamada de notificação de autenticação da aplicação com a instância de PPP especificada. Se não for NULO, esta função de retorno é chamada sempre que a instância PPP recebe um NAK durante a authentiaction.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **nak_authentication_notify**: Ponteiro para funcionar chamado quando a instância PPP recebe um NAK de autenticação. Se NULL, a notificação é desativada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Registo de chamada de notificação bem sucedido.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="example"></a>Exemplo

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a>nx_ppp_pap_enable

Ativar a autenticação do PAP

### <a name="prototype"></a>Prototype

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>Description

Este serviço permite o Protocolo de Autenticação de Palavras-Passe (PAP) para a instância de PPP especificada. Se o ponteiro de função "***verify_login***" for especificado, o PAP é exigido por esta instância de PPP. Caso contrário, o PAP apenas responde aos requisitos de PAP do par, tal como especificado durante a negociação do LCP.

Existem vários itens de dados referenciados abaixo nas funções de retorno necessários. Espera-se que o *nome* do item de dados seja uma cadeia terminada com um tamanho máximo de NX_PPP_NAME_SIZE-1. Espera-se também que a *palavra-passe* do item de dados seja uma cadeia terminada com um tamanho máximo de NX_PPP_PASSWORD_SIZE-1.

>[!NOTE]
> Esta função deve ser chamada após *nx_ppp_create* mas antes *de nx_ip_create* ou *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **generate_login**: Ponteiro para a função de aplicação que produz um *nome* e *senha* para autenticação pelo par. Note que os valores do *nome* e *da palavra-passe* devem ser copiados para os destinos fornecidos.
- **verify_login**: Ponteiro para a função de aplicação que verifica o *nome* e *a palavra-passe* fornecida pelo par. Esta rotina deve comparar o *nome* e *a palavra-passe* fornecidos. Se esta rotina voltar NX_SUCCESS, o nome e a palavra-passe estão corretos e as PPP podem avançar para o passo seguinte. Caso contrário, esta rotina retorna NX_PPP_ERROR e PPP simplesmente espera por outro nome e senha.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) PPP PAP bem sucedido.
- **NX_NOT_IMPLEMENTED**: (0x80) a lógica do PAP foi desativada através de NX_PPP_DISABLE_PAP.
- NX_PTR_ERROR: (0x07) Ponteiro pPP inválido ou ponteiro da função de aplicação.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a>nx_ppp_ping_request

Envie um pedido de ping LCP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>Description

Este serviço envia um pedido de ping LCP e estabelece uma bandeira que o dispositivo PPP está à espera de uma resposta de eco. O serviço regressa assim que o pedido for enviado. Não espera uma resposta. 

Quando uma resposta de eco correspondente é recebida, a tarefa de linha PPP limpará a bandeira. O dispositivo PPP deve ter concluído a parte LCP da negociação das PPP.

Este serviço é útil para configurações de PPP onde a votação do hardware para o estado de ligação pode não ser facilmente possível.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **dados**: Ponteiro para os dados para enviar o pedido de eco.
- **data_size**: Tamanho dos dados para enviar wait_option Hora para esperar para enviar a mensagem de eco LCP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Pedido de eco enviado com sucesso.
- **NX_PPP_NOT_ESTABLISHED:**(0xB5) ligação pPP não estabelecida.
- NX_PTR_ERROR: (0x07) Ponteiro pPP inválido ou ponteiro da função de aplicação.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios de aplicação

### <a name="example"></a>Exemplo

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  strlen("username ");

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a>nx_ppp_raw_string_send

Envie uma cadeia ASCII crua

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>Description

Este serviço envia uma cadeia ASCII não PPP diretamente para fora da interface PPP. É normalmente utilizado após pPP receber um pacote não PPP que contém informações de controlo do modem.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **string_ptr**: Ponteiro para a corda para enviar.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Envio de GPP com sucesso.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido ou ponteiro de cordas.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a>nx_ppp_restart

Reiniciar o processamento de PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Description

Este serviço reinicia o processamento de PPP. É normalmente chamado quando o link precisa ser restabelecido a partir de uma chamada de ligação para baixo ou por uma mensagem de modem não PPP indicando que a comunicação foi perdida.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Reiniciou as PPP com sucesso.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

Iniciar o processamento de PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Description

Este serviço inicia o processamento de PPP. É normalmente chamado após nx_ppp_stop chamado.

>[!NOTE]
> PPP inicia automaticamente o processamento de PPP quando a ligação está ativada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Início de PPP bem-sucedida. 
- **NX_PPP_ALREADY_STARTED**: PPP (0xb9) já começou.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

Obtenha o estado atual de PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>Description

Este serviço obtém o estado atual da instância de PPP especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **status_ptr**: Destino para o estado de PPP, são possíveis valores de estado:
    - **NX_PPP_STATUS_ESTABLISHED**
    - **NX_PPP_STATUS_LCP_IN_PROGRESS**
    - **NX_PPP_STATUS_LCP_FAILED**
    - **NX_PPP_STATUS_PAP_IN_PROGRESS**
    - **NX_PPP_STATUS_PAP_FAILED**
    - **NX_PPP_STATUS_CHAP_IN_PROGRESS**
    - **NX_PPP_STATUS_CHAP_FAILED**
    - **NX_PPP_STATUS_IPCP_IN_PROGRESS**
    - **NX_PPP_STATUS_IPCP_FAILED**

>[!NOTE]
> O estatuto só é válido se a API devolver NX_SUCCESS. Além disso, se algum dos valores de estado *_FAILED for devolvido, o processamento de PPP é efetivamente interrompido até que seja reiniciado novamente pela aplicação.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Pedido de estado de PPP bem sucedido.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="example"></a>Exemplo

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a>nx_ppp_stop

Iniciar o processamento de PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Description

Este serviço impede o processamento de PPP. O utilizador também pode ligar nx_ppp_start para iniciar o processamento de PPP, se necessário.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Início de PPP bem-sucedida. 
- **NX_PPP_ALREADY_STOPPED**: (0xb8) PPP já parou.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

Receber pacote de PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>Description

Este serviço recebe pacote de PPP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **packet_ptr**: Ponteiro para pacote de PPP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Pedido de estado de PPP bem sucedido.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

Desaperte a função de envio de pacote de PPP

### <a name="prototype"></a>Prototype

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>Description

Este serviço define o pacote de PPP enviar funciton.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ppp_ptr**: Ponteiro para o bloco de controlo PPP.
- **nx_ppp_packet_send:** Rotina para enviar pacote de PPP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Pedido de estado de PPP bem sucedido.
- NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```