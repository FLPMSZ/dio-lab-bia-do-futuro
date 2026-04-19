# Passo a Passo da execução


## Setup do Ollama
```bash
1. Instalar o Ollama(Ollama AI)

2. Baixar um modelo leve
ollama pull gpt-oss

3. Testar se funciona
ollama run gpt-oss

```

## Código Completo

```
Todo o código completo está no arquivo `app.py`.
```

## Como Rodar

```bash
# 1. Instalar as dependências
pip install streamlit pandas requests

# 2. Garantir que o Ollama está rodando
ollama serve

# 3. Rodar o APP
streamlit run .\src\app.py
```
