# Version Control System (VCS)

Local (LVCS): RCS
Centralizado (CVCS): CVS, Subversion, Perforce.
Distribuído (DVCS): Mercurial, Darcs, Git

## Estados de arquivos:
1 - Modified: Arquivo modificado, mas ainda não enviado ao banco de dados - untracked files.
2 - Staged: arquivo marcado para ser enviado ao banco de dados no próximo committ
3 - Committed: Arquivo armazenado no banco de dados.

## Seções de um projeto Git
1 - Working directory (working tree)
2 - Staging area
3 - Git directory (.git repository)

Pesquisar sobre convenções em nomes de branchs.

# Comandos básicos

git help <command>

git init
git remote add <name_server> (usando origin) url
git clone url <nome_dir_local>
git clone url --branch feature-1 --single-branch

git status

git add <file_name>

git commit [-m]
git log
git restore <file_name>
git reset
git reflog

git checkout -b <nome_da_nova_branch>
git checkout <nome_da_branch> #muda para outra branch
git branch #lista todas as branches locais
git branch -r #lista todas as branches remotas
git branch -a #lista todas as branches locais e remotas do projeto
git branch -d <branch_name>
git branch -v #exibe último commit de cada branch)

git push origin main

git fetch #baixa as alterações do remoto para o local sem mesclar
git merge #mescla as alterações baixadas
git pull #junção git fetch + git merge

# Melhor prática para um novo repositório:
git init
git branch -M main  #Renomeia a branch principal para 'main'
git add .
git commit -m _"Primeiro commit"_
git remote add origin _<URL_DO_REPO>_
git push -u _origin_ _main_
