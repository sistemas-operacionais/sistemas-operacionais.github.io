# [](#header-1) Docker : uma introdução

## [](#header-2) Instalação e teste

**docker**: instalando e testando
```sh
su dgti
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker aluno
sudo update-rc.d docker defaults
exit
docker run hello-world
```

**Links**:
- [Get docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-convenience-script)
- [Post-installation steps for Linux](https://docs.docker.com/install/linux/linux-postinstall/)


extra: docker **command completion**
- [Command-line completion](https://docs.docker.com/compose/completion/)



## [](#header-2) Criando seu primeiro conteiner

**Objetivo**
1. Criar baixar imagem openjdk
2. Criar container para compilar e executar códigos java
3. Montar diretório hospedeiro no container
4. Empacotar uma aplicação java num container


**1. Criar baixar imagem openjdk** [hub.docker openjdk](https://hub.docker.com/_/openjdk/)
```sh
docker images
docker pull openjdk
docker images
```

**2. Criar container para compilar e executar códigos java** [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)
```sh
docker contaainer ls
## CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
##
docker run -it --rm --name container openjdk bash
```

_verificando noutro terminal_
```sh
docker image ls
# saída esperada
## REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
## openjdk             latest              db77212ffe05        11 days ago         737MB
docker container ls
# saída esperada
## CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
## c42b681b51b9        openjdk             "bash"              2 minutes ago       Up 2 minutes                            container
```

_compilando código java_
```sh
whoami
# saída esperada
## root
echo 'public class Teste { public static void main(String[] args) { System.out.println("Alo mundo de DevOps!"); } }' > Teste.java
javac Teste.java
java Teste
# saída esperada
## Alo mundo de DevOps!
```

```java
public class Teste {
    public static void main(String[] args) {
        System.out.println("Alo mundo de DevOps!");
    }
}
```

_saindo do container_
```sh
exit
whoami
# saída esperada
## aluno
docker image ls
# saída esperada
## REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
## openjdk             latest              db77212ffe05        11 days ago         737MB
docker container ls
# saída esperada
## CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

**3. Montar diretório hospedeiro no container**
```sh
mkdir -p app/src
cd app
docker run -it --rm --volume `pwd`/src:/src-java --workdir /src-java --name container openjdk bash
javac Teste.java
java Teste
# saída esperada
## Alo mundo de DevOps!
exit
docker container ls
# saída esperada
## CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

**4. Empacotar uma aplicação java num container**
```sh
touch Dockerfile
vim Dockerfile
docker build --tag alo .
docker image ls
# saída esperada
## REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
## alo                 latest              22b517233e86        9 seconds ago       737MB
## openjdk             latest              db77212ffe05        11 days ago         737MB
docker container ls
# saída esperada
## CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
docker run -it --rm --name container alo
# saída esperada
## Alo mundo de DevOps!
```

- [Dockerfile](https://docs.docker.com/engine/reference/builder/)
- [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [docker build](https://docs.docker.com/engine/reference/commandline/build/)

_Dockerfile_
```dockerfile
FROM openjdk
RUN mkdir /app
COPY ./src/Teste.java /app
WORKDIR /app
RUN javac Teste.java
CMD [ "java", "Teste" ]
```

**Links**:
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
