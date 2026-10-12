[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | Português (BR) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# Configuração de um ambiente de treinamento com GPU em nuvem

## Desative o proxy de rede do seu computador

Caso contrário, você pode não conseguir abrir a linha de comando do Jupyter

## Faça login na plataforma de GPU em nuvem Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## Inicie uma instância de GPU em nuvem

<grid>
<column width-ratio="0.597692">
![Esta imagem mostra a tela de seleção de instâncias de GPU em nuvem da plataforma Featurize, exibindo principalmente opções de instâncias de GPU em nuvem com diferentes configurações. A opção marcada com uma caixa vermelha é uma instância de GPU em nuvem RTX 5090, listada como 2.0 disponíveis a um preço de pagamento conforme o uso de 3 CNY/hora, com 32.0 GB de memória de GPU, um processador AMD EPYC 9354 de 38 núcleos e 128 GB de RAM. Abaixo dela estão os botões "Start Using" e "Reserve", com uma seta vermelha apontando para "Start Using", correspondendo à orientação "Inicie uma instância de GPU em nuvem" do documento.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![Esta imagem mostra a tela de seleção de imagem da plataforma Featurize. Ela exibe uma aba "Select Image", com três sub-abas abaixo: "Official Images", "My Images" e "Popular Images". Na aba "Official Images", a imagem PyTorch 2 está destacada com uma caixa e uma seta vermelhas; ela tem 14.5 GB de tamanho, foi usada 19.001 vezes e está rotulada como "Official". A imagem está intimamente relacionada ao contexto, que descreve clicar em "JupyterLab" e enviar o código e os conjuntos de dados após iniciar uma instância de GPU em nuvem; esta captura de tela mostra a opção de imagem oficial na etapa de seleção de imagem, usada para a configuração e o ajuste do ambiente subsequentes.](../../en/images/d45-02.png)
</column>
</grid>

![Esta imagem mostra o console de uma instância de GPU em nuvem, correspondendo à etapa "Inicie uma instância de GPU em nuvem" do documento e mostrando as operações disponíveis depois que a instância é iniciada. Ela exibe a configuração de uma instância RTX 5090, incluindo os parâmetros de GPU, CPU, memória e disco, bem como a duração do aluguel, a forma de cobrança e o custo da instância. Uma seta vermelha e uma caixa vermelha destacam o botão "Open Workspace", incentivando o usuário a clicá-lo para prosseguir com as operações no JupyterLab e enviar o código e o conjunto de dados.](../../en/images/d45-03.png)

![Esta imagem mostra a interface do JupyterLab. À esquerda está a área de gerenciamento de arquivos, com as abas "Instances", "Files" e "Terminal", e a aba "Files" atualmente selecionada. À direita está a área Launcher, mostrando opções como Notebook, Console e Python 3 (ipykernel). Uma seta vermelha na imagem aponta para a aba "Files" na área de gerenciamento de arquivos à esquerda, destacando esse local e ecoando o contexto — "clique em JupyterLab abaixo; há um botão de upload no canto superior esquerdo onde você pode enviar o código e os conjuntos de dados" — guiando o usuário pelas operações relacionadas a arquivos no JupyterLab.](../../en/images/d45-04.png)

> Clique em "JupyterLab" abaixo; há um botão de upload no canto superior esquerdo onde você pode enviar o código e os conjuntos de dados

## Instale e configure o ambiente

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

# Pule a instalação se você não for enviar para o HuggingFace e não precisar do wandb
```

> Se o `training` estava faltando quando você instalou o modelo, é preciso instalá-lo adicionalmente
> 
> `pip install -e ".[training]"`

## Faça login no wandb

```Shell
wandb login
Copy and paste the API Key, then press Enter
```

![Esta imagem mostra a tela de login do wandb para o projeto LeRobot, registrando os detalhes do processo de login. Ela começa iniciando o login do wandb, pedindo ao usuário que visite um determinado URL para encontrar a chave de API e que cole a chave e pressione Enter para enviá-la. Também mostra que nenhum arquivo netrc foi encontrado e que a chave de API está sendo adicionada ao caminho correspondente do arquivo netrc, após o que o login é concluído e o usuário conectado é exibido como tommyzihao, junto com um comando para forçar um novo login. Esta imagem corresponde à etapa "Faça login no wandb", apresentando o processo e o resultado do login.](../../en/images/d45-05.png)

## Monte o conjunto de dados

```Shell
Copy the instance download command, something like:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

O conjunto de dados aparece no diretório `~`

## Ajuste a frequência de salvamento dos pesos (opcional)

Abra `lerobot/src/lerobot/configs/train.py`

Altere save_freq de 20_000 para 5_000

Assim você obtém os arquivos de peso do modelo mais cedo durante o treinamento
