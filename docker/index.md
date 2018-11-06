# [](#header-1) DevOps e Docker

## [](#header-2) DevOps

**DevOps** = software development, IT infrastructure operations, and the intersection between them.

- [By wikipedia](https://pt.wikipedia.org/wiki/DevOps)
  - O termo _DevOps_ foi popularizado através de uma série de eventos intitulados [DevOps Days](https://www.devopsdays.org), começando em 2009 na Bélgica.
  - A característica principal do movimento DevOps é defender fortemente a automação e monitoramento em todas as fases da construção do software, da integração, teste, liberação para implantação e gerenciamento de infraestrutura.
  - Deve fornecer:
    - ciclos de desenvolvimento menores
    - frequência de implantação aumentada
    - liberações mais seguras
    - em alinhamento próximo com os objetivos de negócio

![Developement and Operations](images/devops.png)

## [](#header-2) Docker

### [](#header-3) Introdução e nomenclaturas

**Conceitos**

- Hardware, sistema operacional e sistema computacional
- Máquina virtual, sistema hospedeiro (_host_) e sistema convidado (_guest_)
- Monitor de máquina virtual (_virtual machine monitor_ ou _hypervisor_)
- Container/conteiner e imagem

[by wikipedia](<https://pt.wikipedia.org/wiki/Docker_(programa)>)
Docker é uma tecnologia de software que fornece contêineres, promovido pela empresa Docker, Inc.
O Docker fornece uma camada adicional de abstração e automação de virtualização de nível de sistema operacional.
Usa de recursos de um **sistema hospedeiro** para permitir **sistemas convidados** independentes executarem **sem** a necessidade do software do **hardware convidado**, evitando a sobrecarga de iniciar e criar sistemas convidados.

[by docker.com](https://www.docker.com/what-docker)
_Docker enables true independence between applications and infrastructure and developers and IT ops to unlock their potential and creates a model for better collaboration and innovation._

### [](#header-3) Práticas com docker

1. [Introdução com java](intro)
2. [Aplicação web java](web)
3. [Docker compose](docker-compose)
4. Aplicação web com Banco de dados
5. Colocando um proxy reverso
6. Publicando a aplicação na web
