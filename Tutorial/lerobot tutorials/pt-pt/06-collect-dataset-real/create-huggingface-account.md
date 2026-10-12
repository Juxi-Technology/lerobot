[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | Português (PT)

# Registar uma conta Hugging Face (opcional)

## Configurar um espelho do HuggingFace na China

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Adicione isto no final do ficheiro
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# Saída
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# Adicione isto no final do ficheiro
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Saída
# https://hf-mirror.com
```



## Criar um token

https://huggingface.co/settings/tokens

![A imagem mostra a interface da plataforma Hugging Face, com a área do avatar e da informação de perfil do utilizador à esquerda e o conteúdo de modelos e conjuntos de dados à direita. À direita, uma seta vermelha aponta para a opção "Access Tokens", localizada em "Settings". O contexto menciona que, após criar um token, é necessário utilizar as teclas para cima/para baixo para selecionar e colar a chave; esta imagem apresenta visualmente onde se encontra "Access Tokens" na plataforma, está relacionada com o passo de registar o token após criá-lo, e é a interface para definir as permissões relevantes após criar um token.](../../en/images/d34-01.png)

![A imagem mostra a página Access Tokens da plataforma Hugging Face. Na barra de navegação esquerda, a opção "Access Tokens" está selecionada. Do lado direito mostra a informação dos User Access Tokens, incluindo nome, valor, data da última atualização, data da última utilização e permissões. No canto superior direito há um botão "Create new token" realçado com uma seta vermelha. Esta imagem está relacionada com a secção "Criar um token", apresentando visualmente onde criar um novo token e ajudando os utilizadores a compreender a página específica para criar um token no Hugging Face.](../../en/images/d34-02.png)

![Esta imagem mostra a interface para criar um novo token de acesso na plataforma Hugging Face, com o título da página "Create new Access Token". É necessário definir três itens: selecionar o tipo de token designado "Write", definir o nome como "so-arm101" e depois clicar no botão "Create token". Estas operações estão assinaladas com retângulos vermelhos e os números 1, 2 e 3 para orientar os utilizadores na criação de um token com permissão de escrita. Isto corresponde aos passos para criar um token, um passo essencial para obter a chave necessária para associar o Hugging Face.](../../en/images/d34-03.png)

![Esta imagem é a página de gravação do Access Token de uma conta Hugging Face; o seu conteúdo central é um lembrete para guardar corretamente o valor do token, porque depois de fechar a janela pop-up já não pode ser visualizado e, se for perdido, terá de ser criado novamente. A página mostra a chave de acesso gerada hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, com o nome so-arm101 e permissão de escrita. Há um botão "Copy" apontado por uma seta vermelha e realçado com um retângulo vermelho, utilizado para copiar o token, e um botão "Done" no canto inferior direito para concluir a operação atual. Esta imagem corresponde ao passo de registar ou associar o token da conta Hugging Face.](../../en/images/d34-04.png)

## Registar o token

Por exemplo, o meu é:

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## Associar o token

```Shell
hf auth login

hf auth whoami
```

![A imagem mostra o início de sessão com um token da Hugging Face na linha de comandos. Após introduzir o comando "hf auth login", aparece o prompt "? How would you like to log in?" e é apresentada a opção "Paste an access token". Isto está relacionado com o passo "Associar o token", indicando que, após selecionar e colar a chave com as teclas para cima/para baixo, o ecrã de início de sessão pergunta como pretende iniciar sessão, altura em que pode escolher colar um token de acesso para iniciar sessão e concluir a associação do token da Hugging Face.](../../en/images/d34-05.png)

> Utilize as teclas para cima/para baixo para selecionar e colar a chave

![Esta imagem mostra a operação de uma conta Hugging Face na linha de comandos, com um retângulo vermelho a realçar que o token atualmente ativo é "so-arm101-upload", que foi guardado no caminho especificado. A linha de comandos terminou a sessão e voltou a iniciá-la; o sistema avisou que iniciar sessão na Hugging Face requer um token e, após colar o token com êxito, mostrou a permissão do token como write, depois concluiu a gravação e, por fim, apresentou a informação do token atualmente ativo. Este conteúdo corresponde ao passo "Associar o token".](../../en/images/d34-06.png)

> Ecrã de sucesso

## Criar um repositório de conjunto de dados

<grid>
<column width-ratio="0.434605">
![Esta imagem mostra um menu pendente na interface do Hugging Face; no topo o utilizador com sessão iniciada é apresentado como "juxi-admin", e o menu lista várias opções de funções, incluindo novo modelo, novo espaço e novo bucket. A opção realçada com um retângulo vermelho é "New Dataset", correspondendo ao passo "Criar um repositório de conjunto de dados". Esta opção é o ponto de entrada para criar um repositório de conjunto de dados, através do qual os utilizadores podem concluir a criação de um repositório de conjunto de dados.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![A imagem mostra a interface para criar um repositório de conjunto de dados no Hugging Face. Em "Dataset name" está introduzido o valor "so-arm101", a "License" está definida como "apache-2.0", e a opção "Public" está selecionada, o que significa que qualquer pessoa pode ver este conjunto de dados e só o próprio pode fazer commits. Esta imagem está relacionada com o passo "Criar um repositório de conjunto de dados", mostrando um dos ecrãs de configuração e ajudando os utilizadores a compreender a informação essencial a preencher ao criar um.](../../en/images/d34-08.png)
</column>
</grid>

![A imagem mostra a página do conjunto de dados "so - arm101" na plataforma Hugging Face. No topo há uma barra de pesquisa e uma barra de navegação que dá acesso a secções como Models e Datasets. Ao centro mostra informação do conjunto de dados, incluindo a License apache - 2.0 e um tamanho de ficheiro de 2.53 kB. Abaixo há uma secção "Getting started with your dataset", que sugere adicionar metadados e completar o cartão do conjunto de dados para melhorar a sua descobribilidade, e oferece a opção de editar o cartão do conjunto de dados. À direita há os botões "Copy to bucket" e "Edit dataset card", e um registo da transferência de ficheiros do conjunto de dados. Esta imagem está relacionada com a criação de um repositório de conjunto de dados, mostrando a interface de gestão do conjunto de dados.](../../en/images/d34-09.png)
