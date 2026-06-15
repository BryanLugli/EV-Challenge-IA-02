# Resultados dos Testes — Sprint 2
## GoodWe EV ChargeOps Chatbot

**Data de execução:** Junho/2026
**Modelo utilizado:** Qwen/Qwen2.5-7B-Instruct (Hugging Face Inference API)
**Ambiente:** Kaggle Notebooks
**Temperature:** 0.4

---

## Teste 1

**Pergunta enviada:**
> Quanto cada morador consumiu este mês?

**Resposta obtida:**
> Com base nos dados fornecidos, aqui está o consumo de energia por unidade este mês:
>
> - Unidade 101: 42,3 kWh
> - Unidade 108: 78,1 kWh
> - Unidade 204: 15,7 kWh
> - Unidade 302: 95,4 kWh
> - Unidade 415: 31,2 kWh
> - Unidade 512: 60,8 kWh
>
> Se precisar de mais detalhes ou tiver alguma outra pergunta sobre o consumo, estou à disposição!

**Avaliação:** ✅ Adequada

O chatbot apresentou corretamente os dados de consumo de todas as unidades injetados via system prompt, sem inventar valores e mantendo o formato claro para o morador.

---

## Teste 2

**Pergunta enviada:**
> Como funciona a cobrança do carregamento?

**Resposta obtida:**
> A cobrança do carregamento é feita de forma simples e transparente. Você será cobrado pelo consumo de energia em kWh que seu veículo usa para carregar, e o valor é calculado com base na tarifa atual de R$ 0,85 por kWh.
>
> 1. **Medição do Consumo**: O sistema medirá exatamente quantos kWh seu veículo consome durante o carregamento.
> 2. **Cálculo da Cobrança**: O valor será calculado multiplicando o número de kWh consumidos pelo valor da tarifa, que atualmente é R$ 0,85/kWh.
> 3. **Cobrança Mensal**: O valor será acrescido à sua fatura de energia do mês, junto com outros gastos habituais.
>
> Se você usar o carregador no horário de pico (18h às 21h), a potência será reduzida para 50% (3 kW por ponto), o que pode aumentar o tempo necessário para completar o carregamento, mas o valor cobrado será proporcional ao consumo.

**Avaliação:** ✅ Adequada

Explicação clara, detalhada e acessível. O chatbot relacionou corretamente a cobrança com o horário de pico e trouxe uma informação complementar relevante sobre o impacto na velocidade de carregamento.

---

## Teste 3

**Pergunta enviada:**
> Posso carregar meu carro à noite?

**Resposta obtida:**
> Sim, você pode carregar seu carro à noite! Fora do horário de pico (antes das 18h ou após as 21h), os eletropostos operam em sua capacidade máxima de 6 kW, o que é o mais rápido disponível. Isso significa que você pode carregar seu carro à noite sem preocupação de redução de velocidade no carregamento.
>
> Se você tiver alguma unidade específica em mente, posso verificar a disponibilidade para você!

**Avaliação:** ✅ Adequada

Resposta direta e correta. O chatbot informou claramente a diferença entre horário de pico e fora do pico, orientou sobre a potência disponível e ainda se ofereceu para verificar disponibilidade, mostrando proatividade no atendimento.

---

## Teste 4

**Pergunta enviada:**
> O sistema está sobrecarregado?

**Resposta obtida:**
> Atualmente, o sistema está operando dentro dos limites normais. A carga atual é de 12 kW, que representa 25% da potência total disponível de 48 kW. Portanto, não há sobrecarga no sistema.
>
> No entanto, é importante ficar atento ao horário de pico, que vai de 18h às 21h. Durante esse período, a potência máxima por ponto é reduzida para 3 kW, o que pode afetar o tempo de carregamento. Se você ou outros moradores estiverem planejando usar os eletropostos nesse horário, pode ser útil programar o carregamento fora desse intervalo para evitar atrasos.
>
> Se notar que a carga está aumentando e chegando perto dos 48 kW, o sistema de balanceamento dinâmico de carga entre os pontos ativos será ativado para manter a estabilidade do sistema.

**Avaliação:** ✅ Adequada

O chatbot utilizou corretamente os dados de status da rede (12 kW de 48 kW disponíveis) e foi além do esperado ao explicar o comportamento do sistema em caso de sobrecarga futura e mencionar o balanceamento dinâmico de carga.

---

## Teste 5

**Pergunta enviada:**
> Quem está usando o carregador agora?

**Resposta obtida:**
> No momento, os carregadores A2 (Unidade 302) e A5 (Unidade 108) estão sendo utilizados.

**Avaliação:** ✅ Adequada

Resposta objetiva e correta. O chatbot identificou os pontos ocupados e as unidades responsáveis sem expor dados pessoais dos moradores, respeitando a política de privacidade definida no system prompt.

---

## Resumo

| # | Pergunta | Avaliação |
|---|---|---|
| 1 | Quanto cada morador consumiu este mês? | ✅ Adequada |
| 2 | Como funciona a cobrança do carregamento? | ✅ Adequada |
| 3 | Posso carregar meu carro à noite? | ✅ Adequada |
| 4 | O sistema está sobrecarregado? | ✅ Adequada |
| 5 | Quem está usando o carregador agora? | ✅ Adequada |

**Resultado: 5/5 respostas adequadas**

### Observações gerais

- O chatbot manteve o escopo do problema GoodWe em todas as respostas, sem desviar para assuntos fora do contexto.
- Os dados simulados injetados no system prompt (consumo por unidade, status da rede, pontos ocupados e tarifa) foram utilizados corretamente em todas as respostas.
- O modelo demonstrou capacidade de ir além do mínimo esperado, trazendo informações complementares relevantes como o impacto do horário de pico e o funcionamento do balanceamento dinâmico de carga.
- A privacidade dos moradores foi respeitada em todas as interações: o chatbot identificou os usuários apenas pela unidade, nunca por nome.
