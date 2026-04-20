# 🦔 Nico — Educador Financeiro com IA

> Um agente que usa seus próprios dados para te ensinar finanças de forma simples, sem julgamentos e sem complicação.

---

## O que é o Nico?

O Nico é um chatbot educacional financeiro que conversa de forma informal e didática. Ele **não recomenda investimentos** — ele **ensina** como as coisas funcionam, usando o histórico real de gastos e o perfil do próprio cliente como exemplo prático.

Pensa nele como aquele amigo que entende de finanças e nunca te julga pelos seus gastos.

---

## Como funciona

```
Usuário → Streamlit → System Prompt + Contexto → Ollama (local) → Resposta do Nico
```

Os dados do cliente (perfil, transações, histórico de atendimentos e produtos disponíveis) são carregados na inicialização e injetados no prompt como contexto. Isso garante respostas personalizadas sem depender de busca dinâmica.

---

## Estrutura do projeto

```
📁 lab-agente-financeiro/
├── 📁 data/
│   ├── perfil_investidor.json        # Perfil e metas do cliente
│   ├── transacoes.csv                # Histórico de gastos
│   ├── historico_atendimento.csv     # Atendimentos anteriores
│   └── produtos_financeiros.json     # Produtos disponíveis para explicar
│
├── 📁 docs/
│   ├── 01-documentacao-agente.md     # Caso de uso, persona e arquitetura
│   ├── 02-base-conhecimento.md       # Estratégia de dados e integração
│   ├── 03-prompts.md                 # System prompt e exemplos de interação
│   ├── 04-metricas.md                # Testes e avaliação de qualidade
│   └── 05-pitch.md                   # Roteiro do pitch
│
└── 📁 src/
    └── app.py                        # Aplicação Streamlit
```

---

## Persona

**Nome:** Nico  
**Tom:** Informal, educativo, paciente e divertido  
**Regras:** Nunca recomenda investimentos. Admite quando não sabe. Usa os dados do cliente como exemplos reais.

| Situação | Exemplo de resposta |
|----------|---------------------|
| Saudação | *"Oi! Eu sou o Nico 👋 Bora organizar suas finanças sem complicação?"* |
| Limitação | *"Não posso recomendar onde investir, mas posso te explicar como cada produto funciona!"* |
| Fora do escopo | *"Sou especialista em finanças, não em clima 😄 Posso te ajudar com seus gastos?"* |

---

## Como rodar

**Pré-requisito:** [Ollama](https://ollama.ai/) instalado localmente.

```bash
# 1. Baixar o modelo
ollama pull gpt-oss

# 2. Instalar dependências
pip install streamlit pandas requests

# 3. Rodar o Ollama em segundo plano
ollama serve

# 4. Iniciar o app
streamlit run src/app.py
```

> O Nico roda 100% local. Nenhum dado seu é enviado para servidores externos.

---

## Exemplos de uso

**"Onde estou gastando mais?"**  
→ Nico analisa o `transacoes.csv` e responde com os maiores gastos por categoria.

**"O que é CDI?"**  
→ Nico explica em linguagem simples, sem jargão, com analogias.

**"Devo investir em ações?"**  
→ Nico explica prós e contras, mas não recomenda. Educação, não conselho.

---

## Limitações declaradas

- Não faz recomendações de investimento
- Não acessa dados em tempo real
- Não substitui um profissional certificado (CFP, assessor de investimentos)
- Não tem memória entre sessões — cada conversa começa do zero

---

## Decisões de design

- **Dados mockados** foram usados para garantir privacidade e facilitar a validação das respostas
- O produto *Fundo Multimercado* foi substituído por *Fundo Imobiliário (FII)* para aumentar a confiabilidade na validação das respostas
- O contexto é injetado diretamente no prompt (ao invés de RAG dinâmico) por simplicidade — suficiente para o volume de dados atual
- Modelo local via Ollama para evitar custos de API e garantir privacidade dos dados

---

*Desenvolvido como parte do desafio de Agente Financeiro Inteligente com IA Generativa — DIO*
