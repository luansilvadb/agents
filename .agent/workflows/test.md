---
description: Criar e executar testes com o Agente Tester (Engenheiro de QA)
---

# 🧪 Workflow: Agente TEST - Engenheiro de QA

Este workflow aciona o agente Tester para criar suíte de testes e validar o código.

## Quando Usar

- Após ter código implementado
- Quando precisa criar testes automatizados
- Para validar critérios de aceite
- Para identificar bugs antes do deploy

## Pré-requisitos

- Código fonte implementado
- Critérios de aceite (acceptance criteria)
- Requisitos não-funcionais

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\05-tester.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Código fonte a ser testado
- Critérios de aceite das user stories
- Requisitos de cobertura

### Passo 3: Testes Unitários

O agente criará testes unitários para:
- Funções e métodos críticos
- Lógica de negócio
- Validações

### Passo 4: Testes de Integração

O agente criará testes de integração para:
- Endpoints de API
- Fluxos entre componentes
- Integrações com banco de dados

### Passo 5: Revisar Relatório

Verifique o relatório de testes:
- Total de testes (passou/falhou)
- Cobertura de código
- Critérios de aceite validados

### Passo 6: Se Houver Bugs

Se o relatório indicar bugs:
- **Bugs Simples (Fast-Fix)**: Use `/reject_fast` para devolver ao Auto-Coder.
- **Bugs Complexos**: Use `/debug` para acionar o Debugger.

### Passo 7: Se Tudo Passou

Se todos os testes passaram, use `/optimize` para continuar.

## Output Esperado

```yaml
test_report:
  summary:
    total: 45
    passed: 42
    failed: 3
  coverage:
    lines: "84%"

bug_report:
  bugs:
    - id: "BUG-001"
      severity: "high"
      description: "..."
```

```
tests/
├── unit/
├── integration/
└── e2e/
```

---

*DevTeam AI - Agente Tester v1.0.0*
