# [](#header-1) Heroku


## Introdução

- Aula baseada no tutorial [Deploying Tomcat-based Java Web Applications with Webapp Runner](https://devcenter.heroku.com/articles/java-webapp-runner)
- Código-fonte em [github]()

## [](#header-2) Ferramentas
- [git](https://git-scm.com)
- [heroku cli](https://devcenter.heroku.com/articles/heroku-cli)
- [maven](https://maven.apache.org)
- [nodejs](https://nodejs.org/)
- [open jdk](http://openjdk.java.net)

### [](#header-3) Instalando ferramentas

**nodejs** interpretador javascript by [cades](https://github.com/cades-ifrn/)
```sh
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
nvm install node
```

**heroku** linha de comando para administrar app no heroku.com
```sh
npm install --global heroku-cli
```

**maven** automatizador de tarefas para projetos java
```sh
npm install --global maven
```

**git** controlador de versão
```sh
npm install --global git
```

**open jdk** kit de softwares para desenvolvimento em java
```sh
npm install --global jdk-download
```
_não testei essa instalação ;-)_


## [](#header-2) Instalando um app web java no Heroku

### [](#header-3) Criando uma aplicação web java com maven

**usando o maven para criar um novo aplicativo web java**
```sh
mvn archetype:generate -DarchetypeArtifactId=maven-archetype-webapp
# respostas das perguntas
## Define value for property 'groupId': : tads.cnat.ifrn
## Define value for property 'artifactId': : alo-heroku
## Define value for property 'version':  1.0-SNAPSHOT: : <ENTER>
## Define value for property 'package':  tads.cnat.ifrn: : <ENTER>
## ...
##  Y: : <ENTER>

cd alo-heroku
```

**adicionando tomcat** servidor de aplicações java (container web java)

arquivo **pom.xml** deve ficar assim
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>tads.diatinf.cnat.ifrn</groupId>
  <artifactId>alo-heroku</artifactId>
  <packaging>war</packaging>
  <version>1.0-SNAPSHOT</version>
  <name>alo-heroku Maven Webapp</name>
  <url>http://maven.apache.org</url>
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
  <build>
    <finalName>alo-heroku</finalName>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-dependency-plugin</artifactId>
            <version>3.0.2</version>
            <executions>
                <execution>
                    <phase>package</phase>
                    <goals><goal>copy</goal></goals>
                    <configuration>
                        <artifactItems>
                            <artifactItem>
                                <groupId>com.github.jsimone</groupId>
                                <artifactId>webapp-runner</artifactId>
                                <version>8.5.27.0</version>
                                <destFileName>webapp-runner.jar</destFileName>
                            </artifactItem>
                        </artifactItems>
                    </configuration>
                </execution>
            </executions>
        </plugin>
    </plugins>
  </build>
</project>
```

**gerando instalador e testando**
```sh
mvn package
java -jar target/dependency/webapp-runner.jar target/alo-heroku.war
# abrir o navegador e acessar o endereço http://localhost:8080/
```

### [](#header-3) adicionando repositório de códigos-fontes

**inicializando o repositório git**
```sh
git init
echo "target" > .gitignore
git add .
git commit -m "Pronto para publicar app no heroku"
```

**quem desejar publicar o projeto no github**
```sh
git remote add github URL
git pull github master
git push github master
```

### [](#header-3) instalando o app web no heroku

**Procfile** configurando para executar o app web no heroku.com
```sh
echo "web: java $JAVA_OPTS -jar target/dependency/webapp-runner.jar --port $PORT target/alo-heroku.war" > Procfile
git add .
git commit -m "configurando o heroku"
```

*observação*: _próximo passo precisa um login válido_!

**criando e instalando o aplicativo no heroku**
```sh
heroku login
heroku create
git push heroku master
heroku open
```


####  [](#header-4)  Usando o plugin heroku-cli-deploy

*observação*: _não testado pelo professor_!

**criando e instalando o aplicativo no heroku**
```sh
heroku plugins:install heroku-cli-deploy
heroku apps:create alowebjava
heroku war:deploy target/alo-heroku.war --app alowebjava
heroku open --app alowebjava
```

- ```alowebjava``` nome do app no heroku.com
- ```target/alo-heroku.war``` arquivo local de instalação da aplicação web

## [](#header-2) Links
- [Heroku on Github](https://github.com/heroku)
- [Heroku java support](https://devcenter.heroku.com/articles/java-support#specifying-a-java-version)
- [Heroku Cli](https://devcenter.heroku.com/articles/heroku-cli)
- [Deploying Tomcat-based Java Web Applications with Webapp Runner](https://devcenter.heroku.com/articles/java-webapp-runner)
- [Deploying Java Apps on Heroku](https://devcenter.heroku.com/articles/deploying-java)
- [Define config vars](https://devcenter.heroku.com/articles/getting-started-with-java#define-config-vars)
- [WAR Deployment](https://devcenter.heroku.com/articles/war-deployment)