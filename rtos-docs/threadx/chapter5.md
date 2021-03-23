---
title: Capítulo 5 - Controladores de Dispositivos para Azure RTOS ThreadX
description: Este capítulo contém uma descrição dos controladores do dispositivo para Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2432b291f2b3fa7d6d798b8b4c187dd20b97db6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827356"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx"></a>Capítulo 5 - Controladores de Dispositivos para Azure RTOS ThreadX

Este capítulo contém uma descrição dos controladores do dispositivo para Azure RTOS ThreadX. A informação apresentada neste capítulo destina-se a ajudar os desenvolvedores a escrever condutores específicos da aplicação.

## <a name="device-driver-introduction"></a>Introdução do controlador do dispositivo

A comunicação com o ambiente externo é um componente importante da maioria das aplicações incorporadas. Esta comunicação é realizada através de dispositivos de hardware que são acessíveis ao software de aplicação incorporado. Os componentes de software responsáveis pela gestão destes dispositivos são normalmente chamados *de controladores de dispositivos.*

Os controladores de dispositivos em sistemas incorporados e em tempo real são inerentemente dependentes da aplicação. Isto é verdade por duas razões principais: a grande diversidade de hardware-alvo e os requisitos de desempenho igualmente vastos impostos às aplicações em tempo real. Por isso, é praticamente impossível fornecer um conjunto comum de motoristas que satisfaça os requisitos de cada aplicação. Por estas razões, as informações deste capítulo *destinam-se* a ajudar os utilizadores a personalizar os controladores de dispositivos ThreadX fora da prateleira e a escrever os seus próprios controladores específicos.

## <a name="driver-functions"></a>Funções do controlador

Os controladores de dispositivos ThreadX são compostos por oito áreas funcionais básicas, da seguinte forma.

- **Inicialização do condutor**
- **Controlo do Condutor**
- **Acesso ao condutor**
- **Entrada do condutor**
- **Saída do condutor**
- **Interrupções do condutor**
- **Estado do condutor**
- **Rescisão do Condutor**

Com exceção da inicialização, cada área funcional do condutor é opcional. Além disso, o processamento exato em cada área é específico do controlador do dispositivo.

### <a name="driver-initialization"></a>Inicialização do condutor
Esta área funcional é responsável pela inicialização do dispositivo de hardware real e das estruturas de dados internas do condutor. Não é permitido chamar outros serviços de motorista até que a inicialização esteja completa.

> [!NOTE]
> *O componente da função de inicialização do condutor é normalmente chamado da função ***tx_application_define** _ ou de uma inicialização thread._

### <a name="driver-control"></a>Controlo do Condutor

Depois de o condutor ser inicializado e pronto para funcionar, esta área funcional é responsável pelo controlo do tempo de funcionamento. Normalmente, o controlo do tempo de execução consiste em fazer alterações no dispositivo de hardware subjacente. Exemplos incluem a alteração da taxa de baud de um dispositivo em série ou a procura de um novo sector num disco.

### <a name="driver-access"></a>Acesso ao condutor

Alguns controladores de dispositivos são chamados apenas a partir de um único fio de aplicação. Nestes casos, esta área funcional não é necessária. No entanto, em aplicações em que várias linhas necessitam de acesso simultâneo ao condutor, a sua interação deve ser controlada adicionando instalações de atribuição/desbloqueio no controlador do dispositivo. Em alternativa, a aplicação pode utilizar um semáforo para controlar o acesso do condutor e evitar sobrecargas e complicações extra no interior do condutor.

### <a name="driver-input"></a>Entrada do condutor

Esta área funcional é responsável por toda a entrada do dispositivo. As principais questões associadas à entrada do condutor geralmente envolvem como a entrada é tamponada e como os fios aguardam por essa entrada.

### <a name="driver-output"></a>Saída do condutor

Esta área funcional é responsável por toda a saída do dispositivo. As principais questões associadas à saída do condutor geralmente envolvem a forma como a saída é tamponada e como os fios esperam para executar a saída.

### <a name="driver-interrupts"></a>Interrupções do condutor

A maioria dos sistemas em tempo real dependem de interrupções de hardware para notificar o condutor de eventos de entrada, saída, controlo e erro do dispositivo. As interrupções proporcionam um tempo de resposta garantido a tais eventos externos. Em vez de interrupções, o software do controlador pode verificar periodicamente o hardware externo para tais eventos. Esta técnica chama-se *sondagem.* É menos tempo real do que interrupções, mas as sondagens podem fazer sentido para algumas aplicações menos em tempo real.

### <a name="driver-status"></a>Estado do condutor

Esta área de função é responsável por fornecer o estado do tempo de funcionamento e as estatísticas associadas à operação do condutor. A informação gerida por esta área de função normalmente inclui o seguinte.

- Estado atual do dispositivo
- Entradas bytes
- Bytes de saída
- Contagens de erro do dispositivo

### <a name="driver-termination"></a>Rescisão do Condutor

Esta área funcional é opcional. Só é necessário desligar o condutor e/ou o dispositivo de hardware físico. Após a sua demissão, o condutor não deve ser chamado novamente até que seja reiniciado.

## <a name="simple-driver-example"></a>Exemplo simples do condutor

Um exemplo é a melhor maneira de descrever um controlador de dispositivo. Neste exemplo, o controlador assume um simples dispositivo de hardware em série com um registo de configuração, um registo de entrada e um registo de saída. Este exemplo simples do condutor ilustra a inicialização, entrada, saída e interrupção de áreas funcionais.

### <a name="simple-driver-initialization"></a>Inicialização simples do condutor

A ***função tx_sdriver_initialize*** do condutor simples cria dois semáforos de contagem que são utilizados para gerir a operação de entrada e saída do condutor. O semáforo de entrada é definido pela entrada ISR quando um personagem é recebido pelo dispositivo de hardware em série. Por causa disso, o semáforo de entrada é criado com uma contagem inicial de zero.

Inversamente, o semáforo de saída indica a disponibilidade do registo de transmissão de hardware em série. É criado com um valor de um para indicar que o registo de transmissão está inicialmente disponível.

A função de inicialização também é responsável pela instalação dos manipuladores de vetores de interrupção de baixo nível para notificações de entrada e saída. Tal como outras rotinas de serviço de interrupção da ThreadX, o manipulador de baixo nível deve ligar para ***_tx_thread_context_save** _ antes de ligar para o simples controlador ISR. Após a retorna do controlador ISR, o manipulador de baixo nível deve ligar para _*_ _tx_thread_context_restore_**.

> [!IMPORTANT]
> *É importante que a inicialização seja chamada antes de qualquer outra função do controlador. Normalmente, a inicialização do condutor é chamada de ***tx_application_define***.

```c
VOID tx_sdriver_initialize(VOID)
{
    /* Initialize the two counting semaphores used to control
    the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                        "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                        "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
    The initial vector handling should call the ISRs
    defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
    generation, baud rate, stop bits, etc. */
}
```
**FIGURA 9. Inicialização simples do condutor**

### <a name="simple-driver-input"></a>Entrada simples do condutor

Entrada para os centros de condução simples em torno do semáforo de entrada. Quando uma interrupção de entrada de dispositivo de série é recebida, o semáforo de entrada é definido. Se um ou mais fios estiverem à espera de um personagem do condutor, o fio que espera mais tempo é retomado. Se não houver fios à espera, o semáforo permanece simplesmente definido até que um fio chame a função de entrada de unidade.

Existem várias limitações ao simples manuseamento da entrada do condutor. O mais significativo é o potencial de deixar cair os caracteres de entrada. Isto é possível porque não há capacidade de tampão de caracteres de entrada que chegam antes do personagem anterior ser processado. Isto é facilmente manuseado adicionando um tampão de caracteres de entrada.

> [!NOTE]
> *Apenas fios são permitidos para chamar o*  * **tx_sdriver_input** _ _function.*

A figura 10 mostra o código de origem associado à simples entrada do controlador.

```c
UCHAR tx_sdriver_input(VOID)
{
  /* Determine if there is a character waiting. If not,
  suspend. */
  tx_semaphore_get(&tx_sdriver_input_semaphore,
  TX_WAIT_FOREVER;

  /* Return character from serial RX hardware register. */
  return(*serial_hardware_input_ptr);
}
  VOID tx_sdriver_input_ISR(VOID)
{
  /* See if an input character notification is pending. */
  if (!tx_sdriver_input_semaphore.tx_semaphore_count)
  {
    /* If not, notify thread of an input character. */
    tx_semaphore_put(&tx_sdriver_input_semaphore);
  }
}
```
**FIGURA 10. Entrada simples do condutor**

### <a name="simple-driver-output"></a>Saída simples do condutor

O processamento de saída utiliza o semáforo de saída para sinalizar quando o registo de transmissão do dispositivo em série está livre. Antes de um caracter de saída ser realmente escrito para o dispositivo, o semáforo de saída é obtido. Se não estiver disponível, o transmissor anterior ainda não está completo.

A saída ISR é responsável pelo manuseamento da interrupção completa do transmissor. O processamento da saída ISR equivale a definir o semáforo de saída, permitindo assim a saída de outro carácter.

> [!NOTE]
> *Apenas fios são permitidos para chamar o*  * **tx_sdriver_output** _ _function.*

A figura 11 mostra o código fonte associado à simples saída do controlador.

```c
VOID tx_sdriver_output(UCHAR alpha)
{
  /* Determine if the hardware is ready to transmit a
  character. If not, suspend until the previous output
  completes. */
  tx_semaphore_get(&tx_sdriver_output_semaphore,
                                          TX_WAIT_FOREVER);

  /* Send the character through the hardware. */
  *serial_hardware_output_ptr = alpha;
}
  
VOID tx_sdriver_output_ISR(VOID)
{
  /* Notify thread last character transmit is
  complete. */
  tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
**FIGURA 11. Saída simples do condutor**

### <a name="simple-driver-shortcomings"></a>Insuficiências simples do condutor

Este exemplo simples do controlador do dispositivo ilustra a ideia básica de um controlador de dispositivo ThreadX. No entanto, uma vez que o simples controlador do dispositivo não aborda o buffering de dados ou quaisquer problemas de sobrecarga, não representa totalmente os controladores threadX do mundo real. A secção seguinte descreve alguns dos problemas mais avançados associados aos condutores do dispositivo.

## <a name="advanced-driver-issues"></a>Problemas avançados do condutor

Como mencionado anteriormente, os controladores de dispositivos têm requisitos tão únicos como as suas aplicações. Algumas aplicações podem necessitar de uma enorme quantidade de buffering de dados, enquanto outra aplicação pode necessitar de ISRs do controlador otimizados devido a interrupções de dispositivos de alta frequência.

### <a name="io-buffering"></a>Tampão I/O

O tampão de dados em aplicações incorporadas em tempo real requer um planeamento considerável. Parte do design é ditado pelo dispositivo de hardware subjacente. Se o dispositivo fornecer byte I/O básico, um simples tampão circular está provavelmente em ordem. No entanto, se o dispositivo fornecer bloco, DMA ou pacote I/O, um esquema de gestão de tampão é provavelmente justificado.

### <a name="circular-byte-buffers"></a>Tampão Circular Byte

Os amortecedores de byte circular são normalmente utilizados em condutores que gerem um simples dispositivo de hardware em série como um UART. Dois tampão circular são mais frequentemente usados em tais situações - um para entrada e um para saída.

Cada tampão de byte circular é composto por uma área de memória byte (tipicamente uma matriz de **UCHAR** s), um ponteiro de leitura e um ponteiro de escrita. Um tampão é considerado vazio quando o ponteiro de leitura e os ponteiros de escrita referenciam o mesmo local de memória no tampão. A inicialização do condutor define tanto os ponteiros de leitura como os ponteiros tampão para o endereço inicial do tampão.

### <a name="circular-buffer-input"></a>Entrada de tampão circular

O tampão de entrada é utilizado para segurar caracteres que chegam antes de a aplicação estar pronta para eles. Quando um personagem de entrada é recebido (geralmente numa rotina de serviço de interrupção), o novo carácter é recuperado do dispositivo de hardware e colocado no tampão de entrada no local apontado pelo ponteiro de escrita. O ponteiro de escrita é então avançado para a posição seguinte no tampão. Se a próxima posição passar do fim do tampão, o ponteiro de escrita está definido para o início do tampão. A condição completa da fila é tratada cancelando o avanço do ponteiro de escrita se o novo ponteiro de escrita for o mesmo que o ponteiro de leitura.

Os pedidos de byte de entrada de aplicação ao condutor examinam primeiro os ponteiros de leitura e escrita do tampão de entrada. Se os ponteiros de leitura e de escrita forem idênticos, o tampão está vazio. Caso contrário, se o ponteiro de leitura não for o mesmo, o byte apontado pelo ponteiro de leitura é copiado do tampão de entrada e o ponteiro de leitura é avançado para o local do tampão seguinte. Se o novo ponteiro de leitura passar do fim do tampão, é reposto para o início. A figura 12 mostra a lógica do tampão de entrada circular.

```c
UCHAR   tx_input_buffer[MAX_SIZE];
UCHAR   tx_input_write_ptr;
UCHAR   tx_input_read_ptr;

/* Initialization. */
tx_input_write_ptr =    &tx_input_buffer[0];
tx_input_read_ptr =     &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr = tx_input_write_ptr;
*tx_input_write_ptr++ = alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr = &tx_input_buffer[0]; /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr = save_ptr; /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
  alpha = *tx_input_read_ptr++;
  if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
      tx_input_read_ptr = &tx_input_buffer[0];
}
```
**FIGURA 12. Lógica para tampão de entrada circular**

> [!NOTE]
> *Para um funcionamento fiável, pode ser necessário bloquear as interrupções ao manipular os ponteiros de leitura e escrever tanto os tampões circulares de entrada como os tampões circulares de saída. *

### <a name="circular-output-buffer"></a>Tampão de saída circular

O tampão de saída é utilizado para segurar caracteres que chegaram para a saída antes do dispositivo de hardware terminar de enviar o byte anterior. O processamento do tampão de saída é semelhante ao processamento do tampão de entrada, exceto que o processamento de interrupção completa de transmissão manipula o ponteiro de leitura de saída, enquanto o pedido de saída da aplicação utiliza o ponteiro de escrita de saída.
Caso contrário, o processamento do tampão de saída é o mesmo. A figura 13 mostra a lógica do tampão de saída circular.

```c
UCHAR   tx_output_buffer[MAX_SIZE];
UCHAR   tx_output_write_ptr;
UCHAR   tx_output_read_ptr;

/* Initialization. */
tx_output_write_ptr = &tx_output_buffer[0];
tx_output_read_ptr = &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
  *device_reg = *tx_output_read_ptr++;
  if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
      tx_output_read_ptr = &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr = tx_output_write_ptr;
*tx_output_write_ptr++ = alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr = &tx_output_buffer[0]; /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr = save_ptr; /* Buffer full! */
```
**FIGURA 13. Lógica para tampão de saída circular**

### <a name="buffer-io-management"></a>Gestão de I/O do tampão

Para melhorar o desempenho dos microprocessadores incorporados, muitos dispositivos periféricos transmitem e recebem dados com tampão fornecidos pelo software. Em algumas implementações, vários buffers podem ser usados para transmitir ou receber pacotes individuais de dados.

O tamanho e localização dos amortecedores de I/S é determinado pela aplicação e/ou software do condutor. Normalmente, os tampão são fixos em tamanho e geridos dentro de um conjunto de memória de bloco ThreadX. A Figura 14 descreve um tampão de E/S típico e um conjunto de memória de bloco ThreadX que gere a sua alocação.

```c
typedef struct TX_IO_BUFFER_STRUCT
{
      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
      struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
"free_memory_ptr"points to an available memory area that
is 64 KBytes in size. */
tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```

**FIGURA 14. Tampão I/O**

### <a name="tx_io_buffer"></a>TX_IO_BUFFER

O TX_IO_BUFFER da tipa é composto por dois ponteiros. O **ponteiro tx_next_packet** é utilizado para ligar vários pacotes na lista de entradas ou saídas. O **ponteiro tx_next_buffer** é usado para ligar tampãos que compõem um pacote individual de dados do dispositivo. Ambos os ponteiros são definidos para NU QUANDO o tampão é atribuído a partir da piscina. Além disso, alguns dispositivos podem necessitar de outro campo para indicar quanto da área tampão realmente contém dados.

### <a name="buffered-io-advantage"></a>Vantagem de I/O tamponada

Quais são as vantagens de um esquema de E/S de tampão? A maior vantagem é que os dados não são copiados entre os registos do dispositivo e a memória da aplicação. Em vez disso, o controlador fornece ao dispositivo uma série de ponteiros de tampão. O dispositivo físico I/O utiliza diretamente a memória tampão fornecida.

A utilização do processador para copiar pacotes de informação de entrada ou saída é extremamente dispendiosa e deve ser evitada em qualquer situação de I/O de alta produção.

Outra vantagem para a abordagem de E/S tamponada é que as listas de entradas e saídas não têm condições completas. Todos os amortecedores disponíveis podem estar em qualquer uma das listas a qualquer momento. Isto contrasta com os simples tampão circulares byte apresentados anteriormente no capítulo. Cada um tinha um tamanho fixo determinado na compilação.

### <a name="buffered-driver-responsibilities"></a>Responsabilidades do condutor tamponado

Os controladores de dispositivos tamponados só se preocupam com a gestão de listas ligadas de tampões de I/O. Mantém-se uma lista de tampão de entrada para pacotes que são recebidos antes de o software da aplicação estar pronto. Inversamente, mantém-se uma lista de tampão de saída para os pacotes que são enviados mais rapidamente do que o dispositivo de hardware pode manuseá-los. A figura 15 mostra listas simples de entradas e saídas ligadas a pacotes de dados e o(s) tampão(s) que compõem cada pacote.

**Lista de Entradas**

![Lista de Entradas](./media/user-guide/input-list.png)

**Lista de saídas**

![Lista de saídas](./media/user-guide/output-list.png)

**FIGURA 15. Listas Input-Output**

Interface de aplicações com controladores tampão com os mesmos tampões de E/S. No que diz sobre transmissão, o software de aplicação fornece ao condutor um ou mais tampões para transmitir. Quando o software da aplicação solicita a entrada, o controlador devolve os dados de entrada em tampões de E/S.

> [!NOTE]
> *Em algumas aplicações, pode ser útil construir uma interface de entrada do controlador que requer a aplicação para trocar um tampão gratuito por um tampão de entrada do controlador. Isto pode aliviar algum processamento de alocação de tampão dentro do condutor.*

### <a name="interrupt-management"></a>Gestão de Interrupção

Em algumas aplicações, a frequência de interrupção do dispositivo pode proibir a escrita do ISR em C ou interagir com a ThreadX em cada interrupção. Por exemplo, se for preciso 25us para salvar e restaurar o contexto interrompido, não seria aconselhável realizar um contexto completo, salvo se a frequência de interrupção fosse de 50us. Nesses casos, uma pequena linguagem de montagem ISR é usada para manusear a maioria das interrupções do dispositivo. Este ISR de baixa sobrecarga só interagiria com a ThreadX quando necessário.

Uma discussão semelhante pode ser encontrada na discussão de gestão interrompida no final do capítulo 3.

### <a name="thread-suspension"></a>Suspensão do fio

No exemplo simples do condutor apresentado anteriormente neste capítulo, o chamador do serviço de entrada suspende se um personagem não estiver disponível. Em algumas aplicações, isto pode não ser aceitável.

Por exemplo, se o fio responsável pelo processamento da entrada de um condutor também tiver outras funções, suspender apenas a entrada do condutor provavelmente não vai funcionar. Em vez disso, o condutor precisa de ser personalizado para solicitar um processamento semelhante à forma como outros pedidos de processamento são feitos na linha.

Na maioria dos casos, o tampão de entrada é colocado numa lista ligada e uma mensagem de evento de entrada é enviada para a fila de entrada da linha.
