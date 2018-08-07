# Respostas das questão do capítulo 1

## Questão 1
**Abstração e gerência de recursos.**

## Questão 2
**Porque ela provém interfaces de acessos aos dispositivos, o que simplifica no desenvolvimento de aplicações, já que o desenvolvedor não vai precisar acessar os recursos diretamente, apenas terá que se preocupar com o desenvolvimento em alto nível da sua aplicação. Além disso, a abstração é útil até mesmo para os desenvolvedores do próprio SO, pois com a interface simples, o número de problemas e conflitos para acessar o hardware é diminuído.**

## Questão 3
**Com a gerência, não haverá conflitos para uso do hardware, pois o SO define como gerenciar o acesso aos recursos de hardware. Os principais desafios são definir como o uso do processador será distribuído entre as aplicações, impedir que um usuário ou uma aplicação monopolize todos os recursos disponíveis do sistema, etc.**

## Questão 4
**A sua característica essencial é ter um comportamento temporal previsível (ou seja, seu tempo de resposta deve ser conhecido no melhor e pior caso de operação). A estrutura interna de um sistema operacional de tempo real deve ser construída de forma a minimizar esperas e latências imprevisíveis, como tempos de acesso a disco e sincronizações excessivas.
Há 2 tipos de S.O. de tempo real: soft real-time systems e hard real-time systems.
Nos hard real-time systems a perda de prazos pelo sistema pode perturbar o objeto controlado, com graves consequências humanas, econômicas ou ambientais. Já nos soft real-time systems, a perda de prazos implica na degradação do serviço prestado.**

## Questão 5
**Ele é a principal parte do S.O., o coração. O núncleo é responsável pela gerência dos recursos e pela implementação das principais abstrações utilizadas pelos aplicativos.**

## Questão 6
**Não, pois sem os diversos níveis de privilégio, qualquer pessoa/aplicação poderia acessar qualquer recurso, e isso seria uma vulnerabilidade à pessoas/aplicativos mal intencionados, podendo afetar tanto o sistema quanto o hardware.**

## Questão 7
**Sim, caso houvesse uma divisão de processamento em todos os níveis.**

## Questão 8
**Interrupções são eventos oriundos de periféricos, ou seja, externos ao processador. Os circuitos do processador suspendem seu fluxo de execução corrente e fazem um desvio para algum endereço pré-definido, onde há um tratamento para a interrupção.
Exceções são eventos que são causados pelo próprio processador. O funcionamento é semelhante ao das interrupções.
Traps, assim como os anteriores, são eventos, porém, causados por softwares. São instruções especiais que permitem adicionar o mecanismo de interrupções de forma proposital, sem depender de eventos internos ou externos.**

## Questão 9
**Pode trazer uma séries de problemas. Ao desligar as interrupções, a preempção por tempo ou por recursos deixa de funcionar; caso a tarefa entre em um laço infinito dentro da seção crítica, o sistema inteiro será bloqueado. Uma tarefa mal intencionada pode forçar essa situação e travar o sistema. Para evitar tais problemas, o S.O.deve programar a manipulação de interrupção de rede com o mesmo cuidado como cronogramas de execução de processos.**

## Questão 10
**Função de biblioteca. Quando um desenvolvedor está desenvolvendo uma aplicação, ele não utiliza chamadas de sistemas, geralmente, e sim, uma função de biblioteca, a qual irá converter a ação em várias chamadas de sistemas.**

## Questão 11
**Sistemas monolíticos:
Vantagens: desempenho (qualquer componente do núcleo pode acessar os demais componentes, memória e periféricos). Mais compacto, devido à interação direta entre os componentes.
Desvantagens: robustez, dificuldade de desenvolvimento, manuntenção e evolução de núcleos mais complexas. Caso algum componente do núcleo perca o controle, o problema pode se espalhar por todo o núcleo, colapsando o sistema.
Sistemas em camadas:
Vantagens: é uma forma mais elegante de estruturar um S.O.. Permide níveis de abstração e gerência mais sofisticados.
Desvantagens: o empilhamento de várias camadas faz com que cada pedido de uma aplicação demore mais tempo para chegar até o dispositivo periférico ou recurso a ser acessado, prejudicando o desempenho. Além disso, não é tão simples dividir as funcionalidades de um núcleo em camadas horizontais de abstração crescente, pois as funcionalidades são interdependentes.
Sistemas micro-núcleo:
Vantagens: robustez e flexibilidade. Se um subsistema tiver problemas, os mecanismos de proteção de memória e níveis de privilégio irão confiná-lo, impedindo que a instabilidade seja espalhada no restante do sistema. A customização do S.O. também é possível, iniciando somente os componentes necessários ou escolhendo os mais adequados às aplicações que serão executadas.
Desvantagens: custo entre trocas de mensagens pode ser elevado, o que prejudica seu desempenho, diminuindo a aceitação desta abordagem.
Máquinas Virtuais:
Vantagens:  contorna os problemas de compatibilidade ente os componentes de um sistema. Oferece aos demais componentes serviços com outra interface, permitindo o acoplamento entre interfaces destinas. Executa diversos Sistemas Operacionais sobre o mesmo hardware, simultaneamente. Aumenta a portabilidade, diminui os custos com hardware, etc.
Desvantagens: custo adicional de execução dos processos na máquina virtual em comparação com a máquina real.**

## Questão 12
**[T] Deve ter um comportamento temporal previsível, com prazos de resposta
claramente definidos.**

**[S] Sistema operacional usado por uma empresa para executar seu banco de
dados corporativo.**

**[E] São tipicamente usados em telefones celulares e sistemas eletrônicos dedicados.**

**[M] Neste tipo de sistema, a localização física dos recursos do sistema computacional
é transparente para os usuários.**

**[D] Todos os recursos do sistema têm proprietários e existem regras controlando
o acesso aos mesmos pelos usuários.**

**[S] A gerência de energia é muito importante neste tipo de sistema.**

**[K] Sistema que prioriza a gerência da interface gráfica e a interação com o
usuário.**

**[M] Construído para gerenciar de forma eficiente grandes volumes de recursos.**

**[K] O MacOS X é um exemplo típico deste tipo de sistema.**

**[E] São sistemas operacionais compactos, construídos para executar aplicações específicas sobre plataformas com poucos recursos.**

## Questão 13
**Escrever um valor em uma posição da memória e Mascarar uma ou mais interrupções, pois isso poderia afetar o funcionamento do sistema.**

## Questão 14
****

## Questão 15
**[5] A rotina de tratamento da interrupção de software é ativada dentro do núcleo.**

**[9] A função printf finaliza sua execução e devolve o controle ao código do
processo.**

**[2] A função de biblioteca printf recebe e processa os parâmetros de entrada (a
string “Hello world”).**

**[3] A função de biblioteca printf prepara os registradores para solicitar a
chamada de sistema write()**

**[7] O disco rígido gera uma interrupção indicando a conclusão da operação.**

**[8] O escalonador escolhe o processo mais prioritário para execução.**

**[4] Uma interrupção de software é acionada.**

**[1] O processo chama a função printf da biblioteca C.**

**[6] A operação de escrita no terminal é efetuada ou agendada pela rotina de
tratamento da interrupção.**

**[10] O controle volta para a função printf em modo usuário.**

## Questão 16
**I correto.
II correto.
III errado, pois os sistemas distribuídos é que deixam tudo de forma transparente.
IV errado, são os sistemas desktops que devem priorizar as tarefas que interagem com o usuário.
V correto.**

## Questão 17
**I falso, ela permite o acoplamento de interfaces distintas, não sendo específico à uma lingiagem de programação.
II correto.
III falso, somente as abstrações fundamentais ficam no núcleo.
IV falso, issão são desvantagens deles. São usados por terem desepenho alto. 
V correto.**

## Questão 18
**Porque ele precisa acessar as rotinas do Sistema Operacional, e as chamadas de sistemas são como portas de entrada, pois elas irão verificar se a aplicação possui os privilégios necessários para executar a ação.**

## Questão 19
**O ltrace é uma abstração do strace em alto nível, já que o strace são as chamadas de sistemas realizadas pelas chamadas de bibliotecas.**
