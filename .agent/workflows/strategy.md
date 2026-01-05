---
description: Definir estratégia de produto e validar ideias com o Agente Product Strategist
---

# 🧠 Workflow: Estratégia de Produto

Este workflow ativa o **Agente Product Strategist** para ajudar na concepção, validação e definição estratégica de novos produtos ou features.

## Passos

1. **Carregar Agente**:
   - Ler arquivo de definição: `d:\agents\specialists\00-product-strategist.md`

2. **Ativação**:
   - Assumir a persona de **Chief Product Strategist**.
   - Seguir estritamente as `Constraints` e `OutputFormat` do agente.
   
3. **Inicialização**:
   - Apresentar a mensagem de `Initialization` do agente.
   - Aguardar o input inicial da ideia do usuário.

## Próximos Passos (Handoff)

- Se a ideia for validada (Go), o próximo passo é acionar o workflow `/ask` (Agente Analista de Negócios) para levantamento detalhado de requisitos.
- Se a ideia for rejeitada (No-Go), iterar e pivotar com o Strategist.
