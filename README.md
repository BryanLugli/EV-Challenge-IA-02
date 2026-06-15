# EV-Challenge-IA-02

# GoodWe EV ChargeOps — Chatbot de Gestão de Eletropostos

Projeto desenvolvido para o **EV Challenge 2026**, em parceria com a GoodWe, como parte da disciplina de IA da FIAP.

---

## Integrantes

- Bryan Lugli — RM 571350
- Beckman — RM 573442
- Guilherme — RM 573053

---

## O que é esse projeto?

A ideia surgiu de um problema real: condomínios que estão instalando eletropostos não têm uma forma simples de responder às dúvidas do dia a dia dos moradores. Quem está usando o carregador agora? Quanto vou pagar esse mês? Posso ligar meu carro à noite sem prejudicar a rede?

O **EV ChargeOps** é um chatbot com IA que responde exatamente essas perguntas. Ele conhece as regras do condomínio, o status dos pontos de carregamento e o consumo de cada unidade — e conversa em linguagem natural, sem exigir que o morador entenda nada de tecnologia.

O foco é o cenário condominial (EV ChargeOps), onde vários moradores compartilham os mesmos pontos de carga e existe a necessidade de controle justo e transparente.

---

## Como rodar

### Google Colab (mais fácil)

1. Abra o arquivo `goodwe_chatbot.ipynb` no [Google Colab](https://colab.research.google.com)
2. Na barra lateral esquerda, clique no ícone de chave (🔑 Secrets)
3. Crie um secret com o nome `OPENAI_API_KEY` e cole sua chave da OpenAI como valor
4. Vá em **Ambiente de execução → Executar tudo** e pronto

### Rodando local

Se preferir rodar na sua máquina:

```bash
pip install openai
```

Depois configure a variável de ambiente com sua chave:

```bash
# Linux ou macOS
export OPENAI_API_KEY="sua-chave-aqui"

# Windows (PowerShell)
$env:OPENAI_API_KEY="sua-chave-aqui"
```

E abra o notebook normalmente com o Jupyter.

---

## Variáveis de ambiente necessárias

| Variável | Para que serve |
|---|---|
| `OPENAI_API_KEY` | Autenticação com a API da OpenAI |

> Nunca coloque a chave direto no código. Use sempre os Secrets do Colab ou uma variável de ambiente. Nenhuma chave deve aparecer no repositório.

---

## Dependências

Só precisa de uma biblioteca externa:

```
openai>=1.0.0
```

```bash
pip install openai
```

---

## Como o chatbot funciona

O chatbot recebe a pergunta do usuário, monta um histórico de mensagens (para manter o contexto da conversa) e envia tudo para a API da OpenAI junto com um **system prompt** que define quem ele é e o que ele sabe.

Esse system prompt carrega o contexto do condomínio: quais pontos existem, quem está usando agora, o consumo de cada unidade, as regras de horário e a tarifa vigente. Assim o modelo consegue responder de forma coerente sem inventar informações.

Parâmetros utilizados:
- Modelo: `gpt-3.5-turbo`
- Temperature: `0.4` — equilibra consistência com naturalidade
- Max tokens: `600`

Também usamos **few-shot prompting** dentro do system prompt, com exemplos de perguntas e respostas esperadas, para calibrar melhor o estilo das respostas.

---

## Testes realizados

Rodamos os 5 casos de teste definidos na Sprint 1 e documentamos os resultados no arquivo [`docs/testes_resultados.md`](docs/testes_resultados.md).

| Pergunta | Resultado |
|---|---|
| Quanto cada morador consumiu este mês? | Adequado |
| Como funciona a cobrança do carregamento? | Adequado |
| Posso carregar meu carro à noite? | Adequado |
| O sistema está sobrecarregado? | Adequado |
| Quem está usando o carregador agora? | Adequado |

---

| EV Challenge 2026
