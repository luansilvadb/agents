---
description: Criar novo agente especialista usando o template base
---

# 🆕 Criar Novo Agente

Cria um arquivo de agente seguindo o padrão V3.0 e um workflow associado.

## Template V3.0

Para criar um novo agente, utilize o template abaixo e salve em `specialists/NN-nome_agente.md`.

```markdown
# [Emoji] Agente [Nome]

## Role: [Role Principal]

## Background:
[Experiência e filosofia]

## Preferences:
- [Preferências]

## Profile:
- version: 3.0
- language: Portuguese
- description: [Passo e função no pipeline]

## Goals:
1. [Objetivo 1]
2. [Objetivo 2]

## Constraints:
1. [Restrição 1]
2. [Restrição 2]

## Skills:
1. **[Skill]**: [Descrição]

## Toolbelt:
### Sequential Thinking
- Ferramenta: `mcp_sequential-thinking_sequentialthinking`
- Uso: [Para que usar]

## InputArtifacts:
- **Tipo**: [`artifact_name`]
- **Fonte**: [Agente Anterior]
- **Formato**: Markdown
- **Obrigatório**: Sim

## OutputArtifacts:
- **Tipo**: [`artifact_name`]
- **Destino**: [Próximo Agente]
- **Formato**: Markdown
- **Validação**: [Critérios]

## OutputFormat:
1. [Passo 1]
2. [Passo 2]

## Initialization:
Olá! Sou o **[Agente]**. [Emoji]
[Frase de impacto]
**[Pergunta de início?]**
```

## Workflows

Lembre-se de criar também o arquivo de workflow em `.agent/workflows/nome.md`:

```markdown
---
description: [Descrição Curta]
---

# [Emoji] [Nome do Comando]

Aciona o **[Agente]** para [Ação].

## Execução

```bash
agent run specialists/NN-nome_agente.md
```
```
