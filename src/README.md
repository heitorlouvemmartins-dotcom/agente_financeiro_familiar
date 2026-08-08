# Código da Aplicação

# orçamento_basico.py

class OrcamentoFamiliar:
    def __init__(self, renda_mensal):
        self.renda_mensal = renda_mensal
        self.despesas = {}

    def adicionar_despesa(self, categoria, valor):
        if categoria not in self.despesas:
            self.despesas[categoria] = 0
        self.despesas[categoria] += valor

    def total_despesas(self):
        return sum(self.despesas.values())

    def saldo(self):
        return self.renda_mensal - self.total_despesas()

    def resumo(self):
        print("\n--- Resumo do Orçamento Familiar ---")
        print(f"Renda mensal: R$ {self.renda_mensal:.2f}")
        for categoria, valor in self.despesas.items():
            print(f"{categoria}: R$ {valor:.2f}")
        print(f"Total de despesas: R$ {self.total_despesas():.2f}")
        print(f"Saldo disponível: R$ {self.saldo():.2f}")

    def sugestao_economia(self):
        saldo = self.saldo()
        if saldo > 0:
            print(f"Você pode guardar R$ {saldo * 0.2:.2f} (20% do saldo).")
        else:
            print("Atenção: suas despesas estão maiores que a renda!")

# Exemplo de uso
if __name__ == "__main__":
    agente = OrcamentoFamiliar(renda_mensal=3000)

    agente.adicionar_despesa("Alimentação", 800)
    agente.adicionar_despesa("Transporte", 400)
    agente.adicionar_despesa("Moradia", 1200)
    agente.adicionar_despesa("Lazer", 300)

    agente.resumo()
    agente.sugestao_economia()


## Estrutura Sugerida

```
src/
├── app.py              # Aplicação principal (Streamlit/Gradio)
├── agente.py           # Lógica do agente
├── config.py           # Configurações (API keys, etc.)
└── requirements.txt    # Dependências
```

## Exemplo de requirements.txt

```
streamlit
openai
python-dotenv
```

## Como Rodar

```bash
# Instalar dependências
pip install -r requirements.txt

# Rodar a aplicação
streamlit run app.py
```
