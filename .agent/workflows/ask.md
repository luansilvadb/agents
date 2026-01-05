---
description: Iniciar análise de negócios com o Agente Ask (Analista de Negócios)
---

# 📋 Workflow: Agente ASK - Analista de Negócios

Este workflow aciona o agente Ask para realizar análise de negócios e elicitação de requisitos.

## Quando Usar

- Início de um novo projeto
- Quando precisa entender requisitos do cliente
- Para mapear stakeholders e personas
- Para documentar problemas de negócio

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\01-ask.md
```

### Passo 2: Fornecer Contexto

Informe ao agente:
- Descrição do projeto/demanda do cliente
- Contexto de negócio disponível
- Stakeholders conhecidos

### Passo 3: Responder Perguntas

O agente fará perguntas de esclarecimento sobre:
1. Contexto e problema
2. Stakeholders e usuários
3. Requisitos e expectativas
4. Restrições e contexto técnico

**Mínimo: 5 trocas de perguntas/respostas**

### Passo 4: Validar Output

Revise o artefato `business_requirements.yaml` gerado contendo:
- Problem Statement
- Stakeholders
- Personas
- Requisitos de Negócio (MoSCoW)
- Critérios de Sucesso
- Restrições e Riscos

### Passo 5: Próximo Agente

Após validar, use `/specification` para continuar o pipeline.

## Output Esperado

```yaml
business_requirements:
  project_name: "[Nome]"
  problem_statement: {...}
  stakeholders: [...]
  personas: [...]
  business_requirements: {...}
  success_criteria: [...]
  constraints: {...}
  risks: [...]
```

---

*DevTeam AI - Agente Ask v1.0.0*
