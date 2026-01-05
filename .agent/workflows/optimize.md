---
description: Otimizar performance com o Agente Optimizer (Engenheiro de Performance)
---

# ⚡ Workflow: Agente OPTIMIZE - Engenheiro de Performance

Este workflow aciona o agente Optimizer para analisar e otimizar performance do código.

## Quando Usar

- Após código estar funcional e testado
- Quando performance não atende NFRs
- Para identificar gargalos
- Para reduzir tempo de resposta ou uso de recursos

## Pré-requisitos

- Código fonte funcional
- Requisitos não-funcionais de performance
- Ambiente para benchmarks

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\07-optimizer.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Código fonte a otimizar
- NFRs de performance (targets)
- Métricas atuais (se conhecidas)
- Gargalos suspeitos

### Passo 3: Baseline

O agente irá:
- Medir performance atual
- Identificar métricas chave
- Comparar com targets dos NFRs

### Passo 4: Profiling

O agente analisará:
- CPU hotspots
- Uso de memória
- Queries lentas
- Operações de I/O

### Passo 5: Otimizações

O agente implementará:
- Otimização de queries
- Caching strategies
- Paralelização
- Otimização de algoritmos

### Passo 6: Benchmark

Verifique:
- Métricas antes/depois
- Compliance com NFRs
- Trade-offs aceitos

### Passo 7: Próximo Agente

Use `/deploy` para preparar para produção.

## Output Esperado

```yaml
performance_analysis:
  baseline:
    response_time_p95: "450ms"
    throughput: "100 req/s"
  
  nfr_compliance:
    - nfr_id: "NFR-PERF-001"
      target: "< 200ms"
      current: "450ms"
      status: "not_met"

optimization_report:
  before_after:
    - metric: "Response Time P95"
      before: "450ms"
      after: "120ms"
      status: "met"
  
  optimizations_applied:
    - id: "OPT-001"
      type: "caching"
      impact: "73% improvement"
```

---

*DevTeam AI - Agente Optimizer v1.0.0*
