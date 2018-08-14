# Introdução ao Git com o [GitHub](http://github.com)

## Objetivos

1. Aprender trabalhar com "fork" e "pull request"
2. Aprender alguns comandos do git

## Sumário

## Introdução ao VC

- Controle de versão : VC Version Control, VCS Version Control System, SCM Source Control Management
- **objetivo** registrar as diversas versões de arquivos
- _exemplos_ : [git](https://git-scm.com/), mercurial, apache subversion, cvs (concurrent version system)


## Principais comandos do git

- [documentação oficial](https://git-scm.com/doc)
- [comandos básicos](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
  - clone
  - pull e push
  - add e commit


## Serviços online

- [GitHub](http://github.com)
- [Bitbucket](https://bitbucket.org)
- [gitlab.devops.ifrn.edu.br](http://gitlab.devops.ifrn.edu.br)

## Hands on

**Prática 1**
1. Criar conta no [GitHub](http://github.com)
2. Acessar o repositório https://github.com/sistemas-operacionais/git-handson
3. Fazer uma cópia (Fork) do repositório
4. No próprio GitHub, modificar o arquivo ```README.md```, colocando matrícula, nome e email
5. Fazer uma solicitação de modificação no repositório pai

**Prática 2**
1. Clonar o seu repositório para o computador local
2. Criar localmente um diretório com sua matrícula
3. Criar localmente o arquivo ```[matrícula]/index.md```
4. Editar localmente o arquivo e inserir suas informações
5. Adicionar o arquivo para versionamento no git localmente
6. Registrar a modificação localmente
7. Publicar a modificação no seu repositório do GitHub
8. Solicitar a modificação no respositório pai

**lista de comandos**
```sh
git clone https://github.com/leonardo-minora/git-handson.git
cd git-handson
mkdir 2422958
touch 2422958/index.md

git status
## Adicionar os arquivo para versionar
git add 2422958/index.md
## Registrar a versão
git commit -m "Adicionado arquivo com info de Minora"
## Sincronizar do repositório remoto para o repositório local
git pull
## Sincronizar do repositório local para o repositório remoto
git push
```
