---
description: Criar especificações técnicas com o Agente Specification Writer (Analista de Requisitos)
---

# 📝 Workflow: Agente SPECIFICATION - Analista de Requisitos

Este workflow aciona o agente Specification Writer para criar user stories e especificações técnicas.

## Quando Usar

- Após ter requisitos de negócio definidos
- Quando precisa criar user stories detalhadas
- Para definir critérios de aceite testáveis
- Para especificar requisitos não-funcionais

## Pré-requisitos

- `business_requirements.yaml` do agente Ask
- Ou descrição clara dos requisitos de negócio

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\02-specification-writer.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Requisitos de negócio (output do Ask)
- Personas e stakeholders identificados
- Restrições conhecidas

### Passo 3: Revisar User Stories

Para cada user story gerada, verifique:
- Formato "Como [persona], quero [ação], para [benefício]"
- Critérios de aceite em Given-When-Then
- Edge cases e cenários de erro
- Priorização (must/should/could)

### Passo 4: Validar NFRs

Verifique requisitos não-funcionais:
- Performance (com métricas mensuráveis)
- Segurança
- Usabilidade
- Escalabilidade

### Passo 5: Próximo Agente

Após validar, use `/architect` para continuar o pipeline.

## Output Esperado

```yaml
user_stories:
  - id: "US-001"
    title: "[Título]"
    story: "Como... quero... para..."
    acceptance_criteria:
      - id: "AC-001-01"
        given: "..."
        when: "..."
        then: "..."

non_functional_requirements:
  performance: [...]
  security: [...]
  usability: [...]
```

---

*DevTeam AI - Agente Specification Writer v1.0.0*
