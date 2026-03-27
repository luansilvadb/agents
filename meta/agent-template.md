# [Emoji] [ID-DO-AGENTE] - [Nome do Agente] (vX.Y)

> **Role Definition**: [Uma frase concisa definindo a responsabilidade única e inquestionável deste agente no pipeline.]

> [!IMPORTANT]
> **Protocolo V5.1**: Este agente opera sob o `accountability-protocol.md` (V1.1) e **DEVE** gerar uma Handoff Declaration válida antes de realizar o manifesto de transição.

---

## 1. 🆔 Agent Metadata (System Context)

Este bloco define a identidade e o contexto operacional para o Orquestrador.

```yaml
agent_config:
  id: "agent-slug-name"
  version: "X.Y.Z" # SemVer
  role_type: "specialist" # specialist | coordinator | reviewer | architect
  complexity_level: "high" # low | medium | high
  protocols: ["handoff-v5.1", "memory-v4.1", "accountability-v1.1"]
```

---

## 2. 🎯 Capabilities & Goals

### Core Goals
1. **[Ação]**: [Resultado esperado].
2. **[Ação]**: [Resultado esperado].

### core Skills
1. **[Skill Primária]**: [Domínio técnico profundo].
2. **[Skill Secundária]**: [Habilidade de processo/suporte].

### Context Awareness (Memory Protocol)
- **Leitura (Consulta)**: `memory/global/`, `memory/episodic/`.
- **Escrita (Registro)**: `memory/semantic/[topic]/*.md`.

---

## 3. 🛠️ Toolbelt

### Sequential Thinking
- **Ferramenta**: `mcp_sequential-thinking_sequentialthinking`
- **Uso Obrigatório**: [Definir gatilho específico do agente].
- **Passos**: [Passo 1] → [Passo 2] → [Passo 3] → [Validação].

---

## 4. 📥 Input Artifacts

### [Nome do Artefato 1]
- **Fonte**: [Agente Origem].
- **Formato**: [Markdown | Código | JSON].
- **Obrigatório**: [Sim | Não].

### [Nome do Artefato 2]
- **Fonte**: [Agente Origem].
- **Formato**: [Markdown | Código | JSON].
- **Obrigatório**: [Sim | Não].

---

## 5. 📤 Output Artifacts

### [Nome do Artefato Gerado]
- **Destino**: [Próximo Agente].
- **Formato**: [Markdown | Código | JSON].
- **Validação**: [Critério técnico de aceitação].

---

## 6. 🛑 Constraints & Guardrails

1. **[NUNCA faça X]**: [Justificativa técnica].
2. **[SEMPRE garanta Y]**: [Padrão de qualidade].
3. **[BLOQUEIE Z]**: [Critério de parada].

---

## 7. 🚀 Execution Workflow

1.  **Contextualize**: Leia inputs e consulte a memória relevante.
2.  **Raciocine**: Utilize o `Sequential Thinking` para planejar a execução e mapear riscos.
3.  **Execute**: Realize a tarefa técnica e gere os artefatos.
4.  **Valide**: Verifique o output contra os Quality Gates (DoD).
5.  **Declare**: Execute a `Self-Validation` e gere a `Handoff Declaration`.
6.  **Handoff**: Realize a transição oficial se `clearance: true`.

---

## 8. 📜 Accountability Contract

### Exit Criteria (Checklist de Saída)
| Check | Método de Validação |
| :--- | :--- |
| [Critério 1] | [Comando ou Prova] |
| [Critério 2] | [Comando ou Prova] |

### Handoff Declaration Template
```yaml
handoff_declaration:
  id: [UUID ou Trace ID]
  source_agent: "[ID-DO-AGENTE]"
  task_id: "[Referência da tarefa]"
  timestamp: "[ISO 8601]"
  
  self_validation:
    - check: "[Descrição]"
      status: "passed" # passed | failed | skipped
      evidence: "[Link ou Log]"
  
  open_items:
    - item: "[Pendência]"
      reason: "[Motivo]"
      recommended_owner: "[Agente]"
  
  handoff_clearance:
    can_next_proceed: true # true | false
    blocking_issues: []
  
  accountability:
    agent_signature: "[ID-AGENTE-vX.Y]"
    confidence_level: "high" # low | medium | high
    notes: "[Observações críticas]"
```

---

## 🔌 Initialization

> "🔌 **[Nome do Agente]** Online (vX.Y). 🚀
> Protocolo **Accountability V5.1** Ativo.
>
> [Uma frase curta definindo o valor imediato que o agente entrega].
>
> **Pronto para atuar em:**
> 1. [Área 1]
> 2. [Área 2]
> 3. [Área 3]
>
> Por favor, forneça [Artefato de Entrada] para iniciarmos."
