---
title: Capítulo 1 - Introdução ao Cliente DNS duo Azure RTOS NetX Duo
description: O DNS fornece uma base de dados distribuída que contém mapeamento entre nomes de domínio e endereços IP físicos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e878d32d6bcf514bb75a76b51e66c4d267b1a5b34f6c4b2df6ab231e5814ffc5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792063"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dns-client"></a>Capítulo 1 - Introdução ao Cliente DNS duo Azure RTOS NetX Duo

O DNS fornece uma base de dados distribuída que contém mapeamento entre nomes de domínio e endereços IP físicos. A base de dados é referida como *distribuída* porque não existe uma única entidade na Internet que contenha o mapeamento completo. Uma entidade que mantém uma parte do mapeamento é chamada de Servidor DNS. A Internet é composta por numerosos Servidores DNS, cada um dos quais contém um subconjunto da base de dados. Os Servidores DNS também respondem aos pedidos do Cliente DNS para informações de mapeamento de nome de domínio, apenas se o servidor tiver o mapeamento solicitado.

O protocolo DNS Client para o NetX Duo fornece a aplicação com serviços para solicitar informações de mapeamento a partir de um ou mais Servidores DNS.

## <a name="dns-client-setup"></a>Configuração do cliente DNS

Para funcionar corretamente, o pacote DNS Client requer que já tenha sido criada uma instância IP NetX Duo.

Após a criação do Cliente DNS, a aplicação deve adicionar um ou mais servidores DNS à lista de servidores mantida pelo Cliente DNS. Para adicionar servidores DNS, a aplicação utiliza o serviço *nxd_dns_server_add.* O serviço de clientes NetX Duo DNS *nx_dns_server_add também* pode ser usado para adicionar servidores. No entanto, apenas aceita endereços IPv4 e recomenda-se que os desenvolvedores utilizem o serviço *nxd_dns_server_add.*

Se a opção NX_DNS_IP_GATEWAY_SERVER estiver ativada e o endereço de gateway de instância IP não for zero, o gateway de instância IP é automaticamente adicionado como o servidor principal de DNS. Se as informações do servidor DNS não forem conhecidas estáticamente, também pode ser obtida através do Protocolo de Configuração do Anfitrião Dinâmico (DHCP) para o NetX Duo. Consulte o Guia de Utilizador NETX Duo DHCP para obter mais informações.

O Cliente DNS requer um pacote de pacotes para transmitir mensagens DNS. Por predefinição, o Cliente DNS cria este pacote quando o serviço *nx_dns_create* é chamado. As opções de configuração NX_DNS_PACKET_PAYLOAD_UNALIGNED e NX_DNS_PACKET_POOL_SIZE permitem que a aplicação determine o tamanho da carga útil do pacote e o tamanho da piscina do pacote (por exemplo, número de pacotes) deste pacote de piscina, respectivamente. Estas opções são descritas na secção "Opções de Configuração" do Capítulo Dois.

Uma alternativa ao Cliente DNS que cria o seu próprio pool de pacotes é a aplicação para criar o pool de pacotes e defini-lo como o pacote do Cliente DNS usando o serviço *nx_dns_packet_pool_set.* Para tal, a opção NX_DNS_CLIENT_USER_CREATE_PACKET_POOL deve ser definida. Esta opção também requer um pool de pacotes previamente criado usando *nx_packet_pool_create* como entrada do ponteiro do ponteiro do pacote para *nx_dns_packet_pool_set* . Quando a instância do Cliente DNS é eliminada, a aplicação é responsável por eliminar o pacote de pacotes DNS Client se NX_DNS_CLIENT_USER_CREATE_PACKET_POOL estiver ativado se já não for necessário.

> [!NOTE] 
> Para aplicações que optam por fornecer a sua própria piscina de pacotes utilizando a opção NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, o tamanho do pacote precisa de ser capaz de manter o tamanho máximo de massagem DNS (512 bytes) mais quartos para cabeçalho UDP, cabeçalho IPv4 ou IPv6, e o cabeçalho MAC.

## <a name="dns-messages"></a>Mensagens DNS

O DNS tem um mecanismo muito simples para obter mapeamento entre nomes de anfitriões e endereços IP. Para obter um mapeamento, o Cliente DNS prepara uma mensagem de consulta DNS contendo o nome ou o endereço IP que precisa de ser resolvido. A mensagem é então enviada para o primeiro servidor DNS na lista de servidores. Se o servidor tiver tal mapeamento, responde ao Cliente DNS utilizando uma mensagem de resposta DNS que contém as informações de mapeamento solicitadas. Se o servidor não responder, o Cliente DNS consulta o próximo servidor da sua lista até que todos os seus servidores DNS tenham sido consultados. Se não for recebida qualquer resposta de todos os seus servidores DNS, o Cliente DNS tem lógica de recandidúsão da mensagem DNS. Ao reenender uma consulta de DNS, o tempo limite de retransmissão é duplicado. Este processo continua até que o tempo limite máximo de transmissão (definido como NX_DNS_MAX_RETRANS_TIMEOUT em *nxd_dns.h)* seja alcançado ou até que seja obtida uma resposta bem sucedida a partir desse servidor.

O Cliente DNS Duo NetX pode realizar tanto pesquisas de endereços IPv6 (tipo AAAA) como pesquisas de endereços IPv4 (tipo A) especificando a versão do endereço IP na *chamada nxd_dns_host_by_name_get.* O Cliente DNS pode realizar pesquisas inversas de endereços IP (consultas de tipo PTR) para obter nomes de anfitriões da Web usando *nxd_dns_host_by_address_get*. O Cliente DNS Duo NetX ainda suporta o *nx_dns_host_by_name_get* e *nx_dns_host_by_address_get* que são os serviços equivalentes mas que se limitam à comunicação da rede IPv4. No entanto, os desenvolvedores são encorajados a apresentar as aplicações existentes do Cliente DNS para os serviços *de nxd_dns_host_by_name_get* e *nxd_dns_host_by_address_get.*

As mensagens DNS utilizam o protocolo UDP para enviar pedidos e respostas de campo. Um SERVIDOR DNS ouve na porta número 53 para consultas de clientes. Por isso, os serviços UDP devem ser ativados no NetX Duo utilizando o serviço ***nx_udp_enable** _ numa instância IP previamente criada (_*_nx_ip_create_**).

Neste momento, o Cliente DNS está pronto para aceitar pedidos da aplicação e enviar consultas DNS.

## <a name="extended-dns-resource-record-types"></a>Tipos de registo de recursos DNS estendidos

Se NX_DNS_ENABLE_EXTENDED_RR_TYPES estiver ativado, o Cliente DNS da NetX Duo também suporta as seguintes consultas de tipo de registo:

- CNAME: contém o nome canónico para um pseudónimo
- TXT: contém uma cadeia de texto
- NS: contém um servidor de nome autoritário
- SOA: contém o início de uma zona de autoridade
- MX: usado para troca de correio
- SRV: contém informações sobre o serviço oferecido pelo domínio

Com exceção dos tipos de registo CNAME e TXT, a aplicação deve fornecer um tampão alinhado de 4 bytes para receber o registo de dados DNS.

No NetX Duo DNS Client, os dados de gravação são armazenados de forma a fazer uso mais eficiente do espaço tampão.

Abaixo é apresentado um exemplo de um tampão de registo de comprimento fixo (registo tipo AAAA):

![Tampão de registo de comprimento fixo](media/image2.png)

Para as consultas cujos tipos de registo têm comprimento de dados variável, tais como registos NS cujos nomes de anfitrião têm comprimento variável, o Cliente DNS da NetX Duo guarda os dados da seguinte forma. O tampão fornecido na consulta do Cliente DNS é organizado numa área de dados de comprimento fixo e numa área de memória não estruturada. A parte superior do tampão de memória é organizada em entradas de registo alinhadas de 4 byte. Cada entrada de registo contém o endereço IP e um ponteiro para os dados de comprimento variável para esse endereço IP. Os dados de comprimento variável de cada endereço IP são armazenados na memória de área não estruturada a partir do final do tampão de memória. Os dados de comprimento variável para cada entrada de registo sucessivo são guardados na memória da área seguinte adjacente aos dados variáveis de entradas de registo anteriores. Assim, os dados variáveis 'crescem' para a área estruturada da memória que contém as entradas de registo até que não haja memória suficiente para armazenar outra entrada de registo e dados variáveis.

Isto é mostrado na figura abaixo:

![Figura 2](media/image3.png)

O exemplo do armazenamento de dados do nome de domínio DNS (NS) é mostrado acima.

As consultas do NetX Duo DNS Client utilizando o formato de armazenamento de registo devolvem o número de registos guardados para o tampão de gravação. Esta informação permite que a aplicação extraia registos NS do tampão de registo.

Um exemplo de uma consulta do Cliente DNS que armazena dados DNS de comprimento variável utilizando este formato de armazenamento de registo é mostrado abaixo:

```C
UINT  _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, 
                    UCHAR *host_name, VOID *record_buffer, 
                    UINT buffer_size, UINT *record_count, 
                    ULONG wait_option);
```


Mais detalhes estão disponíveis no Capítulo 3, "Descrição dos Serviços ao Cliente do DNS".

## <a name="dns-cache"></a>DNS Cache

Se NX_DNS_CACHE_ENABLE estiver ativado, o Cliente DNS da NetX Duo suporta a funcionalidade DnS Cache. Depois de criar o Cliente DNS, a aplicação pode ligar para a API *nx_dns_cache_initialize para* definir a Cache DNS especial. Se ativar a funcionalidade DNS Cache, o Cliente DNS encontrará a resposta disponível a partir da Cache DNS antes de começar a enviar consulta DNS, se encontrar a resposta disponível, devolver diretamente a resposta à aplicação, caso contrário o Cliente DNS envia mensagem de consulta para o servidor DNS e aguarda a resposta. Quando o Cliente DNS recebe a mensagem de resposta e há cache gratuito disponível, o Cliente DNS devolve a resposta à aplicação e adiciona também a resposta como registo de recursos na cache DNS.

Cada resposta uma estrutura de dados *NX_DNS_RR* (Registo de Recursos) na cache. As cordas (nome de registo de recursos e dados) em Registos são de comprimento variável, pelo que não são armazenadas na estrutura NX_DNS_RR. O Record contém ponteiros para o local de memória real onde as cordas são armazenadas. A mesa de cordas e os Discos partilham a cache. Os registos são armazenados desde o início da cache, e crescem no final da cache. A mesa de cordas começa a partir do fim da cache e cresce para o início da cache. Cada corda na mesa de cordas tem um campo de comprimento e um contra-campo. Quando uma corda é adicionada à tabela de cordas, se a mesma corda já estiver presente na tabela, o valor do contador é incrementado e nenhuma memória é atribuída para a cadeia. A cache é considerada completa se não forem adicionados mais registos de recursos ou novas cordas à cache.

## <a name="dns-client-limitations"></a>Limitações do cliente do DNS

O Cliente DNS suporta um pedido dns de cada vez. Os fios que tentam fazer outro pedido de DNS estão temporariamente bloqueados até que o pedido de DNS anterior esteja concluído.

O Cliente DNS da NetX Duo não utiliza dados de respostas autoritárias para encaminhar consultas adicionais de DNS para outros servidores DNS.

## <a name="dns-rfcs"></a>DNS RFCs

NetX Duo DNS está em conformidade com os seguintes RFCs:

- NOMES DE DOMÍNIO RFC1034 - CONCEITOS E INSTALAÇÕES
- NOMES DE DOMÍNIO RFC1035 - IMPLEMENTAÇÃO E ESPECIFICAÇÃO
- RFC1480 O Domínio dos EUA
- RFC 2782 A DNS RR para especificar a localização dos serviços (DNS SRV)
- Extensões DE DNS RFC 3596 para suporte versão IP 6