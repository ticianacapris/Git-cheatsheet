# Git-cheatsheet

Guia prático para começar com git

<img src="https://i.ibb.co/fdMxnQ4/gitTici.png"  align="center" alt="gitTici"   border="0">

<p >

   <img alt="Forks" src="https://img.shields.io/github/stars/ticianacapris?color=4A90E2&label=FORKS&logo=3C424B&logoColor=3C424B&style=for-the-badge&labelColor=222222" />

   <img alt="Issues" src="https://img.shields.io/github/stars/ticianacapris?color=4A90E2&label=ISSUES&logo=3C424B&logoColor=3C424B&style=for-the-badge&labelColor=222222" />

   <img alt="GitHub license" src="https://img.shields.io/github/stars/ticianacapris?color=4A90E2&label=LICENSE&logo=3C424B&logoColor=3C424B&style=for-the-badge&labelColor=222222" />

  <a href="https://github.com/ticianacapris">
    <img alt="Follow ticianacapriss" src="https://img.shields.io/static/v1?label=Follow&message=ticianacapris&style=for-the-badge&color=4A90E2&labelColor=222222" />
  </a>
</p>
<h1 align="center">
  Principais Comandos do Git
</h1>

<p align="center">
  <a href="README.md">Português</a>
</p>

<p >
Utilize este útil guia para melhorar o seu fluxo de trabalho. O objetivo é poupa-lhe tempo quando simplesmente não se lembra o que é um comando ou não quer usar a ajuda de git na linha de comando. É difícil memorizar todos os comandos importantes de Git de cor, por isso utilize esse guia o seu ambiente de trabalho para recorrer quando ficar preso. Incluí os comandos básicos de Git para o ajudar a aprender Git, e conceitos mais avançados em torno dos ramos de Git, repositórios remotos, desfazer alterações, e muito mais.
</p>

- Iniciar o repositório

  `git init`

---

- Listar arquivos modificados

`git status`

---

- Desfazer mudanças

  - Arquivos que não são monitorados

      `git checkout`

  - Excluir novos arquivos que não foram adicionados ao stage
  
  `git clean -df`
  
  - Excluir arquivos do stage
  
 `git reset`

  - Desfazer o último commit
  
      `git revert HEAD`
  

---

- Renomear Commit

  `git commit —amend`

---

- Branches

  - Listar branch local

    `git branch`

  - Listar também as branches que estão no repositório remoto

    `git branch -a`

  - Navegar para outra branch

    `git checkout outra-branch`

  - Adicionar -b uma nova branch será criada

       `git checkout -b new-branch`
       
  Excluir branche

    `git branch -d nome-da-branch // normal`

    `git branch -D nome-da-branch // forçando`

  - Renomear branche

    `git branch -m novo-nome-da-branch`

  - Se você está em um branch e deseja renomear outro, deve primeiro passar o nome atual do branch que deseja renomear:

    `git branch -m nome-atual novo-nome`

 - Branch Isolada
   Tem este nome porque não está vinculado a branch principal, então seu histórico não é compartilhado
  ```shell
    Exemplo:
      i---j---k     <== branch 'minha branch'
            /
    a---b---c---d---h---l   <== branch 'main'
        \         /
          e---f---g         <== branch 'minha outra branch'

    1---2---3---4           <== branch `órfã`
  ```
  
Isso é útil quando você deseja colocar vários projetos no mesmo repositório. Um bom exemplo é quando você tem um projeto no Github e deseja criar u site para divulgar seu projeto. O aplicativo e o site são diferentes, portanto, seu seu código deve ser controlado por versão separadamente. Colocar ambos no mesmo repositório simplifica o gerenciamento.
 
  Para criar uma branch isolada basta digitar o comando:

  `git checkout --orphan minha-branch-orfa`

---
- Visualizando o Histórico de Commits

  `git log`

  - Histórico de um ou mais arquivos

    `git log -p meus-arquivos`

  - Histórico de um autor

    `git log --author=name-author`

  - Histórico por data

    `git log --after="MMM DD YYYY"`

    `git log --before="MMM DD YYYY"`

  - Histórico Baseado em uma mensagem(commit)

    `git log --grep produtos`

    Usando este comando, teremos o histórico de commits, onde a mensagem de commit
    Existe a palavra "produto". O que experimentamos pode ser uma expressão regular,
    Podemos gastar mais de um:

  Exemplos:

  Procurar por "produtos" OU "usuarios"

  `git log --grep produtos --grep usuarios`

  Procurar por "produtos" E "usuarios"

  `git log --grep produtos --and --grep usuarios`

---

- Exibir branches em um modo mais legível

  O histórico pode ser impresso para mostrar as branches do repositório com determinado conteúdo.
Use comandos para ser mais legível. Obteremos resultados semelhantes aos seguintes:

  ```shell
    * a102055 (HEAD -> master) commit 8
    | * 196d28e (branch-2) commit 7
    | * 07e073c commit 3
    | * 2b077ca new fie
    | | * c1369d8 (branch-3) commit 6
    | | * d11bdcd commit 5
    | |/
    |/|
    * | 2b22b75 commit 2
    |/
    * d5a12b0 .gitignore
    * 9535426 -- commit 1
  ```

  O comando é um pouco comprido:

  `git log --all --decorate --oneline --graph`

  Para decorar tudo o que deve-seescrever após o log.

  ```
    --all
    --decorate
    --oneline
    --graph
  ```

---

- Trabalhar em mais de uma coisa sem fazer commit
 
Às vezes, você pode precisar parar o que está fazendo e começar a trabalhar em outra tarefa.
No entanto, pode não ser bom enviar conteúdo inacabado, resultando em commits que ficarão no histórico e com seu código não funcionando. 
Podemos salvar as alterações feitas mesmo se não houver necessidade de executar o commit para processá-lo novamente mais tarde, isso é chamado de Stash (semelhante a "esconder" ou "acumular").

  Ao fazer isso, seu repositório voltará ao estado do último commit, e as alterações
  feitas anteriormente estarão “escondidas”.

  - Salvar alterações em um Stash

    `git stash`

  - Colocae nome em um stash

    `git stash push -m meu-nome-stash`

  - Listar stash

    `git stash list`

  - Recuperar alterações no stash

    `git stash apply`

  Isso irá recuperar o código oculto mais recente. Se quiser restaurar um stash mais antigo,
  basta olhar para o número de stash exibido quando o listar e ir para o seguinte comando:

  `git stash apply stash@{2}`

  - Remover Stashes

    Quando recuperamos as alterações do stash, ele salva. Delete isso a partir da pilha,
    execute o comando drop próximo ao nome do stash que você deseja excluir

    `git stash drop stash@{5}`

---

       
