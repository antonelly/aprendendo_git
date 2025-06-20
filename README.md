# Version Control System (VCS)

Local (LVCS): RCS  
Centralizado (CVCS): CVS, Subversion, Perforce.<br>
Distribuído (DVCS): Mercurial, Darcs, **Git**

## Estados de arquivos

**1. Modified:** Arquivo modificado, mas ainda não enviado ao banco de dados - _untracked files_.<br>
**2. Staged:** arquivo marcado para ser enviado ao banco de dados no próximo committ - `git add`<br>
**3. Committed:** Arquivo armazenado no banco de dados - `git commit`.

## Seções de um projeto Git

1. Working directory (working tree)<br>
2. Staging area<br>
3. Git directory (.git repository)

# Comandos básicos

>`git help <command>`<br>
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
>
>`git checkout -b <nome_da_nova_branch>` -> Cria nova branch e muda para ela<br>
`git checkout <nome_da_branch>` -> Muda para outra branch<br>
`git branch` -> Lista todas as branches **locais**<br>
`git branch -r` -> Lista todas as branches **remotas**<br>
`git branch -a` -> Lista todas as branches **locais e remotas** do projeto<br>
`git branch -d | --delete <branch_name>` -> Deleta branch local<br>
`git push origin <branch_to_be_deleted> --delete` -> Deleta branch remota <br>
`git branch -v` -> Exibe último commit de cada branch<br>
[^1]:<https://git-scm.com/book/pt-br/v2/Branches-no-Git-Branches-em-poucas-palavras>  
[^2]:<https://git-scm.com/docs/user-manual#what-is-a-branch>

> **Pesquisar sobre convenções em nomes de branches.**

>#### Exemplo
>
>Estou trabalhando na branch `feature-avaliacao` e quero integrar as novas funcionalidades
na branch `main`.
>
>1. Primeiro, eu vou para a branch `main` com `git checkout main`
>2. Eu mesclo as alterações com `git merge feature-avaliacao`

### Sincronizando repositórios (remoto com local)
>
>`git push origin main` -> "Empurra" mudanças locais para remoto<br>
`git fetch` -> Baixa alterações do remoto para o local **sem mesclar**<br>
`git merge` -> Mescla alterações baixadas<br>
`git pull` -> Junção `git fetch` + `git merge`

### Resolvendo conflitos
Ao usar o comando `git push origin main`, o Git apresenta mensagem de erro, indicando que existem modificações conflitantes entre os repositórios local e remoto.  
Deve-se usar o comando `git pull origin main` (que é a combinação dos comandos `git fetch` e `git merge`), para trazer para o repositório local as alterações do repositório remoto.  
Na sequência, deve-se analisar os conflitos apresentados em cada arquivo com conflitos (usar o VS CODE ajuda bastante nesse trabalho) e salvar as alterações.  
Na sequência, executa-se o comando `git add .` para incluir as mudanças no próximo commit e um `git commit` (sem o parâmetro `-m`).  
Nesse momento, o Git vai gerar uma mensagem que deve ser analisada e modificada ou deixada como está. **Essa mensagem se refere ao commit da resolução do conflito**.
Por último, o processo é concluído com `git push origin main`.

>**Observação: Esse processo foi apresentado no curso da Alura e não foi testado por você. Faça esse teste assim que possível para entender melhor como esse processo funciona num ambiente real.**

# Melhor prática para um novo repositório
>
>1. `git init` -> Cria um repositório Git
>2. `git branch -M main`  -> Renomeia a branch principal para 'main'
>3. `git add .` -> Adiciona todos os arquivos à staging area
>4. `git commit -m "Descrição sucinta do commit. Seguir convenções."` -> Adiciona uma mensagem ao commit
>5. `git remote add origin <URL_DO_REPO>` -> Conecta repo local e remoto
>6. `git push -u origin main` ou `git push origin main`<br>
Sem `-u`: informar `repo` e `branch` toda vez<br>
Com `-u`: informar `repo` e `branch` somente na primeira vez

# Coisas que ainda não sei pra que servem, nem como funcionam

>`git flow feature start minha-feature`<br>
\# O que faz esse comando?<br><br>
`git flow feature finish minha-feature`<br>
\# E esse?

>`git flow release start 1.0.0`<br>
\# Descubra o que faz esse aqui também<br><br>
`git flow release finish 1.0.0`<br>
\#E esse...

## Templates para Issue
1. No seu repositório, criar uma pasta chamada `.github`.
2. Dentro da pasta `.github`, criar uma subpasta chamada `ISSUE_TEMPLATE`. Isso é importante para que o GitHub reconheça os arquivos dentro dessa pasta como modelos para Issues.
3. Dentro da pasta `ISSUE_TEMPLATE`, crie arquivos Markdown para diferentes tipos de issues que você deseja suportar (por exemplo, bug_report.md, feature_request.md, etc).
4. Use Markdown para criar um modelo com as seções necessárias, como Descrição, Passos para Reproduzir (no caso de bugs), Comportamento Esperado, Comportamento Atual, etc. Inclua instruções claras para os contribuidores preencherem as informações necessárias.

**Exemplo de modelo de Issue:**
```markdown
---
name: Relatar Problema
about: Crie um relatório para nos ajudar a melhorar

---

**Descreva o problema:**
Uma descrição clara e concisa do que é o problema.

**Passos para Reproduzir:**
Passos para reproduzir o comportamento:

**Comportamento Esperado:**
Uma descrição clara e concisa do que você esperava que acontecesse.

**Capturas de Tela:**
Se aplicável, adicione capturas de tela para ajudar a explicar seu problema.

**Contexto Adicional:**
Escreva qualquer contexto adicional sobre o problema aqui.
```


## Templates para Pull Request
1. Na pasta `.github`, criar uma subpasta chamada `PULL_REQUEST_TEMPLATE`.
2. Dentro da pasta `PULL_REQUEST_TEMPLATE`, crie um arquivo Markdown (por exemplo, pull_request_template.md).
3. Inclua seções como Descrição, Problema Corrigido (referenciando o número da issue, se aplicável), Passos para Testar, Screenshots (se aplicável), etc. Novamente, forneça instruções claras para ajudar os contribuidores a fornecer as informações necessárias.
4. No corpo do PR, você pode usar palavras-chave como `Fixes #123` ou `Resolves #456` para vincular automaticamente o PR à issue correspondente.

**Exemplo de modelo de Pull Request:**
```markdown
---
name: Pull Request
about: Crie um pull request para contribuir com o projeto

---

**Descrição:**
Uma descrição clara e concisa do que este pull request faz.

**Corrige/Resolve:**
# (número da issue)

**Mudanças Propostas:**
Descreva as alterações que você fez.

**Passos de Teste:**
Forneça passos para testar as alterações feitas neste pull request.

**Capturas de Tela:**
Se aplicável, adicione capturas de tela para mostrar as alterações.
```
>Fonte: Curso Alura Git/Github
# Referências

1. [Compreendendo a história: O que é um ramo?](https://git-scm.com/docs/user-manual/pt_BR#what-is-a-branch) (_em inglês_)
2. [Padrões e nomenclaturas no Git](https://github.com/JuniorLima22/padroes-e-nomenclaturas-no-git)
3. [Markdown](https://github.com/luong-komorebi/Markdown-Tutorial/blob/master/README_pt-BR.md)
4. [Modelos para Issue e Pull Request](https://docs.github.com/pt/communities/using-templates-to-encourage-useful-issues-and-pull-requests/about-issue-and-pull-request-templates)
