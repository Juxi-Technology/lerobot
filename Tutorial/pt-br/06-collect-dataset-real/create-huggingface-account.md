[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | Português (BR) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Registrar uma Conta no Hugging Face (Opcional)

## Configurar um Espelho do HuggingFace Baseado na China

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Adicione isto no final do arquivo
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

# Adicione isto no final do arquivo
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Saída
# https://hf-mirror.com
```



## Criar um Token

https://huggingface.co/settings/tokens

![A imagem mostra a interface da plataforma Hugging Face, com o avatar do usuário e a área de informações de perfil à esquerda e conteúdo de modelos e conjuntos de dados à direita. À direita, uma seta vermelha aponta para a opção "Access Tokens", localizada em "Settings". O contexto menciona que, após criar um token, é preciso usar as teclas para cima/para baixo para selecionar e colar a chave; esta imagem apresenta visualmente onde está "Access Tokens" na plataforma, relaciona-se à etapa de registrar o token após criá-lo, e é a interface para configurar as permissões relevantes após criar um token.](../../en/images/d34-01.png)

![A imagem mostra a página Access Tokens da plataforma Hugging Face. Na barra de navegação esquerda, a opção "Access Tokens" está selecionada. O lado direito mostra as informações de User Access Tokens, incluindo nome, valor, data da última atualização, data do último uso e permissões. No canto superior direito há um botão "Create new token" destacado com uma seta vermelha. Esta imagem está relacionada à seção "Criar um Token", apresentando visualmente onde criar um novo token e ajudando os usuários a entender a página específica para criar um token no Hugging Face.](../../en/images/d34-02.png)

![Esta imagem mostra a interface para criar um novo token de acesso na plataforma Hugging Face, com o título da página "Create new Access Token". Três itens precisam ser definidos: selecionar o tipo de token chamado "Write", definir o nome como "so-arm101" e, em seguida, clicar no botão "Create token". Essas operações estão marcadas com caixas vermelhas e os números 1, 2 e 3 para orientar os usuários na criação de um token com permissão de escrita. Isso corresponde às etapas para criar um token, uma etapa-chave para obter a chave necessária para vincular o Hugging Face.](../../en/images/d34-03.png)

![Esta imagem é a página de salvamento do Access Token de uma conta Hugging Face; seu conteúdo central é um lembrete para guardar bem o valor do token, porque depois de fechar a janela pop-up ele não poderá mais ser visualizado, e, se for perdido, deverá ser recriado. A página mostra a chave de acesso gerada hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, com o nome so-arm101 e permissão de escrita. Há um botão "Copy" apontado por uma seta vermelha e destacado com uma caixa vermelha, usado para copiar o token, e um botão "Done" no canto inferior direito para concluir a operação atual. Esta imagem corresponde à etapa de registrar ou vincular o token da conta Hugging Face.](../../en/images/d34-04.png)

## Registrar o Token

Por exemplo, o meu é:

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## Vincular o Token

```Shell
hf auth login

hf auth whoami
```

![A imagem mostra o login com um token do Hugging Face na linha de comando. Após digitar o comando "hf auth login", aparece o prompt "? How would you like to log in?" e a opção "Paste an access token" é exibida. Isso está relacionado à etapa "Vincular o Token", indicando que, após selecionar e colar a chave com as teclas para cima/para baixo, a tela de login pergunta como você gostaria de fazer login, momento em que você pode escolher colar um token de acesso para fazer login e concluir a vinculação do token do Hugging Face.](../../en/images/d34-05.png)

> Use as teclas para cima/para baixo para selecionar e colar a chave

![Esta imagem mostra a operação de uma conta Hugging Face na linha de comando, com uma caixa vermelha destacando que o token ativo no momento é "so-arm101-upload", que foi salvo no caminho especificado. A linha de comando fez logout e depois login novamente; o sistema avisou que fazer login no Hugging Face requer um token e, após colar o token com sucesso, mostrou a permissão do token como write, então concluiu o salvamento e, por fim, exibiu as informações do token ativo no momento. Este conteúdo corresponde à etapa "Vincular o Token".](../../en/images/d34-06.png)

> Tela de sucesso

## Criar um Repositório de Dataset

<grid>
<column width-ratio="0.434605">
![Esta imagem mostra um menu suspenso na interface do Hugging Face; no topo, o usuário conectado é exibido como "juxi-admin", e o menu lista várias opções de funções, incluindo new model, new space e new bucket. A opção destacada com uma caixa vermelha é "New Dataset", correspondendo à etapa "Criar um Repositório de Dataset". Esta opção é o ponto de entrada para criar um repositório de conjunto de dados, por meio do qual os usuários podem concluir a criação de um repositório de conjunto de dados.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![A imagem mostra a interface para criar um Repositório de Dataset no Hugging Face. Em "Dataset name", o valor "so-arm101" está inserido, "License" está definida como "apache-2.0", e a opção "Public" está selecionada, o que significa que qualquer pessoa pode visualizar este Dataset e somente você pode fazer commits. Esta imagem está relacionada à etapa "Criar um Repositório de Dataset", mostrando uma das telas de configuração e ajudando os usuários a entender as informações-chave a serem preenchidas ao criar um.](../../en/images/d34-08.png)
</column>
</grid>

![A imagem mostra a página do conjunto de dados "so - arm101" na plataforma Hugging Face. No topo há uma barra de pesquisa e uma barra de navegação, permitindo acesso a seções como Models e Datasets. No meio, ela mostra as informações do conjunto de dados, incluindo License apache - 2.0 e um tamanho de arquivo de 2.53 kB. Abaixo há uma seção "Getting started with your dataset", sugerindo que você adicione metadados e complete o cartão do conjunto de dados para melhorar a descoberta, e oferecendo a opção de editar o cartão do conjunto de dados. À direita há os botões "Copy to bucket" e "Edit dataset card", e um registro de download de arquivos do conjunto de dados. Esta imagem está relacionada à criação de um Repositório de Dataset, mostrando a interface de gerenciamento do conjunto de dados.](../../en/images/d34-09.png)
