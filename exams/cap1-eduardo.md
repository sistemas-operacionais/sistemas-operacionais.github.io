# Respostas das questões do capítulo 1:

### Questão 01
Abstração e gerência

### Questão 02
Por Prover interfaces de acesso aos dispositivos, tornar os aplicativos independentes do hardware e definir interfaces de acesso 
homogêneas para dispositivos com tecnologias distintas. Sim, através do processo de abstração é possível que os aplicativos sejam 
utilizados em diferentes sistemas utilizando da mesma interface para dispositivos diversos.

### Questão 03
Gerenciar o uso dos recursos de hardware pelos aplicativos, e resolver eventuais disputas de conflitos. A identificação de possíveis 
ataques através da internet é sem dúvidas uma das principais situações a serem melhoradas, afim de que todo um sistema não seja 
prejudicado ou utilizado por um único usuário ou pequeno grupo.

### Questão 04
Sua principal característica é um comportamento temporal previsível, onde seu tempo de resposta é conhecido no melhor e pior caso de 
operação. Suas duas classificações são Soft real-time systems e Hard real-time systems. A principal diferença entre eles é que, no caso 
de perda de prazo de uma determinada operação as consequências serão na degradação do serviço prestado (Soft real-time) ou em graves 
consequências humanas, ambientais e econômicas (Hard real-time).

### Questão 05
O núcleo é responsável pela gerência dos recursos do hardware usados pelas aplicações. Ele também implementa as principais abstrações
utilizadas pelos programas aplicativos, enquanto os módulos externos representam as várias funcionalidades do sistema.

### Questão 06
Não, uma vez que os diferentes níveis de privilégios são de extrema importância para o gerenciamento de todo Sistema Operacional. 
Eles diferem na capacidade de interação com o hardware, em termos de gerência, configuração, utilitários e aplicativos, sem esses níveis 
de privilégios todo o sistema ficaria desestabilizado por inteiro.

### Questão 07
Sim, se houvesse processamento entre os niveís.

### Questão 08
**Interrupção:** O processador suspende seu fluxo de execução e o desvia para um endereço que esteja pré-definido.
**Exceções:** São geradas pelo processador podendo ocasionar o desvio a ser executado, semelhante a uma interrupção.
**Traps:** É um tipo de interrupção que concede o status de nível privilegiado ao processador.

### Questão 09
Se não existissem interrupções, o processador perderia muito tempo “varrendo” todos os dispositivos do sistema para verificar se há 
eventos a serem tratados.

### Questão 10
O comando Fopen é uma função da biblioteca padrão da linguagem C. Essa função está defina no cabeçalho do Stdio.h.

### Questão 11
Em um sistema monolítico, todos os componentes do núcleo operam em modo núcleo e se interrelacionam conforme suas necessidades, sem
restrições de acesso entre si, pois o código no nível núcleo tem acesso pleno a todos os recursos e áreas de memória. A grande vantagem 
dessa arquitetura é seu desempenho: qualquer componente do núcleo pode acessar os demais componentes, toda a memória ou mesmo dispositivos
periféricos diretamente, pois não há barreiras impedindo esse acesso. A interação direta entre componentes também leva a sistemas mais 
compactos. Todavia, a arquitetura monolítica pode pagar um preço elevado por seu desempenho: a robustez e a facilidade de desenvolvimento.
Caso um componente do núcleo perca o controle devido a algum erro, esse problema pode se alastrar rapidamente por todo o núcleo, levando 
o sistema ao colapso (travamento, reinicialização ou funcionamento forçado)
Uma forma mais elegante de estruturar um sistema operacional faz uso da noção de  camadas: 
A camada mais baixa realiza a interface com o hardware, enquanto as camadas intermediárias provem níveis de abstração e gerência cada vez
mais sofisticados. Por fim, a camada superior define a interface do núcleo para as aplicações (as chamadas de sistema). Essa abordagem de
estruturação de software fez muito sucesso no domínio das redes de computadores, através do modelo de referência OSI
(Open Systems Interconnection) [Day, 1983], e também seria de se esperar sua adoção no domínio dos sistemas operacionais. 
No entanto, alguns inconvenientes limitam sua aceitação nesse contexto:
• O empilhamento de várias camadas de software faz com que cada pedido de uma
aplicação demore mais tempo para chegar até o dispositivo periférico ou recurso a
ser acessado, prejudicando o desempenho do sistema.
• Não é óbvio como dividir as funcionalidades de um núcleo de sistema operacional em camadas horizontais de abstração crescente, pois 
essas funcionalidades são interdependentes, embora tratem muitas vezes de recursos distintos. Em decorrência desses inconvenientes, a 
estruturação em camadas é apenas parcialmente adotada hoje em dia. Muitos sistemas implementam uma camada inferior de abstração do 
hardware para interagir com os dispositivos (a camada HAL – Hardware Abstraction Layer, implementada no Windows NT e seus sucessores), e
também organizam em camadas alguns subsistemas como a gerência de arquivos e o suporte de rede (seguindo o modelo OSI). Como exemplos de
sistemas fortemente estruturados em camadas podem ser citados o IBM OS/2 e o MULTICS [Corbató and Vyssotsky, 1965]

### Questão 12   
[ T ] Deve ter um comportamento temporal previsível, com prazos de resposta claramente definidos.
[ S ] Sistema operacional usado por uma empresa para executar seu banco de dados corporativo.
[ E ] São tipicamente usados em telefones celulares e sistemas eletrônicos dedicados.
[ D ] Neste tipo de sistema, a localização física dos recursos do sistema computacional é transparente para os usuários.
[ M ] Todos os recursos do sistema têm proprietários e existem regras controlando o acesso aos mesmos pelos usuários.
[ E ] A gerência de energia é muito importante neste tipo de sistema.
[ K ] Sistema que prioriza a gerência da interface gráfica e a interação com o usuário.
[ S ] Construído para gerenciar de forma eficiente grandes volumes de recursos.
[ K ] O MacOS X é um exemplo típico deste tipo de sistema.
[ E ] São sistemas operacionais compactos, construídos para executar aplicações específicas sobre plataformas com poucos recursos.

### Questão 13
c) No nível usuário o hardware restringe o uso da memória, permitindo o acesso somente a áreas previamente definidas.
e) Ler o valor dos registradores do processador;

### Questão 14
b) Enviar um pacote através da rede;
d) Os sistemas operacionais definem chamadas de sistema para todas as operações envolvendo o acesso a recursos de baixo nível (periféricos, arquivos, alocação de memória, etc.)
e) Remover um arquivo do disco;

### Questão 15
[ 05 ] A rotina de tratamento da interrupção de software é ativada dentro do núcleo.
[ 08 ] A função printf finaliza sua execução e devolve o controle ao código do processo.
[ 03 ] A função de biblioteca printf recebe e processa os parâmetros de entrada (a string “Hello world”).
[ 02 ] A  função  de  biblioteca printf prepara  os  registradores  para  solicitar  a chamada de sistema write()
[ 06 ] O disco rígido gera uma interrupção indicando a conclusão da operação.
[ 04 ] O escalonador escolhe o processo mais prioritário para execução.
[ 07 ] Uma interrupção de software é acionada.
[ 01 ] O processo chama a função printf da biblioteca C.
[ 10 ] A operação de escrita no terminal é efetuada ou agendada pela rotina de tratamento da interrupção.
[ 09 ] O controle volta para a função printf em modo usuário.

### Questão 16
c) As afirmações III e IV estão erradas. 
III está errado pois é uma característica de sistemas distribuídos e não de rede; e IV está errado pois é uma característica de sistemas
desktop e não de tempo real.

### Questão 17
e) As afirmações II e V estão corretas.
I está errada pois uma máquina virtual de sistema é construída para suportar sistemas operacionais convidados completos; 
III está errada pois isso ocorre em sistemas monolíticose não micro-núcleos; 
IV está errada pois sistemas monolíticos não tem uma manutenção fácil e sim complexa.

### Questão 18
Para o carregamento de bibliotecas compartilhadas, mapeamento da memória e -- no final do rastreio -- a emissão das informações sobre
a data para a saída padrão.

### Questão 19
O utilitário date chama uma biblioteca com o fim de comunicar com o núcleo. Esta biblioteca manipula os detalhes de baixo nível 
relacionados com a passagem de informação para o núcleo e com a chamada da rotina privilegiada propriamente dita, nomeadamente a 
conversão de convenções de chamadas. As chamadas de sistema são oferecidas para as aplicações em modo usuário através da system library
que prepara os parâmetros, invoca a interrupção de software e retorna à aplicação os resultados obtidos.
