# intro-git-github-version-control
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
![gitConfig](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/55953a92-7e43-43d8-a347-1f4e1e38bd45)

## 2. Trabalhando com um Repositório Local

O Git acompanha as mudanças no seu código-fonte, permite o versionamento e suporta o desenvolvimento não linear através de milhares de ramificações paralelas sem a necessidade de internet.

### 2.1. Inicializando um Repositório Git Local

1. Em sua máquina local, crie uma nova pasta vazia.
2. Clique com o botão direito dentro da pasta e selecione **Git Bash Here** nas opções.

![open](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/a3a8fb58-8a6c-4df0-8a44-b1dc96a20909)

## 3. Criar um novo repositório na linha de comando
  ```bash
    # Criar o arquivo README.md com cabeçalho "# teste"
    echo "# teste" >> README.md
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

### 4.3. git commit
Este comando confirma as mudanças que foram adicionadas ao índice com o `git add`, criando uma nova revisão no histórico do repositório.
  ```bash
    git commit -m "message"
  ```

### 4.4. git log
Mostra o histórico de commits do repositório Git, exibindo informações como autor, data e mensagem de cada commit.
  ```bash
    git log
  ```
![log](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/a1fd2783-3a9b-4b2d-b40d-aff2f8f4b6b3)

### 4.5. git help
Abre o manual de ajuda do Git, fornecendo informações detalhadas sobre diversos comandos e conceitos.
  ```bash
    git help
  ```
![help](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/151b65d6-f140-4c8c-85a6-37c54f720f7d)

## 5. Estado dos arquivos
No Git, os arquivos em um repositório podem estar em vários estados possíveis. Esses estados refletem a situação dos arquivos em relação ao repositório, à área de preparo (staging area) e ao diretório de trabalho (working directory). Aqui estão os principais estados possíveis dos arquivos no Git:

1. **Untracked (Não Rastreado):** Arquivos que existem no diretório de trabalho, mas não estão sendo rastreados pelo Git.
2. **Unmodified (Não Modificado):** Arquivos que estão sendo rastreados pelo Git e não sofreram alterações desde o último commit. Esses arquivos estão sincronizados com o repositório.
3. **Modified (Modificado):** Arquivos que foram alterados no diretório de trabalho, mas ainda não foram adicionados à área de preparação. Eles estão em um estado de diferença em relação ao último commit.
4. **Staged (Preparado ou Indexado):** Arquivos que foram modificados e, em seguida, adicionados à área de preparação usando git add. Esses arquivos estão prontos para serem incluídos no próximo commit.



## 6. Revisando o Histórico do Repositório


## Referências
1. [Introduction to Git, GitHub, and Version Control](https://github.com/microsoft/workshop-library/tree/main/full/intro-git-github-version-control)
2. [Entendendo GIT | (não é um tutorial!)](https://youtu.be/6Czd1Yetaac?si=Qs_UwvCp6nE0mVKo)
