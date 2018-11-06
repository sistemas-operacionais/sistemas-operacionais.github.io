# [](#docker) Docker :: docker compose - trabalhando com múltiplas imagens e conteineres

## [](#sumario) Sumário

1. Objetivos
2. Motivação
3. Docker compose
4. Anatomia de um arquivo docker-compose.yml

## [](#goals) Objetivos

## [](#motivation) Motivação

- Arquitetura dos aplicativos
  - mobile, web, e _desktop_ ou [PWA](https://developers.google.com/web/progressive-web-apps/)
  - [api](https://cloud.google.com/apis/design/), serviços e micro-serviços web
  - repositório de dados
  - proxy reverso
- Diferentes ambientes de instalação: Desenvolvimento, Teste, Homologação, Produção, etc
- Aproximação da infra-estrutura de produção dos outros ambientes

## [](#compose) Docker compose

[docker compose](https://docs.docker.com/compose/overview/) é um aplicativo para ajudar a definir e executar múltiplos (imagens e) conteineres.

3 passos:

1. Defina o ambiente da aplicação com arquivos `Dockerfile`, assim você consegue replicar em qualquer lugar.
2. Defina os serviços que irão compor sua aplicação com o arquivo `docker-compose.yml`, assim você pode executar em diversos ambientes.
3. Inicialize os serviços com o comando `docker-compose up`, assim você inicia e executa realmente a aplicação

## [](#anatomy) Anatomia de um arquivo docker-compose.yml

Formato [YAML](http://yaml.org) ([wikipedia](https://pt.wikipedia.org/wiki/YAML)) _is a human friendly data serialization standard for all programming languages._

- [version](https://docs.docker.com/compose/compose-file/#versioning) : versão do formato do arquivo
- [services](https://docs.docker.com/compose/compose-file/#service-configuration-reference) : definião da composição dos conteineres (serviços)
- [networks](https://docs.docker.com/compose/networking/) : configuração da rede dos conteineres
- [volumes](https://docs.docker.com/compose/compose-file/#volumes) : configurar volumes (diretórios) para uso nos serviços

```yml
version: "3"
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - logvolume01:/var/log
    links:
      - redis
  ? db

  redis:
    image: redis
networks:
  ? frontend
  ? backend
volumes:
  logvolume01: {}
```

## [](#commands) Comandos

`docker-compose options command args`

- Imagens
  - `build` construir imagens localmente
  - `images` listar imagens
  - `pull` e `push` baixa e envia imagens para o servidor de imagens
- Serviços
  - `up` e `down`
  - `start`, `restart`, `stop` e `kill`
  - `pause` e `unpause`
- View the status of running services
  - `ps`
  -
- Stream the log output of running services
  - `log`
- Run a one-off command on a service
  - `exec`
  - `run`

## [](#features) Características do docker-compose

- Multiple isolated environments on a single host
- Preserve volume data when containers are created
- Only recreate containers that have changed
- Variables and moving a composition between environments
