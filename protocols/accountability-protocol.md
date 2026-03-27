# 🔒 Protocolo de Accountability (V1.1)

> **Princípio Core**: Nenhum agente pode passar o bastão sem **DECLARAR explicitamente** o que validou e assumir **responsabilidade pessoal** pelo que entrega. Isso transforma especialistas de "roteadores de texto" em "donos de domínio".

---

## 1. 🧩 O Problema: Passagem de Bastão Sem Ownership

### Anti-Pattern: A "Cadeia de Indiferença"
```text
❌ Agente A executa → passa para B sem validar.
❌ Agente B executa → passa para C sem validar.
❌ Erro aparece em D → Ninguém sabe a causa raiz.
```

**Consequência**: Sem elicitação e declaração explícita, os agentes perdem o senso de "Definition of Done" (DoD) e o sistema torna-se inaudito e frágil.

---

## 2. 🚦 Elicitação Obrigatória (Pre-Execution Gate)

**ANTES** de iniciar qualquer tarefa, o agente **DEVE** responder internamente (ou em seu Sequential Thinking) aos seguintes critérios:

```yaml
pre_execution_elicitation:
  success_criteria:
    - "O que precisa estar verdadeiro para eu considerar sucesso?"
    - "Quais são os critérios de aceite ESPECÍFICOS desta tarefa?"
  
  blocking_conditions:
    - "O que me impediria de entregar com qualidade máxima?"
    - "Quais dependências críticas precisam estar prontas?"
  
  handoff_requirements:
    - "O que o próximo agente precisa exatamente de mim?"
    - "Em que formato e com que garantias de validade?"
```

> [!IMPORTANT]
> **REGRA DE OURO**: Se você não sabe o que é sucesso para sua tarefa, você **NÃO PODE** começar a executá-la.

---

## 3. 📜 Handoff Declaration (Post-Execution Gate)

Todo agente **DEVE** gerar uma **Handoff Declaration** antes de realizar o manifesto de transição.

### Padrão de Metadados (Auditável)
```yaml
handoff_declaration:
  # Identificação Única (Alinhado à Observabilidade)
  id: [UUID ou Trace ID]
  source_agent: "[Nome do Agente]"
  task_id: "[ID da tarefa executada]"
  timestamp: "[ISO 8601]"
  
  # GATE 1: O que EU validei (Self-Validation)
  self_validation:
    - check: "[Descrição do item verificado]"
      status: "passed" # passed | failed | skipped
      evidence: "[Comando, log ou referência técnica]"
  
  # GATE 2: O que NÃO pude validar (Transparência)
  open_items:
    - item: "[Descrição da pendência]"
      reason: "[Justificativa técnica para não validação]"
      recommended_owner: "[Agente responsável pela resolução]"
  
  # GATE 3: Liberação para Próximo Agente (Clearance)
  handoff_clearance:
    can_next_proceed: true # true | false
    blocking_issues: [] # Lista de impedimentos se clearance=false
  
  # Assinatura de Accountability
  accountability:
    agent_signature: "[ID-AGENTE-vX.Y]"
    confidence_level: "high" # low | medium | high
    notes: "[Observações críticas para o sucessor]"
```

---

## 4. 🔄 Fluxo de Validação Dual (Check & Balance)

O sistema de Accountability opera em duas frentes mandatórias:

1. **Gate de Saída (Emissor)**: Executa a `Self-Validation` e gera a `Declaration`.
2. **Gate de Entrada (Receptor)**: **VALIDE** a `Declaration` recebida antes de aceitar os artefatos.

> [!CAUTION]
> **REJEITE** qualquer entrega que não possua uma Declaration válida ou que apresente `clearance: false` sem um plano de mitigação aprovado.

---

## 5. ⚖️ Matriz de Responsabilidade Mandatória

| Atividade de Validação | Responsável (Owner) | Evidência de Sucesso |
| :--- | :--- | :--- |
| **Sintaxe / Linting** | Desenvolvedor | `npm run lint` ou similar |
| **Testes Unitários** | Desenvolvedor | `npm test` (Status: Passed) |
| **Integridade do Build** | Desenvolvedor / CI | Build sem erros fatais |
| **Segurança (SAST)** | Security Validation | Relatório de Veredito limpo |
| **Contrato de API** | System Analyst | Mock/Spec validado |
| **Documentação** | Technical Writer | README e Docs atualizados |

---

## 6. 🚨 Regras de Escalação (Escalation Protocol)

### Quando BLOQUEAR (`clearance = false`)
- [ ] Testes falhando ou intermitentes (Flakiness).
- [ ] Build quebrado ou ambiente instável.
- [ ] Violação explícita de qualquer Contrato de Handoff.
- [ ] Requisito ambíguo detectado durante a execução.

### Quando ESCALAR (Solicitar Intervenção)
- [ ] Bloqueio técnico sem solução imediata prevista.
- [ ] Conflito de prioridades entre o PO (Negócio) e o Architect (Técnico).
- [ ] Risco de segurança crítico identificado fora do escopo da task.

### Template de Escalação
```markdown
## 🚨 ESCALAÇÃO REQUERIDA
- **Agente**: [Quem escala]
- **Impedimento**: [Por que a tarefa parou]
- **Impacto**: [O que fica bloqueado]
- **Proposta**: [Caminho sugerido para resolução]
- **Destino**: [Tech Lead | Architect | PO]
```

---

## 7. 🧾 Auditoria e Melhoria Contínua

As Handoff Declarations formam o **Trail de Accountability** do projeto:

1. **Rastreabilidade**: Se um erro atinge produção, **IDENTIFIQUE** qual Declaration aprovou a passagem indevida.
2. **Post-Mortem**: **ANALISE** por que um check de validação foi marcado como `passed` quando deveria ser `failed`.
3. **Refinamento**: Adicione novos itens à `self_validation` baseando-se em lições aprendidas de falhas reais.

---

## 8. 🔗 Integração com Protocolos do Sistema

| Protocolo | Integração de Accountability |
| :--- | :--- |
| **Handoff V5.1** | A Declaration é o documento oficial de transição. |
| **Memory Protocol** | Declarations críticas são salvas na camada `episodic/`. |
| **Observability** | O Sequential Thinking deve culminar na geração da Declaration. |

---
*DevTeam AI - "Ownership is not given, it's declared."* - V1.1
