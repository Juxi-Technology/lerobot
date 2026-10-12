[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | Português (BR) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# Bugs comuns e correções

## A captura da câmera falha

![Esta imagem mostra a saída do terminal quando o código do robô LeRobot é executado. Os logs `INFO` mostram a abertura da câmera OpenCV e a desconexão do Follower; o log `ERROR` aponta que, no arquivo `camera_opencv.py`, a função `read` lançou um `RuntimeError` por causa de `OpenCVCamera(0) read failed`. A imagem está relacionada ao problema "A captura da câmera falha", mostrando visualmente o problema que aparece quando o código é executado e ajudando a explicar a causa específica da falha na captura da câmera.](../../en/images/d65-01.png)

Verifique se o cabo da câmera de pulso está solto, especialmente a extremidade próxima à câmera — esse conector é muito propenso a mau contato

## A câmera se desconecta

![Esta imagem mostra a interface de execução do código /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py. No topo ela mostra o horário, o ID do processo e outras informações; abaixo há caminhos de código e mensagens de erro como /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py e "INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.". A parte principal é "raise TimeoutError" e "TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.", indicando que a captura da câmera falhou. A imagem está relacionada ao problema "A captura da câmera falha", mostrando visualmente o erro.](../../en/images/d65-02.png)

Reinicie a linha de comando

## Problema de comunicação com o servo 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![Esta imagem mostra o seguinte.](../../en/images/d65-03.png)

A correção: altere todo `num_retry` no código em `lerobot/src/lerobot/motors/motors_bus.py` para 99, especialmente o da linha que gera o erro

![Esta imagem mostra o conteúdo do arquivo de código `motors_bus.py` no projeto LeRobot. O método `write` da classe `MotorsBusABC` está destacado, com a variável `num_retry` alterada para `99`. A imagem está relacionada à seção "Problema de comunicação com o servo 1", correspondendo à correção de alterar todo `num_retry` no código em `lerobot/src/lerobot/motors/motors_bus.py` para 99, especialmente o da linha que gera o erro.](../../en/images/d65-04.png)

## Problema de comunicação com o servo 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![Esta imagem mostra uma sessão de linha de comando no terminal zsh no macOS. O terminal mostra vários caminhos de arquivo e números de linha de código, como `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`. A linha 587 do arquivo `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` lança um `ConnectionError`, relatando uma falha na escrita de `Torque_Enable` no id=1 sem status packet. A imagem está relacionada ao conteúdo "Problema de comunicação com o servo 2", mostrando visualmente a execução do código no momento do erro.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![Esta imagem mostra uma sessão de linha de comando no terminal zsh no macOS. O terminal mostra vários caminhos de arquivo e números de linha de código, como `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`. Aqui, `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

Solução: recalibre o braço robótico
