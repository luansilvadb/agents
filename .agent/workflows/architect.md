---
description: Definir arquitetura de software com o Agente Architect (Arquiteto de Software)
---

# 🏗️ Workflow: Agente ARCHITECT - Arquiteto de Software

Este workflow aciona o agente Architect para definir arquitetura, stack tecnológico e contratos de API.

## Quando Usar

- Após ter especificações de requisitos
- Quando precisa definir stack tecnológico
- Para criar ADRs (Architecture Decision Records)
- Para definir contratos de API

## Pré-requisitos

- User stories com critérios de aceite
- Requisitos não-funcionais (NFRs)
- Ou descrição clara do que precisa ser construído

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\03-architect.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- User stories e acceptance criteria
- Requisitos não-funcionais
- Restrições técnicas conhecidas
- Preferências de stack (se houver)

### Passo 3: Revisar ADRs

Para cada decisão arquitetural:
- Contexto e problema
- Decisão tomada
- Alternativas consideradas
- Trade-offs aceitos

### Passo 4: Validar Stack

Verifique o stack tecnológico:
- Frontend (framework, linguagem)
- Backend (linguagem, framework)
- Database (tipo, tecnologia)
- Infraestrutura

### Passo 5: Revisar Contratos

Valide contratos de API:
- Endpoints e métodos
- Request/Response schemas
- Códigos de status
- Autenticação

### Passo 6: Próximo Agente

Após validar, use `/code` para continuar o pipeline.

## Output Esperado

```yaml
adr:
  id: "ADR-001"
  title: "[Decisão]"
  decision: "..."
  rationale: "..."

tech_stack:
  frontend: {...}
  backend: {...}
  database: {...}

api_contracts:
  endpoints: [...]

data_model:
  entities: [...]
```

---

*DevTeam AI - Agente Architect v1.0.0*
