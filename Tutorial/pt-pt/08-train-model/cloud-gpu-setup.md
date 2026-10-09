[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | Português (PT)

# Configurar um Ambiente de Treino com GPU na Nuvem

## Desativar o Proxy de Rede do Seu Computador

Caso contrário, poderá não conseguir abrir a linha de comandos do Jupyter

## Iniciar Sessão na Plataforma de GPU na Nuvem Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## Iniciar uma Instância de GPU na Nuvem

<grid>
<column width-ratio="0.597692">
![Esta imagem é o ecrã de seleção de instâncias de GPU na nuvem da plataforma Featurize, mostrando sobretudo opções de instâncias de GPU na nuvem com diferentes configurações. A opção assinalada com uma caixa vermelha é uma instância de GPU na nuvem RTX 5090, listada como 2.0 disponíveis a um preço de pagamento conforme o uso de 3 CNY/hora, com 32.0 GB de memória de GPU, um processador AMD EPYC 9354 de 38 núcleos e 128 GB de RAM. Por baixo encontram-se os botões "Start Using" e "Reserve", com uma seta vermelha a apontar para "Start Using", em correspondência com a orientação "Iniciar uma Instância de GPU na Nuvem" do documento.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![Esta imagem mostra o ecrã de seleção de imagem da plataforma Featurize. Apresenta um separador "Select Image", com três subseparadores por baixo: "Official Images", "My Images" e "Popular Images". Sob o separador "Official Images", a imagem PyTorch 2 está realçada com uma caixa e uma seta vermelhas; tem 14.5 GB de tamanho, foi utilizada 19,001 vezes e está etiquetada como "Official". A imagem está estreitamente relacionada com o contexto, que descreve clicar em "JupyterLab" e carregar código e conjuntos de dados depois de iniciar uma instância de GPU na nuvem; esta captura de ecrã mostra a opção de imagem oficial no passo de seleção de imagem, utilizada para a subsequente preparação e configuração do ambiente.](../../en/images/d45-02.png)
</column>
</grid>

![Esta imagem mostra a consola de uma instância de GPU na nuvem, correspondendo ao passo "Iniciar uma Instância de GPU na Nuvem" do documento e mostrando as operações disponíveis depois de a instância ser iniciada. Apresenta a configuração de uma instância RTX 5090, incluindo os parâmetros de GPU, CPU, memória e disco, bem como a duração do aluguer da instância, o método de faturação e o custo. Uma seta vermelha e uma caixa vermelha realçam o botão "Open Workspace", sugerindo ao utilizador que clique nele para avançar para as operações do JupyterLab e carregar o código e o conjunto de dados.](../../en/images/d45-03.png)

![Esta imagem mostra a interface do JupyterLab. À esquerda está a área de gestão de ficheiros, com separadores para "Instances", "Files" e "Terminal", estando o separador "Files" atualmente selecionado. À direita está a área Launcher, mostrando opções como Notebook, Console e Python 3 (ipykernel). Uma seta vermelha na imagem aponta para o separador "Files" da área de gestão de ficheiros à esquerda, realçando essa localização e fazendo eco do contexto — "clique em JupyterLab abaixo; há um botão de carregamento no canto superior esquerdo onde pode carregar código e conjuntos de dados" — guiando o utilizador nas operações relacionadas com ficheiros no JupyterLab.](../../en/images/d45-04.png)

> Clique em "JupyterLab" abaixo; há um botão de carregamento no canto superior esquerdo onde pode carregar código e conjuntos de dados

## Instalar e Configurar o Ambiente

```Shell
conda create -y -n lerobot python=3.12
conda activate lerobot
conda install ffmpeg=7.1.1 -c conda-forge -y
# git clone https://github.com/Seeed-Projects/lerobot.git ~/work/Lerobot
git clone https://github.com/huggingface/lerobot.git
cd lerobot
pip install -e ".[pi]"
pip install wandb --upgrade
# export HF_ENDPOINT=https://hf-mirror.com
hf auth login

# Ignore a instalação se não estiver a carregar para o HuggingFace e não precisar do wandb
```

> Se `training` estava em falta quando instalou o modelo, precisa de o instalar adicionalmente
> 
> `pip install -e ".[training]"`

## Iniciar Sessão no wandb

```Shell
wandb login
Copie e cole a API Key e, em seguida, prima Enter
```

![Esta imagem mostra o ecrã de início de sessão do wandb para o projeto LeRobot, registando os detalhes do processo de início de sessão. Começa por iniciar o login no wandb, pedindo ao utilizador que visite um determinado URL para encontrar a API key e que cole a chave e prima Enter para a submeter. Mostra também que não foi encontrado nenhum ficheiro netrc e que a API key está a ser adicionada ao caminho do ficheiro netrc correspondente, após o que o início de sessão é concluído e o utilizador com sessão iniciada é apresentado como tommyzihao, juntamente com um comando para forçar um novo início de sessão. Esta imagem corresponde ao passo "Iniciar Sessão no wandb", apresentando o processo e o resultado do início de sessão.](../../en/images/d45-05.png)

## Montar o Conjunto de Dados

```Shell
Copie o comando de descarregamento da instância, algo como:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

O conjunto de dados aparece sob o diretório `~`

## Ajustar a Frequência de Guardar os Pesos (Opcional)

Abra `lerobot/src/lerobot/configs/train.py`

Altere save_freq de 20_000 para 5_000

Assim obtém os ficheiros de pesos do modelo mais cedo no treino
