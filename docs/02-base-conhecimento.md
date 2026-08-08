# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Utilização no Agente |
|----------|----------|----------------------|
| `despesas_familiares.csv` | CSV | Registrar e analisar gastos mensais (alimentação, transporte, moradia, lazer) |
| `orcamento_mensal.json` | JSON | Definir limites de orçamento por categoria e acompanhar saldo disponível |
| `historico_orcamento.csv` | CSV | Comparar evolução dos gastos e identificar padrões ao longo dos meses |
| `perfil_familiar.json` | JSON | Personalizar recomendações de economia conforme tamanho da família e renda |

> [!TIP]
> Você pode expandir com datasets públicos de finanças pessoais no [Hugging Face](https://huggingface.co/datasets), adaptando para o contexto de orçamento familiar.

---

## Adaptações nos Dados

- Criei o arquivo `despesas_familiares.csv` com dados fictícios para simular gastos básicos.  
- Ajustei o `orcamento_mensal.json` para incluir categorias específicas de famílias brasileiras (ex.: alimentação, transporte público, energia elétrica).  
- Expandi o `perfil_familiar.json` para contemplar diferentes faixas de renda e número de dependentes.

---

## Estratégia de Integração

### Como os dados são carregados?
Os arquivos CSV e JSON são carregados no início da sessão e ficam disponíveis no contexto do agente.  
- Os CSV (`despesas_familiares.csv`, `historico_orcamento.csv`) são lidos e transformados em tabelas de gastos.  
- Os JSON (`orcamento_mensal.json`, `perfil_familiar.json`) são interpretados como parâmetros de configuração e perfil do usuário.  

### Como os dados são usados no prompt?
Os dados são consultados dinamicamente durante a interação.  
- O **perfil familiar** é usado para personalizar recomendações de economia.  
- O **orcamento mensal** define limites e alerta quando uma categoria ultrapassa o valor previsto.  
- As **despesas registradas** são incluídas no contexto do prompt para que o agente possa gerar relatórios e sugestões em tempo real.

---

## Exemplo de Contexto Montado

```

Dados da Família:
- Nome: Família Souza
- Perfil: Renda média, 4 pessoas
- Orçamento mensal: R$ 4.500

Últimas despesas:
- 02/08: Supermercado - R$ 520
- 03/08: Transporte público - R$ 180
- 05/08: Energia elétrica - R$ 230
- 06/08: Lazer (cinema) - R$ 120

Resumo:
- Total gasto até agora: R$ 1.050
- Saldo disponível: R$ 3.450
- Alerta: Categoria "Alimentação" já consumiu 35% do orçamento previsto.

```
