# Comandos Git

> Retornar a página **[inicial](README.md)**

## Sumário

- [Tarefas](#Tarefas)
- [Introdução](#Introdução)
- [Instalação](#Instalação)
- [Configurações](#Configurações)
- [Rastreamento](#Rastreamento)
- [Commits](#Commits)
- [Branchs](#Branchs)
- [Rebase](#Rebase)

## Tarefas

- [ ] Atualizar com mais comandos

## Introdução

Git é um sistema de controle de versão distribuída de código aberto. Ele basicamente é um rastreador de conteúdo. Portanto, pode ser usado para armazenar diversos tipos de conteúdos -principalmente códigos, devido aos outros recursos que oferece.

## Instalação

#### Linux

```bash
sudo apt-get install git
```

#### Windows [Git Bash](https://Git-scm.com/download/win)

###### Para verificar a versão instalada, no Terminal do Linux/Windows PowerShell

```bash
git --version
```

## Configurações

###### Esse material é apenas um resumo, para ver a documentação completa do `Git`

```bash
git --help
```

#### Global (em toda a máquina)

```bash
git config --global user.name "<nome de usuário>"
git config --global user.email "<email>"
```

#### Local (único projeto)

```bash
git config user.name "<nome de usuário>"
git config user.email "<email>"
```

###### alterando `<nome de usuário>` e `<email>` pelos desejados. Essas configurações serão utilizadas para indicar quem fez as alterações na história do repositório.

#### Listar

```
git config --list
```

#### Editar

```bash
git config -e
```

#### Iniciar repositório

```bash
git init
```

#### Baixar repositório

```bash
git clone <endereco>
```

###### alterando `<endereco>` pelo endereço do repositório remoto (por padrão a URL do repositório + .git)

#### Repositório nomeado

```bash
git remote add <nome> <endereço>
```

###### alterando `<endereco>` pelo endereço do repositório remoto.

## Rastreamento

##### Para mostrar o estado (em relação à arquivos não rastreados/modificados/deletados e a fila de espera de arquivos a serem _commitados_)

```bash
git status
```

#### Logs

```bash
git log --all --decorate --oneline --graph
```

#### Nome do repositório

```bash
git remote show
```

#### [Plugin](https://github.com/kamranahmedse/git-standup)

## Commits

##### Para adicionar todos os arquivos alterados, no nível do diretório, à fila de espera a serem _commitados_

```bash
git add .
```

##### Para adicionar todos os arquivos alterados à fila de espera a serem _commitados_, execute:

```bash
git add -A
```

###### Opção `-A` de `all`

#### Commitar

```bash
git commit -m "<mensagem>"
```

#### Alterar a mensagem de um commit

```bash
git commit --fixup <HASH OF THE COMMIT "Commit msg example">
```

###### alterando `<mensagem>` e pela mensagem desejada. Opção `-m` de `message`.

#### Enviar commit

```bash
git push <repositorio> <ramo>
```

#### Forçar envio de commit

```bash
git push <repositorio> <ramo> --force
```

###### se usada a opção `-u` (de `upstream`), não é necessário passar o repositório e ramo nas próximas vezes que usar os comandos `push` ou `pull`.

##### _Mergear_ as alterações da `branch` nomeada `<ramo>` na `branch` em que se encontra

```bash
git merge <ramo>
```

#### Alterar autor

```bash
git commit --amend --author="name <email>"
```

#### Voltar para um commit específico

```bash
git reset --hard <HASH OF THE COMMIT>
```

## Branch

#### Listar

```bash
git branch
```

#### Alterar

```bash
git checkout <ramo>
```

#### Criar e entrar

```bash
git checkout -b <ramo>
```

#### Deletar

```bash
git branch -D <ramo>
```

###### Opção `-D` de `delete` e `force`.

#### Atualizar

```bash
git pull <repositorio> <ramo>
```

## Rebase

#### Atualizar

```bash
git rebase -i <ramo>
```

###### Isso irá abrir a linha de comando do editor de texto de sua máquina (`nano` ou `vim`, provavelmente).

##### Para transformar `n` _commits_ em um único que contenha todas as alterações desses commmits

###### (não funciona se for o _commit_ inicial do repositório)

```bash
git rebase -i HEAD~n
```

##### Isso irá abrir a linha de comando do editor de texto de sua máquina. Siga os passos

###### 1. Deixe o primeiro _commit_ como `pick`, para manter a mensagem ou, altere para `reword` para escrever uma nova mensagem

###### 2. Mude os outros para `squash`, caso queria manter as mensagens deles, se caso negativo, troque para `fixup`, para usar somente a mensagem do primeiro _commit_

###### 3. Digite a mensagem desse novo _commit_

##### Como foram apagados os _commit_ anteriores, para enviar as alterações para o repositório remoto, será necessário usar a opção `-f` (de `force`) no comando de `push`. Exemplo

```bash
git push -f origin feature/new-site-section
```

#### Mais esclarecimentos sobre o rebase, [aqui](https://medium.com/@slamflipstrom/a-beginners-guide-to-squashing-commits-with-git-rebase-8185cf6e62ec)
