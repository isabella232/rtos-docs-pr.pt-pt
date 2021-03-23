---
title: Capítulo 3 - Descrição funcional do Cliente LWM2M
description: Este capítulo contém uma descrição funcional do Cliente LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825939"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>Capítulo 3 Descrição funcional do Cliente LWM2M

> Este capítulo contém uma descrição funcional do Cliente LWM2M.

## <a name="lwm2m-client-initialization"></a>Inicialização do cliente LWM2M

O Cliente LWM2M é inicializado ***ligando*** nx_lwm2m_client_create serviço. O Cliente LWM2M funciona no seu próprio fio e pode reportar alguns eventos à aplicação através da utilização de callbacks, ou através de métodos de chamada dos objetos personalizados implementados pela aplicação.

Além disso, as Sessões de Cliente LWM2M devem ser criadas chamando ***nx_lwm2m_client_session_create*** para permitir a comunicação com um ou mais servidores. Uma sessão pode comunicar com dois tipos diferentes de servidores: um Servidor Bootstrap ou um Servidor LWM2M (Gestão de Dispositivos).

### <a name="bootstrap-server-session"></a>Sessão de servidor de botas

Uma sessão de comunicação com um Servidor Bootstrap é usada para fornecer informações essenciais no Cliente LWM2M para permitir ao Cliente LWM2M realizar a operação "Register" com um ou mais Servidores LWM2M. Este tipo de servidor é utilizado durante os modos de bootstrap iniciado pelo cliente e iniciado pelo servidor.

A aplicação pode iniciar uma sessão de Bootstrap ligando ***nx_lwm2m_client_session_bootstrap** _ ou _*_nx_lwm2m_client_session_bootstrap_dtls,_*_ deve fornecer o endereço IP e o número de porta do servidor, e um ID opcional de instância de objeto de segurança. A função _*_nx_lwm2m_client_session_bootstrap_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_bootstrap_dtls_** estabelece uma ligação DTLS segura com o servidor.

Se a operação Bootstrap for bem sucedida, o servidor Bootstrap deveria ter criado instâncias de objetos de segurança para os servidores Bootstrap e LWM2M e instâncias de objetos de servidor para os servidores LWM2M. A aplicação pode ligar para ***nx_lwm2m_client_session_register_info_get*** para obter informações do LWM2M Server(s) e utilizar estas informações para estabelecer uma sessão com o(s) Servidor(s) LWM2M.

Os dados bootstrap devem ser guardados para memória não volátil através da aplicação para configurar o Cliente LWM2M no próximo reinício do dispositivo.

### <a name="lwm2m-server-session"></a>Sessão de servidor LWM2M

Uma sessão de comunicação com um Servidor LWM2M é utilizada para registo, gestão de dispositivos e ativação de serviços.

A aplicação pode registar o Cliente LWM2M num servidor chamando ***nx_lwm2m_client_session_register** _ ou _*_nx_lwm2m_client_session_register_dtls,_*_ deve fornecer o endereço IP e o número de porta do servidor, e o ID do servidor curto que corresponde a uma Instância de Objeto de Servidor existente. A função _*_nx_lwm2m_client_session_register_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_register_dtls_** estabelece uma ligação DTLS segura com o servidor.

A aplicação pode desinscrevê-lo através do registo do Cliente LWM2M ligando para ***nx_lwm2m_client_session_deregister** _, e pedir ao cliente para enviar uma mensagem de 'Update' ligando para _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Chamada do Estado da Sessão

A aplicação regista uma chamada de retorno na criação de uma sessão que é chamada quando o estado da sessão é atualizado, a função de retorno **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** tem o seguinte protótipo.

typedef VOID \* (NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \* session_ptr,UINT);

Os seguintes estados são definidos.

| Estado da Sessão &nbsp; | Descrição |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | O estado inicial após a criação da sessão. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | O cliente está à espera da expiração do temporizador 'Hold Off' ou da Bootstrap iniciado pelo servidor. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | O cliente enviou uma mensagem de 'Pedido' para o Servidor Bootstrap (Bota Iniciada pelo Cliente). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | O cliente está a receber dados do Servidor Bootstrap. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | O Servidor Bootstrap enviou uma mensagem "Acabada". |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | A sessão de botas falhou. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | O cliente enviou uma mensagem de 'Registo' para o Servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | O cliente está registado no Servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | O cliente enviou uma mensagem de 'Actualização' para o Servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | O cliente enviou uma mensagem de "des-registo" para o Servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | O cliente está desscista do Servidor LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | O Servidor LWM2M está desativado. Um 'Registo' será enviado após o termo do temporizador para desativação. |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | A operação de registo ou atualização do Servidor LWM2M falhou. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | A instância do objeto do servidor correspondente ao servidor LWM2M foi eliminada. |

Em caso de erro, a aplicação pode recuperar a causa do erro chamando ***nx_lwm2m_client_session_error_get***.

## <a name="local-device-management"></a>Gestão local de dispositivos

A aplicação pode aceder aos Objetos do Cliente LWM2M utilizando as funções de gestão de dispositivos locais. São fornecidas as seguintes funções.

| Nome da função &nbsp; | Descrição |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | Leia os recursos de uma instância de objeto. |
| ***nx_lwm2m_client_object_discover*** | Obtenha a lista dos recursos de uma Instância de Objeto.
| ***nx_lwm2m_client_object_write*** | Escreva recursos para uma instância de objeto. |
| ***nx_lwm2m_client_object_execute*** | Execute a operação Executar num recurso de uma Instância de Objeto. |
| ***nx_lwm2m_client_object_create*** | Crie uma nova instância de objeto. |
| ***nx_lwm2m_client_object_delete*** | Elimine uma instância de objeto existente. |
| ***nx_lwm2m_client_object_next_get*** | Obtenha o próximo ID do objeto pelo Cliente LWM2M. |
| ***nx_lwm2m_client_object_instance_next_get*** | Obtenha a próxima instância de um objeto. |

## <a name="resource-information"></a>Informação sobre Recursos

Ao ler e escrever para Objetos, um recurso é representado pela estrutura NX_LWM2M_CLIENT_RESOURCE. Esta estrutura contém o ID do Recurso/Instância e o seu valor.

As seguintes funções são fornecidas para a definição de informações e valor dos recursos.

| Nome da função &nbsp; | Descrição |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | Definir informações de recursos: id de recursos e funcionamento: LEIA, WRITE, EXECUTÁVEL. |
| ***nx_lwm2m_client_resource_string_set*** | Desaprova o valor do recurso como cadeia. |
| ***nx_lwm2m_client_resource_integer32_set*** | Desajei o valor do recurso como inteiro de 32 Bits. |
| ***nx_lwm2m_client_resource_integer64_set*** | Desajei o valor do recurso como inteiro de 64 Bits. |
| ***nx_lwm2m_client_resource_float32_set*** | Desaprova o valor do recurso como boia de 32 Bits. |
| ***nx_lwm2m_client_resource_float64_set*** | Desaprova o valor do recurso como boia de 64 Bits. |
| ***nx_lwm2m_client_resource_boolean_set*** | Desaprova o valor do recurso como boolean. |
| ***nx_lwm2m_client_resource_objlnk_set*** | Desaprova o valor do recurso como ligação de objetos. |
| ***nx_lwm2m_client_resource_opaque_set*** | Desajei o valor do recurso como opaco. |
| ***nx_lwm2m_client_resource_instance_set*** | Desfie o valor do recurso como exemplo para vários recursos. |
| ***nx_lwm2m_client_resource_dim_set*** | Desfita a dimensão do recurso para o recurso múltiplo para descobrir. |

As seguintes funções são fornecidas para obter informações e valor de recursos.

| Nome da função &nbsp; | Descrição |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | Obtenha informações sobre recursos: id de recursos e funcionamento: LEIA, ESCREVa, EXECUTE. |
| ***nx_lwm2m_client_resource_string_get*** | Obtenha o valor de um recurso de corda. |
| ***nx_lwm2m_client_resource_integer32_get*** | Obtenha o valor de um recurso inteiro de 32 Bits. |
| ***nx_lwm2m_client_resource_integer64_get*** | Obtenha o valor de um recurso inteiro b4-Bit. |
| ***nx_lwm2m_client_resource_float32_get*** | Obtenha o valor de um recurso flutuante de 32 Bits. |
| ***nx_lwm2m_client_resource_float64_get*** | Obtenha o valor de um recurso flutuante de 64 Bits. |
| ***nx_lwm2m_client_resource_boolean_get*** | Obtenha o valor de um recurso Boolean. |
| ***nx_lwm2m_client_resource_objlnk_get*** | Obtenha o valor de um recurso de ligação de objeto. |
| ***nx_lwm2m_client_resource_opaque_get*** | Obtenha o valor de um recurso opaco. |
| ***nx_lwm2m_client_resource_instance_get*** | Obtenha a instância de recursos para vários recursos. |
| ***nx_lwm2m_client_resource_dim_get*** | Obtenha a dimensão do recurso para vários recursos. |

## <a name="object-implementation"></a>Implementação de objetos

O Cliente LWM2M implementa os objetos obrigatórios OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3). Outros objetos específicos do dispositivo devem ser implementados pela aplicação.

Duas estruturas de dados são usadas para definir um Objeto: a estrutura NX_LWM2M_CLIENT_OBJECT define a implementação do Objeto, incluindo o ID do Objeto e os métodos do objeto, e a estrutura NX_LWM2M_CLIENT_OBJECT_INSTANCE contém os dados de uma Instância de Objeto.

São fornecidas as seguintes funções.

| Nome da função &nbsp; | Descrição |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | Adicione a implementação do objeto ao Cliente LwM2M. |
| ***nx_lwm2m_client_object_remove*** | Remova a implementação do objeto do Cliente LwM2M. |
| ***nx_lwm2m_client_object_instance_add*** | Adicione a instância do objeto ao Objeto. |
| ***nx_lwm2m_client_object_instance_remove*** | Remova a instância do objeto do objeto. |

A função de retorno do método do objeto tem a assinatura apresentada abaixo.

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a>O método 'Ler'

O método 'Ler' é utilizado para ler os valores de recursos a partir de uma instância de objeto. Os parâmetros são definidos da seguinte forma.

| Parâmetro | Descrição |
| --- | --- |
| **operação** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | Ponteiro para a implementação do Objeto. |
| **instance_ptr** | Ponteiro para a Instância do Objeto. |
| **recurso** | Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler. Na volta, a matriz é preenchida com os respetivos tipos e valores. |
| **resource_count** | Apontando para o número de recursos a ler. |
| **args_ptr** | Parâmetro não-apoiado para leitura. |
| **args_length** | Parâmetro não-apoiado para leitura. |

### <a name="the-discover-method"></a>O método 'Descobrir'

O método 'Discover' é utilizado para recuperar a lista de todos os Recursos implementados por um Objeto. Os parâmetros são definidos da seguinte forma.

| Parâmetro | Descrição |
| --- | --- |
| **operação** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | Ponteiro para a implementação do Objeto. |
| **instance_ptr** | Ponteiro para a Instância do Objeto. |
| **recurso** | Ponteiro para uma série de NX_LWM2M_CLIENT_RESOURCE. Na devolução, a matriz é preenchida com informações de recursos correspondentes. |
| **resource_count** | Ponteiro para o número de recursos a descobrir. Na devolução, este parâmetro deve ser atualizado como o verdadeiro valor. |
| **args_ptr** | Parâmetro não-americano para descobrir. |
| **args_length** | Parâmetro não-americano para descobrir. |

### <a name="the-write-method"></a>O método 'Escrever'

O método 'Escrever' é utilizado para atualizar ou substituir recursos de uma Instância de Objeto. Os parâmetros são definidos da seguinte forma.

| Parâmetro  | Descrição |
| --- | --- |
| **operação** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | Ponteiro para a implementação do Objeto. |
| **instance_ptr** | Ponteiro para a Instância do Objeto. |
| **recurso** | Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler. Na volta, a matriz é preenchida com os respetivos tipos e valores. |
| **resource_count** | Ponteiro para o número de recursos a descobrir. |
| **args_ptr** | Escreve bandeiras. |
| **args_length** | A duração dos argumentos. |

As seguintes operações de escrita podem ser especificadas para o parâmetro da *bandeira.*

| Operação | Ação | Descrição |
| --- | ---| --- |
| 0 | Atualização Parcial | Adiciona ou atualiza Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Substituir Instância | Substitui a Instância do Objeto pelos novos valores de recursos fornecidos.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  Substituir recursos | Substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | Criar Instância | Inicializa a instância de objeto recém-criada com os valores de recursos fornecidos (chamados do método **_nx_lwm2m_object_create)._** |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Escrita de Bootstrap | Chamado durante a sequência de Bootstrap. |

### <a name="the-execute-method"></a>O método 'Executar'

O método 'Executar' implementa a execução de um recurso de objeto.

Os parâmetros de entrada são definidos da seguinte forma.

| Parâmetro  | Descrição |
| --- | --- |
| **operação** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | Ponteiro para a implementação do Objeto. |
| **instance_ptr** | Ponteiro para a Instância do Objeto. |
| **recurso** | Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler. Na volta, a matriz é preenchida com os respetivos tipos e valores. |
| **resource_count** | Ponteiro para o número de recursos a descobrir. |
| **args_ptr** | Apontando para os argumentos. |
| **args_length** | A duração dos argumentos.  |

A função deve voltar **NX_LWM2M_CLIENT_NOT_FOUND** se o ID do recurso não existir, ou **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** se não apoiar a execução.

### <a name="the-create-method"></a>O método 'Criar'

O método 'Criar' implementa a criação de uma nova Instância de Objeto.

Os parâmetros de entrada são definidos da seguinte forma.

| Parâmetro  | Descrição |
| --- | --- |
| **operação** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | Ponteiro para a implementação do Objeto. |
| **instance_ptr** | Parâmetro não-americano. |
| **recurso** | Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler. Na volta, a matriz é preenchida com os respetivos tipos e valores. |
| **resource_count** | Ponteiro para o número de recursos a descobrir. |
| **args_ptr** | Identificação de caso de objeto. |
| **args_length** | A duração dos argumentos. |

### <a name="the-delete-method"></a>O método 'Eliminar'

O método 'Eliminar' implementa a eliminação de uma instância de objeto, os parâmetros de entrada são definidos da seguinte forma.

| Parâmetro  | Descrição |
| --- | --- |
| **operação** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | Ponteiro para a implementação do Objeto. |
| **instance_ptr** | Ponteiro para a Instância do Objeto. |
| **recurso** | Parâmetro não-americano. |
| **resource_count** | Parâmetro não-americano. |
| **args_ptr** | Parâmetro não-americano. |
| **args_length** | Parâmetro não-americano. |

No sucesso, o Objeto deve divulgar os dados de Instância do Objeto e qualquer outro recurso atribuído pela instância.

## <a name="example-of-lwm2m-client-application"></a>Exemplo da Aplicação ao Cliente LWM2M

O código a seguir é um exemplo de uma simples Aplicação de Cliente LWM2M que implementa um dispositivo personalizado composto por um sensor de temperatura e um interruptor de luz.

O dispositivo permite que um servidor leia o valor do sensor de temperatura e o estado booleano do interruptor de luz e ligue/desligue o interruptor de luz.

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```