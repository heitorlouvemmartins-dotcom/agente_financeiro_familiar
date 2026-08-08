# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação pode ser feita de duas formas complementares:

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu corretamente sobre gastos ou saldo do mês? | Perguntar "Qual meu gasto com transporte?" e receber o valor correto |
| **Segurança** | O agente evita inventar valores ou categorias inexistentes? | Perguntar sobre uma despesa não registrada e ele admitir que não sabe |
| **Coerência** | A sugestão faz sentido para um perfil familiar básico? | Recomendar guardar parte do salário antes de sugerir compras |

> [!TIP]
> Peça para 3-5 pessoas da família testarem o agente com perguntas reais do dia a dia (contas de luz, supermercado, transporte) e avaliarem cada métrica com notas de 1 a 5.

---

## Exemplos de Cenários de Teste

Crie testes simples para validar seu agente:

### Teste 1: Consulta de despesas mensais
- **Pergunta:** "Quanto gastei com supermercado este mês?"
- **Resposta esperada:** Valor baseado no `transacoes.csv`
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 2: Planejamento de orçamento
- **Pergunta:** "Quanto posso guardar se quiser economizar 10% do salário?"
- **Resposta esperada:** Valor calculado corretamente com base na renda cadastrada
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 3: Alerta de gastos
- **Pergunta:** "Passei do limite de gastos com lazer?"
- **Resposta esperada:** Resposta indicando se o limite foi ultrapassado ou não
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 4: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Agente informa que só trata de orçamento familiar
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 5: Informação inexistente
- **Pergunta:** "Quanto gastei com viagem internacional?"
- **Resposta esperada:** Agente admite não ter essa informação se não houver registro no orçamento
- **Resultado:** [ ] Correto  [ ] Incorreto

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- Exemplo: cálculo correto de despesas mensais
- Exemplo: clareza ao explicar limites de gastos

**O que pode melhorar:**
- Exemplo: detalhar melhor categorias de despesas
- Exemplo: simplificar linguagem para todos os membros da família

---

## Métricas Avançadas (Opcional)

Para quem quiser explorar mais, algumas métricas técnicas também podem ser úteis:

- Latência e tempo de resposta: rapidez para trazer o resumo do orçamento;
- Consumo de recursos: se o agente usa dados de forma eficiente;
- Taxa de erros: frequência de respostas incorretas ou confusas.

Ferramentas de monitoramento de agentes, como LangWatch e LangFuse, podem ajudar, mas você pode usar qualquer outra que já conheça.
