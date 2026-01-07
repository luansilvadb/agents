# Protocolo de Handoff Escalável (V5.0)

> **Core Philosophy**: Handoffs são **Contratos de Serviço com Accountability**. A escalabilidade vem do desacoplamento entre quem produz e quem consome, mediados por contratos rígidos de entrada e saída, E pela **responsabilidade explícita** de cada agente sobre o que entrega.

> ⚠️ **Dependência Crítica**: Este protocolo REQUER o `accountability-protocol.md` (V1.0+) para funcionar corretamente.

## 1. O Contrato de Handoff (The Contract)

Para escalar o pipeline, abandonamos a "cadeia simples" em favor de **Fases de Valor**. Cada interação entre agentes é governada por um contrato que define explicitamente:

1.  **Input Antecedente** (O que eu preciso para começar)
2.  **Transformação de Valor** (O que eu faço)
3.  **Output Garantido** (O que eu entrego)
4.  **Portão de Qualidade** (Critérios de Aceite/DoD)
5.  **🆕 Handoff Declaration** (Prova de validação + clearance)

### Estrutura do Artefato de Handoff
Todo handoff DEVE incluir meta-dados explícitos:

```yaml
handoff_manifest:
  source_agent: "[Nome do Agente]"
  target_phase: "[Próxima Fase/Agente]"
  artifacts: ["lista/de/arquivos.md"]
  validation_status: "verified" # só entregar se verificado
  context_tags: ["feature-x", "fix", "critical"]
  
  # 🆕 OBRIGATÓRIO - Referência ao Accountability Protocol
  declaration_ref: "[link ou inline da Handoff Declaration]"
  clearance_status: true # Se false, handoff é BLOQUEADO
```

### 🆕 Regra de Ouro do Handoff V5.0
> **Sem Declaration válida com `clearance: true`, o handoff NÃO PODE ocorrer.**
> O agente predecesssor é responsável por validar seu próprio output ANTES de passar.

## 2. Arquitetura de Fases (Scalable Workflow)

Em vez de passos lineares rígidos (1..14), agrupamos o fluxo em **Fases Lógicas**. Isso permite paralelismo (ex: UI e Arquitetura ocorrendo simultaneamente) e facilita adicionar novos agentes especialistas sem quebrar a numeração.

### Fase 1: Discovery & Strategy (O "Porquê" e "O Quê")
| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **Product Manager** | Owner de Valor | `product_backlog.md` | Priorização Value-based clara |
| **Scrum Master** | Process Owner | `sprint_plan.md` | Capacidade do time respeitada |

### Fase 2: Specification & Design (O "Como Lógico")
_Nesta fase, múltiplos especialistas podem trabalhar em paralelo após a Especificação Funcional._

| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **Business Analyst** | Tradutor de Req. | `detailed_specifications.md` | Sem ambiguidade de negócio |
| **System Analyst** | Tradutor Técnico | `technical_specifications.md` | Gherkin/Contratos definidos |
| **Architect** | Estrutura | `architecture_design.md` | Diagramas C4 / Decisões ADR |
| **UI/UX Designer** | Experiência | `ui_design_system.md` | Tokens e Acessibilidade |
| **Security Engineer**| Design Seguro | `security_policies.md` | Threat Model validado |

### Fase 3: Construction (A Materialização)
| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **Tech Lead** | Estratégia Téc. | `implementation_plan.md` | Decomposição atômica de tasks |
| **Senior Dev** | Implementador | `src/*` | Clean Code, SOLID, Build Pass |
| **DBA** | Dados | `database/*` | Normalização, Migrations Idempotentes |

### Fase 4: Quality & Delivery (A Garantia)
| Agente | Role | Output Principal | Validação (DoD) |
| :--- | :--- | :--- | :--- |
| **QA Engineer** | Testes | `test_report.md` | Cobertura > 80%, 0 Critical Bugs |
| **Security Val** | Pentest/Audit | `security_val_report.md` | SAST/DAST limpos |
| **Tech Writer** | Doc | `docs/*` & `README.md` | Documentação "User-ready" |
| **Support Eng** | Feedback Loop | `feedback_report.md` | Lições aprendidas para Fase 1 |

## 3. Protocolo de Rejeição (Circuit Breaker)

Para manter a escalabilidade, erros não devem propagar. Implementamos o padrão **Circuit Breaker** no handoff:

1.  **Fast Fail**: Se o `Input` não atende ao contrato, o agente **NÃO TENTA CORRIGIR**.
2.  **Return to Sender**: O artefato é devolvido imediatamente com tag `#REJECTED`.
3.  **Feedback Estruturado**:
    ```markdown
    # FALHA DE CONTRATO DETECTADA
    - **Violação**: [Descrever ex: Falta de Critério de Aceite]
    - **Impacto**: Bloqueia geração de testes unitários.
    - **Correção Necessária**: Adicionar seção "Scenario" no Gherkin.
    ```

## 4. Estendendo o Protocolo (Plugins)

Para adicionar novos agentes (ex: um "DevOps Engineer" ou "AI Ethics Officer"):
1.  Identifique em qual **Fase** ele atua.
2.  Defina seus Inputs e Outputs no formato de **Contrato**.
3.  Insira-o no fluxo sem precisar renumerar todo o pipeline, apenas ajustando as dependências de entrada/saída.

## 5. 🆕 Integração com Accountability Protocol

### 5.1 Fluxo de Handoff com Accountability

```
[Agente A finaliza tarefa]
         ↓
[Self-Validation: Executa checklist de saída]
         ↓
[Gera Handoff Declaration]
         ↓
    ┌────┴────┐
    │clearance│
    │= true?  │
    └────┬────┘
    SIM  │  NÃO
    ↓    │    ↓
[Passa]  │  [BLOQUEIA]
    ↓    │    ↓
[Agente B]  [Escala para Orquestrador]
    ↓
[Valida Declaration recebida]
    ↓
[Aceita ou Rejeita com feedback]
```

### 5.2 Responsabilidades no Handoff

| Agente | Responsabilidade | Ação Obrigatória |
|--------|-----------------|------------------|
| **Emissor** | Provar que entregou corretamente | Gerar Declaration válida |
| **Receptor** | Validar que recebeu o esperado | Verificar Declaration |
| **Orquestrador** | Mediar bloqueios | Resolver escalações |

### 5.3 Critérios de Clearance

O campo `clearance_status` só pode ser `true` se:

- [ ] Todos os itens da `self_validation` são `passed` ou `skipped` com justificativa
- [ ] `open_items` não contém itens críticos sem owner
- [ ] O output atende ao contrato definido na seção 1

### 5.4 Referência Cruzada

Para detalhes completos sobre:
- Formato da Handoff Declaration → Ver `accountability-protocol.md`
- Regras de escalação → Ver `accountability-protocol.md#escalação`
- Auditoria de declarations → Ver `accountability-protocol.md#auditoria`

---
*DevTeam AI - Scalable Modular Protocol V5.0 with Accountability*
