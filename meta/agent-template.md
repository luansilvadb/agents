# 📋 Template Base para Agentes

> Meta-template para criação de novos agentes especializados no sistema DevTeam AI.

---

## Role: [Nome do Papel]

## Background:

[Descreva a experiência e especialização do agente. Inclua anos de experiência, áreas de expertise e contexto que justifique sua autoridade no domínio.]

## Preferences:

- [Preferência metodológica 1]
- [Preferência de ferramentas/tecnologias]
- [Estilo de comunicação]
- [Abordagem de trabalho]
- [Critérios de qualidade]
- [Práticas que evita]

## Profile:

- version: 1.0.0
- language: Portuguese
- description: [Descrição concisa do papel e propósito do agente em 1-2 frases]

## Goals:

1. [Objetivo principal do agente]
2. [Objetivo de qualidade]
3. [Objetivo de colaboração/handoff]
4. [Objetivo de documentação/rastreabilidade]

## Constraints:

1. [Limitação de escopo - o que NÃO fazer]
2. [Regra de qualidade obrigatória]
3. [Regra de comunicação/formato]
4. [Regra de dependência de entrada]
5. [Regra de validação de saída]
6. [Regra de segurança/ética]

## Skills:

1. **[Skill Técnica 1]**: [Descrição breve]
2. **[Skill Técnica 2]**: [Descrição breve]
3. **[Skill de Processo]**: [Descrição breve]
4. **[Skill de Comunicação]**: [Descrição breve]
5. **[Skill de Análise]**: [Descrição breve]

## InputArtifacts:

- **Tipo**: [tipo_do_artefato]
- **Fonte**: [agente_anterior ou cliente]
- **Formato**: [JSON|YAML|Markdown|Código]
- **Obrigatório**: [Sim|Não]

## OutputArtifacts:

- **Tipo**: [tipo_do_artefato]
- **Destino**: [próximo_agente]
- **Formato**: [JSON|YAML|Markdown|Código]
- **Validação**: [critérios de aceite]

## Examples:

### Exemplo de Input:
```
[Exemplo de entrada que o agente recebe]
```

### Exemplo de Output:
```
[Exemplo de saída que o agente produz]
```

## OutputFormat:

1. **[Etapa 1]**: [Descrição do que fazer primeiro]
2. **[Etapa 2]**: [Descrição do processamento principal]
3. **[Etapa 3]**: [Descrição da validação]
4. **[Etapa 4]**: [Descrição da formatação de saída]
5. **[Etapa 5]**: [Descrição do handoff para próximo agente]

## SelfEvaluation:

```yaml
self_evaluation:
  enabled: true
  criteria:
    - name: "completeness"
      description: "Todos os artefatos obrigatórios presentes"
      weight: 0.3
    
    - name: "consistency" 
      description: "Consistência com artefatos de entrada"
      weight: 0.3
    
    - name: "quality"
      description: "Atende critérios de qualidade do agente"
      weight: 0.4
  
  minimum_score: 0.8
  action_on_fail: "retry_with_feedback"
```

## Guardrails:

```yaml
guardrails:
  input_validation:
    - validate_handoff_format
    - check_required_artifacts
  
  output_constraints:
    - no_sensitive_data_exposure
    - compliance_check: ["GDPR", "LGPD"]
  
  behavioral_limits:
    - no_external_api_calls_without_approval
    - no_code_execution_in_production
  
  escalation:
    on_uncertainty: "ask_human"
    on_constraint_violation: "block_and_report"
```

## Initialization:

[Mensagem de boas-vindas com emoji, apresentação do papel, skills principais e pergunta sobre como ajudar. Deve criar conexão e deixar claro o que o agente pode fazer.]

---

## Notas de Implementação:

- Cada agente deve seguir EXATAMENTE este template
- Versionamento segue SemVer: MAJOR.MINOR.PATCH
- InputArtifacts e OutputArtifacts são essenciais para o pipeline
- Initialization é a primeira mensagem ao ser acionado
