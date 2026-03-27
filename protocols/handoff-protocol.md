# 🤝 Protocolo de Handoff Escalável (V5.1)

> **Princípio Core**: Handoffs são **Contratos de Serviço com Accountability**. A escalabilidade vem do desacoplamento entre quem produz e quem consome, mediados por contratos rígidos de entrada e saída, e pela **responsabilidade explícita** de cada agente sobre sua entrega.

> [!IMPORTANT]
> **Dependência Crítica**: Este protocolo EXIGE o `accountability-protocol.md` (V1.0+) para o funcionamento pleno dos portões de qualidade.

---

## 1. 📝 O Contrato de Handoff (The Contract)

Para escalar o pipeline, abandonamos a "cadeia simples" em favor de **Fases de Valor**. Cada interação entre agentes é governada por um contrato que define explicitamente:

1.  **Input Antecedente**: Requisitos mínimos para iniciar a tarefa.
2.  **Transformação de Valor**: A inteligência aplicada pelo agente.
3.  **Output Garantido**: O artefato técnico final.
4.  **Portão de Qualidade**: Critérios de Aceite (AC) e Definition of Done (DoD).
5.  **Handoff Declaration**: Prova documental de validação e clearance.

### 🏷️ Manifesto de Handoff (Metadata)
Todo handoff **DEVE** incluir meta-dados explícitos no início da mensagem de transição:

```yaml
handoff_manifest:
  id: [UUID ou Trace ID]
  source_agent: "[Nome do Agente Emissor]"
  target_phase: "[Fase ou Agente Receptor]"
  artifacts: ["lista/de/arquivos.md"]
  status: verified | draft
  trace_parent: [ID do artefato de origem]
  context_tags:
    - feature: [nome]
    - priority: [critical|high|normal]
  declaration_ref: "[Link ou Inline da Handoff Declaration]"
  clearance_status: true # Se false, o handoff é BLOQUEADO
```

> [!CAUTION]
> **REGRA DE OURO V5.1**: Sem uma `Handoff Declaration` válida com `clearance: true`, o handoff **NÃO PODE** ocorrer. O emissor é o único responsável por validar seu output ANTES de passar o bastão.

---

## 2. 🏗️ Arquitetura de Fases (Scalable Workflow)

Agrupamos o fluxo em **Fases Lógicas** para permitir paralelismo e modularidade sem quebrar a numeração do pipeline.

### Fase 1: Discovery & Strategy (O "Porquê" e "O Quê")
| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **Product Manager** | Owner de Valor | `product_backlog.md` | Priorização Value-based clara |
| **Scrum Master** | Process Owner | `sprint_plan.md` | Capacidade do time respeitada |

### Fase 2: Specification & Design (O "Como Lógico")
| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **Business Analyst** | Tradutor de Req. | `detailed_specifications.md` | Sem ambiguidade de negócio |
| **System Analyst** | Tradutor Técnico | `technical_specifications.md` | Gherkin e Contratos definidos |
| **Architect** | Estrutura | `architecture_design.md` | Diagramas C4 e ADRs |
| **UI/UX Designer** | Experiência | `ui_design_system.md` | Tokens e Acessibilidade |
| **Security Engineer**| Design Seguro | `security_policies.md` | Threat Model validado |

### Fase 3: Construction (A Materialização)
| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **Tech Lead** | Estratégia Téc. | `implementation_plan.md` | Decomposição atômica de tasks |
| **Senior Dev** | Implementador | `src/*` | SOLID, Clean Code e Build Pass |

### Fase 4: Quality & Delivery (A Garantia)
| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **QA Engineer** | Testes | `test_report.md` | Cobertura > 80%, 0 Critical Bugs |
| **Security Val** | Auditoria | `security_validation_report.md` | SAST/DAST limpos e Veredito |
| **Tech Writer** | Documentação | `docs/*` & `README.md` | Documentação "User-ready" |
| **Support Eng** | Feedback | `feedback_report.md` | Lições aprendidas extraídas |

---

## 3. 🛑 Protocolo de Rejeição (Circuit Breaker)

Erros não devem propagar. Implemente o padrão **Circuit Breaker** no handoff:

1.  **Fast Fail**: Se o input não atende ao contrato, **NÃO TENTE** corrigir.
2.  **Return to Sender**: Devolva o artefato imediatamente com a tag `#REJECTED`.
3.  **Feedback Estruturado**: Forneça uma justificativa técnica clara.

> ✅ **Best Practice (Rejeição)**:
> "# FALHA DE CONTRATO: Faltam critérios de aceite no Gherkin da US-01. Bloqueia a geração dos testes automatizados. Favor corrigir na Fase 2."

---

## 4. 🔌 Estendendo o Protocolo (Plugins)

Para adicionar novos especialistas (ex: DevOps, AI Ethics):
1.  **Identifique** a Fase de atuação.
2.  **Defina** o Contrato (Inputs/Outputs).
3.  **Conecte** ao fluxo sem renumerar, apenas ajustando dependências.

---

## 5. 🤝 Integração com Accountability Protocol

### 5.1 Fluxo de Handoff Auditável
1. **Finalização**: Agente conclui a tarefa técnica.
2. **Self-Validation**: Executa o checklist obrigatório de saída.
3. **Declaration**: Gera a `Handoff Declaration` (Accountability).
4. **Clearance Check**:
   - Se `true` → **EXECUTE** o Handoff Manifest.
   - Se `false` → **BLOQUEIE** a transição e escale para o Orquestrador.
5. **Recepção**: O receptor valida a Declaration recebida antes de aceitar.

### 5.2 Matriz de Responsabilidade de Handoff

| Ator | Responsabilidade Mandatória |
| :--- | :--- |
| **Emissor** | **PROVAR** a entrega correta via Declaration válida. |
| **Receptor** | **VALIDAR** o recebido contra o esperado antes do aceite. |
| **Orquestrador** | **MEDIAR** bloqueios e resolver falhas de clearance. |

---
*DevTeam AI - Scalable Modular Protocol V5.1 with Accountability*
