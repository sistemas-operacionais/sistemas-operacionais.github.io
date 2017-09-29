# DevOps na prática com Vagrant

## Objetivo

1. Montar 2 containeres para prover aplicação web:
    1. Banco de dados para armazenar as informações
    2. Um servidor web para prover a aplicação
2. Usar os containeres para compilar, instalar e testar a aplicação



# Preparar máquina hospedeira

## instalar softwares

- [virtual box](https://www.virtualbox.org)
- [vagrant](https://www.vagrantup.com)
- [git](https://git-scm.com/downloads/guis)


## criar diretório do projeto
```
mkdir devops-na-pratica
mkdir devops-na-pratica/vagrant
```

## baixar código-fonte da aplicação web
```
cd devops-na-pratica
git clone https://github.com/dtsato/loja-virtual-devops.git
```

# Trabalhando com o Vagrant

## criar arquivo de configuração do Vagrant
```
touch vagrant/Vagrantfile
vim vagrant/Vagrantfile
```


### Arquivo ```Vagrantfile```
```ruby
VAGRANT_API_VERSION = "2"

Vagrant.configure(VAGRANT_API_VERSION) do |config|
    config.vm.box = "hashicorp/precise32"

    config.vm.define :db do |db_config|
        db_config.vm.hostname = "db"
        db_config.vm.network :private_network,
            :ip => "192.168.33.10"
    end

    config.vm.define :web do |www|
        www.vm.hostname = "web"
        www.vm.network :private_network,
            :ip => "192.168.33.12"
        www.vm.synced_folder "../loja-virtual-devops/",
            "/src"
    end
end
```


## Iniciando as máquinas
```
cd devops-na-pratica/vagrant
vagrant up
```


## Configurando a máquina db
```bash
vagrant ssh db
sudo apt-get update
sudo apt-get install mysql-server
sudo touch /etc/mysql/conf.d/allow_external.cnf
sudo vim /etc/mysql/conf.d/allow_external.cnf
sudo service mysql restart
mysqladmin -u root -p create loja_schema
mysql -u root -p -e "SHOW DATABASES;"
mysql -u root -p -e "DELETE FROM mysql.user WHERE user=''; FLUSH PRIVILEGES;"
mysql -u root -p -e "GRANT ALL PRIVILEGES ON loja_schema.* TO 'loja'@'%' IDENTIFIED BY 'lojasecret'; FLUSH PRIVILEGES;"
mysql -u loja -p loja_schema -e "SELECT database(), user();"
```

**O que faz cada comando:**
1. acessa o terminal remoto da máquina virtual ```db```
2. executa como ```root``` (sudo) a atualização dos pacotes de software do debian na máquina virtual ```db```
3. instala como ```root``` o MySQL Server na máquina virtual ```db```. __Observação__: irá solicitar criar uma senha, **lembrem dela!!!**
4. cria como ```root``` o arquivo ```allow_external.cnf``` no diretório ```/etc/mysql/conf.d/``` máquina virtual ```db```
5. edita como ```root``` o arquivo ```allow_external.cnf``` no diretório ```/etc/mysql/conf.d/``` máquina virtual ```db```
6. como ```root```, reinicia o serviço do MySQL Server
7. cria um 'banco' no MySQL Server como ```root```. a opção ```-p``` serve para solicitar a senha do passo 3 ;-)
8. mostra os 'bancos' do MySQL Server. Deverá aparecer o __loja_schema__!
9. apaga o usuário anônimo e atualiza os direitos do MySQL Server
10. cria usuário ```loja``` com senha ```lojasecret```, com direito de manipular o banco ```loja_schema```
11. testa se o usuário ```loja``` tem permissão de acessar o banco ```loja_schema```


### Arquivo ```/etc/mysql/conf.d/allow_external.cnf```

```bash
[mysqld]
  bind-address = 0.0.0.0
```


## Configurando a máquina web

```bash
vagrant ssh web
sudo apt-get update
sudo apt-get install tomcat7 mysql-client maven2 openjdk-6-jdk vim
sudo keytool -genkey -alias tomcat -keyalg RSA -keystore /var/lib/tomcat7/conf/.keystore
sudo vim /var/lib/tomcat7/conf/server.xml
sudo vim /var/lib/tomcat7/conf/context.xml
sudo vim /etc/default/tomcat7
sudo service tomcat7 restart
```

**O que faz cada comando:**
1. acessa o terminal remoto da máquina virtual ```web```
2. executa como ```root``` (sudo) a atualização dos pacotes de software do debian na máquina virtual ```web```
3. instala como ```root``` o [Apache Tomcat](http://tomcat.apache.org), cliente MySQL, [Apache Maven](https://maven.apache.org) e [JDK Java](http://openjdk.java.net) na máquina virtual ```web```.
4. gerar chave para o protocolo HTTPS. **observação**: os dados são:
   - "Enter keystore password:" secret;
   - "What is your first and last name?" Loja Virtual;
   - "What is the name of your organizational unit?" Devops na prática;
   - "What is the name of your organization?" Casa do Código
   - "What is the name of your City or Locality?" São Paulo;
   - "What is the name of your State or Province?" SP;
   - "What is the two-letter country code for this unit?" BR;
   - "Is CN=Loja Virtual, OU=Devops na prática, O=Casa do cCódigo, L=São Paulo, ST=SP, C=BR correct?" yes;
   - "Enter key password for <tomcat>" secret;
   - "Re-enter new password:" secret
 5. edita o arquivo ```/var/lib/tomcat7/conf/server.xml``` para adicionar configuração do protocolo HTTPS.
 6. edita o arquivo ```/var/lib/tomcat7/conf/context.xml``` para adicionar configuração de acesso ao banco de dados
 7. edita o arquivo ```/etc/default/tomcat7``` para adicionar configuração Java para execução do Apache Tomcat
 8. reinicia o serviço do Apache Tomcat



### Arquivo ```/var/lib/tomcat7/conf/server.xml```
```xml
<?xml version='1.0' encoding='utf-8'?>
<Server port="8005" shutdown="SHUTDOWN">
    <Listener className="org.apache.catalina.core.JasperListener" />
    <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
    <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />
    <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener" />
    <GlobalNamingResources>
        <Resource name="UserDatabase" auth="Container"
            type="org.apache.catalina.UserDatabase"
            description="User database that can be updated and saved"
            factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
            pathname="conf/tomcat-users.xml" />
    </GlobalNamingResources>
    <Service name="Catalina">
        <Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" URIEncoding="UTF-8" redirectPort="8443" />
        <Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true" maxThreads="150" scheme="https" secure="true" keystoreFile="conf/.keystore" keystorePass="secret" clientAuth="false" sslProtocol="SSLv3" />
        <Engine name="Catalina" defaultHost="localhost">
            <Realm className="org.apache.catalina.realm.LockOutRealm">
                <Realm className="org.apache.catalina.realm.UserDatabaseRealm" resourceName="UserDatabase"/>
            </Realm>
            <Host name="localhost"  appBase="webapps" unpackWARs="true" autoDeploy="true">
                <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs" prefix="localhost_access_log." suffix=".txt" pattern="%h %l %u %t &quot;%r&quot; %s %b" />
            </Host>
        </Engine>
    </Service>
</Server>
```


### Arquivo ```/var/lib/tomcat7/conf/context.xml```
```xml
<?xml version='1.0' encoding='utf-8'?>

<Context>
    <WatchedResource>WEB-INF/web.xml</WatchedResource>

    <Resource name="jdbc/web" auth="Container"
        type="javax.sql.DataSource"
        maxActive="100" maxIdle="30" maxWait="10000"
        username="loja" password="lojasecret"
        driverClassName="com.mysql.jdbc.Driver"
        url="jdbc:mysql://192.168.33.10:3306/loja_schema"
    />
    <Resource name="jdbc/secure" auth="Container"
        type="javax.sql.DataSource"
        maxActive="100" maxIdle="30" maxWait="10000"
        username="loja" password="lojasecret"
        driverClassName="com.mysql.jdbc.Driver"
        url="jdbc:mysql://192.168.33.10:3306/loja_schema"
    />
    <Resource name="jdbc/storage" auth="Container"
        type="javax.sql.DataSource"
        maxActive="100" maxIdle="30" maxWait="10000"
        username="loja" password="lojasecret"
        driverClassName="com.mysql.jdbc.Driver"
        url="jdbc:mysql://192.168.33.10:3306/loja_schema"
    />
</Context>
```

### Arquivo ```/etc/default/tomcat7```
```bash
TOMCAT7_USER=tomcat7

TOMCAT7_GROUP=tomcat7

JAVA_OPTS="-Djava.awt.headless=true -Xmx512m -XX:+UseConcMarkSweepGC"
```


# Compilando o código e fazendo a instalação do sistema

**Compilando**

```bash
vagrant ssh web
cd /src/
mvn install
```


**Instalando**
```bash
vagrant ssh web
cp combined/target/devopsnapratica.war /var/lib/tomcat7/webapps
```



# Monitorando o servidor web


# Terminar trabalho


## Desligar containeres

```bash
vagrant halt
```

## Finalizando um acesso ```vagrant ssh```

```bash
exit
```

ou ```CTRL+D```
