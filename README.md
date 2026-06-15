# EV-Challenge-IA-02

# GoodWe EV ChargeOps — Chatbot de Gestão de Eletropostos

Projeto desenvolvido para o **EV Challenge 2026**, em parceria com a GoodWe, como parte da disciplina de Inteligência Artificial da FIAP.

---

## Integrantes

- Bryan Lugli — RM 571350
- Beckman — RM 573442
- Guilherme — RM 573053

---

## O problema que motivou o projeto

Com a chegada dos veículos elétricos nos condomínios, surgiu um problema que parece simples mas gera bastante confusão no dia a dia: como gerenciar de forma justa o uso compartilhado dos eletropostos?

Hoje, moradores não sabem se o ponto de carregamento está livre, síndicos não têm como responder rapidamente dúvidas sobre consumo e cobrança, e a falta de informação gera conflitos. Além disso, a ausência de controle sobre a carga elétrica pode sobrecarregar a rede do condomínio em horários de pico.

Foi com esse contexto que desenvolvemos o **EV ChargeOps**: um chatbot com inteligência artificial que serve como assistente operacional do sistema de eletropostos, respondendo em linguagem natural as dúvidas de moradores, síndicos e administradores.

---

## O que o chatbot faz

- Informa o consumo de energia de cada unidade no mês
- Explica como funciona a cobrança proporcional por kWh
- Mostra quais pontos estão disponíveis ou ocupados no momento
- Avisa sobre restrições de horário (ex: horário de pico entre 18h e 21h)
- Monitora o status da rede elétrica e alerta sobre riscos de sobrecarga
- Responde dúvidas sobre as regras do condomínio relacionadas ao carregamento
- Respeita a privacidade dos moradores: identifica uso por unidade, nunca por nome

O chatbot mantém **memória da conversa**, ou seja, você pode fazer perguntas encadeadas e ele vai lembrar do contexto — como se fosse uma conversa de verdade.

---

## Tecnologias utilizadas

- **Python 3.10+**
- **Hugging Face Inference API** — modelo `Mistral-7B-Instruct-v0.3`
- **Kaggle Notebooks** como ambiente de execução principal
- **Few-shot prompting** para calibrar o estilo e qualidade das respostas
- **System prompt contextualizado** com dados do condomínio, regras e status simulado do sistema GoodWe

---



## Variáveis de ambiente

| Variável | Descrição | Obrigatório |
|---|---|---|
| `HF_API_KEY` | Chave de autenticação da API do Hugging Face | Sim |

---

## Dependências

O projeto usa apenas uma biblioteca externa:

```
huggingface_hub>=0.20.0
```


## Como o chatbot foi construído

O núcleo do chatbot é a classe `GoodWeChatbot`, que gerencia duas coisas principais:

**1. O system prompt** — um texto de contexto enviado em toda chamada à API, que define quem o assistente é, o que ele sabe (dados do condomínio, status dos pontos, tarifas, regras) e como ele deve se comportar. É aqui que fica a "inteligência" do negócio.

**2. O histórico de mensagens** — a cada troca, o código acumula as mensagens anteriores e reenvia tudo para a API. Isso é o que permite o chatbot "lembrar" do que foi dito antes na mesma conversa.

Além disso, usamos **few-shot prompting** dentro do system prompt: incluímos exemplos de perguntas e respostas esperadas para guiar o modelo a responder no estilo certo — objetivo, claro e acessível para quem não tem conhecimento técnico.

---

## Testes realizados

Os 5 casos de teste definidos na Sprint 1 foram executados e os resultados estão documentados em [docs/testes_resultados(01).md] testes_resultados (1).md.

| # | Pergunta | Avaliação |
|---|---|---|
| 1 | Quanto cada morador consumiu este mês? | Adequado |
| 2 | Como funciona a cobrança do carregamento? | Adequado |
| 3 | Posso carregar meu carro à noite? | Adequado |
| 4 | O sistema está sobrecarregado? | Adequado |
| 5 | Quem está usando o carregador agora? | Adequado |

Os testes validaram que o chatbot mantém o escopo do problema GoodWe, utiliza corretamente os dados simulados do condomínio e não inventa informações fora do contexto.

---

