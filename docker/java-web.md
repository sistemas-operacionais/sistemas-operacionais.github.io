# [](#header-1) Um App Java Web com Docker

## [](#header-2) Sumário

1. Contruindo o app java web no netbeans.
2. Adicionando o container do banco de dados.
3. Adicionando o container do servidor de app java.
4. Publicando o App num serviço de Cloud.

**Observação** aplicativos instalados na máquina hospedeira:
1. Java JDK
2. Netbeans para JEE
3. Docker CE
4. Maven
5. wget



## [](#header-2) 1a Etapa. Contruindo o app java web no netbeans

Seguindo o tutorial [Creating a Simple Web Application Using a MySQL Database](https://netbeans.org/kb/docs/web/mysql-webapp.html)

**Passo 1** Crie projeto Java Web no NetBeans usando Maven

**maven**
1. Na linha de comando, execute ```mvn archetype:generate -DgroupId=ifrn.cnat.diatinf -DartifactId=JavaWebDocker -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false```
2. Execute o NetBeans
3. Acesse o menu _Abrir Projeto..._, escolha o diretório que foi criado pelo maven, e clique no botão _Abrir Projeto_

ou **NetBeans**
1. Acesse o menu _Novo projeto..._, em Categorias acesse _Maven_, em Projetos acesse _Aplicação Web_, e clique no botão _Próximo_.
2. Em Nome do projeto digite _JavaWebDocker_, ID de grupo digite _ifrn.cnat.diatinf_, e clique no botão _Próximo_.
3. Em Servidor selecione _GlassFish Server 4_, em Versão do Java EE selecione _Java EE 7 Web_, e clique no botão _Finalizar_.


**Passo 2** Teste o projeto JavaWebDocker

1. Na aba de Projetos, clique com o _botão direito_ em _JavaWebDocker_.
2. No menu de contexto, clique em _Construir_.
3. Novamente, na aba de Projetos, clique com o _botão direito_ em _JavaWebDocker_.
4. No menu de contexto, clique em _Executar_.



**Passo 4** Crie o modelo (entidade) Usuário com um vetor de usuários


**Passo 5** Crie o controler para recuperar todos os (entidade) Usuários


**Passo 6** Crie a visualização para mostrar todos os (entidade) Usuários


**Passo 7** Teste a aplicação sem o banco de dados


**Passo 8** Crie o banco de dados e importe os dados do randomuser.me

Faça o download dos dados da API randomuser.me
Na linha de comando, acesse o diretório da aplicação JavaWebDocker
```sh
cd JavaWebDocker
wget wget -O data.json https://randomuser.me/api/?results=50
```

**Passo 9** Adicione a conexão ao modelo (entidade) Usuário

**Passo 10** Teste a aplicação com o banco de dados


## [](#header-2) 2a Etapa. Adicionando o container do banco de dados


## [](#header-2) 3a Etapa. Adicionando o container do servidor de app java


## [](#header-2) 4a Etapa. Publicando o App num serviço de Cloud


# [](#header-1) Alguns links de tutoriais

https://netbeans.org/kb/index.html
https://netbeans.org/kb/docs/web/mysql-webapp.html
https://netbeans.org/kb/docs/web/jsf20-crud.html
https://platform.netbeans.org/tutorials/nbm-maven-quickstart.html

https://netbeans.org/kb/docs/ide/java-db.html
https://stackoverflow.com/questions/27466361/reading-a-file-into-a-derby-database