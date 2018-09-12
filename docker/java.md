# [](#header-1) Docker : uma introdução

## [](#header-2) Sumário

1. Instalação e teste
2. Criando seu primeiro conteiner
   1. Download da imagem
   2. Criar um container para compilar e executar códigos java
   3. Montar diretório hospedeiro no container
   4. Empacotar uma aplicação java num container



## [](#header-2) 1. Instalação e teste

**instalar**

```sh
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker aluno
sudo update-rc.d docker defaults
```


**testar**

```sh
docker run hello-world
# Saída
### Unable to find image 'hello-world:latest' locally
### latest: Pulling from library/hello-world
### 9db2ca6ccae0: Pull complete 
### Digest: sha256:4b8ff392a12ed9ea17784bd3c9a8b1fa3299cac44aca35a85c90c5e3c7afacdc
### Status: Downloaded newer image for hello-world:latest
### 
### Hello from Docker!
### This message shows that your installation appears to be working correctly.
### 
### To generate this message, Docker took the following steps:
###  1. The Docker client contacted the Docker daemon.
###  2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
###     (amd64)
###  3. The Docker daemon created a new container from that image which runs the
###     executable that produces the output you are currently reading.
###  4. The Docker daemon streamed that output to the Docker client, which sent it
###     to your terminal.
### 
### To try something more ambitious, you can run an Ubuntu container with:
###  $ docker run -it ubuntu bash
### 
### Share images, automate workflows, and more with a free Docker ID:
###  https://hub.docker.com/
### 
### For more examples and ideas, visit:
###  https://docs.docker.com/engine/userguide/
###
```

**Links**:
- [Get docker](https://get.docker.com/)
- [Imagens Docker](https://hub.docker.com/)
- [Post-installation steps for Linux](https://docs.docker.com/install/linux/linux-postinstall/)


extra: **docker command completion**
- [Command-line completion](https://docs.docker.com/compose/completion/)



## [](#header-2) 2. Criando seu primeiro conteiner

**Sumário**
1. Download da imagem
2. Criar um container para compilar e executar códigos java
3. Montar diretório hospedeiro no container
4. Empacotar uma aplicação java num container


### [](#header-3) Passo 1. Criar baixar imagem Debian Stretch

[hub.docker debian](https://hub.docker.com/_/debian/)

```sh
docker login
# Saída
### Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
### Username: leominora
### Password:
### Login Succeeded

docker images
# Saída
### REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

docker pull debian:stretch
# Saída
### stretch: Pulling from library/debian
### 55cbf04beb70: Pull complete
### Digest: sha256:f1f61086ea01a72b30c7287adee8c929e569853de03b7c462a8ac75e0d0224c4
### Status: Downloaded newer image for debian:stretch

docker images
# Saída
### REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
### debian              stretch             3bbb526d2608        5 weeks ago         101MB
```

### [](#header-3) Passo 2. Criar container para compilar e executar códigos java

[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)


Etapa 1. **criar container**

```sh
docker container ls
# Saída
### CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
###

whoami
# Saída
### leo
hostname
# Saída
### MacBook-Pro-de-Leonardo.local

docker run -it --rm --name conteiner debian:stretch bash
# Saída
### root@8206568f2fb5:/# 

whoami
# Saída
### root

hostname
# Saída
### 8206568f2fb5
```



Etapa 2. **verificando** noutro terminal

```sh
docker image ls
# saída esperada
## REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
## debian              stretch             3bbb526d2608        5 weekss ago        101MB

docker container ls
# saída esperada
## CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
## c92ea9f52828        debian:stretch      "bash"              2 minutes ago       Up 2 minutes                            conteiner
```



Etapa 3. **instalar open jdk**

```sh
java -version
# Saída
### bash: javac: command not found

apt-get update
## Saída
### Get:1 http://security.debian.org/debian-security stretch/updates InRelease [94.3 kB]
### Get:4 http://security.debian.org/debian-security stretch/updates/main amd64 Packages [390 kB]
### Get:3 http://cdn-fastly.deb.debian.org/debian stretch-updates InRelease [91.0 kB]
### Get:5 http://cdn-fastly.deb.debian.org/debian stretch Release [118 kB]
### Get:6 http://cdn-fastly.deb.debian.org/debian stretch-updates/main amd64 Packages [5148 B]
### Get:7 http://cdn-fastly.deb.debian.org/debian stretch Release.gpg [2434 B]
### Get:8 http://cdn-fastly.deb.debian.org/debian stretch/main amd64 Packages [7099 kB]
### Fetched 7800 kB in 10s (762 kB/s)
### Reading package lists... Done

apt-cache search openjdk
## Saída
### icedtea-8-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
### jtreg - Regression Test Harness for the OpenJDK platform
### openjdk-8-dbg - Java runtime based on OpenJDK (debugging symbols)
### openjdk-8-demo - Java runtime based on OpenJDK (demos and examples)
### openjdk-8-doc - OpenJDK Development Kit (JDK) documentation
### openjdk-8-jdk - OpenJDK Development Kit (JDK)
### openjdk-8-jdk-headless - OpenJDK Development Kit (JDK) (headless)
### openjdk-8-jre - OpenJDK Java runtime, using Hotspot JIT
### openjdk-8-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
### openjdk-8-jre-zero - Alternative JVM for OpenJDK, using Zero/Shark
### openjdk-8-source - OpenJDK Development Kit (JDK) source files
### openjdk-8-jre-dcevm - Alternative VM for OpenJDK 8 with enhanced class redefinition
### uwsgi-plugin-jvm-openjdk-8 - Java plugin for uWSGI (OpenJDK 8)
### uwsgi-plugin-jwsgi-openjdk-8 - JWSGI plugin for uWSGI (OpenJDK 8)
### uwsgi-plugin-ring-openjdk-8 - Closure/Ring plugin for uWSGI (OpenJDK 8)
### uwsgi-plugin-servlet-openjdk-8 - JWSGI plugin for uWSGI (OpenJDK 8)

apt-get install nano
# 
### Reading package lists... Done
### Building dependency tree       
### Reading state information... Done
### Suggested packages:
###   spell
### The following NEW packages will be installed:
###  nano
### 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
### Need to get 485 kB of archives.
### After this operation, 2092 kB of additional disk space will be used.
### Get:1 http://cdn-fastly.deb.debian.org/debian stretch/main amd64 nano amd64 2.7.4-1 [485 kB]
### Fetched 485 kB in 0s (515 kB/s)
### debconf: delaying package configuration, since apt-utils is not installed
### Selecting previously unselected package nano.
### (Reading database ... 6498 files and directories currently installed.)
### Preparing to unpack .../nano_2.7.4-1_amd64.deb ...
### Unpacking nano (2.7.4-1) ...
### Setting up nano (2.7.4-1) ...
### update-alternatives: using /bin/nano to provide /usr/bin/editor (editor) in auto mode
### update-alternatives: using /bin/nano to provide /usr/bin/pico (pico) in auto mode

nano /etc/apt/sources.list
# conteúdo do arquivo 
### deb http://deb.debian.org/debian stretch main
### deb http://security.debian.org/debian-security stretch/updates main
### deb http://deb.debian.org/debian stretch-updates main
### 
### deb http://deb.debian.org/debian unstable main


apt-get update
# Saída
### Hit:2 http://security.debian.org/debian-security stretch/updates InRelease
### Ign:1 http://cdn-fastly.deb.debian.org/debian stretch InRelease                
### Hit:3 http://cdn-fastly.deb.debian.org/debian stretch-updates InRelease        
### Get:4 http://cdn-fastly.deb.debian.org/debian unstable InRelease [233 kB]
### Hit:5 http://cdn-fastly.deb.debian.org/debian stretch Release
### Get:6 http://cdn-fastly.deb.debian.org/debian unstable/main amd64 Packages [8235 kB]
### Fetched 8468 kB in 4s (1722 kB/s)                       
### Reading package lists... Done

apt-cache search openjdk
# Saída
### icedtea-8-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
### jtreg - Regression Test Harness for the OpenJDK platform
### openjdk-8-dbg - Java runtime based on OpenJDK (debugging symbols)
### openjdk-8-demo - Java runtime based on OpenJDK (demos and examples)
### openjdk-8-doc - OpenJDK Development Kit (JDK) documentation
### openjdk-8-jdk - OpenJDK Development Kit (JDK)
### openjdk-8-jdk-headless - OpenJDK Development Kit (JDK) (headless)
### openjdk-8-jre - OpenJDK Java runtime, using Hotspot JIT
### openjdk-8-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
### openjdk-8-jre-zero - Alternative JVM for OpenJDK, using Zero/Shark
### openjdk-8-source - OpenJDK Development Kit (JDK) source files
### openjdk-8-jre-dcevm - Alternative VM for OpenJDK 8 with enhanced class redefinition
### uwsgi-plugin-jvm-openjdk-8 - Java plugin for uWSGI (OpenJDK 8)
### uwsgi-plugin-jwsgi-openjdk-8 - JWSGI plugin for uWSGI (OpenJDK 8)
### uwsgi-plugin-ring-openjdk-8 - Closure/Ring plugin for uWSGI (OpenJDK 8)
### uwsgi-plugin-servlet-openjdk-8 - JWSGI plugin for uWSGI (OpenJDK 8)
### openjdk-10-dbg - Java runtime based on OpenJDK (debugging symbols)
### openjdk-10-demo - Java runtime based on OpenJDK (demos and examples)
### openjdk-10-doc - OpenJDK Development Kit (JDK) documentation
### openjdk-10-jdk - OpenJDK Development Kit (JDK)
### openjdk-10-jdk-headless - OpenJDK Development Kit (JDK) (headless)
### openjdk-10-jre - OpenJDK Java runtime, using Hotspot JIT
### openjdk-10-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
### openjdk-10-jre-zero - Alternative JVM for OpenJDK, using Zero
### openjdk-10-source - OpenJDK Development Kit (JDK) source files
### openjdk-11-dbg - Java runtime based on OpenJDK (debugging symbols)
### openjdk-11-demo - Java runtime based on OpenJDK (demos and examples)
### openjdk-11-doc - OpenJDK Development Kit (JDK) documentation
### openjdk-11-jdk - OpenJDK Development Kit (JDK)
### openjdk-11-jdk-headless - OpenJDK Development Kit (JDK) (headless)
### openjdk-11-jre - OpenJDK Java runtime, using Hotspot JIT
### openjdk-11-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
### openjdk-11-jre-zero - Alternative JVM for OpenJDK, using Zero
### openjdk-11-source - OpenJDK Development Kit (JDK) source files
### uwsgi-plugin-jvm-openjdk-11 - Java plugin for uWSGI (OpenJDK 11)
### uwsgi-plugin-jwsgi-openjdk-11 - JWSGI plugin for uWSGI (OpenJDK 11)
### uwsgi-plugin-ring-openjdk-11 - Closure/Ring plugin for uWSGI (OpenJDK 11)
### uwsgi-plugin-servlet-openjdk-11 - JWSGI plugin for uWSGI (OpenJDK 11)

apt-get install openjdk-10-jdk
# Saída
### Reading package lists... Done
### Building dependency tree       
### Reading state information... Done
### The following additional packages will be installed:
###   adwaita-icon-theme at-spi2-core ca-certificates ca-certificates-java dbus
###   ...
###   ...
### Suggested packages:
###   default-jre libasound2-plugins alsa-utils glibc-doc libc-l10n locales colord
###   ...
###   ...
### Recommended packages:
###   manpages
### The following NEW packages will be installed:
###   adwaita-icon-theme at-spi2-core ca-certificates ca-certificates-java dbus
###   ...
###   ...
### The following packages will be upgraded:
###   libc-bin libc6 libcap-ng0 libgcrypt20 libnettle6 libsystemd0 zlib1g
### 7 upgraded, 204 newly installed, 0 to remove and 72 not upgraded.
### Need to get 332 MB of archives.
### After this operation, 857 MB of additional disk space will be used.
### Get:1 http://cdn-fastly.deb.debian.org/debian unstable/main amd64 libc6 amd64 2.27-5 [2911 kB]
### Get:2 http://cdn-fastly.deb.debian.org/debian unstable/main amd64 libc-bin amd64 2.27-5 [781 kB]
### ...
### ...
### Get:211 http://cdn-fastly.deb.debian.org/debian unstable/main amd64 xdg-user-dirs amd64 0.17-1 [53.5 kB]
### Fetched 332 MB in 1min 49s (3034 kB/s)                                         
### debconf: delaying package configuration, since apt-utils is not installed
### (Reading database ... 6598 files and directories currently installed.)
### Preparing to unpack .../libc6_2.27-5_amd64.deb ...
### debconf: unable to initialize frontend: Dialog
### ...
### ...
### Setting up openjdk-10-jre:amd64 (10.0.2+13-1) ...
### Setting up openjdk-10-jdk:amd64 (10.0.2+13-1) ...
### update-alternatives: using /usr/lib/jvm/java-10-openjdk-amd64/bin/appletviewer to provide /usr/bin/appletviewer (appletviewer) in auto mode
### update-alternatives: using /usr/lib/jvm/java-10-openjdk-amd64/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
### Processing triggers for libc-bin (2.27-5) ...
### Processing triggers for systemd (239-7) ...
### Processing triggers for ca-certificates (20180409) ...
### Updating certificates in /etc/ssl/certs...
### 0 added, 0 removed; done.
### Running hooks in /etc/ca-certificates/update.d...
### 
### done.
### done.
### Processing triggers for libgdk-pixbuf2.0-0:amd64 (2.36.12-2) ...

java -version
# Saída
### openjdk version "10.0.2" 2018-07-17
### OpenJDK Runtime Environment (build 10.0.2+13-Debian-1)
### OpenJDK 64-Bit Server VM (build 10.0.2+13-Debian-1, mixed mode)
```



Etapa 4. **compilando código java**

```sh
pwd
# Saída
### /

cd

pwd
# Saída
### /root

ls

echo 'public class Teste { public static void main(String[] args) { System.out.println("Alo mundo de DevOps!"); } }' > Teste.java
# Saída

ls
# Saída
### Teste.java

javac Teste.java

java Teste
# Saída
### Alo mundo de DevOps!
```

```java
public class Teste {
    public static void main(String[] args) {
        System.out.println("Alo mundo de DevOps!");
    }
}
```

Etapa 5. **saindo do container**
```sh
exit
# Saída
### leo:~$ 

whoami
# Saída
### leo

docker image ls
# Saída
### REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
### debian              stretch             3bbb526d2608        5 weeks ago         101MB

docker container ls -a
# saída esperada
### CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
```

**links**:
- [Entendendo APT do Debian](https://wiki.debian.org/pt_BR/SourcesList)
- [Conheça o APT-GET](https://www.vivaolinux.com.br/artigo/Principios-do-APTGET-Conheca-esta-fantastica-ferramenta-do-Debian)



### [](#header-3) Passo 3. Montar diretório hospedeiro no container**

```sh
mkdir -p app/src
cd app/
ls src/
# Saída
### 

docker run -it --rm --volume `pwd`/src:/src-java --workdir /src-java --name container debian:stretch bash
# Saída
### root@988c6a321061:/src-java# 

java --version
# Saída
### bash: java: command not found

# instalação novamente do java
apt-get update
apt-get install -y nano
nano /etc/apt/sources.list
apt-get update
apt-get install -y openjdk-10-jdk

echo 'public class Teste { public static void main(String[] args) { System.out.println("Alo mundo de DevOps!"); } }' > Teste.java
javac Teste.java
java Teste
# saída esperada
## Alo mundo de DevOps!

exit
# Saída
### leo:~$ 

docker container ls -a
# Saída
### CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
### 
```

**links**:
- [Use the Docker command line](https://docs.docker.com/engine/reference/commandline/cli/)
- Para o nosso estudo de caso até o momento, prefira veja
  - [docker create](https://docs.docker.com/engine/reference/commandline/create/)
  - [docker exec](https://docs.docker.com/engine/reference/commandline/exec/#run-docker-exec-on-a-running-container)
  - [docker kill](https://docs.docker.com/engine/reference/commandline/kill/)
  - [docker pause](https://docs.docker.com/engine/reference/commandline/pause/)
  - [docker restart](https://docs.docker.com/engine/reference/commandline/restart/)



### [](#header-3) Passo 4. Empacotar uma aplicação java num container**

**Dockerfile** 1a versão

```sh
pwd
# Saída
### /home/leo/app
# se não for essa sáida, procurar diretório app

touch Dockerfile
nano Dockerfile
# conteúdo do arquivo
### FROM debian:stretch
###
### RUN mkdir /app
### COPY ./src/Teste.java /app
### 
### WORKDIR /app
### 

docker build --tag appjava:v1 .
### Sending build context to Docker daemon  3.584kB
### Step 1/5 : FROM debian:stretch
###  ---> 3bbb526d2608
### Step 2/5 : RUN mkdir /app
###  ---> Running in bff619cf4978
### Removing intermediate container bff619cf4978
###  ---> 15f0a50f0576
### Step 3/5 : COPY ./src/Teste.java /app
###  ---> 5a9a2051c69f
### Step 4/5 : WORKDIR /app
###  ---> Running in 66793dbe9f14
### Removing intermediate container 66793dbe9f14
###  ---> 2b104ac61cf7
### Step 5/5 : CMD [ "bash" ]
###  ---> Running in 46906a903146
### Removing intermediate container 46906a903146
###  ---> 92af8463feb9
### Successfully built 92af8463feb9
### Successfully tagged minora:appjava
### 

docker image ls
# Saída
### REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
### appjava             v1                  92af8463feb9        About a minute ago   101MB
### debian              stretch             3bbb526d2608        5 weeks ago          101MB
### hello-world         latest              2cb0d9787c4d        6 weeks ago          1.85kB

docker container ls -a
# Saída
### CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                   PORTS               NAMES
### 62a22ab79481        hello-world         "/hello"            7 hours ago         Exited (0) 7 hours ago                       epic_borg

docker run -it --rm --name conteiner appjava:v1
# Saída
### root@03c6a207715f:/app#

pwd
# Saída
### /app
ls -l
# Saída
### total 4
### -rw-r--r-- 1 root root 122 Aug 22 17:24 Teste.java

exit
```

**Dockerfile** 2a versão

```sh
pwd
# Saída
### /home/leo/app
# se não for essa sáida, procurar diretório app

mv Dockerfile Dockerfile.v2
touch Dockerfile
nano Dockerfile
# conteúdo do arquivo
### FROM debian:stretch
### 
### RUN echo 'deb http://deb.debian.org/debian unstable main' >> /etc/apt/sources.list
### RUN apt-get update
### RUN apt-get install -y openjdk-10-jdk
### 
### RUN mkdir /app
### COPY ./src/Teste.java /app
### 
### WORKDIR /app
### 
### RUN javac Teste.java
### CMD [ "java", "Teste" ]

docker build --tag appjava:v2 .
# Saída
### Sending build context to Docker daemon  4.096kB
### Step 1/9 : FROM debian:stretch
###  ---> 3bbb526d2608
### Step 2/9 : RUN echo 'deb http://deb.debian.org/debian unstable main' >> /etc/apt/sources.list
###  ---> Using cache
###  ---> 29e22c0ba99f
### Step 3/9 : RUN apt-get update
###  ---> Running in 006d772704fb
### Get:1 http://security.debian.org/debian-security stretch/updates InRelease [94.3 kB]
### Ign:2 http://cdn-fastly.deb.debian.org/debian stretch InRelease
### Get:5 http://security.debian.org/debian-security stretch/updates/main amd64 Packages [391 kB]
### Get:3 http://cdn-fastly.deb.debian.org/debian stretch-updates InRelease [91.0 kB]
### Get:4 http://cdn-fastly.deb.debian.org/debian unstable InRelease [233 kB]
### Get:6 http://cdn-fastly.deb.debian.org/debian stretch Release [118 kB]
### Get:7 http://cdn-fastly.deb.debian.org/debian stretch-updates/main amd64 Packages [5148 B]
### Get:8 http://cdn-fastly.deb.debian.org/debian stretch Release.gpg [2434 B]
### Get:9 http://cdn-fastly.deb.debian.org/debian unstable/main amd64 Packages [8235 kB]
### Get:10 http://cdn-fastly.deb.debian.org/debian stretch/main amd64 Packages [7099 kB]
### Fetched 16.3 MB in 5s (3075 kB/s)
### Reading package lists...
### Removing intermediate container 006d772704fb
###  ---> b480c573b1b1
### Step 4/9 : RUN apt-get install -y openjdk-10-jdk
###  ---> Running in 4d60250a0869
### Reading package lists...
### Building dependency tree...
### Reading state information...
### The following additional packages will be installed:
###   adwaita-icon-theme at-spi2-core ca-certificates ca-certificates-java dbus
### ...
### ...
### Successfully built 56c8a10f8f91
### Successfully tagged appjava:v2

docker image ls
# Saída
### REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
### appjava             v1                  92af8463feb9        About a minute ago   101MB
### appjava             v2                  92af8463feb9        About a minute ago   101MB
### debian              stretch             3bbb526d2608        5 weeks ago          101MB
### hello-world         latest              2cb0d9787c4d        6 weeks ago          1.85kB

docker container ls -a
# Saída
### CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                   PORTS               NAMES
### 62a22ab79481        hello-world         "/hello"            7 hours ago         Exited (0) 7 hours ago                       epic_borg

docker run -it --rm --name conteiner appjava:v2
# Saída
### Alo mundo de DevOps!

```



**links**

- [Dockerfile](https://docs.docker.com/engine/reference/builder/)
- [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [docker build](https://docs.docker.com/engine/reference/commandline/build/)


## [](#header-2) Alguns links

- [Docker by wikipedia](https://pt.wikipedia.org/wiki/Docker_\(programa\)) 
- [docker.com](https://www.docker.com/)
  - Instalação
    - [Get docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-convenience-script)
    - [Post-installation steps for Linux](https://docs.docker.com/install/linux/linux-postinstall/)
    - [Install Docker Compose](https://docs.docker.com/compose/install/)
    - [Command-line completion](https://docs.docker.com/compose/completion/)
  - Referência
    - [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)
      - [docker build](https://docs.docker.com/engine/reference/commandline/build/)
      - [docker container](https://docs.docker.com/engine/reference/commandline/container/)
      - [docker image](https://docs.docker.com/engine/reference/commandline/image/)
      - [docker pull](https://docs.docker.com/engine/reference/commandline/pull/)
      - [docker run](https://docs.docker.com/engine/reference/commandline/run/)
    - [Dockerfile](https://docs.docker.com/engine/reference/builder/)
    - [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
  - Imagens
    - [hub.docker openjdk](https://hub.docker.com/_/openjdk/)
