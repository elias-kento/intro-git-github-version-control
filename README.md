# Git e GitHub: Primeiros Passos
Tutorial de uso do Git e GitHub.

## 1. Configurando o Git

### 1.1. Verificar a versão do Git instalada
  ```bash
    # git --version
  ```
![version](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/4d425bfe-d882-4ce0-bbdc-25502103c251)

### 1.2. Configure seu perfil do Git
  ```bash
    # Configura o Git com seu nome
    git config --global user.name "<Your-Full-Name>"
  ```
  ```bash
    # Exemplo
    git config --global user.name "Robert Oppenheimer"
  ```
  ```bash
    # Configura o Git com seu e-mail
    git config --global user.email "<your-email-address>"
  ```
  ```bash
    # Exemplo
    git config --global user.email "robert@oppenheimer.com"
  ```

### 1.3. Configure a cor de saída da interface do usuário
  ```bash
    # Garante que a saída do Git esteja colorida
    git config --global color.ui auto
   ```

### 1.4. Reveja todas as opções de configuração
  ```bash
    # Lista todas as propriedades de configuração
    git config --list
  ```
![2024-07-21_23-42-01_v05](https://github.com/user-attachments/assets/98e03911-3fd8-44cc-9e8c-f4b9fdd110e0)

## 2. Trabalhando com um Repositório Local

O Git acompanha as mudanças no seu código-fonte, permite o versionamento e suporta o desenvolvimento não linear através de milhares de ramificações paralelas sem a necessidade de internet.

### 2.1. Inicializando um Repositório Git Local

1. Em sua máquina local, crie uma nova pasta vazia.
2. Clique com o botão direito dentro da pasta e selecione **Git Bash Here** nas opções.

![open](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/a3a8fb58-8a6c-4df0-8a44-b1dc96a20909)

## 3. Criar um novo repositório na linha de comando
  ```bash
    # Criar o arquivo README.md com cabeçalho "# Teste"
    echo "# Teste" >> README.md
    # Inicializa um novo repositório Git no diretório atual
    git init
    # Adiciona o arquivo README.md a "Staging Area" para ser preparado para o commit
    git add README.md
    # Realiza o commit com uma mensagem de commit "first commit"
    git commit -m "first commit"
    # Renomeia a branch padrão de "master" para "main"
    git branch -M main
    # Adiciona um repositório remoto chamado "origin" com o URL fornecido
    git remote add origin https://github.com/elias-kento/teste.git
    # Envia as mudanças do repositório local para o repositório remoto "origin" na branch "main"
    git push -u origin main
  ```

### 3.1. Listar os remotes criados e validar sua URL
  ```bash
    git remote
    git remote get-url origin
  ```
![remote](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/80ad1795-b51d-4d05-aff3-83c9b901af06)

## 4. Comandos básicos do Git
![basico](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/1c5ff94b-0623-4047-aecd-9792eab3240b)

### 4.1. git status
Este comando mostra o estado atual do seu repositório Git, incluindo arquivos modificados, arquivos prontos para serem commitados e outras informações relevantes.
  ```bash
    git status
  ```
![status](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/90bab51a-8b7a-497c-91b5-8b1527633c90)

### 4.2. git add
Utilizado para adicionar mudanças feitas nos arquivos ao índice do Git, preparando-as para serem incluídas no próximo commit.
  ```bash
    git add new-text-file.txt
  ```
| Comando       | Novos Arquivos | Arquivos Modificados | Arquivos Removidos | Escopo                           |
|---------------|----------------|----------------------|--------------------|----------------------------------|
| `git add .`   | Sim            | Sim                  | Não                | Diretório atual e subdiretórios  |
| `git add -A`  | Sim            | Sim                  | Sim                | Todo o repositório               |

### 4.3. git commit
Este comando confirma as mudanças que foram adicionadas ao índice com o `git add`, criando uma nova revisão no histórico do repositório.
  ```bash
    git commit -m "message"
  ```

#### 4.3.1. git commit --amend --no-edit
Este comando é usado para modificar o último commit no seu repositório Git sem alterar sua mensagem de commit. Isso é útil quando você deseja adicionar mais mudanças ao commit mais recente ou corrigir algo que você esqueceu de incluir.

  ```bash
    # Passo 1: Crie e commite o arquivo inicialmente
    echo "Conteúdo inicial" > arquivo1.txt
    git add arquivo1.txt
    git commit -m "Adicionar arquivo1.txt com conteúdo inicial"
    
    # Passo 2: Perceba que esqueceu de adicionar mais conteúdo
    
    # Passo 3: Faça a alteração esquecida em arquivo1.txt
    echo "Conteúdo adicional" >> arquivo1.txt
    
    # Passo 4: Adicione a alteração ao índice
    git add arquivo1.txt
    
    # Passo 5: Emende o commit anterior
    git commit --amend --no-edit
   ```
:warning: É uma péssima ideia alterar os commits que foram compartilhados com outro desenvolvedor ou que foram publicados (pushed) em um repositório compartilhado, como o GitHub.

### 4.4. git diff
O comando `git diff` é utilizado no Git para comparar alterações entre commits, branches, arquivos ou o estado atual do repositório com versões anteriores. Esse comando é essencial para revisar mudanças no código, identificar diferenças e colaborar de maneira eficiente com outros desenvolvedores.
  ```bash
    # Mostra alterações não preparadas para commit
    git diff
    # Mostra todas as mudanças desde o último commit, incluindo as que estão no índice e as que ainda não estão
    git diff HEAD
    # Mostra alterações feitas no último commit
    git diff HEAD^
  ```

### 4.5. git log
O comando `git log` é utilizado para exibir o histórico de commits de um repositório. Ele fornece uma lista dos commits anteriores, mostrando informações como o hash do commit, autor, data, e a mensagem do commit.
  ```bash
    # Mostra o histórico de commits de forma padrão
    git log
    # Exibe o histórico de commits em uma linha por commit, mostrando um resumo compacto
    git log --oneline
    # Mostra os diffs introduzidos por cada commit
    git log -p
    # Filtra commits por autor
    git log --author=<nome>
  ```
![log](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/a1fd2783-3a9b-4b2d-b40d-aff2f8f4b6b3)

`git log`: Ideal para revisar o histórico de commits, entender a sequência de mudanças ao longo do tempo e buscar commits específicos com base em critérios como autor, data, ou mensagens de commit. É uma ferramenta de navegação no histórico do repositório.

### 4.6. git show
O comando `git show` é usado para mostrar detalhes sobre um objeto específico no Git, geralmente um commit. A saída padrão do git show inclui o diff (as diferenças nas mudanças) introduzido por um commit específico, além das informações básicas do commit (como hash, autor, data e mensagem).
  ```bash
    git show
  ```
![gitShow](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/bc44db11-c09e-47c0-8aa3-ecf4954e9359)

`git show`: Mais adequado para inspecionar um commit específico em detalhe. Mostra não só as informações do commit, mas também o conteúdo das mudanças realizadas (diff). É uma ferramenta de inspeção profunda para um commit único.

### 4.7. git help
Abre o manual de ajuda do Git, fornecendo informações detalhadas sobre diversos comandos e conceitos. Um sinal de adição (+) é exibido na frente das linhas que foram adicionadas e um sinal de subtração (-) indica as linhas que foram excluídas.
  ```bash
    git help
  ```
![help](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/151b65d6-f140-4c8c-85a6-37c54f720f7d)

## 5. Estado dos arquivos
No Git, os arquivos em um repositório podem estar em vários estados possíveis. Esses estados refletem a situação dos arquivos em relação ao repositório, à área de preparo (staging area) e ao diretório de trabalho (working directory). Aqui estão os principais estados possíveis dos arquivos no Git:

- **Untracked (Não Rastreado):** Arquivos que existem no diretório de trabalho, mas não estão sendo rastreados pelo Git.
- **Unmodified (Não Modificado):** Arquivos que estão sendo rastreados pelo Git e não sofreram alterações desde o último commit. Esses arquivos estão sincronizados com o repositório.
- **Modified (Modificado):** Arquivos que foram alterados no diretório de trabalho, mas ainda não foram adicionados à área de preparação. Eles estão em um estado de diferença em relação ao último commit.
- **Staged (Preparado ou Indexado):** Arquivos que foram modificados e, em seguida, adicionados à área de preparação usando git add. Esses arquivos estão prontos para serem incluídos no próximo commit.

![arquivos](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/5f8a59bd-cfa2-458a-afbc-49ce00da7a07)

## 6. Clonar um repositório (git clone)
O comando `git clone` é utilizado para copiar um repositório remoto do Git no computador. Para isso, basta navegar até o diretório onde você deseja copiar o repositório e usar o comando `git clone` seguido pela URL do repositório.
  ```bash
    git clone https://github.com/usuario/nome-do-repositorio.git
  ```

## 7. Ignorar arquivos (.gitignore)
*.gitignore* é um arquivo muito importante no mundo do Git, porque impede que arquivos incorretos sejam enviados para o controle de versão. Os arquivos *.gitignore* clichês podem ser encontrados [AQUI](https://github.com/github/gitignore).

## 7. Branches
Um branch no Git é uma ramificação do projeto principal, permitindo que os desenvolvedores trabalhem em funcionalidades novas, correções de bugs ou experimentações de forma isolada do código principal.

### 7.1. Criando um Novo Branch
Criando um novo branch chamado `testing`:
  ```bash
    git branch testing
  ```

### 7.2. Alternando entre Branches
Vamos mudar para o novo branch `testing`:
  ```bash
    git checkout testing
  ```

### 7.3. Criando e Alternando para Branch
Vamos criar e mudar para o novo branch `testing`:
  ```bash
    git checkout -b testing
  ```

### 7.4. Excluindo um Branch
Excluir o branch `testing`:
  ```bash
    git branch -D testing
  ```

### 7.5. Comandos para visualizar a organização dos Branches
  ```bash
    git log --oneline --decorate
    git log --oneline --decorate --graph --all
  ```

### 7.6. Mesclagem (Merge)
- Primeiro, certifique-se de estar na branch em que você deseja realizar a mesclagem. Por exemplo, se você deseja mesclar mudanças da branch `feature` para a branch `main`, você deve estar na branch `main`.
  ```bash
    git checkout main
  ```
- Em seguida, execute o comando `git merge` seguido do nome da branch que você deseja mesclar. Neste caso, a branch `feature`.
  ```bash
    git merge feature
  ```
## X. Observações
1. As pessoas costumam se surpreender quando descobrem que o Git não considera a adição de um diretório vazio como sendo uma alteração. Isso ocorre porque o Git controla apenas as alterações em *arquivos*, não em diretórios.

## Referências
1. [Introduction to Git, GitHub, and Version Control](https://github.com/microsoft/workshop-library/tree/main/full/intro-git-github-version-control)
2. [Entendendo GIT | (não é um tutorial!)](https://youtu.be/6Czd1Yetaac?si=Qs_UwvCp6nE0mVKo)
3. [Introdução ao controle de versão com o Git](https://learn.microsoft.com/pt-br/training/paths/intro-to-vc-git/)
5. [Markdown Basic Syntax](https://www.markdownguide.org/basic-syntax/)
6. [Emoji cheat sheet](https://github.com/ikatyang/emoji-cheat-sheet/tree/master)
