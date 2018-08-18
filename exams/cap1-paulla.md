# Respostas Lista de Exercícios Cap. 1

# Q1:

Abstração e gerência de recursos.

# Q2:

Por prover interfaces de acesso aos dispositivos, tornar os aplicativos independentes do hardware e definir interfaces de acesso homogêneas para dispositivos com tecnologia distintos. 

# Q3:

Executando os aplicativos simultaneamente em velocidade adequada, gerando filas de acesso para que não ocorram conflitos entre processos. O principal desafio ao se implantar essa solução é impedir que os recursos do sistema sejam utilizados por um só usuário. 

# Q4:

Um sistem operacional em tempo real possui um comportamento temporal previsível. As duas classificações deste tipo de sistemas são: soft 
real-time systems, onde o atraso implica a perda de prazos implica na degradação do serviço prestado(gravação de CDs, reprodução de 
músicas, etc) e o hard real-time systems, onde a perda de prazos pelo sistema pode perturbar o objeto controlado, com graves consequências
humanas, econômicas ou ambientais.

# Q5: 

O núcleo é o responsável pela gerência dos recursos do hardware usados pelas aplicações e também implementa as principais
abstrações utilizadas pelos programas aplicativos.

# Q6:

Não, pois sem níveis de privilégio as aplicações teriam acesso pleno ao hardware, o que tornaria inúteis os mecanismos de segurança e
controle de acesso aos recursos (tais como arquivos, diretórios e áreas de memória).

# Q7:

Sim, se houvesse necessidade de processamento entre os níveis.

# Q8:

As **interrupções** são causadas por dispositivos externos ao processador, as **exceções** são causadas pelo próprio processador e **traps** são eventos causados por softwares.  

# Q9: 

O processador perde muito tempo varrendo todos os dispositivos do sistema para verificar se há eventos a serem tratados ou não. 

# Q10:

O comando Fopen é uma função da biblioteca padrão da linguagem C. Essa função está defina no cabeçalho do Stdio.h.

# Q11:

**Monolíticos**

Vantagem: desempenho.</br>
Desvantagem: robustez e velocidade de desenvolvimento.

**Camadas**

Vantagem: domínio das redes de computadores.</br>
Desvantagem: demora no pedido da aplicação, prejudicando o desempenho do sistema.

**Micronúcleos**

Vantagem: robustez eflexibilidade.</br>
Desvantagem: custo associado às trocas de mensagens muito elevado.

**Máquinas Virtuais** 

Vantagem: evita a construção de novas aplicações ou adapta as já existentes.</br>
Desvantagem: custo adicional de execução dos processos na máquina virtual em comparação com a máquina real.
 
# Q12:

[ T ] Deve ter um comportamento temporal previsível, com prazos de resposta claramente definidos.<br/>
[ S ] Sistema operacional usado por uma empresa para executar seu banco de dados corporativo.<br/>
[ E ] São tipicamente usados em telefones celulares e sistemas eletrônicos dedicados.<br/>
[ D ] Neste tipo de sistema, a localização física dos recursos do sistema computacional é transparente para os usuários.<br/>
[ M ] Todos os recursos do sistema têm proprietários e existem regras controlando o acesso aos mesmos pelos usuários.<br/>
[ S ] A gerência de energia é muito importante neste tipo de sistema.<br/>
[ K ] Sistema que prioriza a gerência da interface gráfica e a interação com o usuário.<br/>
[ S ] Construído para gerenciar de forma eficiente grandes volumes de recursos.<br/>
[ K ] O MacOS X é um exemplo típico deste tipo de sistema.<br/>
[ E ] São sistemas operacionais compactos, construídos para executar aplicações específicas sobre plataformas com poucos recursos.<br/>


# Q13: 

(b) Efetuar uma divisão inteira.</br>
(e) Ler o valor dos registradores do processador.</br>
(f) Mascarar uma ou mais interrupções.</br>

Os recursos internos do processador e áreas de memória são acessíveis apenas no nível núcleo. 

# Q14:

(b) Enviar um pacote através da rede.</br>
(d) Preencher uma área de memória do processo com zeros.</br>
(e) Remover um arquivo do disco.</br>

Os sistemas operacionais definem chamadas de sistema para todas as operações envolvendo o acesso a recursos de baixo nível (periféricos, arquivos, alocação de memória, etc).

# Q15:


[ 05 ] A rotina de tratamento da interrupção de software é ativada dentro do núcleo.</br>
[ 08 ] A função printf finaliza sua execução e devolve o controle ao código do processo.</br></br>
[ 03 ] A função de biblioteca printf recebe e processa os parâmetros de entrada (a string “Hello world”).</br>
[ 02 ] A  função  de  biblioteca printf prepara  os  registradores  para  solicitar  a chamada de sistema write()</br>
[ 06 ] O disco rígido gera uma interrupção indicando a conclusão da operação.</br>
[ 04 ] O escalonador escolhe o processo mais prioritário para execução.</br>
[ 07 ] Uma interrupção de software é acionada.</br>
[ 01 ] O processo chama a função printf da biblioteca C.</br>
[ 10 ] A operação de escrita no terminal é efetuada ou agendada pela rotina de tratamento da interrupção.</br>
[ 09 ] O controle volta para a função printf em modo usuário.</br>


# Q16:

**(c) As afirmações III e IV estão erradas.** <br/>
III está errado pois é uma característica de sistemas distribuídos e não de rede; e IV está errado pois é uma característica de sistemas
desktop e não de tempo real.

# Q17:

**(e) As afirmações II e V estão corretas.**<br/>
I está errada pois uma máquina virtual de sistema é construída para suportar sistemas operacionais convidados completos; III está errada
pois isso ocorre em sistemas monolíticos e não micro-núcleos; IV está errada pois sistemas monolíticos não tem uma manutenção fácil e
sim complexa.

# Q18:

Para o carregamento de bibliotecas compartilhadas, mapeamento da memória e -- no final do rastreio -- a emissão das informações sobre a
data para a saída padrão.


# Q19:

O utilitário date chama uma biblioteca com o fim de comunicar com o núcleo. Esta biblioteca manipula os detalhes de baixo nível
relacionados com a passagem de informação para o núcleo e com a chamada da rotina privilegiada propriamente dita, nomeadamente a
conversão de convenções de chamadas. As chamadas de sistema são oferecidas para as aplicações em modo usuário através da system library
que prepara os parâmetros, invoca a interrupção de software e retorna à aplicação os resultados obtidos.




 
 









