# Git Cheat Sheet 📃

## git add ➕

`git add <arquivo>` = Adiciona um arquivo específico à área de preparação (staging area).

`git add .` = Adiciona todas as alterações no diretório atual à área de preparação (staging area).

`git add -p <arquivo>` = Usado para adicionar alterações interativamente à área de preparação (staging area). Ele permite que você revise e selecione as mudanças em seus arquivos de maneira mais granular, linha por linha ou bloco por bloco.

- `y` (yes) - Adiciona a parte (hunk) à área de preparação (staging area).
- `n` (no) - Não adiciona a parte à área de preparação.
- `d` (no) - Não adiciona a parte à área de preparação, mas também não adiciona as partes restantes no arquivo.
- `s` (split) - Divide a parte em partes menores para que você possa escolher quais partes adicionar separadamente.
- `e` (edit) - Permite editar a parte manualmente antes de adicioná-la à área de preparação.
- `?` (help) - Exibe uma lista de opções disponíveis.
- `q` (quit) - Sai do modo interativo sem adicionar mais partes à área de preparação.
- `a` (all) - Adiciona todas as partes restantes do arquivo à área de preparação.
- `j` (next) - Vai para a próxima parte sem fazer nada com a parte atual.
- `k` (previous) - Volta para a parte anterior sem fazer nada com a parte atual.
- `/` (search)- Permite procurar um pedaço que corresponde ao regex fornecido.

## git commit 📝

`git commit -m "Mensagem de commit"` = cria um novo commit com as alterações na área de preparação (staging area) e o adiciona ao histórico do repositório.

### Conventional Commits 📌

As mensagens de commit no Git devem seguir um padrão consistente e informativo para tornar o histórico do repositório mais legível e compreensível.

`git commit -m "<tipo>(<âmbito>): <descrição>"`

- \<tipo>: Descreve a natureza da mudança realizada no commit. Exemplos comuns de tipos incluem feat (feature - nova funcionalidade), fix (bugfix - correção de erro), docs (documentação), chore (tarefa de manutenção), style (formatação ou estilo de código), refactor (refatoração), perf (performance), build (Mudanças no processo de construção/compilação/empacotamento), ci (Mudanças na configuração de integração/entrega contínua  ), test (testes), entre outros.

- <âmbito> (opcional): Define a área do projeto ou o componente específico onde a mudança foi feita. Nem todos os commits têm um âmbito, mas ele pode ser útil para projetos maiores com várias partes.

- <descrição>: Uma descrição breve e concisa da mudança realizada. Deve começar com letra minúscula, não deve terminar com ponto final e usar imperativo, presente: “mudar” e não “alterado” nem “alterar”.

Exemplo:
`git commit -m "feat(auth): adiciona autenticação por token JWT"`

## git status 🟢🟡🔴

`git status` = é usado para verificar o estado atual do seu repositório Git. Ele fornece informações sobre quais arquivos foram modificados, quais estão na área de preparação (staging area) e quais ainda não estão sendo rastreados pelo Git. 

## git checkout 🔁

`git checkout <nome_da_branch>` =  alternar para uma branch diferente no seu repositório.

`git checkout -b <nome_nova_branch>` = Você pode criar uma nova branch e, ao mesmo tempo, alternar para ela.

`git checkout <branch_origem_arquivo> -- caminho/do/arquivo/arquivo.txt` = Isso copiará o arquivo da branch `branch_origem_arquivo` para a branch atual, mantendo o histórico de commit do arquivo original. O arquivo agora estará na mesma localização relativa na branch atual.

<!--`git checkout fix_branch folder1/update.txt` = copia uma arquivo da branch especifica para a branch atual, sobrescrevendo o arquivo-->

`git checkout -p <branch_origem_arquivo> -- caminho/do/arquivo/arquivo.txt` = Você pode navegar pelo arquivo pedaço por pedaço e escolher se deseja ou não adicioná-los à área de preparação. Isso permite que você copie apenas os trechos específicos que deseja para a branch atual. Você verá um prompt que pergunta se deseja "Stage this hunk?" (Adicionar este pedaço?). Você pode responder com as seguintes opções:

- `y` ou `n` - Para adicionar ou não adicionar o pedaço à área de preparação (staging).
- `s` - Para dividir o pedaço em partes menores.
- `q` - Para sair do modo interativo quando terminar.

`git checkout <commit-hash> -- <caminho/do/arquivo>` = reverter um arquivo para um commit específico.

`git checkout <commit-hash>~1 -- <caminho/do/arquivo>` = reverter para o commit anterior ao especificado, anexe ~1(onde 1 é o número de commits que você deseja voltar)

`git checkout <commit-hash>` =  visualizar o estado do repositório em um commit específico, criando um "estado desconectado" temporário.

`git checkout -b <nova-branch> <commit-hash>` = Criar uma nova branch a partir de um commit específico.

## git push 📤

`git push` = é usado para enviar (ou "empurrar") as alterações feitas no seu repositório Git local para um repositório remoto. Isso significa que você está sincronizando o estado do seu repositório local com o repositório remoto.

`git push <repositório-remoto> <branch-local>:<branch-remoto>` = é usado para enviar (ou "empurrar") as alterações feitas no seu repositório Git local para um repositório remoto. Isso significa que você está sincronizando o estado do seu repositório local com o repositório remoto.

- <repositório-remoto> - Especifica o nome do repositório remoto para o qual você deseja enviar as alterações. Isso geralmente é chamado de "origin", mas você pode ter outros repositórios remotos configurados.
- \<branch-local> - Especifica a branch local que você deseja enviar para o repositório remoto.
- \<branch-remoto> - Especifica a branch remota para a qual você deseja enviar as alterações. Geralmente, é o mesmo nome da branch local, mas pode ser diferente se você quiser fazer push para uma branch com um nome diferente no repositório remoto.

## git pull 📥

`git pull` = é usado para atualizar sua branch local com as alterações mais recentes do repositório remoto. Essencialmente, ele combina dois passos em um: primeiro, ele executa um git fetch para buscar as alterações do repositório remoto, e depois, ele executa um git merge para combinar essas alterações com sua branch local. Isso garante que sua branch local esteja sincronizada com o estado atual do repositório remoto.

`git pull <repositório-remoto> <branch-remota>` = com esse comando estamos puxando as alterações da branch remota "<branch-remota>" do repositório remoto "<repositório-remoto>" para a branch local atual.
- \<repositório-remoto>: Especifica o nome do repositório remoto do qual você deseja buscar as alterações. Normalmente, é chamado de "origin", mas você pode ter outros repositórios remotos configurados.
- \<branch-remota>: Especifica a branch remota da qual você deseja buscar as alterações. Isso normalmente se alinha com a branch local em que você está trabalhando.
  
<!--`git pull origin develop --allow-unrelated-histories` = busca e mescla quaisquer commits da branch develop para a branch atual-->

## git diff 🔀

`git diff` ou `git diff <nome_arquivo>`=  é usado para mostrar as diferenças entre duas áreas no Git. Ele é comumente usado para visualizar as diferenças entre Diretório de Trabalho e Área de Preparação (Staging).

`git diff --staged` ou `git diff --staged <nome_arquivo>`= é usado para mostrar as diferenças entre duas áreas no Git. Ele é comumente usado para visualizar as diferenças entre Área de Preparação (Staging) e o Último Commit.

`git diff <commit-hash-a> <commit-hash-b>` =  é usado para mostrar as diferenças entre duas áreas no Git. Ele é comumente usado para visualizar as diferenças entre Dois Commits.

`git diff <branchB> <branchA>` =  é usado para mostrar as diferenças entre duas áreas no Git. Ele é comumente usado para visualizar as diferenças entre Dois Branches.

`git diff -u HEAD~1 HEAD` = é usado para mostrar as diferenças entre o último commit e o commit anterior em formato unificado.

## git branch 🗃

`git branch` = listar todas as branches locais no seu repositório.

`git branch <nome_branch>` = cria uma nova branch a partir da branch atual, mas não a tornará a branch atual. Para alternar para a nova branch, você pode usar `git checkout` ou `git switch`.

`git branch -d branch-a-ser-deletada` = excluir (deletar) uma branch. 

`git branch -m <nome-branch-atual> <novo-nome-branch>` = renomear uma branch.

`git branch -r` = listar as branches remotas disponíveis no repositório.

## git merge 🔗

`git merge <branch-de-origem>` = é usado para integrar as alterações de uma branch em outra no Git. 

## git log 🧾

`git log` =  é usado para visualizar o histórico de commits de um repositório Git.

`git log -n <limite-linhas> --graph -p --oneline --author=John --since="2023-01-01" --until="2023-12-31" --abbrev-commit`

- \<limite-linhas> = Limitar o Número de Commits Exibidos
- `--graph` = Exibir Gráfico de Ramificações
- `-p` = Exibe as diferenças (diffs) de cada commit, ou seja, as alterações específicas introduzidas por cada commit.
- `--author=John:` = Filtra os commits para mostrar apenas os feitos pelo autor com o nome "John".
- `--since="2023-01-01"` = Filtra os commits para mostrar apenas aqueles feitos desde 1º de janeiro de 2023.
- `--until="2023-12-31"` = Filtra os commits para mostrar apenas aqueles feitos até 31 de dezembro de 2023.
- `--abbrev-commit` = Usa um hash de commit abreviado para economizar espaço.

`git log <branchB>..<branchA>` = Isso mostrará todos os commits que estão em **branchA** mas não em **branchB**.

`git log --follow` = mostra os commits que alteraram o arquivo, mesmo entre renomeações

## git reset ‼️

`git reset --soft <commit-hash>` = Este tipo de reset desfaz commits, mas mantém as alterações no seu diretório de trabalho e na área de preparação (staging area) que foram feitas nos commits que você está desfazendo. Isso permite que você faça alterações adicionais e faça um novo commit. 

`git reset <commit-hash>` = O reset misto desfaz commits e remove as alterações da área de preparação (staging area), mas mantém as alterações no seu diretório de trabalho. Isso permite que você revise as alterações antes de prepará-las para um novo commit. 

`git reset --hard <commit-hash>` =  O reset rígido desfaz commits, remove as alterações da área de preparação (staging area) e descarta todas as alterações no seu diretório de trabalho que foram feitas nos commits que você está desfazendo. Isso restaura seu diretório de trabalho para o estado exato do commit especificado. Tenha cuidado ao usar git reset --hard, pois ele pode resultar na perda irreversível de alterações não commitadas.

`git reset <arquivo>` = remove um arquivo da stage mantendo as alterações no diretório de trabalho

`git reset HEAD~1` = desfaz o ultimo commit 

`git reset --hard origin/mybranch` = Isso efetivamente redefine sua branch local para corresponder exatamente ao estado da branch remota, descartando todas as alterações não commitadas no processo. Portanto, use com cautela, pois pode resultar na perda permanente de trabalho não commitado. 

## git revert ↩️

`git revert <commit-hash>` =  é usado para criar um novo commit que desfaz as alterações introduzidas por um ou mais commits anteriores. Em essência, ele é usado para desfazer commits sem reescrever o histórico de commits, o que o torna uma opção segura quando você precisa corrigir erros no seu projeto.

## git stash 📚

`git stash` = é usado para temporariamente armazenar (ou "guardar") alterações não commitadas em seu diretório de trabalho, permitindo que você trabalhe em uma área limpa sem perder suas mudanças não commitadas.

`git stash --include-untracked` = criará uma stash que incluirá todas as alterações no seu diretório de trabalho, incluindo as alterações nos arquivos rastreados e não rastreados.

`git stach list` = listar todas as stashes disponíveis.

`git stach apply` = recuperar as alterações da stash mais recente e aplicá-las ao seu diretório de trabalho. Não apaga o stash.

`git stach apply <indice lista>` = Se você tem várias stashes e deseja recuperar uma específica.

`git stach drop <indice>` = para excluir uma stash específica.

`git stash pop` = recuperar as alterações da stash mais recente e aplicá-las ao seu diretório de trabalho. Apaga o stash.

`git stach pop <indice>` =  Se você tem várias stashes e deseja recuperar uma específica. Após recuperado o stash é apagado.

`git stash push -m "Sua mensagem de stash"` = é usado para criar uma nova stash (um local temporário para armazenar alterações não commitadas) com uma mensagem de stash personalizada. 

## git tag 🏷

`git tag -a nome-da-tag -m "Sua mensagem aqui"` = criar uma tag anotada (uma tag com uma mensagem associada).

`git tag nome-da-tag` = criar tags leves (tags sem mensagens associadas) .

`git tag` = listar todas as tags existentes no repositório.

`git tag -l "v1*"` =  listar tags que correspondem a um padrão específico usando curingas.

`git show nome-da-tag` = ver informações detalhadas sobre uma tag específica, incluindo a mensagem associada

`git push origin --tags` = envia todas as tags locais para o repositório remoto.

`git tag -d nome-da-tag` =  excluir uma tag.

## inicializa git

`git init` = é usado para iniciar um novo repositório Git em um diretório.

`git clone <url>` = é usado para criar uma cópia local de um repositório Git existente em um servidor remoto.
<!--
## git config

### config user

`git config --global user.name "<nome e sobrenome>"` = define o nome que irá assinar os commits

`git config --global user.email "<e-mail>"` = define o e-mail que irá assinar os commits

### config mergetool

`git config --global merge.tool vscode`
`git config --global mergetool.vscode.cmd 'code --wait $MERGED'`

### config cor review

`git config --global color.ui auto` = defina a coloração automática da linha de comando para o Git para facilitar a revisão

### config difftool

`git config --global diff.tool vscode`
`git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'`

### define editor

`git config --global core.editor "code --wait"`

### visualiza configs

`git config --global -e`


https://git-scm.com/docs/git-checkout


git show [SHA] = show any object in Git in human-readable format

git rm [file] = delete the file from project and stage the removal for commit

git mv [existing-path] [new-path] = change an existing file path and stage the move

git log --stat -M = show all commit logs with indication of any paths that moved -->
