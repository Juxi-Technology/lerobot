[English](../en/02-install.md) | [简体中文](../zh-hans/02-install.md) | [繁體中文](../zh-hant/02-install.md) | [Deutsch](../de/02-install.md) | [Español](../es/02-install.md) | [Français](../fr/02-install.md) | [Italiano](../it/02-install.md) | [日本語](../ja/02-install.md) | [한국어](../ko/02-install.md) | [Português (BR)](../pt-br/02-install.md) | Português (PT)

# 2 · Instalar e executar

> **Anterior:** [01 Visão geral](01-overview.md)
> **Seguinte:** [03 Ligar e calibrar](03-calibration.md)

Ambos os métodos instalam também o LeRobot — o LeLab precisa dele.

---

## Método A · Uma única linha

Requer [uv](https://docs.astral.sh/uv/). Instala num ambiente isolado:

```bash
uv tool install --with-executables-from huggingface_hub git+https://github.com/Juxi-Technology/leLab.git && lelab
```

O navegador abre em `http://localhost:8000/`.

## Método B · A partir do código-fonte

```bash
git clone https://github.com/Juxi-Technology/leLab.git
cd leLab
pip install -e .
```

`pip install -e .` compila o front-end React e integra-o no pacote Python, pelo que um único processo serve a API e a interface. A primeira instalação demora alguns minutos.

Se a compilação não encontrar o Node.js, instale o **Node.js 22** e tente novamente. O Node só é necessário no momento da instalação e em modo de desenvolvimento — não para executar o LeLab depois.

> **Prefere antes o código original?** Este repositório é uma cópia. O original, mantido pela equipa LeRobot da Hugging Face, está em <https://github.com/huggingface/leLab>. Tudo nestas páginas se aplica a ele sem alterações.

---

## Iniciar

```bash
lelab
```

Serve a interface em **<http://localhost:8000/>** e abre o navegador.

| Opção | O que faz |
|---|---|
| `lelab` | Modo de produção. Um processo serve a API e a interface compilada em `:8000` |
| `lelab --dev` | Hot-reload do Vite em `:8080` e uvicorn `--reload` em `:8000`. Requer Node.js 22 |
| `lelab --rebuild` | Recompila o front-end a partir do código-fonte local e inicia em modo de produção |
| `lelab --no-open` | Inicia sem abrir o navegador |
| `lelab --stop` | Para um LeLab em execução e liberta as portas 8000 e 8080 |

Para com `Ctrl+C`, ou a partir de outro terminal:

```bash
lelab --stop
```

Use `--stop` quando a página deixa de carregar: um processo antigo a ocupar a porta 8000 ou 8080 é a causa habitual.

---

## Verificar se funcionou

Abra <http://localhost:8000/>. A página inicial tem separadores para **Calibration**, **Teleoperation**, **Recording**, **Datasets**, **Training** e **Inference**.

A partir do terminal:

```bash
curl http://localhost:8000/health
```

Devolve um estado JSON.

---

## Modo de desenvolvimento

```bash
lelab --dev
```

Vite em `:8080`, a API com recarregamento automático em `:8000`. As alterações em `frontend/src/` atualizam a página sem reiniciar; as alterações em `lelab/` recarregam o servidor.

**No modo `--dev`, aceda a `:8080`, não a `:8000`.** A porta 8000 dá-lhe a API sem interface.

---

## Atualização

O LeLab verifica se o ramo a partir do qual foi instalado avançou e propõe uma atualização na interface. Para atualizar manualmente:

```bash
uv tool install --with-executables-from huggingface_hub git+https://github.com/Juxi-Technology/leLab.git --force
```

As instalações editáveis (`pip install -e .`) estão excluídas desta verificação. Atualize-as com `git pull`.

---

> **Seguinte:** [03 Ligar e calibrar](03-calibration.md)
