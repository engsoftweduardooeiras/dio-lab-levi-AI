# Base de Conhecimento

## Dados Utilizados

Descrição de uso dos arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |
| `Linha_de_cartao_de_credito_enriquecido_parte_1A_1.csv`| CSV | Analisar histórico de operações |
| `Linha_de_cartao_de_credito_enriquecido_parte_1A_2.csv`| CSV | Analisar histórico de operações |
| `Linha_de_cartao_de_credito_enriquecido_parte_1A_3.csv`| CSV | Analisar histórico de operações |
| `Linha_de_cartao_de_credito_enriquecido_parte_1B_1.csv`| CSV | Analisar histórico de operações |
| `Linha_de_cartao_de_credito_enriquecido_parte_1B_2.csv`| CSV | Analisar histórico de operações |
| `Linha_de_cartao_de_credito_enriquecido_parte_1B_3.csv`| CSV | Analisar histórico de operações |
| `Linha_de_cartao_de_credito_enriquecido_parte_2A.csv`| CSV | Analisar histórico de operações |
| `Linha_de_cartao_de_credito_enriquecido_parte_2B.csv`| CSV | Analisar histórico de operações |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Expandi e modifiquei os dados mockados?

Adcionei os dados de `Cartao_de_cerdito_url_geral_arquivo_original`, ampliado em arquivos separados como `Linha_de_cartao_de_credito_enriquecido_parte_1A_1.csv`, em complementação aos dados de `transacoes.csv`

---

## Estratégia de Integração

### Como os dados são carregados?
> Descrição de como esse agente acessa a base de conhecimento:

Os JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Os dados serão inseridos diretamente no terminal com estrutura dinâmica que permite a abertura

```python
import pandas as pd
import json


# CSVs
historico = pd.read_csv('data/historico_atendimento.csv')
transacoes = pd.read_csv('data/transacoes.csv')
linha_de_credito_1A_1 = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_1A_1.csv`)
linha_de_credito_1A_2 = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_1A_2.csv`)
linha_de_credito_1A_3 = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_1A_3.csv`)
linha_de_credito_1B_1 = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_1B_1.csv`)
linha_de_credito_1B_2 = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_1B_2.csv`)
linha_de_credito_1B_3 = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_1B_3.csv`)
linha_de_credito_2A = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_2A.csv`)
linha_de_credito_2B = pd.read_csv(`data/Linha_de_cartao_de_credito_enriquecido_parte_2B.csv`)


# JSONs
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
    perfil = json.load(f)
    
with open('data/produtos_financeiros.json', 'r', encoding='utf-8') as f:
    produtos = json.load(f)

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
