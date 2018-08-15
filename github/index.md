# Introdução ao Git com o [GitHub](http://github.com)

## Objetivos

1. Aprender trabalhar com "fork" e "pull request"
2. Aprender alguns comandos do git

## Sumário
1. Introdução ao sistema de controle de versão
2. Principais comandos do git
3. Práticas (hands on)


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

1. Fork e Modificação via GitHub
2. Modificação local e publicação no repositório remoto
3. Trabalhando sempre com o shell


### Prática 1 : Fork e Modificação via GitHub

1. Criar conta no [GitHub](http://github.com)
2. Acessar o repositório https://github.com/sistemas-operacionais/git-handson
3. Fazer uma cópia (Fork) do repositório
4. No próprio GitHub, modificar o arquivo ```README.md```, colocando matrícula, nome e email
5. Fazer uma solicitação de modificação no repositório pai



### Prática 2 : Modificação local e publicação no repositório remoto

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



### Prática 3 : Trabalhando sempre com o shell

1. Clonar o seu repositório remoto (origin) para computador (local) ```git clone```
2. Adicionar o repositório pai (upstream) no repositório local ```git remote add```
3. Sincronizar do repositório pai (upstream) para o seu repositório (origin) ```git fetch```, ```git merge``` e ```git push```
4. Editar arquivo ```README.md```, adicionando link para suas informações
5. Adicionar o arquivo ```README.md``` para versionamento no git localmente ```git add```
6. Registrar a modificação localmente ```git commit```
7. Verificar informações no GitHub (origin e upstream) - **nada mudou**
8. Editar arquivo ```[Matrícula]/index.md```, adicionando link para sua página no GitHub
9. Criar e editar o arquivo ```[Matrícula]/resume.md```
10. Adicionar os arquivos ```[Matrícula]/index.md``` e ```[Matrícula]/resume.md``` para versionamento no git localmente ```git add```
11. Registrar a modificação localmente ```git commit```
12. Verificar informações no GitHub (origin e upstream) - **nada mudou ainda**
13. Publicar a modificação no seu repositório do GitHub (origin) ```git push```
14. Verificar informações no GitHub (origin e upstream) - **mudou em origin**
15. No site do GitHub solicitar a modificação no respositório pai
16. Verificar informações no GitHub (origin e upstream) - **mudou em ambos**


**lista de comandos**
```sh
## Item 1. Clonar o seu repositório remoto (origin)
git clone https://github.com/leonardo-minora/git-handson.git
cd git-handson
ls -la
git remote -v

## Item 2. Adicionar o repositório pai (upstream)
## https://help.github.com/articles/configuring-a-remote-for-a-fork/
git remote add upstream https://github.com/sistemas-operacionais/git-handson.git
git remote -v

## Item 3. Sincronizar do repositório pai
## https://help.github.com/articles/syncing-a-fork/
git fetch upstream
git checkout master
#### modificou localmente
git status
#### modificar em origin
#### https://help.github.com/articles/merging-an-upstream-repository-into-your-fork/
git push origin master

## Item 5 e 6. Adicionar e registrar o arquivo README.md
git status
git add README.md
git commit -m "Incluído link para info de Minora"
git status

## Item 10 e 11. Adicionar e registrar o arquivo README.md
git status
git add 2422958/index.md 2422958/resume.md
git commit -m "Atualizado info e adicionado resumo de Minora"
git status

## Item 13.  Publicar a modificação no seu repositório do GitHub (origin)
git push origin master

```
