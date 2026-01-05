# 👁️ Protocolo de Observabilidade e Auditoria (v1.0)

> "Se não está nos logs, não aconteceu."

Este protocolo define os padrões obrigatórios para registro de atividades, raciocínio (Chain of Thought) e estado de saúde dos agentes no ecossistema DevTeam AI. O objetivo é garantir **reprodutibilidade**, **debugabilidade** e **auditabilidade** das decisões autônomas.

## 1. Princípios Fundamentais

1.  **Imutabilidade**: Logs nunca devem ser alterados ou apagados durante a execução de um projeto.
2.  **Transparência Cognitiva**: Todo agente deve logar não apenas O QUÊ fez, mas POR QUE fez (Rationale).
3.  **Estrutura Uniforme**: Todos os logs devem seguir o formato JSON estruturado definido neste protocolo.
4.  **Traceability**: Cada ação deve estar vinculada a um `trace_id` que permeia toda a cadeia de execução.

## 2. Estrutura de Log Padrão

Todo output de log deve ser encapsulado em um bloco YAML ou JSON dentro dos arquivos de artefato ou streams de comunicação, seguindo este schema:

```yaml
log_entry:
  timestamp: "ISO8601"
  trace_id: "uuid-da-demanda-original"
  span_id: "uuid-da-acao-atual"
  agent: "AgentName"
  type: "[DECISION | ACTION | ERROR | INFO | THOUGHT]"
  
  # Contexto crítico
  context:
    current_state: "StateName"
    iteration: 0
  
  # O conteúdo principal do log
  payload:
    description: "Texto legível por humanos"
    rationale: "Explicação do raciocínio (CoT) para esta ação"
    data: {} # Dados técnicos relevantes (diffs, argumentos, etc)
```

## 3. Tipos de Log Obrigatórios

### 3.1. THOUGHT (Raciocínio)
Obrigatório antes de qualquer ação que altere arquivos ou estado. Deve capturar o monólogo interno do agente.

*Exemplo:*
```yaml
type: THOUGHT
payload:
  rationale: "Identifiquei um erro de sintaxe no arquivo main.py linha 40. O erro ocorre porque a variável 'user' não foi inicializada. Planejo adicionar uma verificação de nulidade antes do acesso."
```

### 3.2. DECISION (Decisão)
Registra bifurcações no fluxo. Obrigatório quando o agente opta entre múltiplas alternativas viáveis.

*Exemplo:*
```yaml
type: DECISION
payload:
  description: "Escolha de Framework de Teste"
  rationale: "Optei pelo Pytest em vez do Unittest devido à necessidade de fixtures complexas citadas nos requisitos."
  alternatives_considered: ["Unittest", "Nose2"]
```

### 3.3. ACTION (Ação)
Registra a execução efetiva de uma ferramenta ou comando.

*Exemplo:*
```yaml
type: ACTION
payload:
  tool: "write_to_file"
  target: "src/utils.py"
  status: "SUCCESS"
```

## 4. Health Checks e Monitoramento

Os agentes devem ser capazes de responder a um comando de `/status` com um report de saúde:

**Health Report Schema:**
```yaml
agent_health:
  status: "[HEALTHY | DEGRADED | CRITICAL]"
  memory_usage: "Percentual estimado da janela de contexto usada"
  last_error: "Timestamp e mensagem do último erro (se houver)"
  active_task: "ID da tarefa atual ou null"
```

## 5. Auditoria de Falhas (Post-Mortem)

Sempre que um fluxo for abortado ou rejeitado pelo Orquestrador, um log de `ERROR` deve ser gerado contendo:
1.  **Root Cause Analysis (RCA)**: Hipótese do agente sobre por que falhou.
2.  **Self-Correction Plan**: O que o agente faria diferente na próxima vez.

## 6. Implementação nos Agentes

Todos os prompts de sistema (System Prompts) devem incluir a seguinte diretriz:

> "CRÍTICO: Mantenha observabilidade total. Antes de cada uso de ferramenta complexa, gere um log do tipo THOUGHT explicando seu plano. Ao finalizar, gere um log do tipo ACTION com o resultado."
