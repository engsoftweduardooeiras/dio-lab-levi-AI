# Base de Conhecimento

## Dados Utilizados

Descrição de uso dos arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |
| `cartao_de_credito_sintetico_parte_01.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_02.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_03.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_04.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_05.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_06.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_07.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_08.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_09.csv`| CSV | Analisar histórico de operações |
| `cartao_de_credito_sintetico_parte_10.csv`| CSV | Analisar histórico de operações |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Expandi e modifiquei os dados mockados?

Adcionei os dados de `Cartao_de_cerdito_url_geral_arquivo_original`, ampliado em arquivos separados como `cartao_de_credito_sintetico_parte_01.csv`, em complementação aos dados de `transacoes.csv`

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
linha_de_credito_01 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_01.csv`)
linha_de_credito_02 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_02.csv`)
linha_de_credito_03 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_03.csv`)
linha_de_credito_04 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_04.csv`)
linha_de_credito_05 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_05.csv`)
linha_de_credito_06 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_06.csv`)
linha_de_credito_07 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_07.csv`)
linha_de_credito_08 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_08.csv`)
linha_de_credito_09 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_09.csv`)
linha_de_credito_10 = pd.read_csv(`data/cartao_de_credito_sintetico_parte_10.csv`)


# JSONs
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
    perfil = json.load(f)
    
with open('data/produtos_financeiros.json', 'r', encoding='utf-8') as f:
    produtos = json.load(f)

---

### Exemplo de Contexto Montado

> Mostrando exemplos de como os dados são formatados para o agente

```
Dados do Dispositivo e Conectividade:
- IP do Dispositivo: 192.168.228.19
- Tipo de Conexão: Fibra residencial
- Última Ação Cadastrada: Autenticação MFA

Informações da Transação Atual:
- Tempo Decorrido (Time): 0.0 segundos
- Valor Comercial (Amount): R$ 149,62
- Classificação de Risco (Class): 0 (Legítima)

Indicadores Vetoriais de Comportamento (PCA):
- Componente V1: -1.3598
- Componente V2: -0.0728
- Componente V3: 2.5363
- Componente V4: 1.3781
- Componente V5: -0.3383
...
```
