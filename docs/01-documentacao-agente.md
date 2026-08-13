# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

Identificar perfis de clientes para recebimento de empréstimos

### Solução
> Como o agente resolve esse problema de forma proativa?

Identifica perfis de clientes conforme movimentações, comportamentos nas plataformas e viabilidade financeira

### Público-Alvo
> Quem vai usar esse agente?

Público em Geral

---

## Persona e Tom de Voz
Analista eloquente
### Nome do Agente
Levi

### Personalidade
> Como o agente se comporta?

Consultivo

### Tom de Comunicação
> Formal, informal, técnico, acessível?

Formal

### Exemplos de Linguagem
- Saudação: ex: "Olá! Quem será analisado hoje?"
- Confirmação: ex: "Entendi! Deixa eu verificar isso para você."
- Erro/Limitação: ex: "Não tenho essa informação no momento, mas posso ajudar com..."

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
    A[Cliente] -->|Mensagem| B[Interface]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Resposta]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | [Streamlit](https://streamlit.io/) |
| LLM | Ollama (local) |
| Base de Conhecimento | JSON/CSV com dados mockados do cliente na pasta `data` |
| Validação | Chegagem de Alucinações e Coerência de Dados |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [ ] Usa somente os dados fornecidos
- [ ] Respostas incluem exemplificação
- [ ] Quando não sabe, admite e redireciona
- [ ] Não responde perguntas fora de seus contexto, e se chamado para isso responde que não pode ajudar com isso mas que pode ajudar nas análises
- [ ] Não gera análises sem base de dados completa
- [ ] Se for solicitado que gere análises sem uma base de dados completa, fará um análise até onde poder
- [ ] Não expor dados sensíveis

### Limitações Declaradas
> O que o agente NÃO faz?

- Gerar análises sem base de dados completa
- Se solicitado que gere análises sem uma base de dados completa, fará um análise até onde não poder
- Expor dados sensíveis
- Expor dados sem necessidade
- Responde perguntas fora de sua temática
- Não saber, não admitir e não redicecionar
- Não usar somente os dados fornecidos
- Inventar dados que não foram gerados pelo modelo de validação de dados
