# intro-git-github-version-control
Repositório com comandos básicos do Git.

## 1. Configurando o Git

### 1.1. Configure seu perfil do Git
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

### 1.2. Configure a cor de saída da interface do usuário
  ```bash
    # Garante que a saída do Git esteja colorida
    git config --global color.ui auto
   ```

### 1.3. Reveja todas as opções de configuração
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

![gitBash](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/865d15a6-a227-4511-b33c-61da2af74149)

## 3. Criar um novo repositório na linha de comando
  ```bash
    echo "# teste" >> README.md # Criar o arquivo README.md com cabeçalho "# teste"
    git init # Inicializa um novo repositório Git no diretório atual
    git add README.md # Adiciona o arquivo README.md a "Staging Area" para ser preparado para o commit
    git commit -m "first commit" # Realiza o commit com uma mensagem de commit "first commit"
    git branch -M main # Renomeia a branch padrão de "master" para "main"
    git remote add origin https://github.com/elias-kento/teste.git # Adiciona um repositório remoto chamado "origin" com o URL fornecido
    git push -u origin main # Envia as mudanças do repositório local para o repositório remoto "origin" na branch "main"
  ```
## 4. Revisando o Histórico do Repositório


## Referências
1. [Introduction to Git, GitHub, and Version Control](https://github.com/microsoft/workshop-library/tree/main/full/intro-git-github-version-control)
2. [Entendendo GIT | (não é um tutorial!)](https://youtu.be/6Czd1Yetaac?si=Qs_UwvCp6nE0mVKo)
