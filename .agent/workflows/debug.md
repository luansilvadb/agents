---
description: Corrigir bugs com o Agente Debugger (Engenheiro de Correção de Bugs)
---

# 🔧 Workflow: Agente DEBUG - Engenheiro de Correção de Bugs

Este workflow aciona o agente Debugger para analisar e corrigir bugs reportados.

## Quando Usar

- Após testes identificarem bugs
- Quando há erros em produção
- Para análise de causa raiz
- Para correções cirúrgicas de código

## Pré-requisitos

- Bug report com passos de reprodução
- Código fonte com o bug
- Logs/evidências (se disponíveis)

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\06-debugger.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Bug report do Tester (ou descrição do bug)
- Código fonte relevante
- Logs de erro (se houver)
- Passos para reproduzir

### Passo 3: Reprodução

O agente irá:
- Confirmar reprodução do bug
- Identificar frequência (sempre, intermitente)
- Isolar cenário mínimo

### Passo 4: Investigação

O agente aplicará:
- Análise de hipóteses
- Técnica dos 5 Porquês
- Identificação de causa raiz

### Passo 5: Correção

O agente implementará:
- Correção mínima e cirúrgica
- Teste de regressão para o bug
- Documentação da correção

### Passo 6: Validação

Verifique:
- Bug foi corrigido
- Não houve side effects
- Testes existentes ainda passam

### Passo 7: Próximo Passo

Use `/test` para re-executar testes, ou `/optimize` se tudo passou.

## Output Esperado

```yaml
bug_analysis:
  bug_id: "BUG-001"
  root_cause:
    description: "..."
    location: "file:line"
    category: "logic_error"

fix_code:
  changes:
    - file: "..."
      before: "..."
      after: "..."
  
  new_tests:
    - file: "..."
      purpose: "Prevenir regressão"

fix_report:
  bugs_fixed: 3
  escalated: 0
```

---

*DevTeam AI - Agente Debugger v1.0.0*
