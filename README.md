# AX Academy — Módulo de Sistemas Multiagentes

Material e atividades do **Módulo 4 – Sistemas Multiagentes** (AIX Academy · FPFtech): vários agentes LangChain, cada um com seu papel, prompt e ferramentas, coordenados por Python.

## Estrutura

```
ax_academy_multiagent_module/
├── aulas/          Conteúdo das aulas disponibilizado pelo professor (pptx, pdf)
├── exemplos/       Código disponibilizado pelo professor (ipynb, py)
├── exercicios/     Minhas atividades
├── keys.env        Configuração do LLM (não versionado)
├── requirements.txt
└── .venv/          Ambiente virtual (não versionado)
```

## Configuração

```powershell
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

O material do professor fixa estas versões (a célula "Preparar o Colab" confere e para se forem diferentes): `langchain==1.4.7`, `langchain-core==1.7.1`, `pydantic==2.13.5`, `langchain-ollama==1.1.0`, `langgraph==1.2.18`, `ollama==0.6.3`.

### LLM: Ollama local com Qwen

Os notebooks do professor usam o Ollama na nuvem (`https://ollama.com`, chave no segredo `segredo` do Colab). Localmente uso o Ollama instalado na máquina, sem chave:

```powershell
ollama pull qwen2.5:3b
ollama list            # confirma o modelo baixado
```

`keys.env` na raiz:

```
OLLAMA_BASE_URL=http://localhost:11434
OLLAMA_MODEL=qwen2.5:3b
```

Os notebooks carregam com `dotenv.load_dotenv(dotenv.find_dotenv("keys.env", usecwd=True))`, que procura o arquivo subindo pelas pastas. Atenção: o `ChatOllama` usa a URL **sem** `/v1` (diferente do `openai` SDK do módulo anterior, que usava `http://localhost:11434/v1`).
