Comandos Git
=============

>Retornar a página **[inicial](README.md)**

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

```
sudo apt-get install git
```

#### Windows [Git Bash](https://Git-scm.com/download/win)

###### Para verificar a versão instalada, no Terminal do Linux/Windows PowerShell

```
git --version
```

## Configurações

###### Esse material é apenas um resumo, para ver a documentação completa do `Git`

```
git --help
```

#### Global (em toda a máquina)

```
git config --global user.name "<nome de usuário>"
git config --global user.email "<email>"
```


#### Local (único projeto)

```
git config user.name "<nome de usuário>"
git config user.email "<email>"
```

###### alterando `<nome de usuário>` e `<email>` pelos desejados. Essas configurações serão utilizadas para indicar quem fez as alterações na história do repositório.

#### Listar

```
git config --list
```

#### Editar

```
git config -e
```

#### Iniciar repositório

```
git init
```

#### Baixar repositório

```
git clone <endereco>
```

###### alterando `<endereco>` pelo endereço do repositório remoto (por padrão a URL do repositório + .git)

#### Repositório nomeado

```
git remote add <nome> <endereço>
```
###### alterando `<endereco>` pelo endereço do repositório remoto.

## Rastreamento

##### Para mostrar o estado (em relação à arquivos não rastreados/modificados/deletados e a fila de espera de arquivos a serem *commitados*)

```
git status
```

#### Logs

```
git log --all --decorate --oneline --graph
```

#### Nome do repositório

```
git remote show
```

#### [Plugin](https://github.com/kamranahmedse/git-standup)

## Commits

##### Para adicionar todos os arquivos alterados, no nível do diretório, à fila de espera a serem *commitados*

```
git add .
```

##### Para adicionar todos os arquivos alterados à fila de espera a serem *commitados*, execute:

```
git add -A
```

###### Opção `-A` de `all`.

#### Commitar

```
git commit -m "<mensagem>"
```

###### alterando `<mensagem>` e pela mensagem desejada. Opção `-m` de `message`.

#### Enviar commits

```
git push <repositorio> <ramo>
```

###### se usada a opção `-u` (de `upstream`), não é necessário passar o repositório e ramo nas próximas vezes que usar os comandos `push` ou `pull`.

##### *Mergear* as alterações da `branch` nomeada `<ramo>` na `branch` em que se encontra

```
git merge <ramo>
```

#### Alterar autor

```
git commit --amend --author="name <email>"
```

## Branch

#### Listar

```
git branch
```

#### Alterar

```
git checkout <ramo>
```

#### Criar e entrar

```
git checkout -b <ramo>
```

#### Deletar

```
git branch -D <ramo>
```

###### Opção `-D` de `delete` e `force`.

#### Atualizar

```
git pull <repositorio> <ramo>
```

## Rebase

#### Atualizar

```
git rebase -i <ramo>
```

###### Isso irá abrir a linha de comando do editor de texto de sua máquina (`nano` ou `vim`, provavelmente).

##### Para transformar `n` *commits* em um único que contenha todas as alterações desses commmits

###### (não funciona se for o *commit* inicial do repositório)

```
git rebase -i HEAD~n
```

##### Isso irá abrir a linha de comando do editor de texto de sua máquina. Siga os passos:

###### 1. Deixe o primeiro *commit* como `pick`, para manter a mensagem ou, altere para `reword` para escrever uma nova mensagem.

###### 2. Mude os outros para `squash`, caso queria manter as mensagens deles, se caso negativo, troque para `fixup`, para usar somente a mensagem do primeiro *commit*.

###### 3. Digite a mensagem desse novo *commit*.

##### Como foram apagados os *commit* anteriores, para enviar as alterações para o repositório remoto, será necessário usar a opção `-f` (de `force`) no comando de `push`. Exemplo:
```
git push -f origin feature/new-site-section
```
#### Mais esclarecimentos sobre o rebase, [aqui](https://medium.com/@slamflipstrom/a-beginners-guide-to-squashing-commits-with-git-rebase-8185cf6e62ec).