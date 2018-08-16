	Aluno: Rômulo Valentim
ATIVIDADE DE SISTEMAS OPERACIONAIS
1 - Abstração e gerência
2 - Prover interfaces de acesso aos dispositivos, tornar os aplicativos independentes do hardware e definir interfaces de acesso homogêneas para dispositivos com tecnologias distintas. Sim, através do processo de abstração é possível que os aplicativos sejam utilizados em diferentes sistemas utilizando da mesma interface para dispositivos diversos.
3 - A identificação de possíveis ataques através da internet é essencial para um sistema, para que o mesmo não seja prejudicado. 
4 - sua característica essencial é ter um comportamento temporal previsível (ou seja, seu tempo de resposta deve ser conhecido no melhor e pior caso de operação). Suas duas classificações são: Soft real-time systems e Hard real-time systems, principal diferença entre eles é que, no caso de perda de prazo de uma determinada operação as consequências serão na degradação do serviço prestado (Soft real-time) ou em graves consequências humanas, ambientais e econômicas (Hard real-time).
5 - O núcleo  é o coração do sistema operacional, responsável pela gerência dos recursos do hardware usados pelas aplicações.
6 - Os níveis de privilégios são de extrema importância para o gerenciamento de todo Sistema Operacional, sem esses níveis de privilégios todo o sistema ficaria desestabilizado por inteiro.
7 - Sim.
8 - A Interrupção: os circuitos do processador suspendem seu fluxo de execução corrente e desviam para um endereço pré-definido,.
As Exceções: desviam a execução para uma rotina de tratamento dentro do núcleo, que provavelmente irá abortar o programa em execução.
Os Traps: É um tipo de interrupção que concede o status de nível privilegiado ao processador.
9 - Se não existissem interrupções, o processador perderia muito tempo “varrendo” todos os dispositivos do sistema para verificar se há eventos a serem tratados. Além disso, as interrupções permitem construir funções de entrada/saída assíncronas, ou seja, o processador não precisa esperar a conclusão de cada operação solicitada a um dispositivo, pois o dispositivo gera uma interrupção para “avisar” o processador quando a operação for concluída..
10 - É uma função da biblioteca padrão da linguagem C. Essa função está defina no cabeçalho do Stdio.h.
11 - Sistemas monolíticos;
    Positivo(s): Grande Desempenho
    Negativo(s): a robustez e a facilidade de desenvolvimento
    Complexa manutenção e evolução do núcleo
Sistema em camadas
Positivo(s):  
Melhor estruturação do Sistema Operacional
Negativo(s):
O empilhamento de várias camadas de software faz com que cada pedido de uma aplicação demore mais tempo para chegar até o dispositivo periférico ou recurso a ser acessado, prejudicando o desempenho do sistema.
Sistemas micronúcleo;
    Positivo(s): 
   Robustez e flexibilidade
    Negativo(s): 
    Custo elevado
12  -   T
    K
    E
    D
    M
    E
    K
    S
    K
13 - C
O nível usuário permite o acesso somente a áreas previamente definidas.
14 - D
Os sistemas operacionais definem chamadas de sistema para todas as operações envolvendo o acesso a recursos de baixo nível.
15 -
16  - (c) As afirmações III e IV estão erradas. 
III está errado pois é uma característica de sistemas distribuídos. 
IV está errado pois é uma característica de sistemas desktop.
17 - (e) As afirmações II e V estão corretas.
I Uma máquina virtual de sistema é construída para suportar sistemas operacionais convidados completos.
 III está errada pois isso ocorre em sistemas monolíticos; 
IV está errada pois sistemas monolíticos tem uma manutenção complexa.

18 - Para o carregamento de bibliotecas compartilhadas, mapeamento da memória e -- no final do rastreio -- a emissão das informações sobre
a data para a saída padrão.

19 - O utilitário date chama uma biblioteca com o fim de comunicar com o núcleo. Esta biblioteca manipula os detalhes de baixo nível 
relacionados com a passagem de informação para o núcleo e com a chamada da rotina privilegiada propriamente dita, nomeadamente a 
conversão de convenções de chamadas. As chamadas de sistema são oferecidas para as aplicações em modo usuário através da system library
que prepara os parâmetros, invoca a interrupção de software e retorna à aplicação os resultados obtidos.
