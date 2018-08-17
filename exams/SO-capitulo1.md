Sistemas Operacionais: Conceitos e Mecanismos 
Resolução do capítulo 1 (1-6)
Discente: Ricardo Rafael 

1- Abstração de recursos e gerenciamento de recursos
2- Porque a abstração pode prover interfaces de acesso aos dispositivos mais simples de usar que as interfaces de baixo nível; 
tornando os aplicativos independentes do hardware e define interfaces de acesso homogêneas para dispositivos com tecnologias distintas. 
3- A principal vantagem é poder realizar várias atividades simultaneamente, sem o surgimento de conflitos no uso do hardware. 
Os desafios para implementação são o uso do processador para distribuição entre todos os aplicativos do sistema.
4- No sistema operacional de tempo real, sua característica essencial é ter um comportamento temporal previsível (ou seja, seu tempo de 
resposta deve ser conhecido no melhor e pior caso de operação). A estrutura interna de um sistema operacional de tempo real deve ser 
construída de forma a minimizar esperas e latências imprevisíveis, como tempos de acesso a disco e sincronizações excessivas. 
Classificação de sistema operacional de tempo real: soft real-time systems, nos quais a perda de prazos implica na degradação do
serviço prestado. E hard real-time systems a perda de prazos pelo sistema pode perturbar o objeto controlado, com graves consequências 
humanas, econômicas ou ambientais.
5- é o coração do sistema operacional, responsável pela gerência dos recursos do hardware usados pelas aplicações. Ele também 
implementa as principais abstrações utilizadas pelos programas aplicativos.
6- Não, por que uma aplicação poderá interferir nas áreas de memória de outras aplicações ou do núcleo. Sem os privilégios uma 
aplicação pode acessar a placa de rede para enviar ou receber dados.
7- Sim. 
8- Interrupção: quando o processador suspende seu fluxo de execução corrente e desvia para um endereço pré-definido, onde se
encontra uma rotina de tratamento de interrupção.                                                                                                          Exceções: são eventos gerados pelo próprio processador, que podem ocasionar o desvio de execução usando o mesmo mecanismo das interrupções.                                                                                                        Traps: é uma interrupção que comuta o processador para o nível privilegiado e procede de forma similar ao tratamento de uma interrupção.
9- O processador perde tempo para varrer todos os dispositivos do sistema para verificar se há eventos a serem tratados ou não. 
10-  Função definida na Biblioteca Padrão de Entrada/Saída (Standard I/O Library, definida no arquivo de cabeçalho stdio.h). 
11- Sistemas Monolíticos: -Positivo(s): grande desempenho; -Negativos(s): robustez e facilidade de desenvolvimento. Complexa
manutenção  e evolução de núcleos;  Sistema em camadas: -Positivo(s): melhor estruturação do Sistema Operacional; 
-Negativo(s): O empilhamento de várias camadas de software faz com que cada pedido de uma aplicação demore mais tempo para chegar 
até o dispositivo periférico ou recurso a ser acessado, prejudicando o desempenho do sistema. Sistema Micronúcleo: 
-Positivo(s): robustez e flexibilidade; -Negativo(s): custo elevado;
12- (T)-(K)-(E)-(D)-(M)-(E)-(K)-(S)-(K)-(E)
13- (C) - O nível usuário permite o acesso somente a áreas previamente definidas.
14- (D) - Os sistemas operacionais definem chamadas de sistema para todas as operações envolvendo o acesso a recursos de baixo nível.
 
16- (C) As afirmações III e IV estão erradas. III está errado pois é uma característica de sistemas distribuídos.
IV está errado pois é uma característica de sistemas desktop.
17- (E) As afirmações II e V estão corretas. I Uma máquina virtual de sistema é construída para suportar sistemas 
operacionais convidados completos.  III está errada pois isso ocorre em sistemas monolíticos; IV está errada pois sistemas
monolíticos tem uma manutenção complexa.



