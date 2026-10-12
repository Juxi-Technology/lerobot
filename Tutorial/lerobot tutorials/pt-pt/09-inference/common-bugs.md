[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | Português (PT)

# Erros Comuns e Correções

## A captura da câmara falha

![Esta imagem mostra a saída do terminal quando o código do robô LeRobot é executado. Os registos `INFO` mostram a abertura da câmara OpenCV e a desconexão do Follower; o registo `ERROR` assinala que, no ficheiro `camera_opencv.py`, a função `read` lançou um `RuntimeError` devido a `OpenCVCamera(0) read failed`. A imagem relaciona-se com o problema "A captura da câmara falha", mostrando visualmente o problema que surge quando o código é executado e ajudando a explicar a causa específica da falha de captura da câmara.](../../en/images/d65-01.png)

Verifique se o cabo da câmara de pulso está solto, especialmente a extremidade junto à câmara — esse conector tem muita tendência a fazer mau contacto

## A câmara desliga-se

![Esta imagem mostra a interface de execução do código /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py. No topo mostra a hora, o ID do processo e outra informação; por baixo estão caminhos de código e mensagens de erro como /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py e "INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.". A parte essencial é "raise TimeoutError" e "TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.", indicando que a captura da câmara falhou. A imagem relaciona-se com o problema "A captura da câmara falha", mostrando visualmente o erro.](../../en/images/d65-02.png)

Reinicie a linha de comandos

## Problema de comunicação com o servo 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![Esta imagem mostra o seguinte.](../../en/images/d65-03.png)

A correção: altere todos os `num_retry` no código em `lerobot/src/lerobot/motors/motors_bus.py` para 99, especialmente o da linha que dá erro

![Esta imagem mostra o conteúdo do ficheiro de código `motors_bus.py` no projeto LeRobot. O método `write` da classe `MotorsBusABC` está realçado, com a variável `num_retry` alterada para `99`. A imagem relaciona-se com a secção "Problema de comunicação com o servo 1", correspondendo à correção de alterar todos os `num_retry` no código em `lerobot/src/lerobot/motors/motors_bus.py` para 99, especialmente o da linha que dá erro.](../../en/images/d65-04.png)

## Problema de comunicação com o servo 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![Esta imagem mostra uma sessão de linha de comandos no terminal zsh no macOS. O terminal mostra vários caminhos de ficheiros e números de linha de código, como `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`. A linha 587 do ficheiro `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` lança um `ConnectionError`, reportando uma escrita falhada de `Torque_Enable` no id=1 sem pacote de estado. A imagem relaciona-se com o conteúdo "Problema de comunicação com o servo 2", mostrando visualmente a execução do código no momento do erro.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![Esta imagem mostra uma sessão de linha de comandos no terminal zsh no macOS. O terminal mostra vários caminhos de ficheiros e números de linha de código, como `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`. Aqui, `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

Solução: recalibre o braço do robô
