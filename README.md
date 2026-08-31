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

### 1.4. Configure o Code Editor
  ```bash
    # Associar o VSCode com o Git
    git config --global core.editor "code --wait"
   ```

### 1.5. Reveja todas as opções de configuração
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
> :warning: **Observação:** Caso o comando `git init` seja executado em um diretório que já é um repositório Git, o repositório será **reinicializado**. Os arquivos, commits e o histórico existente são preservados. Na prática, raramente é necessário reinicializar manualmente um repositório; isso pode ocorrer, por exemplo, em scripts automatizados ou para recriar alguns arquivos internos do Git.

### 3.1. Listar os remotes criados e validar sua URL
  ```bash
    git remote
    git remote get-url origin
  ```
![remote](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/80ad1795-b51d-4d05-aff3-83c9b901af06)

## 4. Comandos básicos do Git
![basico](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/1c5ff94b-0623-4047-aecd-9792eab3240b)

### 4.1. start .
No Windows, abre no Explorador de Arquivos a pasta atual do terminal.

![start](https://github.com/user-attachments/assets/ddd88370-6b53-4b04-8f1b-f8be0db5fc25)

### 4.2. git status
Este comando mostra o **estado atual** do seu repositório Git, incluindo arquivos modificados, arquivos prontos para serem commitados e outras informações relevantes.
  ```bash
    git status
  ```
![status](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/90bab51a-8b7a-497c-91b5-8b1527633c90)

### 4.3. git log
O comando `git log` é utilizado para **exibir o histórico de commits** de um repositório. Ele fornece uma lista dos commits anteriores, mostrando informações como o hash do commit, autor, data, e a mensagem do commit.
  ```bash
    # Mostra o histórico de commits de forma padrão
    git log

    # Exibe o histórico de commits em uma linha por commit, mostrando um resumo compacto
    git log --oneline

    # Mostra o patch, isto é, as alterações introduzidas por cada commit (mesmo que --patch)
    git log -p

    # Filtra os commits pelo nome ou e-mail do autor
    git log --author="<nome-ou-email>"

    # Mostra um resumo das alterações de cada commit, incluindo os arquivos modificados
    # e a quantidade de linhas adicionadas e removidas
    git log --stat
  ```
![log](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/a1fd2783-3a9b-4b2d-b40d-aff2f8f4b6b3)

> :warning: `git log`: Ideal para revisar o histórico de commits, entender a sequência de mudanças ao longo do tempo e buscar commits específicos com base em critérios como autor, data, ou mensagens de commit. É uma ferramenta de navegação no histórico do repositório.

- Comparação entre `git log` e `git log --oneline`:

![oneline](https://github.com/user-attachments/assets/b68b837d-28c6-4c7c-b4b8-608d39491aad)

- Exemplo de uso do comando `git log --stat`:

![stat](https://github.com/user-attachments/assets/a450d83e-7989-4574-a8a3-29c0fc61f2dd)

- Exemplo de uso do comando `git log -p`:

![patch](https://github.com/user-attachments/assets/40a933aa-6044-476f-a774-2cae71cbd162)

> #### Entendendo a saída do comando `git log -p`

O comando `git log -p` mostra o histórico de commits do repositório e o **patch** associado a cada um deles. Um patch apresenta as diferenças entre a versão anterior e a nova versão dos arquivos modificados pelo commit.

Na figura, a área delimitada pelo retângulo roxo corresponde ao patch do commit cuja mensagem é:

```text
Center content on page
```

Esse commit modificou o arquivo `css/app.css`.

#### A) Identificação do arquivo comparado

```text
diff --git a/css/app.css b/css/app.css
```

Essa linha indica que o Git está comparando duas versões do arquivo `css/app.css`.

Por convenção:

- `a/css/app.css` representa a versão anterior do arquivo;
- `b/css/app.css` representa a nova versão do arquivo.

As letras `a` e `b` não fazem parte do nome original do arquivo. Elas são prefixos utilizados pelo Git para diferenciar as duas versões.

#### B) Identificadores das versões do arquivo

```text
index 07c36fa..3cbd0b8 100644
```

Os valores `07c36fa` e `3cbd0b8` são identificadores abreviados (hash) das versões do conteúdo do arquivo:

- `07c36fa`: conteúdo anterior;
- `3cbd0b8`: conteúdo posterior.

O número `100644` representa o modo do arquivo. Nesse caso, indica que se trata de um arquivo comum e não executável.

#### C) Arquivo anterior e arquivo posterior

```text
--- a/css/app.css
+++ b/css/app.css
```

Essas linhas identificam as duas versões utilizadas na comparação:

- `---` identifica a versão anterior;
- `+++` identifica a nova versão.

É importante não confundir esses três sinais com os sinais usados nas linhas individuais do patch. No conteúdo do patch, um único `+` indica uma linha adicionada e um único `-` indica uma linha removida.

#### D) Cabeçalho do trecho alterado

```text
@@ -38,6 +38,11 @@
```

Essa linha é chamada de **cabeçalho do trecho** ou **cabeçalho do bloco de alterações**. Ela informa a localização e a quantidade de linhas apresentadas em cada versão.

- `-38,6`: na versão anterior, o trecho começa na linha 38 e contém 6 linhas;
- `+38,11`: na nova versão, o trecho começa na linha 38 e contém 11 linhas.

O sinal `-` está relacionado à versão anterior, enquanto o sinal `+` está relacionado à nova versão.

### Numeração das linhas

Na figura, os marcadores coloridos representam a contagem das linhas informada no cabeçalho do trecho:

- os marcadores **amarelos** numeram as 6 linhas da versão anterior;
- os marcadores **verdes** numeram as 11 linhas da nova versão.

As linhas que começam com `+` foram adicionadas pelo commit:

```diff
+.container {
+    margin: auto;
+    max-width: 1300px;
+}
+
```

Essas cinco linhas pertencem apenas à nova versão. Por isso, elas recebem somente a numeração verde.

As linhas que não começam com `+` nem com `-` são chamadas de **linhas de contexto**. Elas não foram modificadas e aparecem apenas para facilitar a compreensão da região em que a alteração ocorreu.

Como as linhas de contexto existem nas duas versões, elas recebem simultaneamente:

- uma numeração amarela, referente à versão anterior;
- uma numeração verde, referente à nova versão.

Neste exemplo, nenhuma linha foi removida. Foram apenas adicionadas cinco linhas. Por isso, o trecho passou de 6 linhas na versão anterior para 11 linhas na nova versão: 11 = 6 + 5

#### Resumo dos sinais do patch

| Símbolo | Significado |
|:---:|---|
| `+` | Linha adicionada na nova versão |
| `-` | Linha removida da versão anterior |
| espaço | Linha de contexto, sem alteração |
| `---` | Identificação do arquivo anterior |
| `+++` | Identificação do novo arquivo |
| `@@` | Delimitação do cabeçalho do trecho alterado |

#### Teclas de atalho
> O Git utiliza um programa chamado `less` como **paginador** (*pager*). O `less` permite navegar pelo conteúdo utilizando o teclado, avançando ou retornando linhas e páginas, além de possibilitar a pesquisa de textos. Enquanto o paginador estiver aberto, o terminal não estará travado: basta pressionar `q` para encerrá-lo e retornar ao prompt de comandos.

Principais teclas de navegação do `less`:

- `↑` ou `k` → subir uma linha
- `↓` ou `j` → descer uma linha
- `Page Up` → subir uma página
- `Page Down` → descer uma página
- `Space` → próxima página
- `b` → página anterior
- `g` → ir para o início
- `G` → ir para o final
- `/texto` → pesquisar um texto
- `n` → próxima ocorrência da busca
- `q` → sair do `git log`

### 4.4. `git show`

O comando `git show` é utilizado para exibir informações detalhadas sobre um objeto do Git, geralmente um commit. Quando executado sem argumentos, ele mostra o commit mais recente:

```bash
git show
```

Por padrão, a saída inclui:

- o identificador (hash) do commit;
- o autor;
- a data;
- a mensagem do commit;
- o patch com as alterações realizadas.

![Saída do comando git show](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/bc44db11-c09e-47c0-8aa3-ecf4954e9359)

Para inspecionar um commit específico, basta informar seu hash:

```bash
git show <hash-do-commit>
```

Por exemplo:

```bash
git show fdf5493
```

O `git log -p <hash>` e o `git show <hash>` exibem basicamente as mesmas informações. A principal diferença é que o `git log -p <hash>` começa no commit indicado e continua exibindo os commits anteriores, enquanto o `git show <hash>` apresenta somente o commit especificado.

O comando também pode ser combinado com diferentes opções:

```bash
# Mostra um resumo dos arquivos e das linhas alteradas
git show --stat <hash-do-commit>

# Mostra as estatísticas e o patch
git show --stat -p <hash-do-commit>

# Ignora alterações relacionadas apenas a espaços em branco
git show -w <hash-do-commit>
```

>  :warning: `git show` é especialmente adequado para analisar um único commit. Ele apresenta tanto as informações básicas do commit quanto o conteúdo das alterações realizadas, permitindo uma inspeção detalhada das mudanças.

#### Resumo dos comandos

Os comandos `git status`, `git log` e `git show` permitem observar diferentes aspectos de um repositório Git. Enquanto `git status` apresenta a **situação atual dos arquivos**, `git log` permite **navegar pelo histórico de commits** e `git show` é utilizado principalmente para **inspecionar detalhadamente um commit específico**.

> **Em resumo:**  
> `git status` → presente | `git log` → histórico | `git show` → um commit em detalhe

### 4.5. git add
O comando `git add` é utilizado para adicionar à **Staging Area** as alterações realizadas no **Working Directory**, preparando-as para serem incluídas no próximo commit.

Antes de realizar um commit, é necessário indicar ao Git quais alterações deverão fazer parte dele. Esse processo de adicionar alterações à Staging Area é chamado de **staging**. Uma alteração presente na Staging Area é chamada de **staged**.

Para adicionar um arquivo específico:

```bash
git add new-text-file.txt
```

Também é possível adicionar vários arquivos de uma só vez:

```bash
git add arquivo1.txt arquivo2.txt
```

O ponto (`.`) representa o diretório atual. Dessa forma, o comando abaixo adiciona à Staging Area todas as alterações do diretório atual e de seus subdiretórios:

```bash
git add .
```

Já a opção `-A` adiciona todas as alterações existentes no repositório:

```bash
git add -A
```

> **Atenção:** ao utilizar `git add .` ou `git add -A`, podem ser adicionadas à Staging Area alterações que você não pretendia incluir no próximo commit. Por isso, é recomendado utilizar `git status` para verificar quais alterações estão na Staging Area.

#### 4.5.1. Unstage

Caso uma alteração seja adicionada à **Staging Area** por engano, é possível removê-la antes de realizar o commit. Esse processo é chamado de **unstage**.

Se o repositório **já possui pelo menos um commit**, para retirar as alterações de um arquivo da Staging Area, utilize:

```bash
git restore --staged <arquivo>
```

Por exemplo:

```bash
git restore --staged new-text-file.txt
```

Esse comando desfaz o efeito do `git add` sobre a Staging Area, sem apagar as alterações realizadas no arquivo. As alterações permanecem no **Working Directory**.

No entanto, se o repositório **ainda não possui nenhum commit**, o Git pode sugerir o comando:

```bash
git rm --cached <arquivo>
```

Por exemplo:

```bash
git rm --cached new-text-file.txt
```

Nesse caso, o arquivo é removido da Staging Area, mas **permanece no Working Directory**. Isso ocorre porque ainda não existe um commit anterior (`HEAD`) que possa ser utilizado pelo `git restore --staged` como referência.

> **Dica:** utilize `git status` para verificar o estado dos arquivos. Além de mostrar quais alterações estão na Staging Area, o Git geralmente indica o comando apropriado para realizar o *unstage*.

![unstage](https://github.com/user-attachments/assets/f8dc7416-9ecd-40c6-8053-e104df187213)

### 4.6. git commit
Este comando confirma as mudanças que foram adicionadas ao índice com o `git add`, criando uma nova revisão no histórico do repositório.
  ```bash
    git commit -m "message"
  ```

#### 4.6.1. git commit --amend --no-edit
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

:link: [How to Write a Git Commit Message](https://chris.beams.io/git-commit)

:link: [Udacity Git Commit Message Style Guide](https://udacity.github.io/git-styleguide/)

### 4.7. git diff
O comando `git diff` é utilizado no Git para comparar alterações entre commits, branches, arquivos ou o estado atual do repositório com versões anteriores. Esse comando é essencial para revisar mudanças no código, identificar diferenças e colaborar de maneira eficiente com outros desenvolvedores.
  ```bash
    # Mostra alterações não preparadas para commit
    git diff
    # Mostra todas as mudanças desde o último commit, incluindo as que estão no índice e as que ainda não estão
    git diff HEAD
    # Mostra alterações feitas no último commit
    git diff HEAD^
  ```

### 4.8. git help
Abre o manual de ajuda do Git, fornecendo informações detalhadas sobre diversos comandos e conceitos. Um sinal de adição (+) é exibido na frente das linhas que foram adicionadas e um sinal de subtração (-) indica as linhas que foram excluídas.
  ```bash
    git help
  ```

![help](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/151b65d6-f140-4c8c-85a6-37c54f720f7d)

### 4.9. git clone
O comando `git clone` é utilizado para criar uma cópia local de um repositório remoto. Ao executar esse comando, o Git baixa todos os arquivos, branches e o histórico de commits do repositório para o seu computador.
  ```bash
    git clone <url-do-repositorio>
  ```

Exemplo:
  ```bash
    git clone https://github.com/udacity/course-git-blog-project
  ```

Após executar o comando, uma nova pasta com o nome do repositório será criada automaticamente no diretório atual.

:warning: Antes de utilizar o `git clone`, verifique se o diretório atual do terminal não está dentro de outro repositório Git, evitando criar repositórios aninhados.

Para verificar o diretório atual:
  ```bash
    pwd
  ```

#### 4.9.1. Evitando repositórios Git aninhados
Antes de utilizar o comando `git clone`, é importante verificar em qual diretório o terminal está localizado. O comando `git clone` cria automaticamente uma nova pasta contendo um repositório Git.

Um erro comum é executar o `git clone` dentro de outro repositório Git já existente, criando um repositório Git dentro de outro.

#### Cenário correto
Você já está em uma pasta comum:
  ```text
    meu-repo/
  ```

E executa:
  ```bash
    git clone https://github.com/user/app.git
  ```

Resultado:
  ```text
    meu-repo/
    └── app/
        └── .git/
  ```
Tudo certo.

#### Cenário errado
Você já está dentro de um repositório Git:
  ```text
    meu-repo/
    └── .git/
  ```

E executa:
  ```bash
    git clone https://github.com/user/app.git
  ```

Resultado:
  ```text
    meu-repo/
    └── .git/
    └── app/
        └── .git/
  ```
Agora existe um Git dentro de outro Git.

#### 4.9.2. Clonando para um diretório com outro nome
Por padrão, o Git cria uma pasta com o mesmo nome do repositório remoto. Porém, é possível definir manualmente o nome da pasta local adicionando um argumento extra ao comando `git clone`.

Você já está em uma pasta comum:
  ```text
    meu-repo/
  ```

E executa:
  ```bash
    git clone https://github.com/user/app.git
  ```

Nesse exemplo, o repositório será clonado para um diretório chamado `app`.

Resultado:
  ```text
    meu-repo/
    └── app/
        └── .git/
  ```

Mas, se executar:
  ```bash
    git clone https://github.com/user/app.git meu_app
  ```

O repositório será clonado para um diretório chamado `meu_app`.

Resultado:
  ```text
    meu-repo/
    └── meu_app/
        └── .git/
  ```

## 5. Estado dos arquivos
No Git, os arquivos em um repositório podem estar em vários estados possíveis. Esses estados refletem a situação dos arquivos em relação ao repositório, à área de preparo (staging area) e ao diretório de trabalho (working directory). Aqui estão os principais estados possíveis dos arquivos no Git:

- **Untracked (Não Rastreado):** Arquivos que existem no diretório de trabalho, mas não estão sendo rastreados pelo Git.
- **Unmodified (Não Modificado):** Arquivos que estão sendo rastreados pelo Git e não sofreram alterações desde o último commit. Esses arquivos estão sincronizados com o repositório.
- **Modified (Modificado):** Arquivos que foram alterados no diretório de trabalho, mas ainda não foram adicionados à área de preparação. Eles estão em um estado de diferença em relação ao último commit.
- **Staged (Preparado ou Indexado):** Arquivos que foram modificados e, em seguida, adicionados à área de preparação usando git add. Esses arquivos estão prontos para serem incluídos no próximo commit.

![arquivos](https://github.com/elias-kento/intro-git-github-version-control/assets/77618691/5f8a59bd-cfa2-458a-afbc-49ce00da7a07)

## 6. Ignorar arquivos (.gitignore)
Nem todos os arquivos de um projeto precisam ser armazenados no repositório. O arquivo `.gitignore`, geralmente localizado na raiz do repositório (mesma pasta que contém o diretório oculto `.git`), permite indicar os arquivos e diretórios que não devem ser rastreados pelo Git.

Cada linha do `.gitignore` representa um nome ou padrão a ser ignorado. Por exemplo:

~~~gitignore
# Ignora todos os arquivos com extensão .log
*.log

# Ignora arquivos JPG diretamente dentro da pasta imagens
imagens/*.jpg

# Ignora a pasta build e todo o seu conteúdo
build/

# Ignora arquivos chamados configuracao.json em qualquer diretório
**/configuracao.json
~~~

:warning: **Atenção:** o `.gitignore` não afeta arquivos que já estão sendo rastreados pelo Git.

:link: Modelos de arquivos `.gitignore` para diferentes linguagens e ferramentas podem ser encontrados no repositório [github/gitignore](https://github.com/github/gitignore).

## 7. Tags
Uma **tag** é um rótulo utilizado para identificar um commit específico no histórico do repositório. Ela permite identificar pontos importantes do projeto com nomes fáceis de reconhecer, como versões lançadas (`v1.0`, `v1.1` e `v2.0`).

Diferentemente de um branch, uma tag normalmente permanece apontando para o mesmo commit. Por esse motivo, é adequada para marcar versões estáveis, entregas ou outros marcos do projeto.

### 7.1. Criando uma Tag Anotada
As **tags anotadas** armazenam informações adicionais, como o nome e o e-mail de quem criou a tag, a data e uma mensagem. Para criar uma tag anotada no commit atual, utilize a opção `-a`:

```bash
git tag -a v1.0
```

Esse comando cria uma tag chamada `v1.0` e abre o editor de texto configurado no Git para que seja inserida uma mensagem.

![tag](https://github.com/user-attachments/assets/2cb9ef3a-3f2c-436a-92de-eb39547e22a2)

No editor, escreva a mensagem da tag em uma linha que não comece com #, por exemplo:

![tag02](https://github.com/user-attachments/assets/3c7158e1-01eb-42bd-b68c-78934cbe8dd6)

Depois:

1. Salve o arquivo com Ctrl + S;
2. Feche a aba ou a janela aberta pelo Git.

Após o fechamento do editor, a tag será criada.

![tag03](https://github.com/user-attachments/assets/f34c4e22-afe6-4b3e-a341-4dd967bbdc6f)

Também é possível informar a mensagem diretamente no comando com a opção `-m`:

```bash
git tag -a v1.0 -m "Primeira versão estável"
```

:warning: Além das tags anotadas, o Git permite criar uma **tag leve** (*lightweight tag*), que funciona apenas como um marcador apontando para determinado commit. Ela é criada sem a opção `-a`:

```bash
git tag v1.0
```

Uma **tag leve** não permite armazenar uma mensagem própria. Ao utilizar a opção `-m`, o Git cria uma tag anotada automaticamente.

### 7.2. Criando uma Tag em um Commit Anterior
Por padrão, a tag é associada ao commit atual (`HEAD`). Para marcar um commit anterior, informe o hash do commit:

```bash
git tag -a v0.9 <hash-do-commit> -m "Versão de testes"
```

Por exemplo:

```bash
git tag -a v0.9 fdf5493 -m "Versão de testes"
```

O hash pode ser localizado utilizando:

```bash
git log --oneline
```

### 7.3. Listando as Tags
Para listar todas as tags existentes no repositório:

```bash
git tag
```

Também é possível filtrar as tags por um padrão. O comando abaixo lista apenas as tags que começam com `v1.`:

```bash
git tag -l "v1.*"
```

### 7.4. Exibindo as Informações de uma Tag
O comando `git show` permite visualizar as informações armazenadas na tag e o commit para o qual ela aponta:

```bash
git show v1.0
```

### 7.5. Enviando Tags para o Repositório Remoto
As tags criadas localmente não são enviadas automaticamente por um `git push` comum. Para enviar uma tag específica ao repositório remoto:

```bash
git push origin v1.0
```

Para enviar todas as tags locais que ainda não existem no repositório remoto:

```bash
git push origin --tags
```

> :warning: Antes de publicar uma tag, verifique se ela aponta para o commit correto. Tags publicadas costumam representar versões permanentes do projeto.

### 7.6. Excluindo uma Tag
Para excluir uma tag apenas do repositório local:

```bash
git tag -d v1.0
```

Se a tag já tiver sido enviada ao repositório remoto, ela também deverá ser excluída remotamente:

```bash
git push origin --delete v1.0
```

> **Em resumo:**  
> `git tag -a` → cria uma tag anotada | `git tag` → lista as tags | `git show` → inspeciona uma tag | `git push origin` → publica uma tag

## 8. Branches
Um **branch** é uma ramificação do histórico do projeto. Ele permite desenvolver novas funcionalidades, corrigir erros ou realizar experimentos de forma isolada, sem alterar imediatamente o branch principal.

Cada branch aponta para um commit específico. Quando um novo commit é realizado no branch atual, esse apontador avança para o novo commit.

### 8.1. Listando os Branches
Para listar os branches existentes no repositório:

```bash
git branch
```

O branch atual é identificado por um asterisco (`*`):

```text
  main
* testing
```

Nesse exemplo, `testing` é o branch atualmente selecionado.

### 8.2. Criando um Novo Branch
Para criar um branch chamado `testing` a partir do commit atual:

```bash
git branch testing
```

Esse comando cria o branch, mas não muda automaticamente para ele.

Também é possível criar um branch a partir de um commit anterior. Para isso, informe o hash do commit:

```bash
git branch testing <hash-do-commit>
```

Por exemplo:

```bash
git branch testing fdf5493
```

O hash pode ser localizado utilizando:

```bash
git log --oneline
```

Para criar um branch e mudar para ele em um único comando, utilize:

```bash
git checkout -b testing
```

Esse comando equivale a executar:

```bash
git branch testing
git checkout testing
```

### 8.3. Alternando entre Branches
Para mudar para o branch `testing`:

```bash
git checkout testing
```

Ao alternar entre branches, o Git atualiza os arquivos do **Working Directory** para representar o estado do branch selecionado.

> :warning: Antes de mudar de branch, verifique o estado do repositório com `git status`. Alterações ainda não confirmadas podem impedir a troca de branch ou permanecer no **Working Directory** após a mudança.

### 8.4. Excluindo um Branch
Antes de excluir um branch, é importante verificar se seus commits já foram incorporados ao branch em que você está trabalhando. Por exemplo, se as alterações do branch `testing` já foram incorporadas ao branch `main`, o branch `testing` pode ser excluído sem que essas alterações sejam perdidas.

Primeiro, mude para outro branch, pois o Git não permite excluir o branch atualmente selecionado:

```bash
git checkout main
```

Em seguida, para excluir o branch `testing` de maneira segura:

```bash
git branch -d testing
```

A opção `-d` somente permite a exclusão se os commits do branch `testing` já tiverem sido incorporados ao branch atual. Caso ainda existam commits não incorporados, o Git impedirá a exclusão para evitar que essas alterações sejam perdidas.

Para forçar a exclusão, mesmo que existam commits ainda não incorporados:

```bash
git branch -D testing
```

> :warning: A opção `-D` força a exclusão do branch e pode dificultar a recuperação de commits que ainda não tenham sido incorporados a outro branch. Utilize-a apenas quando tiver certeza de que essas alterações não serão mais necessárias.

### 8.5. Visualizando a Organização dos Branches
O comando abaixo mostra o histórico resumido e indica os branches e as tags associados aos commits:

```bash
git log --oneline --decorate
```

Por padrão, o `git log` apresenta somente os commits acessíveis a partir do branch atual. Para representar graficamente as ramificações e mostrar todos os branches:

```bash
git log --oneline --decorate --graph --all
```

![git_log](https://github.com/user-attachments/assets/cb2753a0-d1a2-477b-92de-4478eb6a914a)

Nesse comando:

- `--oneline` exibe cada commit em uma única linha;
- `--decorate` mostra os nomes dos branches e das tags;
- `--graph` representa graficamente as ramificações;
- `--all` inclui todos os branches na visualização.

### 8.6. Mesclagem (*Merge*)
A mesclagem permite incorporar as alterações de um branch em outro.

Por exemplo, para incorporar as alterações do branch `feature` ao branch `main`, primeiro mude para o branch que receberá as alterações:

```bash
git checkout main
```

Em seguida, execute `git merge`, indicando o branch cujas alterações serão incorporadas:

```bash
git merge feature
```

Nesse exemplo, os commits do branch `feature` são incorporados ao histórico do branch `main`.

Após verificar que a mesclagem foi concluída corretamente, o branch `feature` poderá ser excluído:

```bash
git branch -d feature
```

> **Em resumo:**  
> `git branch` → lista os branches | `git branch <nome>` → cria um branch | `git checkout <nome>` → muda de branch | `git checkout -b <nome>` → cria e muda de branch | `git branch -d <nome>` → exclui um branch com segurança | `git merge <nome>` → incorpora outro branch ao branch atual
  
## X. Observações
1. As pessoas costumam se surpreender quando descobrem que o Git não considera a adição de um diretório vazio como sendo uma alteração. Isso ocorre porque o Git controla apenas as alterações em *arquivos*, não em diretórios.

## Referências
1. [Introduction to Git, GitHub, and Version Control](https://github.com/microsoft/workshop-library/tree/main/full/intro-git-github-version-control)
2. [Entendendo GIT | (não é um tutorial!)](https://youtu.be/6Czd1Yetaac?si=Qs_UwvCp6nE0mVKo)
3. [Introdução ao controle de versão com o Git](https://learn.microsoft.com/pt-br/training/paths/intro-to-vc-git/)
5. [Markdown Basic Syntax](https://www.markdownguide.org/basic-syntax/)
6. [Emoji cheat sheet](https://github.com/ikatyang/emoji-cheat-sheet/tree/master)
