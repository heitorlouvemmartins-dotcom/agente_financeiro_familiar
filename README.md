# 🤖 Agente Financeiro Familiar

Agente de IA voltado para **educação financeira básica**, com foco em orçamento familiar e controle de gastos. O projeto foi desenvolvido a partir do laboratório *"Bia do Futuro"* da Digital Innovation One (DIO), adaptado para o contexto de finanças domésticas de famílias brasileiras.

---

## 📌 Sobre o projeto

Muitas famílias brasileiras não têm controle sobre o orçamento doméstico, o que leva a endividamento, falta de planejamento e dificuldades financeiras no dia a dia. O **Agente Financeiro Familiar** foi criado para resolver isso de forma proativa: ele orienta sobre organização de receitas e despesas, ajuda a montar um orçamento familiar e sugere boas práticas financeiras — sempre com base nos dados reais fornecidos, sem inventar informações.

**Público-alvo:** famílias brasileiras que querem aprender a controlar melhor as finanças pessoais, especialmente iniciantes em educação financeira.

### Persona

- **Nome:** Agente Financeiro Familiar
- **Personalidade:** consultiva e educativa, com postura acolhedora e prática
- **Tom de voz:** acessível e amigável, evitando jargões técnicos, mas mantendo credibilidade

Exemplos de linguagem usados pelo agente:
> "Olá! Vamos organizar juntos o seu orçamento familiar?"
> "Entendi! Vou te mostrar uma forma simples de controlar essa despesa."

---

## 🏗️ Arquitetura

```
👨‍👩‍👧‍👦 Família/Cliente
        │  Mensagem
        ▼
💬 Interface (Chatbot Educativo)
        │
        ▼
🧠 LLM — Agente de IA
        │◄──────────────┐
        ▼                │
📚 Base de Conhecimento ─┘
        │
        ▼
✅ Validação (consistência e clareza)
        │
        ▼
📊 Resposta — Orientação sobre orçamento familiar
```

| Componente | Descrição |
|---|---|
| **Interface** | Chatbot educativo (Streamlit), onde o usuário interage de forma simples e acessível |
| **LLM** | Modelo de linguagem (ex: GPT-4 via API) responsável por interpretar dúvidas financeiras e gerar respostas |
| **Base de Conhecimento** | Dados estruturados em JSON/CSV com despesas, orçamento e perfil da família |
| **Validação** | Módulo que garante consistência das respostas, evitando alucinações |
| **Resposta** | Orientações práticas para organizar receitas, despesas e planejamento |

---

## 🔒 Segurança e anti-alucinação

- O agente só responde com base nos dados fornecidos na base de conhecimento
- Quando não sabe ou não tem informação suficiente, admite a limitação
- Não faz recomendações de investimento ou produtos financeiros específicos sem contexto adequado
- Não substitui consultoria financeira profissional
- Não acessa dados bancários reais ou informações privadas dos usuários

---

## 📂 Base de conhecimento (dados)

| Arquivo | Formato | Uso no agente |
|---|---|---|
| `despesas_familiares.csv` | CSV | Registrar e analisar gastos mensais (alimentação, transporte, moradia, lazer) |
| `orcamento_mensal.json` | JSON | Definir limites de orçamento por categoria e acompanhar saldo disponível |
| `historico_orcamento.csv` | CSV | Comparar evolução dos gastos e identificar padrões ao longo dos meses |
| `perfil_familiar.json` | JSON | Personalizar recomendações conforme tamanho da família e renda |

Os CSVs são carregados como tabelas de gastos e os JSONs como parâmetros de configuração/perfil, ficando disponíveis no contexto do agente durante a conversa.

---

## 💬 Exemplo de interação

**Usuário:** Quanto já gastamos em alimentação este mês?
**Agente:** Até agora, a categoria *Alimentação* registra R$ 565 em despesas. Isso representa 38% do limite mensal definido em R$ 1.500. Recomendo atenção para não ultrapassar o orçamento.

**Usuário:** Qual é o saldo disponível da família Souza?
**Agente:** A renda mensal da Família Souza é de R$ 4.500. Os gastos somam R$ 1.050 até o momento, restando um saldo disponível de R$ 3.450.

---

## 📁 Estrutura do repositório

```
agente_financeiro_familiar/
│
├── README.md
│
├── data/                          # Dados mockados usados pelo agente
│   ├── despesas_familiares.csv
│   ├── orcamento_mensal.json
│   ├── historico_orcamento.csv
│   └── perfil_familiar.json
│
├── docs/                          # Documentação do projeto
│   ├── 01-documentacao-agente.md  # Caso de uso, persona e arquitetura
│   ├── 02-base-conhecimento.md    # Estratégia de dados
│   ├── 03-prompts.md              # System prompt, few-shot e edge cases
│   ├── 04-metricas.md             # Avaliação e métricas de qualidade
│   └── 05-pitch.md                # Roteiro do pitch
│
├── src/                           # Código da aplicação (chatbot)
│
├── assets/                        # Imagens e diagramas
│
└── examples/                      # Referências e exemplos
```

---

## 🚀 Como executar

> ⚠️ Ajuste este trecho conforme os arquivos reais dentro de `src/` (ex: `app.py`) e as dependências do projeto (`requirements.txt`), caso ainda não estejam presentes no repositório.

```bash
# Clone o repositório
git clone https://github.com/heitorlouvemmartins-dotcom/agente_financeiro_familiar.git
cd agente_financeiro_familiar

# Crie um ambiente virtual (opcional, mas recomendado)
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Instale as dependências
pip install -r requirements.txt

# Configure sua chave de API do modelo de linguagem (ex: OpenAI)
# Crie um arquivo .env com: OPENAI_API_KEY=sua_chave_aqui

# Rode a aplicação (Streamlit)
streamlit run src/app.py
```

---

## 🛠️ Ferramentas e tecnologias

| Categoria | Ferramentas |
|---|---|
| **LLM** | GPT-4 / outros modelos via API |
| **Interface** | [Streamlit](https://streamlit.io/) |
| **Dados** | CSV / JSON |

---

## 📊 Avaliação

O agente é avaliado com base em três métricas principais:

- **Assertividade** — responde corretamente sobre gastos e saldo?
- **Segurança** — evita inventar valores ou categorias inexistentes?
- **Coerência** — as sugestões fazem sentido para o perfil familiar?

Veja o detalhamento dos cenários de teste em [`docs/04-metricas.md`](docs/04-metricas.md).

---

## ⚠️ Limitações

- Não substitui consultoria financeira profissional
- Não fornece recomendações de investimento personalizadas
- Não acessa dados bancários reais
- Não garante resultados financeiros — apenas orienta boas práticas de orçamento
- Não cobre tópicos avançados de finanças (bolsa de valores, derivativos, etc.)

---

## 🙏 Créditos

Projeto desenvolvido a partir do repositório-modelo [`digitalinnovationone/dio-lab-bia-do-futuro`](https://github.com/digitalinnovationone/dio-lab-bia-do-futuro), como parte de um desafio de prototipagem de agentes de IA generativa aplicados ao setor financeiro.
