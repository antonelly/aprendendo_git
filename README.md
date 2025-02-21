# Version Control System (VCS)

Local (LVCS): RCS  
Centralizado (CVCS): CVS, Subversion, Perforce.<br>
Distribuído (DVCS): Mercurial, Darcs, **Git**

## Estados de arquivos:
**1. Modified:** Arquivo modificado, mas ainda não enviado ao banco de dados - _untracked files_.<br>
**2. Staged:** arquivo marcado para ser enviado ao banco de dados no próximo committ - `git add`<br>
**3. Committed:** Arquivo armazenado no banco de dados - `git commit`.

## Seções de um projeto Git
1. Working directory (working tree)<br>
2. Staging area<br>
3. Git directory (.git repository)

# Comandos básicos

`git help <command>`<br>
`git init`<br>
`git remote add <apelido_url_pode_ser_origin> url`<br>
`git clone url <nome_dir_local>` (eu não testei informar path_dir) <br>
`git clone url --branch feature-1 --single-branch` (ainda não entendi)<br>
`git status`<br>
`git add <file_name>`<br>
`git commit [-m] "mensagem_sucinta_usar_convenção"`<br>
`git log`<br>
`git restore <file_name>`<br>
`git reset` (descobrir pra que serve)<br>
`git reflog` (descobrir pra que sere)<br>

### Trabalhando com branch[^1][^2]
`git checkout -b <nome_da_nova_branch>` -> Cria nova branch<br>
`git checkout <nome_da_branch>` -> Muda para outra branch<br>
`git branch` -> Lista todas as branches **locais**<br>
`git branch -r` -> Lista todas as branches **remotas**<br>
`git branch -a` -> Lista todas as branches **locais e remotas** do projeto<br>
`git branch -d | --delete <branch_name>` -> Deleta branch local<br>
`git push origin <branch_to_be_deleted> --delete` -> Deleta branch remota <br>
`git branch -v` -> Exibe último commit de cada branch<br>
[^1]:https://git-scm.com/book/pt-br/v2/Branches-no-Git-Branches-em-poucas-palavras  
[^2]:https://git-scm.com/docs/user-manual#what-is-a-branch

> Pesquisar sobre convenções em nomes de branches.

>#### Exemplo:
>Estou trabalhando na branch `feature-avaliacao` e quero integrar as novas funcionalidades
na branch `main`.  
>1.  Primeiro, eu vou para a branch `main` com `git checkout main` 
>2. Eu mesclo as alterações com `git merge feature-avaliacao`


### Sincronizando repositórios (remoto com local)
`git push origin main` -> "Empurra" mudanças locais para remoto<br>
`git fetch` -> Baixa alterações do remoto para o local **sem mesclar**<br>
`git merge` -> Mescla alterações baixadas<br>
`git pull` -> Junção `git fetch` + `git merge`

# Melhor prática para um novo repositório:
1. `git init` -> Cria um repositório Git
2. `git branch -M main`  -> Renomeia a branch principal para 'main'
3. `git add .` -> Adiciona todos os arquivos à staging area
4. `git commit -m "Descrição sucinta do commit. Seguir convenções."` -> Adiciona uma mensagem ao commit
5. `git remote add origin <URL_DO_REPO>` -> Conecta repo local e remoto
6. `git push -u origin main` ou `git push origin main`<br>
Sem `-u`: informar `repo` e `branch` toda vez<br>
Com `-u`: informar `repo` e `branch` somente na primeira vez

# Referências
1. [Compreendendo a história: O que é um ramo?](https://git-scm.com/docs/user-manual/pt_BR#what-is-a-branch) (_em inglês_)
2. [Padrões e nomenclaturas no Git](https://github.com/JuniorLima22/padroes-e-nomenclaturas-no-git)
3. [Markdown](https://github.com/luong-komorebi/Markdown-Tutorial/blob/master/README_pt-BR.md)