---
title: Capítulo 3 - Descrição funcional do Azure RTOS NetX LWM2M
description: Este capítulo contém uma descrição funcional de Azure RTOS NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6424023a02aedf43c7433c9adc09231b8c146af13b9bddc15ebd1f2fc02e8c8a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784942"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>Capítulo 3 - Descrição funcional do Azure RTOS NetX LWM2M

Este capítulo contém uma descrição funcional de Azure RTOS NetX LWM2M.

## <a name="lwm2m-client-initialization"></a>Inicialização do cliente LWM2M

O Cliente LWM2M é inicializado ***ligando*** nx_lwm2m_client_create serviço. O Cliente LWM2M funciona no seu próprio fio e pode reportar alguns eventos à aplicação através da utilização de callbacks, ou através de métodos de chamada dos objetos personalizados implementados pela aplicação.

Além disso, as Sessões de Cliente LWM2M devem ser criadas chamando ***nx_lwm2m_client_session_create*** para permitir a comunicação com um ou mais servidores. Uma sessão pode comunicar com dois tipos diferentes de servidores: um Servidor Bootstrap ou um Servidor LWM2M (Gestão de Dispositivos).

### <a name="bootstrap-server-session"></a>Sessão de servidor de botas

Uma sessão de comunicação com um Servidor Bootstrap é usada para fornecer informações essenciais no Cliente LWM2M para permitir ao Cliente LWM2M realizar a operação "Register" com um ou mais Servidores LWM2M. Este tipo de servidor é utilizado durante os modos de bootstrap iniciado pelo cliente e iniciado pelo servidor.

A aplicação pode iniciar uma sessão de Bootstrap ligando ***nx_lwm2m_client_session_bootstrap** _ ou _*_nx_lwm2m_client_session_bootstrap_dtls,_*_ deve fornecer o endereço IP e o número de porta do servidor, e um ID opcional de instância de objeto de segurança. A função _*_nx_lwm2m_client_session_bootstrap_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_bootstrap_dtls_** estabelece uma ligação DTLS segura com o servidor.

Se a operação Bootstrap for bem sucedida, o servidor Bootstrap deveria ter criado instâncias de objetos de segurança para os servidores Bootstrap e LWM2M e instâncias de objetos de servidor para os servidores LWM2M. A aplicação deve utilizar estas informações para estabelecer uma sessão com o(s) Servidor LWM2M.

Os dados bootstrap devem ser guardados para memória não volátil através da aplicação, a fim de configurar o Cliente LWM2M no próximo reinício do dispositivo.

### <a name="lwm2m-server-session"></a>Sessão de servidor LWM2M

Uma sessão de comunicação com um Servidor LWM2M é utilizada para registo, gestão de dispositivos e ativação de serviços.

A aplicação pode registar o Cliente LWM2M num servidor chamando ***nx_lwm2m_client_session_register** _ ou _*_nx_lwm2m_client_session_register_dtls,_*_ deve fornecer o endereço IP e o número de porta do servidor, e o ID do servidor curto que corresponde a uma Instância de Objeto de Servidor existente. A função _*_nx_lwm2m_client_session_register_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_register_dtls_** estabelece uma ligação DTLS segura com o servidor.

A aplicação pode desinscrevê-lo através do registo do Cliente LWM2M ligando para ***nx_lwm2m_client_session_deregister** _, e pedir ao cliente para enviar uma mensagem de 'Update' ligando para _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Chamada do Estado da Sessão

A aplicação regista uma chamada de retorno na criação de uma sessão que é chamada quando o estado da sessão é atualizado, a função de retorno NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK tem o seguinte protótipo:

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

São definidos os seguintes estados:

- **NX_LWM2M_CLIENT_SESSION_INIT**: O estado inicial após a criação da sessão.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: O cliente aguarda a expiração do temporizador 'Hold Off' ou da Bootstrap iniciado pelo servidor.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: O cliente enviou uma mensagem de 'Pedido' para o Servidor Bootstrap (Bota Iniciada pelo Cliente).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: O cliente está a receber dados do Servidor Bootstrap.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: O Servidor Bootstrap enviou uma mensagem 'Acabada'.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: A sessão de botas falhou.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING**: O cliente enviou uma mensagem de 'Registo' para o Servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED**: O cliente está registado no servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_UPDATING**: O cliente enviou uma mensagem de 'Actualização' para o Servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: O cliente enviou uma mensagem de 'Des-registo' para o Servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: O cliente está dessesc recenseado a partir do Servidor LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DISABLED**: O Servidor LWM2M está desativado. Um 'Registo' será enviado após o termo do temporizador para desativação.

- **NX_LWM2M_CLIENT_SESSION_ERROR**: A operação de registo ou atualização do Servidor LWM2M falhou.

- **NX_LWM2M_CLIENT_SESSION_DELETED**: A instância do objeto do servidor correspondente ao Servidor LWM2M foi eliminada. Em caso de erro, a aplicação pode recuperar a causa do erro chamando **_nx_lwm2m_client_session_error_get_**.

## <a name="local-device-management"></a>Gestão local de dispositivos

A aplicação pode aceder aos Objetos do Cliente LWM2M utilizando as funções de gestão de dispositivos locais. São fornecidas as seguintes funções:

- ***nx_lwm2m_client_object_read***: Leia os recursos de uma Instância de Objeto.

- ***nx_lwm2m_client_object_discover***: Obtenha a lista dos recursos de uma Instância de Objeto.

- ***nx_lwm2m_client_object_write***: Escreva recursos para uma instância de objeto

- ***nx_lwm2m_client_object_execute***: Efetuar a operação Executar num recurso de uma Instância de Objeto.

- ***nx_lwm2m_client_object_create:*** Criar uma nova instância de objeto.

- ***nx_lwm2m_client_object_delete***: Eliminar uma instância de objeto existente.

- ***nx_lwm2m_client_object_get_next***: Implemente o próximo ID do Objeto pelo Cliente LWM2M.

- ***nx_lwm2m_client_object_instance_get_next:*** Obtenha a próxima instância de um objeto.

## <a name="resource-information"></a>Informação sobre Recursos

Ao ler e escrever para Objetos, um recurso é representado pela estrutura NX_LWM2M_RESOURCE. Esta estrutura contém o ID do Recurso/Instância e o seu valor. A codificação do valor depende do seu tipo e da sua origem (aplicação ou rede).

A estrutura NX_LWM2M_RESOURCE tem a seguinte definição:

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- **nx_lwm2m_resource_id**: O ID do Recurso ou da Instância.
- **nx_lwm2m_resource_type**: O tipo de valor, ver abaixo.
- **nx_lwm2m_resource_value**: O valor do Recurso depende do tipo de valor.

São definidos os seguintes valores:

- **NX_LWM2M_RESOURCE_NONE:** Recursos vazios.

- **NX_LWM2M_RESOURCE_STRING**: Um valor de cadeia UTF-8 sem fim armazenado em *nx_lwm2m_resource_stringdata*.

- **NX_LWM2M_RESOURCE_INTEGER32**: Um valor inteiro de 32 bits armazenado em *nx_lwm2m_resource_integer32data*.

- **NX_LWM2M_RESOURCE_INTEGER64**: Um valor inteiro de 64 bits armazenado em *nx_lwm2m_resource_integer64data*.

- **NX_LWM2M_RESOURCE_FLOAT32**: Um valor flutuante de 32 bits armazenado em *nx_lwm2m_resource_float32data*.

- **NX_LWM2M_RESOURCE_FLOAT64**: Um valor flutuante de 64 bits armazenado em *nx_lwm2m_resource_float64data*.

- **NX_LWM2M_RESOURCE_BOOLEAN**: Um valor booleano armazenado em *nx_lwm2m_resource_booleandata*.

- **NX_LWM2M_RESOURCE_OPAQUE**: Um valor opaco definido por *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_OBJLNK**: Valor de ligação de objetos armazenado em *nx_lwm2m_resource_objlnkdata*.

- **NX_LWM2M_RESOURCE_TLV**: Um valor codificado por TLV definido por *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_TEXT**: Um valor codificado Plain-Text definido por *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_MULTIPLE**: Um recurso múltiplo definido por *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* é um ponteiro para uma série de **estruturas NX_LWM2M_RESOURCE** que contêm informações sobre cada Instância de Recursos.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV**: Um recurso múltiplo definido por *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* é um ponteiro para um tampão codificado TLV.

As funções de conveniência são fornecidas para recuperar o valor e verificar o seu tipo, a aplicação nunca deve aceder diretamente ao campo *nx_lwm2m_resource_value* quando obter um valor de uma estrutura NX_LWM2M_RESOURCE. São definidas as seguintes funções:

- ***nx_lwm2m_resource_get_***: Obtenha um valor com o tipo dado.
- ***nx_lwm2m_resource_multiple_get_***: Obtenha um valor com o tipo dado a partir de um Recurso Múltiplo.

O **NX_LWM2M_RESOURCE_IS_MULTIPLE** macro (tipo) pode ser utilizado para verificar se um tipo de recurso é um Recurso Múltiplo.

## <a name="object-implementation"></a>Implementação de objetos

O Cliente LWM2M implementa os objetos obrigatórios OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3). Outros objetos específicos do dispositivo devem ser implementados pela aplicação.

Duas estruturas de dados são usadas para definir um Objeto: a estrutura NX_LWM2M_OBJECT define a implementação do Objeto, incluindo o ID do Objeto e os métodos do objeto, e a estrutura NX_LWM2M_OBJECT_INSTANCE contém os dados de uma Instância de Objeto.

A estrutura NX_LWM2M_OBJECT tem a seguinte definição:

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- **nx_lwm2m_object_next:** O próximo objeto da lista.
- **nx_lwm2m_object_id:** O ID do objeto.
- **nx_lwm2m_object_read**: O método 'Ler', ver abaixo.
- **nx_lwm2m_object_discover**: O método 'Descobrir', veja abaixo.
- **nx_lwm2m_object_write**: O método 'Escrever', ver abaixo.
- **nx_lwm2m_object_execute**: O método 'Executar', ver abaixo.
- **nx_lwm2m_object_create**: O método 'Criar', ver abaixo.
- **nx_lwm2m_object_delete**: O método 'Eliminar', ver abaixo.
- **nx_lwm2m_object_instances**: A lista de casos de objetos terminados por NULOS.

A estrutura NX_LWM2M_OBJECT_INSTANCE tem a seguinte definição:

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next:** A próxima instância da lista.
- **nx_lwm2m_object_instance_id:** O ID da Instância do Objeto.

O Objeto deve implementar os métodos correspondentes às operações definidas pela Interface de Gestão de Dispositivos LWM2M: 'Ler', 'Descobrir', 'Escrever', 'Executar', 'Criar' e 'Eliminar'. Os métodos 'Criar' e 'Eliminar' podem ser definidos para NU SE o objeto não suportar a criação dinâmica de instâncias.

### <a name="the-read-method"></a>O método 'Ler'

O método 'Ler' é utilizado para ler valores de recursos a partir de uma Instância de Objeto, a função tem a seguinte definição:

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

Os parâmetros de entrada são definidos da seguinte forma:

- **object_ptr**: Ponteiro para a implementação do objeto.

- **instance_ptr**: Ponteiro para a Instância do Objeto.

- **num_values:** O número de recursos a ler.

- **values_ptr**: Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos para ler. Na volta, a matriz é preenchida com os tipos e valores correspondentes.

### <a name="the-discover-method"></a>O método 'Descobrir'

O método 'Descobrir' é utilizado para recuperar a lista de todos os Recursos implementados por um Objeto, a função tem a seguinte definição:

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

Os parâmetros de entrada são definidos da seguinte forma:

- **object_ptr**: Ponteiro para a implementação do objeto.

- **instance_ptr**: Ponteiro para a Instância do Objeto.

- **num_resources_ptr**: No tamanho do tampão de destino, na saída o número de elementos escritos para o tampão.

- **resources_ptr**: Ponteiro para o tampão de destino.

A informação de recursos é devolvida numa estrutura NX_LWM2M_RESOURCE_INFO definida da seguinte forma:

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id:** A identificação do recurso.

- **nx_lwm2m_resource_info_flags**: Veja abaixo.

- **nx_lwm2m_resource_info_dim**: A dimensão do Recurso Múltiplo se a bandeira NX_LWM2M_RESOURCE_INFO_MULTIPLE estiver definida.

O campo *nx_lwm2m_resource_flags* pode ter aos seguintes valores:

- 0: Único recurso legível.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE:** O recurso múltiplo, *nx_lwm2m_resource_info_dim* deve ser definido.

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE:** Recurso executável ou não legível.

### <a name="the-write-method"></a>O método 'Escrever'

O método 'Escrever' é utilizado para atualizar ou substituir recursos de uma Instância de Objeto, a função tem a seguinte definição:

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

Os parâmetros de entrada são definidos da seguinte forma:

- **object_ptr**: Ponteiro para a implementação do objeto.
- **instance_ptr**: Ponteiro para a Instância do Objeto.
- **num_values:** O número de recursos para escrever.
- **values_ptr**: Pontear os valores dos recursos.
- **write_op:** O tipo de operações de escrita.

As seguintes operações de escrita podem ser especificadas para o parâmetro *write_op:*

- 0 &mdash; Atualização Parcial: adição ou atualizações Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados,

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Instância de substituição: substitui a Instância do Objeto pelos novos valores de recursos fornecidos.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Substituir Recurso: substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: inicializa a instância de objeto recém-criada com os valores de recursos fornecidos (chamados do método *nx_lwm2m_object_create).*

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: chamado durante a sequência de Bootstrap.

### <a name="the-execute-method"></a>O método 'Executar'

O método 'Executar' implementa a execução de um recurso de objeto, a função tem a seguinte definição:

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

Os parâmetros de entrada são definidos da seguinte forma:

- **object_ptr**: Ponteiro para a implementação do objeto
- **instance_ptr**: Ponteiro para a Instância do Objeto.
- **resource_id:** O ID do recurso.
- **arguments_ptr**: Ponto a partir dos argumentos da operação de execução. Pode ser NULO se *arguments_length* for zero.
- **arguments_length:** A duração dos argumentos.

A função deve voltar NX_LWM2M_NOT_FOUND se o ID do recurso não existir, ou NX_LWM2M_METHOD_NOT_ALLOWED se não apoiar a execução.

### <a name="the-create-method"></a>O método 'Criar'

O método 'Criar' implementa a criação de uma nova Instância de Objeto, a função tem a seguinte definição:

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

Os parâmetros de entrada são definidos da seguinte forma:

- **object_ptr**: Ponteiro para a implementação do objeto.
- **instance_id**: A identificação do novo Exemplo.
- **num_values**: O número de recursos para inicializar.
- **values_ptr**: Pontear os valores dos recursos.
- **instance_ptr**: Ponteiro para o ponteiro de destino da instância criada.
- **bootstrap**: Verdadeiro se chamado da sequência de botas.

O Objeto deve atribuir e rubricar uma nova instância do Objeto, utilizando a lista fornecida de valores de recursos.

### <a name="the-delete-method"></a>O método 'Eliminar'

O método 'Eliminar' implementa a supressão de uma instância de objeto, a função tem a seguinte definição:

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

Os parâmetros de entrada são definidos da seguinte forma:

- **object_ptr**: Ponteiro para a implementação do objeto.
- **instance_ptr**: Ponteiro para a Instância do Objeto.

No sucesso, o Objeto deve divulgar os dados de Instância do Objeto e qualquer outro recurso atribuído pela instância.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>Adicionar implementações e instâncias de objetos ao cliente LWM2M

A aplicação pode adicionar nova implementação de objeto ao Cliente LWM2M, ligando para o serviço ***nx_lwm2m_client_object_add.***

Se o Objeto não suporta a criação dinâmica de Instâncias, por exemplo, se for apenas um objeto de instância única, o campo *nx_lwm2m_object_instances* da estrutura do objeto deve apontar para a lista das estruturas de instâncias estáticas.

Se o Objeto suportar a criação de instâncias dinâmicas, *nx_lwm2m_object_instances* deve ser definido para NU E o serviço ***nx_lwm2m_client_object_create*** deve ser utilizado para chamar o método 'Criar' do objeto.

## <a name="example-of-lwm2m-client-application"></a>Exemplo da Aplicação ao Cliente LWM2M

O código a seguir é um exemplo de uma simples Aplicação de Cliente LWM2M que implementa um dispositivo personalizado composto por um sensor de temperatura e um interruptor de luz.

O dispositivo permite que um servidor leia o valor do sensor de temperatura e o estado booleano do interruptor de luz e ligue/desligue o interruptor de luz.

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
