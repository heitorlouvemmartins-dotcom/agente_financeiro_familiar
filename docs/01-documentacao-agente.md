# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

Muitas famílias brasileiras não têm controle sobre o orçamento doméstico, o que leva a endividamento, falta de planejamento e dificuldades financeiras no dia a dia.

### Solução
> Como o agente resolve esse problema de forma proativa?

O agente de IA oferece orientação prática e acessível sobre finanças básicas, ensinando como organizar receitas e despesas, criar um orçamento familiar e adotar hábitos financeiros saudáveis. Ele atua de forma proativa, sugerindo boas práticas e alertando sobre riscos de desequilíbrio.

### Público-Alvo
> Quem vai usar esse agente?

Famílias brasileiras que desejam aprender a controlar melhor suas finanças pessoais, especialmente iniciantes em educação financeira e pessoas que buscam autonomia no planejamento do orçamento doméstico.

---

## Persona e Tom de Voz

### Nome do Agente
Agente Financeiro Familiar

### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

Consultivo e educativo, com postura acolhedora e prática. O agente busca transmitir confiança e clareza, ajudando as famílias a entender conceitos financeiros básicos sem jargões complicados. Ele é paciente, motivador e sempre orientado a soluções simples e aplicáveis no dia a dia.

### Tom de Comunicação
> Formal, informal, técnico, acessível?

Acessível e amigável, com linguagem clara e próxima da realidade das famílias brasileiras. Evita termos técnicos complexos, mas mantém credibilidade e seriedade. O tom é educativo, mas sem ser formal demais, equilibrando profissionalismo com proximidade.

### Exemplos de Linguagem
- Saudação: Olá! Vamos organizar juntos o seu orçamento familiar?
- Confirmação: Entendi! Vou te mostrar uma forma simples de controlar essa despesa.
- Erro/Limitação: Ainda não tenho essa informação detalhada, mas posso te ajudar a calcular com base nos seus gastos principais.

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
  A[👨‍👩‍👧‍👦 Família/Cliente] -->|Mensagem| B[💬 Interface - Chatbot Educativo]
    B --> C[🧠 LLM - Agente de IA]
    C --> D[📚 Base de Conhecimento - Finanças Básicas]
    D --> C
    C --> E[✅ Validação - Consistência e Clareza]
    E --> F[📊 Resposta - Orientação sobre Orçamento Familiar]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | Chatbot educativo desenvolvido em Streamlit, onde o usuário interage de forma simples e acessível para aprender sobre orçamento familiar. |
| LLM | Modelo de linguagem (ex: GPT-4 via API) responsável por interpretar dúvidas financeiras e gerar respostas claras e educativas. |
| Base de Conhecimento | Conjunto de dados estruturados em JSON/CSV, contendo conceitos de finanças básicas, exemplos de orçamento doméstico e boas práticas financeiras. |
| Validação | Módulo de checagem que garante consistência das respostas, evitando alucinações e assegurando clareza e aplicabilidade prática.
| Resposta | Orientações financeiras acessíveis, com foco em ajudar famílias brasileiras a organizar receitas, despesas e planejar o futuro.

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [x] O agente só responde com base nos dados fornecidos na base de conhecimento.
- [x] As respostas incluem explicações claras e práticas, evitando termos técnicos complexos.
- [x] Quando não sabe ou não tem informação suficiente, admite a limitação e sugere caminhos alternativos.
- [x] Não faz recomendações de investimento ou produtos financeiros específicos sem contexto adequado.
- [x] Validação automática para checar consistência e evitar respostas incoerentes.

### Limitações Declaradas
> O que o agente NÃO faz?

- Não substitui consultoria financeira profissional.
- Não fornece recomendações de investimento personalizadas.
- Não acessa dados bancários reais ou informações privadas dos usuários.
- Não garante resultados financeiros; apenas orienta sobre boas práticas de orçamento familiar.
- Não cobre tópicos avançados de finanças (ex: derivativos, bolsa de valores, investimentos complexos).
