# 🔒 Protocolo de Accountability (V1.0)

> **Princípio Core**: Nenhum agente pode passar o bastão sem **DECLARAR explicitamente** o que validou e assumir **responsabilidade pessoal** pelo que entrega. Isso transforma especialistas de "roteadores de texto" em "donos de domínio".

## 1. O Problema que Este Protocolo Resolve

### Anti-Pattern: "Passagem de Bastão Sem Ownership"
```
❌ Agente A executa → passa para B sem validar
❌ Agente B executa → passa para C sem validar
❌ Erro aparece em D → Quem causou? Ninguém sabe.
```

**Causa Raiz**: Sem elicitação explícita, o agente não sabe:
- O que é sucesso para sua tarefa
- O que precisa garantir antes de entregar
- O que deve bloquear e escalar

**Resultado**: Especialistas viram meros "routers de texto".

---

## 2. Elicitação Obrigatória (Pre-Execution Gate)

**ANTES** de executar qualquer tarefa, o agente DEVE responder internamente:

```yaml
pre_execution_elicitation:
  success_criteria:
    - "O que precisa estar verdadeiro para eu considerar sucesso?"
    - "Quais são os critérios de aceite ESPECÍFICOS desta tarefa?"
  
  blocking_conditions:
    - "O que me impediria de entregar?"
    - "Quais dependências preciso que estejam prontas?"
  
  handoff_requirements:
    - "O que o próximo agente precisa de mim?"
    - "Em que formato e com que garantias?"
```

> **Regra de Ouro**: Se você não sabe o que é sucesso, você não pode entregar sucesso.

---

## 3. Handoff Declaration (Post-Execution Gate)

### Formato Obrigatório
Todo agente DEVE gerar uma **Handoff Declaration** antes de passar o bastão:

```yaml
handoff_declaration:
  # Identificação
  source_agent: "[Nome do Agente]"
  task_id: "[ID da tarefa executada]"
  timestamp: "[ISO 8601]"
  
  # GATE 1: O que EU validei (Self-Validation)
  self_validation:
    - check: "[Descrição do que foi verificado]"
      status: "passed" # passed | failed | skipped
      evidence: "[Link, comando, ou referência]"
    - check: "[Outro item validado]"
      status: "passed"
      evidence: "[Evidência]"
  
  # GATE 2: O que NÃO pude validar (Transparência)
  open_items:
    - item: "[Descrição do que não foi validado]"
      reason: "[Por que não foi possível]"
      recommended_owner: "[Quem deveria resolver]"
  
  # GATE 3: Liberação para Próximo Agente
  handoff_clearance:
    can_next_proceed: true # true | false
    blocking_issues: [] # Lista vazia se true
    # Se false, listar:
    # - "[Issue 1 que bloqueia]"
    # - "[Issue 2 que bloqueia]"
  
  # Assinatura de Accountability
  accountability:
    agent_signature: "[ID-AGENTE-vX.Y]"
    confidence_level: "high" # low | medium | high
    notes: "[Observações importantes para o próximo]"
```

### Exemplo Real

```yaml
handoff_declaration:
  source_agent: "Senior Developer"
  task_id: "TASK-AUTH-042"
  timestamp: "2024-03-20T15:30:00Z"
  
  self_validation:
    - check: "Testes unitários passando"
      status: "passed"
      evidence: "npm test → 47 passed, 0 failed"
    - check: "Linter sem erros"
      status: "passed"
      evidence: "npm run lint → 0 errors"
    - check: "Build de desenvolvimento"
      status: "passed"
      evidence: "npm run dev → Server started on :3000"
  
  open_items:
    - item: "Teste de integração com banco de produção"
      reason: "Sem acesso ao ambiente de staging"
      recommended_owner: "QA Engineer"
    - item: "Validação de performance sob carga"
      reason: "Fora do escopo desta task"
      recommended_owner: "Tech Lead"
  
  handoff_clearance:
    can_next_proceed: true
    blocking_issues: []
  
  accountability:
    agent_signature: "SeniorDev-v3.1"
    confidence_level: "high"
    notes: "Implementação completa. Edge cases cobertos. Pronto para QA."
```

---

## 4. Fluxo de Validação Dual (Entrada + Saída)

```
┌─────────────────────────────────────────────────────────────┐
│                      AGENTE A                               │
│                                                             │
│  [1. Recebe Input]                                          │
│       ↓                                                     │
│  [2. GATE DE ENTRADA: Valida se input atende contrato]     │
│       ↓ (se OK)                                             │
│  [3. Elicitação: Define critérios de sucesso]              │
│       ↓                                                     │
│  [4. Execução da Tarefa]                                   │
│       ↓                                                     │
│  [5. GATE DE SAÍDA: Self-Validation Checklist]             │
│       ↓                                                     │
│  [6. Gera Handoff Declaration]                             │
│       ↓                                                     │
│  [7. clearance=true?]─────────────────────────────────┐    │
│       │ SIM                                      NÃO  │    │
│       ↓                                           ↓   │    │
│  [Passa para Agente B]              [BLOQUEIA + Escala]    │
└─────────────────────────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────────────────────────┐
│                      AGENTE B                               │
│                                                             │
│  [1. Recebe Declaration + Artefatos]                       │
│       ↓                                                     │
│  [2. GATE DE ENTRADA: Valida Declaration]                  │
│       ↓                                                     │
│  [3. Declaration.clearance = true?]                        │
│       │ SIM                                      NÃO       │
│       ↓                                           ↓        │
│  [Aceita e Executa]              [Rejeita com #REJECTED]   │
└─────────────────────────────────────────────────────────────┘
```

---

## 5. Matriz de Responsabilidade

| Validação | Responsável Primário | Backup | Evidência Esperada |
|-----------|---------------------|--------|-------------------|
| **Sintaxe/Linter** | Dev que escreveu | Tech Lead | `npm run lint` |
| **Testes Unitários** | Dev que escreveu | QA | `npm test` |
| **Build** | Dev que escreveu | CI/CD | `npm run build` |
| **Arquitetura** | Tech Lead | Architect | Diagrama atualizado |
| **Segurança Básica** | Dev que escreveu | Security Eng | Checklist OWASP |
| **Integração** | QA Engineer | Dev | Testes E2E |
| **Documentação** | Technical Writer | Dev | README atualizado |

---

## 6. Regras de Escalação

### Quando Bloquear (clearance = false)
- [ ] Testes falhando
- [ ] Build quebrado
- [ ] Violação de contrato de entrada/saída
- [ ] Requisito ambíguo não resolvido
- [ ] Dependência externa indisponível

### Quando Escalar
- [ ] Bloqueio sem solução imediata
- [ ] Conflito entre requisitos
- [ ] Decisão arquitetural necessária
- [ ] Risco de segurança identificado

### Template de Escalação
```markdown
## 🚨 ESCALATION REQUIRED

- **Agent**: [Quem está escalando]
- **Task**: [ID e descrição]
- **Block Reason**: [Por que não pode prosseguir]
- **Impact**: [O que fica parado]
- **Suggested Resolution**: [Proposta, se houver]
- **Escalate To**: [Quem pode resolver: Tech Lead / Architect / PO]
```

---

## 7. Auditoria e Post-Mortem

### Trail de Accountability
Todas as Handoff Declarations devem ser armazenadas ou referenciadas para permitir:

1. **Rastreamento de Origem**: Se um bug aparece em Produção, podemos rastrear qual Declaration aprovou a passagem.

2. **Post-Mortem Estruturado**:
   - Qual agente declarou "clearance: true" indevidamente?
   - Qual validação foi "skipped" e deveria ter sido "passed"?
   - Quais "open_items" se materializaram em problemas?

3. **Melhoria Contínua**: Patterns de falha alimentam novos checks na self_validation.

---

## 8. Integração com Outros Protocolos

| Protocolo | Integração |
|-----------|-----------|
| **Handoff V4.0** | Declaration é o "manifesto" da transição |
| **Memory Protocol** | Declarations significativas vão para `episodic/` |
| **Observability** | Sequential Thinking deve culminar em Declaration |

---

*DevTeam AI - "Ownership is not given, it's declared."* - V1.0
