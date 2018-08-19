# Respostas das questões do capítulo 1

### Questão 1
Abstrair recursos de hardware para o software e gerenciar recursos.

### Questão 2
Para que a tarefa de um desenvolvedor de software não seja tão árdua e complexa. Sim, o desenvolvedor do Sistema Operacional reutiliza abstrações já implementadas dentro do próprio SO.

### Questão 3
O gerenciamento de recursos foi implementado para que os softwares executando na máquina possam ser executados sem paralelo sem que um atrapalhe o outro de forma prejudicial. A principal dificuldade é escrever um software que não bloqueie o hardware.

### Questão 4
Sua característica essencial é ter um comportamento temporal previsível (ou seja, seu tempo de resposta deve ser conhecido no melhor e pior caso de operação).

**Soft real-time systems:** A perda de prazos implica na degradação do serviço prestado.

**Hard real-time systems:** a perda de prazos pelo sistema pode perturbar o objeto controlado, com graves consequências humanas, econômicas ou ambientais.

### Questão 5
**Núcleo do Sistema:** é o coração do sistema operacional, responsável pela gerência dos recursos do hardware usados pelas aplicações. O restante das aplicações têm que acessar o núcleo.

### Questão 6
Não, porque os sistemas seriam muito suscetíveis à ataques.

### Questão 7
A maioria dos sistemas operacionais usam apenas os níveis 0 e 3, porém pode haver algum sistema que use os níveis intermediários.

### Questão 8

**Exceções:** Eventos gerados pelo próprio processador podem ocasionar o desvio da execução
usando o mesmo mecanismo das interrupções

**Interrupções:** É o evento que ocorre quando um controlador de periférico tem uma informação importante a fornecer ao processador.

**Traps:**

### Questão 9



### Questão 10
O comando **fopen** do C é uma função da biblioteca padrão de Entrada/Saída.

### Questão 11

Arquitetura               | Benefícios                  | Deficiências
------------------------- | --------------------------- | ------------
Sistema Monolítico        | - Desempenho                | Mal funcionamento de aplicações do núcleo pode alastrar instabilidades.
Sistema em Camadas        | - Separação de código; - Permite que uma camada trabalhe com outra de diferente versão; |  Aumento do número de classes existentes no sistema.
Sistema Micronúcleo       | - Robustez e flexibilidade. | - Custo associado a troca de mensagens entre componentes.
Máquinas Virtuais         | - Simulação de configurações e situações do mundo real; - Diminuir custo com hardware. | Custo adicional de execução dos processos na máquina virtual em comparação a máquina real.


### Questão 12

- Distribuído (D);
- Multi-usuário (M);
- Desktop (K);
- Servidor (S);
- Embarcado (E);
- Tempo-real (T).

[T] Deve ter um comportamento temporal previsível, com prazos de resposta
claramente definidos.

[S] Sistema operacional usado por uma empresa para executar seu banco de
dados corporativo.

[E] São tipicamente usados em telefones celulares e sistemas eletrônicos dedicados.

[D] Neste tipo de sistema, a localização física dos recursos do sistema computacional
é transparente para os usuários.

[M] Todos os recursos do sistema têm proprietários e existem regras controlando
o acesso aos mesmos pelos usuários.

[E] A gerência de energia é muito importante neste tipo de sistema.

[K] Sistema que prioriza a gerência da interface gráfica e a interação com o
usuário.

[S] Construído para gerenciar de forma eficiente grandes volumes de recursos.

[K] O MacOS X é um exemplo típico deste tipo de sistema.

[E] São sistemas operacionais compactos, construídos para executar aplicações
específicas sobre plataformas com poucos recursos.

### Questão 13

- (c) Escrever um valor em uma posição de memória;

- (e) Ler o valor dos registradores do processador;

### Questão 14
- (b) Enviar um pacote através da rede;

- (d) Preencher uma área de memória do processo com zeros;

- (e) Remover um arquivo do disco;

### Questão 15

[5] A rotina de tratamento da interrupção de software é ativada dentro do núcleo.

[8] A função printf finaliza sua execução e devolve o controle ao código do
processo.

[3] A função de biblioteca printf recebe e processa os parâmetros de entrada (a
string “Hello world”).

[2] A função de biblioteca printf prepara os registradores para solicitar a
chamada de sistema write()

[6] O disco rígido gera uma interrupção indicando a conclusão da operação.

[4] O escalonador escolhe o processo mais prioritário para execução.

[7] Uma interrupção de software é acionada.

[1] O processo chama a função printf da biblioteca C.

[10] A operação de escrita no terminal é efetuada ou agendada pela rotina de
tratamento da interrupção.

[9] O controle volta para a função printf em modo usuário.

### Questão 16
- (b) Apenas a afirmação V está correta.

### Questão 17
- (e) As afirmações II e V estão corretas.

### Questão 18
Porque é preciso acessar o hardware diretamente via código de máquina.

### Questão 19
O ltrace e strace tem as mesmas características, mas o strace ao invés de monitorar as chamadas do sistema, ele monitora as chamadas às funções das bibliotecas carregadas dinamicamente.
